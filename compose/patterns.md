---
industry: automotive
region: Global
updated: 2026-11-19
---

# 🧩 Composition patterns — Automotive

> Concrete recipes: named repos, named wiring, stated assumptions. Every repo referenced here is verified
> in `repos/foundations.md` or `agents/top.md` (URL probed live 2026-10-26).
> **New on 2026-11-19: P14 (assurance artefact factory), P15 (vehicle-agent evaluation harness) and
> P16 (on-device cockpit agent) — see the end of this file.**
> **Added 2026-10-26: P7 (S-CORE safety-core engagement) and P8 (USMCA rules-of-origin traceability).**
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

## P6 — Teacher→student distillation from an open VLA *(revised; see **P9** before choosing the teacher)*

> 🆕 **2026-10-31 — read P9 first.** This pattern assumes a chosen teacher model. As of this pass there are
> **three Apache-2.0 suppliers** and the NVIDIA line is **third** on the only published open comparison.
> Choose the teacher with the P9 bench on the client's own logs rather than inheriting it.


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

## P9 🆕 — Model-agnostic E2E policy bench (pick a driving model instead of inheriting one)

**Region fit:** Global; strongest in **North America** (validation buyers) and **APAC** (three of the four
candidate models are APAC-origin or APAC-benchmarked).
**Problem:** a client is about to standardise on one open driving model — almost always Alpamayo, because
it is the one with marketing behind it. As of 2026-10-31 that is a measurably questionable default:
**Qwen-Drive-1.0** and **AutoE2E** both sit ahead of **Alpamayo 1.5** on AutoE2E's published eight-model
comparison, and the comparison is **not like-for-like**. Nobody — including this KB — can tell the client
which model is best *for their data*. The deliverable is the apparatus that answers that, on their logs.

**Wiring:**
1. **Interface first, models second.** Define one adapter contract — `(surround frames, ego history,
   optional map raster, route) → (trajectory | acceleration + curvature)`. Every candidate implements it.
   This is the whole point of the pattern: the client ends up owning a bench, not a model choice.
2. **Load four candidates, all Apache-2.0 code:**
   - [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) — 79.9M params,
     camera-first, no HD map required, **~76 FPS on an RTX 5080**. The on-target realist.
   - [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) — 4B, BEV perception head +
     flow-matching planner. Tops the published table.
   - [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) — 10B, the recipe-supported incumbent.
   - [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) — 0.5B, the floor case for
     cost-per-inference and teaching.
3. **Reproduce the published numbers before trusting your own.** AutoE2E ships the evaluation scripts:
   PRs **#220** and **#229** added Qwen Drive 1.0 and Alpamayo 1.5 evaluation, and issue **#210**
   coordinates the community benchmark. Reproduce the KITScenes-Multimodal ADE/FDE figures first — if the
   bench cannot reproduce a published row, the bench is wrong, not the paper.
4. **Then re-score on the client's logs, open-loop, and normalise the inputs.** This is where the published
   table's weakness becomes your value: AutoE2E receives an HD map and the route while others do not.
   **Hold inputs constant across candidates** and the ranking may invert. Say so in the report.
