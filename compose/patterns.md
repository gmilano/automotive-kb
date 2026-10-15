---
industry: automotive
region: Global
updated: 2026-10-15
---

# 🧩 Composition patterns — Automotive

> Concrete recipes: named repos, named wiring, stated assumptions. Every repo referenced here is verified
> in `repos/foundations.md` or `agents/top.md` (URL, licence, stars checked 2026-10-15).
> **The previous version of this file contained one empty template** ("Receta 1: [Por definir]", all
> fields `—`). Replaced with six buildable patterns.

## Base shape

```
[Open vertical base or in-vehicle data layer]
            ↓  (domain exposed as typed tools / MCP, named in VSS where vehicle-shaped)
[Agent orchestration + RAG over service/regulatory corpus]
            ↓  (confidence scoring)
[HUMAN GATE — mandatory for anything that actuates a vehicle or commits money]
            ↓
[Conversational UI / API + immutable evidence trail]
```

The human gate and the evidence trail are not optional extras: the gate is what makes the EU AI Act's
"human oversight" requirement demonstrable, and the trail is what makes post-market monitoring auditable.
Build both in from day one — retrofitting them is the expensive path.

---

## P1 — Scenario regression factory (closed-loop AV validation)

**Region fit:** North America primarily (test-mile volume + per-state reporting), EMEA secondarily.
**Problem:** fleets generate millions of log miles; failures are rediscovered manually and never become
regression tests.

**Wiring:**
1. **Mine failures** — [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine)
   (Apache-2.0): run open-loop rollouts of the current policy over real logs to surface failure-prone
   scenarios automatically. This is the step that replaces a manual triage team.
2. **Reconstruct** — WorldEngine's 3D Gaussian Splatting stage rebuilds each failure scene as a
   simulatable asset.
