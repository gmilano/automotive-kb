---
industry: automotive
region: Global
updated: 2026-10-26
---

# 🧩 Composition patterns — Automotive

> Concrete recipes: named repos, named wiring, stated assumptions. Every repo referenced here is verified
> in `repos/foundations.md` or `agents/top.md` (URL probed live 2026-10-26).
> **New this pass: P7 (S-CORE safety-core engagement) and P8 (USMCA rules-of-origin traceability).**
> P3 and P6 were revised — P3 gains the S-CORE core and the published blueprint, P6 gains a licence
> correction and a small-model option.

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
   (Apache-2.0, 528★): open-loop rollouts of the current policy over real logs surface failure-prone
   scenarios automatically. This step replaces a manual triage team.
2. **Reconstruct** — WorldEngine's 3D Gaussian Splatting stage rebuilds each failure scene as a
   simulatable asset.
3. **Formalise as scenarios** — export to ASAM OpenSCENARIO; execute with
   [esmini/esmini](https://github.com/esmini/esmini) (MPL-2.0) for lightweight CI runs and
   [carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) (MIT) on
   [carla-simulator/carla](https://github.com/carla-simulator/carla) (MIT, 14.5k★) for full sensor
   simulation.
4. **Evaluate policies closed-loop** — [NVlabs/alpasim](https://github.com/NVlabs/alpasim) (Apache-2.0,
   1.3k★) with [NVlabs/alpagym](https://github.com/NVlabs/alpagym) (Apache-2.0, 163★) for RL refinement.
5. **Gate the merge** — every mined scenario becomes a permanent regression case; policy changes must not
   regress the suite.

🆕 **Sharpened sales angle:** **NHTSA is now explicitly assessing AI training and validation strategies
within ADS**, and a **national AV performance standard is in development** (3-year, $5M SAE ITC
partnership). This pipeline stops being an engineering nicety and becomes the artefact a regulator asks
for. Lead with that, not with the tooling.

**Estimate:** 8–10 weeks to a working pipeline on a client's own logs; the long pole is log ingestion and
sensor-config matching, not the models.
**Licence note:** fully permissive end to end. Safe for a proprietary client deliverable.

---

## P2 — Warranty & aftersales claim agent

**Region fit:** North America (43% dealer AI adoption), EMEA.
**Problem:** warranty claims are validated by hand against repair orders and OEM rules; error rates and
cycle times are both high, and fraud detection is retrospective.

**Wiring:**
1. **No open base exists** — confirmed again this pass. There is **no open-source DMS**, and the
   open-source *repair-shop* managers are tiny, GPL or archived (see `verticals/solutions.md`). Integrate
   against the client's **CDK / Reynolds & Reynolds / Tekion / DealerSocket** at VIN level. Budget the API
   access negotiation explicitly as its own line item.
2. **Orchestrate** with a general-purpose framework — **LangGraph** (MIT) is the right shape: a state
   machine, not a free-running loop, because each claim step must be replayable for audit.
3. **RAG corpus**: service manuals, OEM warranty policy, TSBs, labour-time guides. Keep the retrieval index
   **versioned** — a claim decision must be reproducible against the policy text *as it stood that day*.
4. **Tools, not prose**: `check_eligibility(vin, component, date)`, `fetch_repair_order(ro_id)`,
   `validate_against_oem_rules(claim)`, `flag_anomaly(claim)`. Deterministic where the rule is
   deterministic; the model routes and explains, it does not adjudicate.
5. **Human gate** — the "Technician-in-the-Loop" pattern: low-confidence or high-value claims route to a
   warranty administrator with the model's cited evidence. **Never auto-submit.**
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

## P3 — Sovereign SDV stack + AI Act evidence pipeline *(revised)*

**Region fit:** EMEA. Highest-margin pattern in this KB.
**Problem:** an OEM must satisfy EU AI Act governance duties (technical file, post-market monitoring,
serious-incident pipeline, human oversight, data quality) *and* UNECE R156 software-update traceability,
across suppliers, without shipping vehicle data to a third-party cloud.

**Wiring:**
1. **Signal vocabulary** — [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification)
   (MPL-2.0, 451★), with [COVESA/vss-tools](https://github.com/COVESA/vss-tools) for generation. Every
   signal carries its VSS name; that is what makes supplier data comparable and the technical file coherent.
2. **In-vehicle data layer** — [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker)
   (Apache-2.0, 82★, Rust, gRPC, 0.6.1, Quarkslab-audited); prototype against it with
   [eclipse-kuksa/kuksa-python-sdk](https://github.com/eclipse-kuksa/kuksa-python-sdk).
3. 🆕 **Platform core** — [eclipse-score/score](https://github.com/eclipse-score/score) (Apache-2.0, 111★,
   `v0.7.3` 07 Oct 2026). Use it where the client needs an **ASIL-B-targeted** core rather than a bare data
   broker. Pair with [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) for deterministic
   fixed execution order, and lift `eclipse-score/process_description` into the client's own safety
   argument instead of writing one from scratch.
4. **On-vehicle orchestration** — [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios)
   (Apache-2.0, 125★) for workloads on automotive HPCs where Kubernetes does not fit.
5. 🆕 **Start from the published topology, not a diagram** —
   [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management)
   (Apache-2.0, 27★) already wires Kuksa CSV Provider → Databroker → FMS Forwarder → **Eclipse uProtocol**
   → FMS Consumer → InfluxDB → Grafana, with an **rFMS API** server. Stand it up in week 1 as the
   reference, then replace the CSV provider with the client's real signal source. This removes ~2 weeks of
   architecture debate from the front of the project.
6. **Evidence pipeline** (the billable part): every model version, dataset version, VSS signal schema,
   update campaign and incident writes to an append-only store that renders the AI Act technical file and
   the R156 update log **as a generated artefact, not a hand-written document**. Map controls to
   ISO/PAS 8800 alongside ISO 26262 and ISO 21448/SOTIF — it complements them, it does not replace them,
   and the AI Act does not displace ISO/SAE 21434, UN R155 or UN R156 either.
7. Self-hosted throughout, which answers data-residency objections directly.

🆕 **Procurement answer to have ready:** if asked "who supports this?", the Eclipse SDV ↔ VDA memorandum
covers **32 companies**, **Hyundai Mobis** joined in May 2026, and founding member **Qorix** sells a
commercial distribution built on S-CORE. "Unsupported open source" is not a valid objection here.

**Estimate:** 10–14 weeks for the data layer + evidence pipeline on one vehicle programme; add 3–4 weeks if
the S-CORE core is in scope rather than Kuksa alone.
**⚠️ Scope caveat:** confirm the applicable AI Act date before contracting. General application is
2 Aug 2026, safety-component AI appears to start Aug 2027, and one source cites 2 Dec 2027 for standalone
Annex III systems — unverified against the Official Journal. 🆕 Also confirm whether the programme must
answer **UN GTR No. 26 / UN Regulation No. 185** (ADS, adopted 24 Jun 2026) — verify the numbering against
UNECE directly. See `intel/market.md` → EMEA.

---

## P4 — Multi-jurisdiction policy layer *(revised)*

**Region fit:** APAC.
**Problem:** one vehicle programme sells into China, Japan, South Korea and India and faces four different
AI/AV regimes — and 🆕 **two of them became binding in 2026**: **Korea's AI Basic Act took effect
22 Jan 2026**, and **China issued mandatory standards for combined driving assistance and automated
driving** (reported Jul 2026, with a mandatory L3/L4 standard reported for 1 Jul 2027 — unverified).
Japan requires **remote monitoring for all Level 4**. India's **AIS 140** telematics mandate and
**BNCAP 2.0** ADAS expectations apply. Vietnam's Digital Technology Industry Law lands from 2026.

**Wiring:**
1. **Policy as configuration, not code.** One rule set per market, versioned, each rule naming the
   instrument it derives from. Resist encoding jurisdiction rules as `if` statements in feature code.
2. 🆕 **Model the global baseline separately from the national deltas.** With **UN GTR No. 26** adopted by
   Canada, China, the EU, Japan, the UK and the US, the honest structure is one baseline rule set plus a
   per-market delta — not four independent rule sets. This is a real reduction in maintenance surface, and
   it is new as of June 2026.
3. **Evaluate at runtime** in a LangGraph (MIT) policy node between the driving/feature policy and
   actuation: given market + vehicle state + feature request, return allow / degrade / deny **plus the
   citation**.
4. **Feature degradation, not feature flags** — the same binary ships everywhere and degrades per market
   (e.g. L3 hand-off permitted in Japan, denied elsewhere). 🆕 Note that OEM autonomy ladders are diverging
   even as regulation centralises — **XPeng has said it will "skip L3"** — so do not assume the rule schema
   can key on SAE level alone.
5. **Telematics compliance** — for India's AIS 140, build on
   [traccar/traccar](https://github.com/traccar/traccar) (Apache-2.0, 7.9k★, 200+ device protocols) rather
   than licensing a proprietary stack.
6. **Evidence trail** shared with P3 — the same append-only store serves both regimes.

🆕 **Second buyer in this region:** Korea's AI Basic Act imposes **governance duties on high-impact AI in
sensitive sectors**, and its decree and ministry guidelines are **interpretive rather than binding** — so
the conformity *interpretation* is billable work, exactly as it is in EMEA.

**Estimate:** 12–14 weeks for four markets; each additional market ~2 weeks once the rule schema exists.

---

## P5 — LGPD-compliant fleet telematics (and pilot industrialisation)

**Region fit:** LATAM — Brazil and Mexico specifically.
**Problem:** LATAM automotive AI is at pilot stage with limited, uneven adoption. 🆕 **This pass verified
that neither Brazil nor Mexico has an AI law in force** (Brazil's PL 2338/2023 is stalled in the Câmara,
last movement 2 Sep 2026; Mexico has 85 initiatives since Apr 2023 with 67 pending). **So the compliance
hook is data protection, not AI regulation:** **LGPD** applies as soon as video, audio, driver identity,
vehicle or location data can identify a person, and **Anatel** certification is required before selling
AI-enabled vehicle devices such as dashcams.

**Wiring:**
1. **Base** — [traccar/traccar](https://github.com/traccar/traccar) (Apache-2.0), **self-hosted
   in-country**. Its multi-tenant user/permission model already supports several client accounts on one
   server.
2. **LGPD layer as a first-class feature, not a policy PDF**: per-subject data inventory, retention
   windows, deletion and access-request endpoints, driver-identity pseudonymisation at ingest. Keep raw
   video out of the primary store; reference it.
3. **Edge inference** for dashcam/driver-monitoring so video need not leave the vehicle — which also eases
   the Anatel-certified-device constraint.
4. **Agent layer**: route optimisation, predictive maintenance from OBD/CAN signals via
   [commaai/opendbc](https://github.com/commaai/opendbc) (MIT, 3.5k★) +
   [cantools/cantools](https://github.com/cantools/cantools) (MIT), driver-coaching summaries.
5. **For Mexico's manufacturing base**, the P3 evidence-pipeline machinery applies to production-line AI —
   the region's strongest near-term fit, not retail AV.

**Estimate:** 6–8 weeks to a self-hosted LGPD-defensible deployment.
**⚠️ Pitch correction:** do **not** sell "AI Act-style compliance" here. There is no AI law to comply with
in Brazil or Mexico yet, and a client can check that in an afternoon. Sell LGPD/Anatel, and sell P8.

---

## P6 — Teacher→student distillation from an open VLA *(revised)*

**Region fit:** Global.
**Problem:** NVIDIA publishes Alpamayo Apache-2.0 but positions it as a **teacher model, not in-car
software**, and Alpamayo 1 Nano alone needs a GPU with ≥24 GB VRAM. The gap between "free weights" and
"runs on the target ECU" is the engagement.

**Wiring:**
1. **Start from the current practical head** — [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5)
   (Apache-2.0 code, 370★). **Not** [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo), which now
   carries an explicit limited-maintenance banner. 🆕 Reach for
   [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) (Apache-2.0, 287★, **34B** = 32B VLM + 2B
   diffusion expert) only as the teacher — it is too large to be the student.
2. 🆕 **Consider a small open alternative for the student or for feasibility work** —
   [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) (Apache-2.0, 824★, AAAI 2026) ships a
   **0.5B checkpoint on Hugging Face**. Two orders of magnitude smaller than Alpamayo 2, which makes
   on-target experiments and client demos possible without a GPU budget.
3. **Use the published recipes** — [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes)
   (Apache-2.0, 217★). Verified recipe set: **Alpamayo 1 SFT** and **1.5 SFT** (HF Trainer + DeepSpeed),
   **1.x RL post-training** (Cosmos-RL + GRPO), and **1.5 quantization** via the Model Optimizer Toolkit
   covering **FP8 and NVFP4+FP8 mixed precision**. The quantization recipe is the one that matters for
   target hardware.
4. **Fine-tune on client fleet data**; keep the reasoning traces — they are the Chain-of-Causation output
   and double as the explainability artefact the AI Act's transparency duty wants.
5. **Validate closed-loop** on AlpaSim + AlpaGym, and feed failures into **P1** so distillation regressions
   are caught automatically.
6. **Distil to a deployable student** sized for the target SoC; keep the teacher off-board for continued
   post-training.

🔴 🆕 **Licence correction — this one can sink a deliverable.** The Alpamayo 1.5 repository is Apache-2.0,
**but its README states the model weights are under `OpenMDW-1.1`.** Code licence ≠ weight licence. Read
OpenMDW-1.1 before distributing fine-tuned derivatives, and never infer a checkpoint's terms from the
repository badge. The previous version of this pattern recorded Apache-2.0 for both.

**⚠️ Data licence trap (unchanged):** do **not** train on
[OpenDriveLab/DriveLM](https://github.com/OpenDriveLab/DriveLM) language data for a commercial deliverable
— code is Apache-2.0, language data is **CC BY-NC-SA 4.0 (non-commercial)**. The same split applies to most
AV datasets: check the code licence and the dataset licence separately, every time.

**Estimate:** 10–12 weeks to a validated quantized student on representative hardware.

---

## P7 🆕 — ASIL-B safety-core engagement on Eclipse S-CORE

**Region fit:** EMEA primarily (VDA-backed, German OEM bloc), APAC secondarily (Hyundai Mobis joined the
SDV Working Group in May 2026).
**Problem:** an OEM or Tier-1 has an SDV roadmap and a functional-safety obligation, and is choosing between
building a proprietary middleware core, buying one, or adopting the open one. The open one now exists, has
a release cadence, and has a commercial distribution behind it — but almost no consultancy knows it.

**Wiring:**
1. **Pin a release and read the process first.** [eclipse-score/score](https://github.com/eclipse-score/score)
   (Apache-2.0, 111★) ships roughly monthly — `v0.5.5` (26 Apr) through `v0.7.3` (07 Oct 2026). Pin a tag;
   do not track `main` in a programme with a safety argument.
2. **Lift the published process.** `eclipse-score/process_description` publishes the project's development
   process as a repository. Map the client's existing ISO 26262 process onto it and **record the deltas** —
   that gap analysis is the first deliverable and it is the one that de-risks everything after it.
3. **Language and toolchain decision.** `0.6.0` brought full **C++ and Rust** support including the
   **Ferrocene** safety-critical Rust toolchain. For a greenfield component, Rust-plus-Ferrocene is now a
   defensible choice in a safety context — that was not true 18 months ago. Make the call explicitly and
   write down why.
4. **Determinism** — [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) (Apache-2.0, 7★)
   provides the fixed execution order framework. It is an *incubation* repository at 7 stars: treat it as
   a design input and a contribution target, **not** as a dependency you would ship against unexamined.
5. **Contribute the client's component back through `eclipse-score/module_template`.** This is a
   positioning play as much as an engineering one: a client whose module is upstream is a client whose
   platform risk is shared with 32 VDA companies.
6. **Integration testing** — `eclipse-score/itf` is the project's own test framework; wire the client's
   evidence pipeline (P3 step 6) to its output so test evidence lands in the technical file automatically.

**⚠️ Three caveats to state in writing, before anyone signs:**
- **ASIL-B is a design target, not a certification.** Say this explicitly. A client who hears
  "ASIL-B certified" from us and discovers otherwise has a legitimate grievance.
- **The 1.0 date is contested:** the Eclipse project page lists v1.0.0 at **2026-12-14**, the newsroom says
  a full release is planned for 2026 targeting programmes reaching market by 2030, and an ETAS presentation
  says a complete solution is on track for **2028**. Plan against the pinned release you tested, not a
  roadmap date.
- **Secondary-source dates conflict with the repository.** Trade press puts 0.6.0 in Feb 2026 and 0.7.0 in
  May 2026; the GitHub releases page says 26 Jun and 24 Aug. **Use the releases page.**

**Estimate:** 4–6 weeks for the process gap analysis and a pinned-release build on client hardware; 12–16
weeks to a first upstreamed module with test evidence flowing into the P3 pipeline.
**Licence note:** Apache-2.0 throughout, with the Eclipse caveat that some sources/binaries may carry
different terms — verify per module before shipping.

---

## P8 🆕 — USMCA rules-of-origin traceability (LATAM / North America)

**Region fit:** LATAM (Mexico) and North America — this is the one LATAM offering with a dated deadline
behind it rather than a projection.
**Problem:** Mexico **removed the 10% auto-parts import tariff for five years effective 14 October 2026**
(limited to terminal automakers under authorised fiscal-warehouse status), and the **2026 USMCA review** is
expected to **raise regional value-content thresholds for autos**. Nearshoring that still depends on
Chinese sub-components may lose duty-free access. Proving regional content then becomes a
component-level evidence problem across suppliers — which is the same machine as an AI Act technical file,
pointed at trade compliance.

**Wiring:**
1. **Reuse the P3 evidence pipeline wholesale.** Append-only store, versioned schema, generated artefact.
   The only thing that changes is what the artefact renders: a rules-of-origin certification instead of a
   technical file.
2. **Component-level provenance per VIN.** Model part → supplier → origin → value, versioned, with the
   USMCA rule applied at query time rather than baked into the record. Thresholds are expected to move;
   a record that has a threshold baked in is a record you re-ingest after the review.
3. **ERP base, permissive** — [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework)
   (Apache-2.0, 1.1k★) carries supply-chain and manufacturing resource planning and is the most permissive
   full ERP base in this KB. Avoid Odoo here (**LGPL-3.0**) if the deliverable is a hosted proprietary
   product.
4. **Agent layer where it earns its place**: classify and reconcile supplier declarations against bills of
   materials, flag components whose origin evidence is missing or stale, draft the certification narrative
   with citations back to the underlying records.
5. **Human gate, non-negotiable.** A rules-of-origin certification is a legal attestation. The model
   assembles evidence and drafts; a customs-compliance specialist signs. Same architecture as P2's
   technician gate, higher stakes.
6. **Plant-floor extension.** The same store serves production-line AI evidence for Mexican manufacturing
   (P5 step 5) — one pipeline, two buyers inside the same client.

**⚠️ Evidence caveat:** the tariff decree (14 Oct 2026), the FDI figures (~$41B over the first three
quarters of 2025, +15% YoY; record $40.87B for 2025) and the expectation of higher RVC thresholds come from
trade and business press, **not from the USMCA review text**. The review's actual outcome is not knowable
from this pass's sources. Scope phase 1 as traceability infrastructure that is useful at any threshold —
**do not scope deliverables against a specific future RVC number.**

**Estimate:** 8–10 weeks for provenance modelling + evidence pipeline on one vehicle line; the second line
is ~2 weeks once the supplier-declaration connectors exist.

---
*Eight patterns, 2026-10-26. Effort estimates are planning figures for a studio team, not quotes.
P7 and P8 are new this pass; P3, P4, P5 and P6 were revised against findings dated after 2026-10-15.*