5. **Close the loop for the shortlist only.** Promote the top two into
   [NVlabs/alpasim](https://github.com/NVlabs/alpasim) + [NVlabs/alpagym](https://github.com/NVlabs/alpagym),
   or CARLA + [scenario_runner](https://github.com/carla-simulator/scenario_runner), and score on the
   client's own failure scenarios mined per **P1**. Open-loop ADE/FDE is a screening metric, not a
   driving-quality metric.
6. **Report cost-per-inference alongside accuracy.** 79.9M vs 4B vs 10B is a silicon-budget decision as much
   as an accuracy one, and it is the number the client's hardware team will actually act on.

**🔴 Licence gate before any deliverable ships.** All four repositories are Apache-2.0 **for code**.
**Weights are a separate grant and could not be verified this pass** — `huggingface.co` does not resolve
from the research session, Alpamayo 1.5's weights are **OpenMDW-1.1** while its code is Apache-2.0, and a
secondary source makes the same claim about AutoE2E. **Read every model card before distributing a
fine-tuned derivative.** Put this step in the statement of work as a named task, not an assumption.

**Estimate:** 3–4 weeks for the adapter contract plus two models reproducing published numbers; +2 weeks per
additional model; +3–4 weeks to re-score on client logs with normalised inputs. The bench is reusable across
engagements, which is what makes it worth building once properly.

## P10 🆕 — Aftersales diagnostic copilot on a published contract (MCP all the way down)

**Region fit:** **North America** first (43% dealer AI adoption, a further 47% planning to; NHTSA vPIC VIN
API is free and US-scoped), then **EMEA**; the reference implementation is EMEA-origin.
**Problem:** a dealer group or independent-workshop chain wants AI help with diagnosis and customer
communication. The instinct is to build a bespoke stack. As of this pass, **both ends are already
specified** — the vehicle end by the MCP diagnostics cluster, the business end by Auto Agent Protocol — so
the budget should go to the domain and the gate, not to re-inventing two interfaces.

**Wiring, bottom to top:**
1. **Vehicle access layer — pick by access depth, and mind the licence:**
   - Consumer / fast demo: [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) (**MIT**, 2★) — DTCs,
     live data, freeze frame, VIN over ELM327, and it **bundles a mock vehicle so it runs with no
     hardware**. This is how you demo in a workshop before anyone buys a dongle.
   - Professional depth: J2534 PassThru (UDS, KWP2000, DTC lookup, PID decoding).
     ⚠️ **[cyrusdavirusss/j2534-mcp-server](https://github.com/cyrusdavirusss/j2534-mcp-server) is the
     reference design and is NOT usable** — its README says "MIT" but the repository has **no LICENSE file**
     (404 on `LICENSE`, `LICENSE.md`, `LICENSE.txt` across `main` and `master`). **Read it, do not vendor
     it.** Either ask the maintainer to add the file, or implement the J2534 tool surface yourself against
     the SAE spec.
2. **Agent orchestration — copy the one that exists.**
   [castlebbs/Vehicle-Diagnostic-Assistant](https://github.com/castlebbs/Vehicle-Diagnostic-Assistant)
   (**MIT**, 8★) is the most complete open design: LangGraph with `InMemorySaver` checkpointing and UUID
   sessions, MCP over streamable HTTP / JSON-RPC 2.0, a **sandboxed** OBD-II formula evaluator, VIN decode
   against the **NHTSA vPIC** API, repair-tutorial retrieval. Its hardware path (W600-B800 MCU → UART
   38400 → ELM327 → CAN) is a working answer to "what dongle".
3. **Ground the reasoning in the client's own documents, not the open web.** RAG over *their* service
   manuals, TSBs and historical repair orders. This is the differentiator — the open projects all stop at
   generic knowledge, and two of them run on **simulated data catalogues**.
4. **Speak VSS upward.** Name every vehicle signal with
   [COVESA VSS](https://github.com/COVESA/vehicle_signal_specification) (MPL-2.0) so the model's vocabulary
   matches the industry's and the same tools serve a connected-vehicle programme later.
5. **Business end — implement Auto Agent Protocol, do not invent a schema.**
   [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol)
   (**Apache-2.0** spec/schemas/code, docs **CC BY 4.0**, 110★, v3.1): publish the dealer's **Agent Card**,
   **Poppy document** and **`llms.txt`**, serve the MCP tool catalogue and A2A OpenAPI from versioned
   `/v3.0/` paths, and use its **consented-inquiry** flow for lead capture. 🔴 **Do not tell the client the
   industry has standardised on this** — the spec is verified, its deployment is not. The accurate pitch is
   "an open contract exists and we implement both sides".
6. **Service-order back office, licence-led:** [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework)
   (Apache-2.0) or [krayin/laravel-crm](https://github.com/krayin/laravel-crm) (MIT) if the deliverable is a
   hosted proprietary product. **Avoid** Odoo (LGPL-3.0), Dolibarr (**GPL-3.0**) and
   `navariltd/Fleet-Management-System` (**GPL-3.0**) for that case.
7. **Human gate on everything that actuates, commits money, or tells a customer their car is safe.**
   A diagnosis is advice; a technician signs it. Notably **two independent projects found this pass arrived
   at the same gate on their own**, which is the strongest available evidence that it is the correct
   architecture rather than this KB's preference.

**Why this pattern is cheap to start and hard to copy:** steps 1–2 and 5 are free and specified, step 3 is
the client's proprietary corpus, and step 7 is the thing that makes it deployable. The moat is 3 and 7.

**Estimate:** 2 weeks for a mock-vehicle demo (step 1 + step 2 off the shelf, no hardware); 6–8 weeks for a
grounded pilot on one workshop's manuals with the technician gate; +3–4 weeks to expose the AAP surface.


---

## P11 🆕 — Productionise an open L2 ADAS stack with a homologation evidence pipeline

**Region fit:** **EMEA** first — this region's budget line is compliance, and a stack with a certification
roadmap is the first credible answer to *"we cannot certify community code."* Then **APAC** (the upstream
is there) and **North America** (FMVSS No. 127 makes AEB federal).
**Problem:** a Tier-1 or a vehicle integrator wants L2 ADAS features — AEB, ACC, LKAS, LDW, ISA — without
licensing a black-box stack per unit, and must be able to show a homologation story.

**The stack, all named and all verified 2026-11-13:**

1. **Base — [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot)**
   (Apache-2.0, 927★, 196 forks, 4,282 commits). You get ACC, FCW, AEB, LKAS, LDW, ISA and single-lane
   hands-free highway Autopilot, **mapless**, from **one front monocular camera (52–55° HFOV, 1–2 MP)** on
   **ONNX Runtime**, GPU **or CPU**. Docker images, optional ROS 2 interface, **CARLA 0.9.16** closed loop.
2. **Swap the three models for the client's sensor and ODD.** The architecture is explicitly three models —
   **AutoSpeed** (closest in-path object), **AutoSteer** (ego-path waypoints), **AutoDrive** (E2E distance +
   in-path presence + curvature). These are the retraining targets; the feature logic above them stays.
3. **Perception inputs from the same org, so vocabulary matches:**
   [`scene_3d`](https://github.com/autowarefoundation/scene_3d) (Apache-2.0) for monocular depth — deploy
   **Scene3DLite**, the DepthAnythingV2-distilled variant, not the full model — and
   [`ego_lanes`](https://github.com/autowarefoundation/ego_lanes) (Apache-2.0) as the **lane-segmentation
   baseline to beat** (its maintainers call it *"legacy"*; treat it as the floor).
4. **Latency — [`agnocast`](https://github.com/autowarefoundation/agnocast)** (Apache-2.0, 212★, 1,258
   commits). **True zero-copy IPC that keeps the rclcpp API**, including unsized message types, via a
   kernel module plus heaphook, on ROS 2 Humble/Jazzy. This is the piece that makes a multi-process
   perception graph meet a cycle budget without rewriting it.
5. **Safety element — [`autoware-safety-island`](https://github.com/autowarefoundation/autoware-safety-island)**
   (**Apache-2.0**, read from `license.rst` after GitHub mislabelled it "Other"; 608 commits) on ARM SoCs,
   sitting beside **Eclipse S-CORE** (Apache-2.0, ASIL-B **target**, ~monthly releases, dual C++/Rust with
   Ferrocene) and **[`eclipse-score/itf`](https://github.com/eclipse-score/itf)** as the integration-test
   framework the evidence comes out of.
6. **Hardware reality check — [`openadkit-rcar-x5h`](https://github.com/autowarefoundation/openadkit-rcar-x5h)**
   (Apache-2.0 per org listing). Renesas R-Car X5H board support; this is what makes "runs on automotive
   silicon" checkable rather than asserted.
7. **Evidence pipeline:** every CARLA scenario run emits a signed artefact — scenario ID, model hashes,
   metrics, pass/fail — into the same store P3 uses for AI Act evidence. **The deliverable is the evidence
   as much as the code.**

**Why it holds together:** one licence family (Apache-2.0 end to end, no copyleft anywhere in the chain),
one org's vocabulary, one ROS 2 runtime, and a published safety element rather than a hand-drawn one.

🔴 **Say these three things out loud before the client does.** (a) *"Safety certifiable"* is **the
project's own aspiration** — there is no certification, and nothing published shows progress against
ISO 26262 or ISO 8800. (b) The sensor set today is **one narrow-FOV camera** — no radar, no surround view,
until the roadmap lands. (c) **No benchmark is published** for `vision_pilot`; the only multi-model open
comparison in this field is AutoE2E's ADE/FDE table from Oct 2026, which was never like-for-like and now
covers a minority of models. **This is an L2 base, never an L3 shortcut.**

**Estimate:** 3–4 weeks to a CARLA-based demo on the client's ODD with the stock models; **10–14 weeks**
to retrained AutoSpeed/AutoSteer/AutoDrive on the client's sensor set with the evidence pipeline wired;
**+8–12 weeks** for the safety-island integration and an S-CORE-conforming module. Homologation itself is
the client's programme, not this engagement.

---

## P12 🆕 — Freight diagnostics copilot on J1939, with a technician gate

**Region fit:** **North America** — freight is where the region's autonomy capital is visibly moving
(**Kodiak AI** demonstrations in **Indiana and Ohio**; **California DMV's 28 April 2026 AV rules now cover
heavy-duty vehicles**). Secondarily **EMEA**, where the rFMS blueprint and the agent are both EMEA-origin.
**Problem:** a carrier or fleet operator wants faster fault triage across a mixed truck fleet, where the
bus is **SAE J1939**, not the passenger-car OBD-II that every demo assumes.

**The stack:**

1. **Diagnostics agent — [farzadnadiri/Peykan](https://github.com/farzadnadiri/Peykan)** (**MIT, 26★**).
   The only project in this KB covering **J1939** alongside CAN, OBD-II and UDS, and it ships a
   **simulator, a Docker setup and a live dashboard** — so the pilot runs before a truck is instrumented.
   🔴 **Addressing note: every search result points at `farzadnadiri/mcp-can`, which is a rename of this
   repo.** Pin the new name and the commit; do not hard-code the old URL.
2. **Harden the tool surface with the better design — [ayhammouda/obd-mcp-server](https://github.com/ayhammouda/obd-mcp-server)**
   (**dual Apache-2.0 + MIT**, 1★, 19 commits). Do not depend on it at 1 star — **copy its three design
   decisions**: read-only by construction, a **deterministic simulator as the default backend**, and
   **seven typed MCP tools** instead of a free-form command passthrough. That is the shape that survives a
   safety review.
3. **Fleet telemetry — [traccar/traccar](https://github.com/traccar/traccar)** (Apache-2.0, 7.9k★, 200+
   device protocols, multi-tenant) for the aftermarket path, **or** the
   **[Eclipse SDV fleet-management blueprint](https://github.com/eclipse-sdv-blueprints/fleet-management)**
   (Apache-2.0) when the client is an OEM/truck maker with its own SDV stack — Kuksa CSV Provider → Kuksa
   Databroker → FMS Forwarder → uProtocol → FMS Consumer → InfluxDB → Grafana, with an **rFMS API** server.
4. **Signal vocabulary — [COVESA VSS](https://github.com/COVESA/vehicle_signal_specification)** (MPL-2.0)
   for everything signal-shaped, so the model's vocabulary is the industry's.
5. **Back office — [aureuserp/aureuserp](https://github.com/aureuserp/aureuserp)** (**MIT**, 12.2k★,
   Laravel + FilamentPHP) for work orders, parts and inventory. **MIT matters here**: this is the first full
   ERP in this KB that can ship inside a proprietary client deliverable with no copyleft and no carve-out —
   unlike Odoo (LGPL-3.0), Dolibarr (GPL-3.0) or `open-mercato` (MIT core, commercial `packages/enterprise`).
6. **The gate.** The agent proposes a fault hypothesis, the parts list and the labour estimate; **a
   technician signs off before any work order is committed or any actuation occurs.** Every credible
   automotive agent reviewed across five passes of this KB has independently arrived at this gate.
7. **Watch, do not build on yet — [`autoware.trucks`](https://github.com/autowarefoundation/autoware.trucks)**
   (Apache-2.0, 9 commits). A charter for L2+ → L4 highway trucking. Track it; the autonomy layer is not
   there, while the diagnostics layer above is shippable today.

**Estimate:** 2–3 weeks to a simulator-only demo (Peykan's simulator + the typed tool surface, no
hardware); **8–10 weeks** for a grounded pilot on one depot with the technician gate and Traccar
integration; **+4 weeks** to wire the AureusERP work-order path.

---

## P13 🆕 — Licence and provenance diligence as a delivered artefact

**Region fit:** **Global**, with the sharpest commercial edge in **EMEA** (AI Act technical documentation
duties make provenance an obligation, not hygiene) and **LATAM** (LGPD plus Brazilian ANPD instruments).
**Problem:** a client has assembled open-source AI components and cannot evidence what they are permitted
to ship. This pattern exists because of a measured rate, not a hunch: **of 19 repositories probed on
2026-11-13, six carried a licence defect — and of four ERP/CRM licence claims, exactly one held as stated.**

**The pipeline, built from this KB's own method:**

1. **Enumerate** every repository, model checkpoint and dataset in the client's dependency closure —
   including transitive ones, since `python-can` (**LGPL-3.0**) is a transitive dependency of half the
   diagnostics stack.
2. **Fetch the licence file, never the badge.** Probe `LICENSE`, `LICENSE.md`, `LICENSE.txt` **and
   `license.rst`** on **every** default branch, raw. Both failure directions are real and both are
   expensive:
   - **False positive:** `autoware_latent_drive` — no field, no README statement, all four filenames
     **404**, published **inside the Autoware Foundation's own org**. `petrpatek/obd2-mcp-server` and
     `j2534-mcp-server` — README says MIT, no file.
   - **False negative:** `autoware-safety-island` reads **"Other"** only because its file is
     `license.rst`; it is **verbatim Apache-2.0**, 608 commits, and a label-trusting pipeline **silently
     discards** it.
3. **Separate code from weights from data from docs.** Four distinct grants, routinely different:
   Alpamayo 1.5 (**Apache-2.0 code, OpenMDW-1.1 weights**), DriveLM (**Apache-2.0 code, CC BY-NC-SA 4.0
   language data** — non-commercial), Auto Agent Protocol (**Apache-2.0 spec/code, CC BY 4.0 docs**).
4. **Flag directory-level carve-outs.** `open-mercato` is MIT with `packages/enterprise` under a separate
   **commercial** licence. The repo badge is MIT; the tree is not.
5. **Check liveness, not just licence.** Huly (`hcengineering/platform`) is **28.1k★** and its page states
   it is **"frozen and is no longer actively maintained."** A healthy star count is not a maintained
   project. Likewise `NVlabs/alpamayo` carries a *"no longer under active development"* banner, and
   `ChanMeng666/Automotive-Repair-Management-System` was **archived 2026-07-08**.
6. **Re-verify claimed URLs — renames rot silently.** `farzadnadiri/mcp-can` → **`Peykan`**;
   `openedx/edx-platform` → `openedx/openedx-platform` (recorded by this pipeline in the education KB).
7. **Deduplicate near-identical forks before they become separate entities.** `awesome-vla-for-ad` exists
   as **at least five** forks (`776styjsu`, `tongnie`, `ruiguoz`, `mengmengliu1998`, `worldbench`);
   `worldbench` is the apparent upstream. Five rows for one artefact is a data defect.
8. **Deliver** a signed SBOM-plus-grant matrix: component → licence → *evidence channel and date* →
   permitted use → obligations on distribution. The **evidence channel** column is what makes it auditable
   rather than asserted — this KB records, for instance, that `curl` and `api.github.com` return **HTTP
   403** here and that `huggingface.co` does not resolve, so **no model-weight licence has been verified
   in four passes.** A gap that is named is defensible; a gap that is silent is a liability.

**Why a client buys it:** it is cheap, it is verifiable, it blocks a category of expensive late surprise,
and it is the natural door-opener into P3's AI Act evidence pipeline and P11's homologation evidence.

**Estimate:** 2–3 weeks for a one-off audit of a 50–150 component closure; **5–7 weeks** to deliver it as a
re-runnable CI gate that fails a build on a new unlicensed or copyleft dependency.

---
*Thirteen patterns, 2026-11-13. Effort estimates are planning figures for a studio team, not quotes.
**P11, P12 and P13 are new this pass** (2026-10-31 added P9 and P10; 2026-10-26 added P7 and P8). Every
repository named above was verified live on its stated date — for this pass, from the rendered repository
page or a raw licence file, since `curl` and `api.github.com` both return HTTP 403 in this session. Where a
licence is flagged ⚠️ or 🔴, the flag is the finding.*

---

## P14 🆕 — The assurance artefact factory (ISO 26262 / 21434 / 21448 / ASPICE as agent output, with a named owner)

**Added 2026-11-19.** This is the highest-leverage new pattern in this file, because the same build sells
into all four regions for four different reasons (see `intel/trends.md` → **N9**).

**Who buys it:** an OEM or Tier-1 that must produce a safety case — in North America because AV
rulemaking is heading toward a required safety case for SAE L3–L5 and NHTSA enforcement is live
(**EA26002**, ~3.2M vehicles); in EMEA because the AI Act delta on top of **UNECE R151** type-approval
documentation has to be written; in APAC because the China-co-led **ADS GTR** plus stricter domestic OTA
rules demand release evidence; in LATAM because a Bajío supplier shipping into the US needs
export-readiness it cannot currently demonstrate.

**Components**
| Role | Repo / asset | Licence |
|---|---|---|
| Artefact generators | [`jherrodthomas/automotive-skills-suite`](https://github.com/jherrodthomas/automotive-skills-suite) — 76 builder+reviewer pairs → `.xlsx` across ISO 26262 (HARA, FSC/TSC, FMEDA, safety case), ISO/SAE 21434 (TARA, incident response), ISO 21448 SOTIF, AIAG-VDA (APQP/DFMEA/PFMEA/control plans/PPAP), Automotive SPICE | **MIT**, 2,907★ |
| Repository *shape* to copy | [`jherrodthomas/LionDriver`](https://github.com/jherrodthomas/LionDriver) — living safety case (claims / evidence / **defeaters**), 89 V-cycle work products, field-monitoring process | **MIT**, 65★ |
| Traceability engine | [`Lieubk/automotive-safety-security-assurance-kit`](https://github.com/Lieubk/automotive-safety-security-assurance-kit) — ASPICE 3.1/4.0 + 26262 + 21434 trace engine | **MIT** |
| Systems-engineering spine | [`de4sdv/DE4SDV`](https://github.com/de4sdv/DE4SDV) — **SysML v2**, product-line engineering, digital continuity | **Apache-2.0** |
| Requirements intake | [`BUAksakal/reqlens`](https://github.com/BUAksakal/reqlens) — LangGraph supervisor + LlamaIndex RAG over PDF specs, flags conflicts and vague wording, engineer in the loop | **MIT** |
| Communication-matrix bridge | [`ebroecker/canmatrix`](https://github.com/ebroecker/canmatrix) — **`.arxml` ⇄ `.dbc` ⇄ `.kcd`** | **BSD-2-Clause** |

**Wiring**
1. **Ingest** the client's requirement set with `reqlens`; its conflict/vagueness report is the first
   deliverable and it lands in week one — it is also the cheapest possible proof of value.
2. **Model** the system in `DE4SDV` (SysML v2). Requirements allocate to architecture here, so
   traceability is structural rather than a spreadsheet column.
3. **Generate** each artefact with the matching builder skill from `automotive-skills-suite`; run the
   **paired reviewer skill** on every output. Reviewers do not mutate source artefacts — gaps become
   recommended actions, which is the property that makes the output auditable.
4. **Trace** with the assurance-kit's trace engine: requirement → architecture element → work product →
   test → evidence. Break the build when a link is missing.
5. **Pull real bus facts** through `canmatrix` so communication-matrix and diagnostics artefacts cite the
   client's actual ARXML rather than a restated summary.
6. **Structure the repository like LionDriver**: claims, evidence items, and — the part that matters —
   **open defeaters, counted and published**.
7. **Assign a named responsible engineer to every generated artefact** before it leaves the studio.

**🔴 The two non-negotiables, and the pattern fails without them**
- **No generated artefact ships as generated.** The skills-suite repository page carries **no
  "not certified" disclaimer** while advertising coverage of six standards and the word "compliance".
  The studio must supply the disclaimer, the review step and the named owner the upstream project does
  not. Write this into the SoW, not into a readme.
- **Publish the defeater count.** LionDriver's credibility comes from stating **36 claims, 50 evidence
  items, 0 accepted, 42 open defeaters** — not from claiming completeness. A client-facing safety case
  with no open defeaters is either finished (it is not) or dishonest.

**Also note:** the skills suite installs via *"Save skill"* in **Cowork or Claude Desktop**; the page
names **no Claude Code or non-Claude runtime**. If the client's agent platform is something else, budget
repackaging as explicit scope.

**Estimate:** **4–5 weeks** for one artefact family (e.g. ISO 26262 HARA → FSC → TSC with traceability)
on a defined item. **12–16 weeks** for a full V-cycle work-product set with a CI traceability gate.
**Add 3–4 weeks** if the client's agent runtime is not a Claude surface.

---

## P15 🆕 — Vehicle-agent evaluation harness (buy the harness, not the model)

**Added 2026-11-19.** Clients keep asking which model should drive. The sellable answer is a harness that
makes the question answerable repeatedly — and `drivingbench_harness_code` has published the reference
design, including the safety envelope.

**Components**
| Role | Repo | Licence |
|---|---|---|
| Harness + MCP contract | [`aditya-ramabadran/drivingbench_harness_code`](https://github.com/aditya-ramabadran/drivingbench_harness_code) — `drivingbench_sandbox` exposing `observe()` / `set_motion()` / `stop_now()`; chat models, API models and HTTP-served VLA policies all drive the same course | **MIT**, 63★ |
| Vehicle platform | [`commaai/openpilot`](https://github.com/commaai/openpilot) (comma four; DrivingBench pins upstream `59fcd340`) | **MIT** |
| Off-car compute | [`zoompilot/jetlink`](https://github.com/zoompilot/jetlink) — openpilot's large driving model on **Jetson Orin Nano / macOS / iOS / Android / CUDA laptops** | **MIT** |
| Simulation first | [`NVlabs/alpasim`](https://github.com/NVlabs/alpasim) (Apache-2.0, 1,304★), [`carla-simulator/carla`](https://github.com/carla-simulator/carla) (MIT, 14,655★), [`Farama-Foundation/HighwayEnv`](https://github.com/Farama-Foundation/HighwayEnv) (MIT, 3,342★) | permissive |
| Candidate policies | `xiaomi-research/recogdrive` (Apache-2.0, ICLR 2026), `TabGuigui/WorldDrive`, `chenshi3/DriveWAM` (Apache-2.0, NeurIPS 2026), `ASGuard-UCI/safedrive-vla` (Apache-2.0, CoRL 2026), `autowarefoundation/vision_pilot` (Apache-2.0) | **Apache-2.0** |
| Candidate shortlist source | [`Thinklab-SJTU/Awesome-LLM4AD`](https://github.com/Thinklab-SJTU/Awesome-LLM4AD) (Apache-2.0, 1,906★) | Apache-2.0 |

**Wiring**
1. **Three architectural rules first, copied verbatim from DrivingBench, because they are the deliverable
   a safety reviewer will actually read:**
   - the agent's free-text `reason` is **logged for the operator and never sent to the controller** —
     prompt text cannot reach an actuator;
   - `observe()` returns **image age**, so staleness is an input rather than an assumption;
   - **four independent stoppers**: operator-set speed ceiling (default **3 m/s**), **hard cutoff at
     6 m/s**, command expiry, and cancellation on brake / gas / steering override / disengagement.
2. **Run the simulator leg first** — DrivingBench's course is a Gaussian splat over the real control
   stack, and it runs with placeholder frames if no splat exists. `HighwayEnv` is cheaper still for
   planning-policy triage. Nothing reaches a vehicle until it clears simulation.
3. **Serve every candidate behind one interface**: chat models over MCP, API models through the runner
   loop, trained VLAs over HTTP returning timed curvature + speed plans. One interface is what makes the
   comparison honest.
4. **Record everything**: every tool call, telemetry sample, settings change and **every image the model
   saw**, replayable. This is the evidence artefact that connects to **P14**.
5. **Closed course, human supervising, parking-lot speed.** DrivingBench calls itself *"research software
   for closed courses"*. Treat that as a contractual constraint, not advice.
6. **Report a decision, not a score.** ⚠️ DrivingBench publishes **no leaderboard and no results**, and
   `drivingbench.com` has not been read by this KB. The deliverable is *"policy X behaved this way on
   your course under your limits, with traces"* — never a benchmark number.

**🔴 Hard constraints:** closed course only; a trained safety driver present; the client's insurer and
legal team consulted **before** week one; and every result scoped to the exact vehicle configuration
tested — DrivingBench itself names specific platforms (comma four on a pinned build, recent Toyota TSS2,
Tesla Model 3 HW3) rather than "a car".

**Estimate:** **3–4 weeks** simulator-only, 4–6 candidate policies, with traces and a written decision.
**8–10 weeks** including a closed-course leg on one vehicle. Add the client's own legal/insurance
timeline, which is usually the critical path.

---

## P16 🆕 — On-device cockpit agent (no cloud fallback, confirmation-gated)

**Added 2026-11-19.** The OEM direction of travel is explicit: Mercedes-Benz × **Liquid AI** (announced
23 Apr 2026, multi-year) runs **Liquid Foundation Models on-device** on **MB.OS** for 3rd/4th-generation
MBUX in North America — speech recognition, language understanding and reasoning **local, no cloud
dependence** — targeting *"initial production deployment as early as H2 2026"*. CES 2026 analyses
describe the same move toward **domain-specific automotive language models trained on navigation data,
vehicle controls and safety rules** rather than general LLMs. The open supply side moved the same way in
the same window.

**Components**
| Role | Repo | Licence |
|---|---|---|
| Agent framework | [`yancent-dao/cockpit-agent-sim`](https://github.com/yancent-dao/cockpit-agent-sim) — **zero-backend**, **tiered permissions**, **confirmation flow**, card orchestration, **fast/slow dual layer**, real third-party integrations; *"add a capability = add data, not code"* | **MIT**, 98★ |
| On-device perception precedent | [`Sherin-SEF-AI/Lyne-ADAS`](https://github.com/Sherin-SEF-AI/Lyne-ADAS) — 100% on-device Android ADAS that **self-tunes from budget phones to flagships** | **MIT** |
| Model portability | [`zoompilot/jetlink`](https://github.com/zoompilot/jetlink) (Jetson Orin Nano / mobile / laptop) and [`YassineYousfi/openpilot.distill`](https://github.com/YassineYousfi/openpilot.distill) (distil on your own drives) | **MIT** |
| Vehicle signal access | [`eclipse-kuksa/kuksa-databroker`](https://github.com/eclipse-kuksa/kuksa-databroker) + [`COVESA/vehicle_signal_specification`](https://github.com/COVESA/vehicle_signal_specification) | Apache-2.0 / MPL |
| In-vehicle transport | [`nanomq/nanomq`](https://github.com/nanomq/nanomq) (MIT, 2,666★), [`eclipse-iceoryx/iceoryx`](https://github.com/eclipse-iceoryx/iceoryx) (Apache-2.0, 2,212★) | permissive |
| Target image | [`eclipse-leda/leda-distro`](https://github.com/eclipse-leda/leda-distro) — Yocto build for SDV.EDGE | Apache-2.0 |
| Determinism / observability | [`xronos-inc/xronos`](https://github.com/xronos-inc/xronos) | BSD-3-Clause |

**Wiring**
1. **Adopt `cockpit-agent-sim`'s fast/slow split as the architecture, not as an optimisation.** The fast
   layer answers deterministically from VSS signals and cards; the slow layer is the model. The fast
   layer must remain correct when the slow layer is unavailable, because **there is no cloud fallback by
   design**.
2. **Read signals through `kuksa-databroker` against the COVESA VSS vocabulary** — never from raw CAN in
   the HMI path. The bus work stays in the diagnostics layer (see **P10**, **P12**).
3. **Keep the tiered-permission model and the confirmation flow.** Any action that changes vehicle state
   requires explicit driver confirmation on the card. This is **T8** (human gate) applied to the cockpit
   and it is also what the APAC OTA/marketing-terminology rules reward.
4. **Size the model to the worst device in the fleet, then self-tune up** — the `Lyne-ADAS` discipline.
   Use `openpilot.distill` as the precedent for distilling against the client's own captured data rather
   than shipping a generic model.
5. **Boot on target via `leda-distro`**; transport over `nanomq` for general telemetry and `iceoryx`
   where the latency budget is hard.
6. **Instrument with `xronos`** so timing non-determinism is diagnosable rather than mysterious — in a
   cockpit agent, the defect is almost always latency variance, not accuracy.
7. **Evidence:** every confirmed action and every refused action logged with its signal snapshot. Feeds
   **P14** directly; in EMEA that log *is* the AI Act risk-management evidence for the feature.

**Regional notes**
- **North America:** the Mercedes programme makes "on-device, no cloud" a procurement expectation rather
  than a differentiator. Lead with the fallback design and the latency budget.
- **EMEA:** on-device materially simplifies the data-protection story, and the confirmation log is
  reusable as AI Act risk-management evidence (see **P3**).
- **APAC:** `cockpit-agent-sim` is CN-origin and MIT, which fits the market it came from; China's
  **marketing-terminology restrictions** mean the HMI copy itself is a compliance surface — review
  strings, not just behaviour.
- **LATAM:** connectivity gaps make on-device the *practical* choice, not merely the private one. This
  is the one pattern where the LATAM constraint and the global trend point the same way.

**Estimate:** **6–8 weeks** for a bench prototype on a dev board with 3–5 capabilities and the full
confirmation flow. **14–18 weeks** to run on target hardware through `leda-distro` with VSS signal
access and an evidence log.

---
*Sixteen patterns, 2026-11-19. Effort estimates are planning figures for a studio team, not quotes.
**P14, P15 and P16 are new this pass** (2026-11-13 added P11–P13; 2026-10-31 added P9 and P10;
2026-10-26 added P7 and P8). Every repository named in P14–P16 was verified on 2026-11-19 through
`gh api -X GET search/repositories` — the GitHub REST API, so licence SPDX IDs, stars, forks and push
dates are first-hand API fields; 39 of 39 repos re-queried by exact `repo:owner/name` resolved. `curl` to
`github.com` and `api.github.com` returns **HTTP 403** in this session (host policy), and
`huggingface.co` does not resolve, so **no model-weight licence has been verified first-hand in five
passes.** Where a licence is flagged ⚠️ or 🔴, the flag is the finding.*