3. **Formalise as scenarios** — export to ASAM OpenSCENARIO; execute with
   [esmini/esmini](https://github.com/esmini/esmini) (MPL-2.0) for lightweight CI runs and
   [carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) (MIT) on
   [carla-simulator/carla](https://github.com/carla-simulator/carla) (MIT) for full sensor simulation.
4. **Evaluate policies closed-loop** — [NVlabs/alpasim](https://github.com/NVlabs/alpasim) (Apache-2.0)
   with [NVlabs/alpagym](https://github.com/NVlabs/alpagym) (Apache-2.0) for RL refinement.
5. **Gate the merge** — every mined scenario becomes a permanent regression case; policy changes must not
   regress the suite.

**Estimate:** 8–10 weeks to a working pipeline on a client's own logs; the long pole is log ingestion and
sensor-config matching, not the models.
**Licence note:** fully permissive end to end. Safe for a proprietary client deliverable.

---

## P2 — Warranty & aftersales claim agent

**Region fit:** North America (43% dealer AI adoption), EMEA.
**Problem:** warranty claims are validated by hand against repair orders and OEM rules; error rates and
cycle times are both high, and fraud detection is retrospective.

**Wiring:**
1. **No open base exists** — there is no open-source DMS (see `verticals/solutions.md`). Integrate against
   the client's **CDK / Reynolds & Reynolds / Tekion / DealerSocket** at VIN level. Scope this as
   integration work, and budget the API access negotiation explicitly.
2. **Orchestrate** with a general-purpose agent framework — **LangGraph** (MIT) is the right shape here: a
   state machine, not a free-running loop, because each claim step must be replayable for audit.
3. **RAG corpus**: service manuals, OEM warranty policy, TSBs, labour-time guides. Keep the retrieval index
   versioned — a claim decision must be reproducible against the policy text *as it stood that day*.
4. **Tools, not prose**: `check_eligibility(vin, component, date)`, `fetch_repair_order(ro_id)`,
   `validate_against_oem_rules(claim)`, `flag_anomaly(claim)`. Deterministic where the rule is
   deterministic; the model routes and explains, it does not adjudicate.
5. **Human gate** — the "Technician-in-the-Loop" pattern: low-confidence or high-value claims route to a
   warranty administrator with the model's cited evidence. Never auto-submit.
6. **Fraud layer**: anomaly detection over claim patterns per dealer/technician/component as a separate
   batch model, not inside the per-claim agent.

**Reference architecture to read (do not reuse):**
[Hemanth-N-code/Connected-Car-AI-Support-Agent](https://github.com/Hemanth-N-code/Connected-Car-AI-Support-Agent)
implements almost exactly this shape — LangGraph routing over CRM + telematics + subscription data, ChromaDB
RAG over service manuals, confidence scoring, technician sign-off before OTA actions. **It carries no
licence** (README badge: "Academic Evaluation") and its data sources are mock JSON. Read the design; write
your own code.

**Estimate:** 6–8 weeks per DMS integration; the second dealer group is ~2 weeks once one connector exists.

---

## P3 — Sovereign SDV data layer + AI Act evidence pipeline

**Region fit:** EMEA. Highest-margin pattern in this KB.
**Problem:** an OEM must satisfy EU AI Act governance duties (technical file, post-market monitoring,
serious-incident pipeline, human oversight, data quality) *and* UNECE R156 software-update traceability,
across suppliers, without shipping vehicle data to a third-party cloud.

**Wiring:**
1. **Signal vocabulary** — [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification)
   (MPL-2.0). Every signal in the system carries its VSS name. This is what makes supplier data comparable
   and the technical file coherent.
2. **In-vehicle data layer** — [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker)
   (Apache-2.0, Rust, gRPC, 0.6.1 + security-audited): maps low-level signals onto VSS data points,
   containerised.
3. **On-vehicle orchestration** — [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios)
   (Apache-2.0) for workload management on automotive HPCs where Kubernetes does not fit.
4. **Transport** — Zenoh between Kuksa and off-board services, per the
   [eclipse-sdv-blueprints](https://github.com/eclipse-sdv-blueprints) service-to-signal reference topology.
   Do not invent this topology; it is published.
5. **Evidence pipeline** (the billable part): every model version, dataset version, VSS signal schema,
   update campaign and incident writes to an append-only store that renders the AI Act technical file and
   the R156 update log **as a generated artefact, not a hand-written document**. Map controls to
   ISO/PAS 8800 alongside ISO 26262 and ISO 21448/SOTIF — it complements them, it does not replace them.
6. Self-hosted throughout, which answers data-residency objections directly.

**Estimate:** 10–14 weeks for the data layer + evidence pipeline on one vehicle programme.
**⚠️ Scope caveat:** confirm the applicable AI Act date before contracting. General application is
2 Aug 2026, but safety-component AI appears to start Aug 2027 and one source cites 2 Dec 2027 for
standalone Annex III systems — unverified against the Official Journal. See `intel/market.md` → EMEA.

---

## P4 — Multi-jurisdiction policy layer

**Region fit:** APAC.
**Problem:** one vehicle programme sells into China, Japan, South Korea and India and faces four different
AI/AV regimes — Beijing/Shanghai driverless licensing, Japan's L3 framework, Korea's AI Basic Act (2026),
India's AIS 140 telematics mandate — plus Vietnam's Digital Technology Industry Law (2026).

**Wiring:**
1. **Policy as configuration, not code.** One rule set per market, versioned, each rule naming the
   instrument it derives from. Resist encoding jurisdiction rules as `if` statements in feature code.
2. **Evaluate at runtime** in a LangGraph (MIT) policy node sitting between the driving/feature policy and
   actuation: given market + vehicle state + feature request, return allow / degrade / deny **plus the
   citation**.
3. **Feature degradation, not feature flags** — the same binary ships everywhere and degrades per market
   (e.g. L3 hand-off permitted in Japan, denied elsewhere).
4. **Telematics compliance** — for India's AIS 140, build on
   [traccar/traccar](https://github.com/traccar/traccar) (Apache-2.0, 200+ device protocols) rather than
   licensing a proprietary stack.
5. **Evidence trail** shared with P3 — the same append-only store serves both regimes.

**Estimate:** 12–14 weeks for four markets; each additional market ~2 weeks once the rule schema exists.

---

## P5 — LGPD-compliant fleet telematics (and pilot industrialisation)

**Region fit:** LATAM — Brazil and Mexico specifically.
**Problem:** per `intel/market.md`, LATAM automotive AI is at pilot stage with limited, uneven adoption, and
the concrete regulatory hooks are **Anatel device certification** and **LGPD** (which applies as soon as
video, audio, driver identity, vehicle or location data can identify a person). Proprietary fleet vendors
handle data residency and LGPD subject rights poorly.

**Wiring:**
1. **Base** — [traccar/traccar](https://github.com/traccar/traccar) (Apache-2.0), **self-hosted in-country**.
   Its multi-tenant user/permission model already supports several client accounts on one server.
2. **LGPD layer as a first-class feature, not a policy PDF**: per-subject data inventory, retention
   windows, deletion and access-request endpoints, and driver-identity pseudonymisation at ingest. Keep raw
   video out of the primary store; reference it.
3. **Edge inference** for dashcam/driver-monitoring so video need not leave the vehicle — which also eases
   the Anatel-certified-device constraint.
4. **Agent layer**: route optimisation, predictive maintenance from OBD/CAN signals via
   [commaai/opendbc](https://github.com/commaai/opendbc) (MIT) +
   [cantools/cantools](https://github.com/cantools/cantools) (MIT), driver-coaching summaries.
5. **For Mexico's manufacturing base**, the same evidence-pipeline machinery from P3 applies to
   production-line AI — this is the region's strongest near-term fit, not retail AV.

**Estimate:** 6–8 weeks to a self-hosted LGPD-defensible deployment.
**⚠️ Evidence caveat:** this pattern is built on a **declared research gap** — no 2026 LATAM-specific
automotive AI analysis was found. The regulatory hooks (Anatel, LGPD) are solid; the market sizing behind
them is not. Validate demand with the client before building.

---

## P6 — Teacher→student distillation from an open VLA

**Region fit:** Global.
**Problem:** NVIDIA publishes Alpamayo Apache-2.0 but positions it as a **teacher model, not in-car
software**, and Alpamayo 1 Nano alone needs a GPU with ≥24 GB VRAM. The gap between "free weights" and
"runs on the target ECU" is the engagement.

**Wiring:**
1. **Start from the current head** — [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5)
   (Apache-2.0). **Not** [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo), which is explicitly in
   limited maintenance.
2. **Use the published recipes** — [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes)
   (Apache-2.0) covers fine-tuning, RL post-training, **quantization and deployment**. The quantization
   recipe is the one that matters for target hardware.
3. **Fine-tune on client fleet data**; keep the reasoning traces — they are the Chain-of-Causation output
   and double as the explainability artefact the AI Act's transparency duty wants.
4. **Validate closed-loop** on AlpaSim + AlpaGym, and feed failures into **P1** so distillation regressions
   are caught automatically.
5. **Distil to a deployable student** sized for the target SoC; keep the teacher off-board for continued
   post-training.

**Estimate:** 10–12 weeks to a validated quantized student on representative hardware.
**⚠️ Data licence trap:** do **not** train on [OpenDriveLab/DriveLM](https://github.com/OpenDriveLab/DriveLM)
language data for a commercial deliverable — the code is Apache-2.0 but the language data is
**CC BY-NC-SA 4.0 (non-commercial)**. The same split applies to most AV datasets: check the code licence
and the dataset licence separately, every time.

---
*Six patterns, 2026-10-15. Effort estimates are planning figures for a studio team, not quotes.*
