---
industry: automotive
region: Global
updated: 2026-11-24
---

# 🧩 Composition patterns — Automotive

> Concrete recipes: named repos, named wiring, stated assumptions. Every repo referenced here is verified
> in `repos/foundations.md` or `agents/top.md` (URL probed live 2026-10-26).
> **New on 2026-11-21: P17 (dealer retail agent layer on a permissive ERP), P18 (cockpit agent graded
> against China's C1–C5 scale) and P19 (shelf audit as a repeatable service) — see the end of this file.**
> Every repo named in P17–P19 had its URL probed with `git ls-remote` and its licence **byte-read** from
> `raw.githubusercontent.com` on 2026-11-21.
>
> *Earlier —* **2026-11-19: P14 (assurance artefact factory), P15 (vehicle-agent evaluation harness) and
> P16 (on-device cockpit agent).**
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
5. **Check liveness, not just licence — and keep "service" separate from "project".** A healthy star
   count is not a maintained project: `NVlabs/alpamayo` carries a *"no longer under active development"*
   banner, and `ChanMeng666/Automotive-Repair-Management-System` was **archived 2026-07-08**.
   🔄 **Corrected 2026-11-21 — Huly is no longer the example here, because it was the wrong one.** This
   step previously read that Huly (`hcengineering/platform`, 28.1k★) *"is frozen and no longer actively
   maintained."* The notice actually says the **hosted Huly service** is being discontinued for lack of
   hosting funding, and directs users to **self-hosting**; the repository was **pushed 2026-11-09**, is
   **`archived: false`**, and its last commits are real fixes. **The inverse error is as expensive as the
   one this step warns about:** reading a SaaS wind-down as an abandoned codebase discarded a viable
   28k★ EPL-2.0 base. **Diligence test: `pushed_at` + `archived` + *who* the notice is about** — the
   service, or the code. See `verticals/solutions.md` → 2026-11-21.
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

---

## P17 🆕 — Dealer retail agent layer on a permissive ERP (the DMS gap, worked around instead of waited out)

**Region: North America** (the agent layer's vocabulary is US dealer retail). **Problem:** there is no
open-source DMS — seventh consecutive confirmation in `verticals/solutions.md` — and the gap is
structural, so waiting is not a plan. Meanwhile **43% of US dealers are reported already deploying AI
and 47% planning to**. The addressable estate is dealer **operations**, not the DMS itself.

**Parts, all licence-verified by byte-read this pass:**

| Role | Repo | Licence |
|---|---|---|
| Dealer-ops agent skills | [arielcoro/dealer-ai-skills](https://github.com/arielcoro/dealer-ai-skills) | **MIT**, 3★, pushed 2026-10-21 |
| Service-advisor assistant (VIN decode + labour times) | [rogue-media-lab/waypoint](https://github.com/rogue-media-lab/waypoint) | **MIT**, 1★, pushed 2026-11-13 |
| CRM base | [krayin/laravel-crm](https://github.com/krayin/laravel-crm) | **MIT** |
| ERP base (if accounting/inventory needed) | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | **Apache-2.0** |
| Diagnostics tool surface | [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) (**bundles a mock vehicle**) | **MIT** |
| Outward-facing contract | [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | **Apache-2.0** |

**Wiring.**
1. **Krayin (MIT) is the system of record for the pilot, not the DMS.** Do not attempt DMS replacement —
   integrate read-only against whatever DMS the dealer runs (CDK/Reynolds/Dealertrack are proprietary;
   treat them as external systems behind an adapter).
2. **Install `dealer-ai-skills` as the agent skill set** over that record: SEO/AEO/GEO, BDC follow-up,
   F&I, fixed ops, equity mining. It runs on Claude Code / Codex / Cursor / Gemini CLI, so **no runtime
   lock-in** — this is the part that would otherwise be rebuilt from scratch per engagement.
3. **`waypoint` supplies the service lane**: VIN decode → labour-time lookup → advisor draft.
4. **Expose diagnostics through `obd2-mcp`'s MCP tools.** The bundled mock vehicle means **the demo runs
   before any hardware or dealer data exists** — this is what makes the pattern sellable pre-contract.
5. **Any dealer-facing discovery/inventory/pricing surface implements Auto Agent Protocol**, not a
   bespoke schema (the standing rule in `agents/top.md`).
6. **Human gate on anything that quotes a price or commits money.** Non-negotiable, and it is also the
   answer to the consumer-protection exposure that is the real regulatory surface in US dealer retail.

**Why this beats waiting for an open DMS:** every part above is MIT/Apache-2.0 and verified live, and the
value sits in the **workflow skills**, which are portable across whatever DMS the dealer already pays for.
⚠️ **Stated assumption:** `dealer-ai-skills` is 3★ and single-author — treat it as a **well-shaped
starting point to fork**, not a dependency to pin. Its MIT grant is what makes forking safe.

## P18 🆕 — Cockpit agent graded against China's C1–C5 scale (APAC)

**Region: APAC.** **Why now:** **GB/Z 177.7—2026** (released 30 Apr 2026, CATARC-drafted) grades
intelligent-cockpit AI **C1–C5** — reported as the first such scale anywhere. That converts "our cockpit
is smart" into a **measurable, evidenced target**, which is a far better engagement shape than a feature
argument. Two **mandatory** standards (vehicle cybersecurity, software updates) already apply to newly
approved models from **1 Jul 2026**, and **GB 47955—2026** (combined driving assistance) lands
**1 Jan 2027**.

**Parts:**

| Role | Repo | Licence |
|---|---|---|
| Deterministic intent routing + slot extraction, on-device | [neura-edit/omni-intent](https://github.com/neura-edit/omni-intent) | **MIT**, pushed 2026-10-03 |
| Cloud-edge cockpit multi-agent orchestration | [SuperdeMan/cockpit-agent](https://github.com/SuperdeMan/cockpit-agent) | **Apache-2.0**, 30★, pushed 2026-10-19 |
| Vehicle signal contract | [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) + [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | **MPL-2.0** (both byte-read) |
| In-vehicle data broker | [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | **Apache-2.0** |
| Warning-omission test generation | [keklikci/deeptest-talking-manual-26](https://github.com/keklikci/deeptest-talking-manual-26) | **MIT** |

**Wiring.**
1. **`omni-intent` owns the hot path, and this is the whole design decision.** It does deterministic
   multi-intent routing with **no auto-regressive generation**, which is the only shape that survives a
   cockpit latency budget. An LLM that must emit tokens before the car responds cannot hit C-grade
   responsiveness targets.
2. **`cockpit-agent` (Apache-2.0) supplies the cloud-edge split**: fast on-device intent, cloud LLM for
   planning, cross-domain orchestration. Use it as the architecture reference for the slow path.
3. **All vehicle signals go through VSS (MPL-2.0) into `kuksa-databroker`.** MPL-2.0 is file-level
   copyleft only, so proprietary cockpit modules stay proprietary — **byte-confirmed this pass**, which
   matters because an automated licence read misreports VSS as AGPL-3.0 (see `intel/trends.md` N11).
4. **Grade the result.** Build the C1–C5 evidence package as a deliverable: latency traces from the
   deterministic path, capability coverage per level, and **`deeptest-talking-manual-26` run against any
   manual/owner-info assistant to hunt omitted safety warnings** — which is exactly the kind of negative
   evidence a grading submission needs and nobody generates by hand.
5. **Design for Qualcomm NPU targets** (~**71.4%** of China's cockpit domain-controller chip market in
   H1 2026) **but keep the intent engine portable** — `omni-intent` is Kotlin and on-device, so this is
   feasible rather than aspirational.
6. **OTA and cybersecurity evidence are mandatory, not optional**, from 1 Jul 2026. Budget the update
   pipeline and its evidence package as first-class scope.

⚠️ **Stated assumptions:** `omni-intent` is 1★ and `cockpit-agent` is 30★ — both are **reference designs
to fork**, not vendors. **GB/Z 177.7—2026 is a guidance document (`GB/Z`), not a mandatory standard
(`GB`)** — the grading is a market and procurement lever, while the 1 Jul 2026 cybersecurity/OTA
standards are the hard requirement. Do not conflate the two in a client conversation.

## P19 🆕 — Shelf audit as a repeatable service (the diligence pattern, now cheap)

**Region: Global.** `P13` already sells licence and provenance diligence as a delivered artefact. This
pass makes the **mechanics** cheap enough to run continuously, and that changes it from an engagement
deliverable into a standing service.

**The four channels (verified working 2026-11-21 — see `intel/trends.md` N10):**

```bash
# 1. Liveness AND the default branch, in one call, no API quota, parallelisable
git ls-remote --symref https://github.com/<owner>/<repo> HEAD   # "ref: refs/heads/X" = live, X is the
                                                                # default branch; credential prompt = gone
#    Use --symref, not --heads: channel 2 needs the branch name, and GUESSING it main-then-master is a
#    silent false-negative generator. Measured 2026-11-21: anomalib=main,
#    awslabs/sagemaker-defect-detection=mainline, hcengineering/platform=develop.

# 2. The grant, byte for byte (github.com is 403; THIS host is 200)
curl -sS https://raw.githubusercontent.com/<owner>/<repo>/<default-branch>/LICENSE
#    Try LICENSE, LICENSE.txt, LICENSE.md, LICENCE, COPYING, *and* license.rst before concluding "none".

# 3. Stars / forks / pushed_at / archived / SPDX
gh api -X GET search/repositories -f q='repo:<owner>/<repo>'
#    NOT `gh api repos/<o>/<r>` — per-repo REST is scoped and returns 403
```

**Wiring.**
1. **Sweep liveness first, discover second.** A full 174-URL sweep took minutes. An audited shelf of
   verified repos is worth more to an engagement than three new unverified rows.
2. **Byte-read the LICENSE; never trust `license.spdx_id`.** It returns `NOASSERTION` for a plainly-MIT
   30,954★ repo (`PythonRobotics`), for a dual GPL-3.0-OR-Commercial grant it cannot express
   (`autoas/as`), and for an Apache-2.0-with-named-carve-out (`waymo-open-dataset`).
   🆕 **And the reason, measured 2026-11-21: GitHub's classifier is near-exact-match, so *appending
   honest information* to verbatim licence text defeats it.** `PythonRobotics` inserts a contributors
   URL; `MayankGangwal-code/ev-battery-soc-estimation` appends a dataset attribution. **`NOASSERTION`
   therefore tracks conscientious authorship, not risk** — careless repos carry no licence file at all
   and measure `NONE`. **Read every `NOASSERTION` as a likely pointer to a dataset grant (step 6).**
3. **Classify on the licence's title line, never by substring.** MPL/GPL/LGPL/EPL texts all name *other*
   licences in their bodies (`intel/trends.md` N11). Size-check too: `openremote/openremote`'s
   172,870-byte LICENSE bundles a dependency listing around a one-paragraph **AGPL-3.0** grant.
4. **Check `pushed_at` *and* `archived` *and* the README banner, and keep them separate.** A
   discontinued **hosted service** is not a dead **project** — the Huly correction in
   `verticals/solutions.md` moved a repo from *rejected* back to *viable* on exactly this distinction.
5. **Flag, never overwrite, a curated cell.** Automation disagreed with this base's published licences
   8 times and was wrong 8 times. Two repos state their grant only in a README or source header, so a
   LICENSE-only probe would downgrade them and call it a refresh. **Emit diffs for human adjudication.**
6. 🆕 **Enumerate the DATASETS, not only the repos.** Added 2026-11-21: a permissive code grant says
   **nothing** about the corpus the model was fitted to, and **this sweep cannot see that axis at all**.
   `anomalib` is Apache-2.0 while **MVTec AD, its benchmark, is CC BY-NC-SA 4.0 — non-commercial**
   (`intel/trends.md` **N17**). Shipping weights trained on it, or quoting its benchmark in a proposal,
   is commercial use of NC data. **For every AI repo, record `{code grant, training-data grant,
   benchmark-data grant}` as three separate cells.**
7. **Deliverable:** per-repo row of `{url, live?, default branch, grant (byte-read), SPDX (for contrast),
   dataset grants, stars, pushed_at, archived, carve-outs}` plus a **refused list** with reasons. The refusals are the part
   clients cannot get elsewhere — e.g. `mikko-lab/kopilotti-sales-demo` is on the `automotive-ai` topic
   page and reads like a finding, but its LICENSE is **"All Rights Reserved"**; and `xtuple/xtuple`
   is **404** while still appearing in current ERP roundups.

**Why it sells:** this industry's licence-defect rate is high in **both** directions (`intel/trends.md`
N5/N11) — false-permissive claims that create exposure, and false-restrictive labels that discard usable
bases. Both are expensive, and **both are found by the same half-hour sweep.**

---

## P20 🆕 — The AI Act type-approval boundary inventory (EMEA, and it is sellable while the dates are still disputed)

**Region: EMEA.** This KB has argued the AI Act **date** across four passes (2 Aug 2026 / 2 Aug 2028 /
2027) and never resolved it. **P20 exists because the date was the wrong question.** The mechanism
resolves to an enumerated article list, and that converts an unanswerable timing question into a
**triage** a studio can actually deliver — see `intel/trends.md` **N13** and `intel/market.md` → `### EMEA`.

**The legal spine (verify against the OJ before client use — `eur-lex.europa.eu` is unreachable here):**
an AI system that is a **safety component of a type-approved vehicle** is a product under **AI Act
Annex I, Section B** (which lists **Reg. (EU) 2018/858** and **Reg. (EU) 2019/2144**). For those systems
**Art. 2(2) applies only Art. 6(1), Arts. 102–109 and Art. 112 directly, with no separate AI Act
conformity assessment**; requirements arrive via **Art. 109 → Reg. 2019/2144 → delegated/implementing
acts under the amended Reg. 2018/858**. **Systems outside those regimes take the full AI Act on the
general timeline.**

**The deliverable is the boundary, not a deadline memo:**

| Column | Path | Typical systems |
|---|---|---|
| **A — inside type approval** | Art. 2(2) narrow path; no separate conformity assessment | ADAS, ADS, event-data recorders, GSR driver monitoring |
| **B — outside type approval** | Full AI Act obligations, general timeline | Cockpit/voice assistants, dealer & CRM AI, manufacturing quality AI, HR and marketing AI |

**How to wire it, using only repos this KB has licence-verified:**

1. **Enumerate the client's automotive AI systems.** Seed the taxonomy from
   [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification)
   (**MPL-2.0**, 455★) for in-vehicle signal scope, and from the client's own type-approval dossier for
   what is already a declared safety component.
2. **Place each system in column A or B, and record the reason.** This is the billable judgement. The
   output is a table with a per-system rationale, not a RAG status.
3. **For column A, build the evidence trace.** Use the assurance-as-code layer —
   [lieubk/automotive-safety-security-assurance-kit](https://github.com/lieubk/automotive-safety-security-assurance-kit)
   (**MIT**) and the `automotive-skills-suite` builder/reviewer pairs (**MIT**, 2,907★) in
   `repos/foundations.md` **Layer D** — to generate the ISO 26262 / 21434 / 21448 artefacts that the
   delegated-act route will ask for, and map **UNECE R157 transition-demand design → the human-oversight
   requirement** (the mapping already recorded under `### EMEA`).
4. **For column B, run the ordinary high-risk workflow.** No automotive relief applies; these are
   general-purpose AI systems that happen to belong to a carmaker.
5. **Ship the boundary table as the artefact**, with every placement cited to Art. 2(2), Annex I §B, or
   the absence of both.

**Why it sells, and why now:** ⚠️ **the date conflict is a feature of this engagement, not an obstacle to
it.** Each column's deadline follows from which column a system is in, so **the work can be scoped,
priced and delivered while the Digital Omnibus timing is still contested** — and the EC's own
**Apply AI Strategy** consultation is explicitly collecting *"barriers to AI adoption and practical
challenges in implementing the AI Act"*, which is this deliverable described by the regulator.
**Proving a system sits in column A reduces the client's obligations**, which is the rare compliance
engagement that subtracts work — and it is argued from statutory text rather than from a forecast.

---

## P21 🆕 — Colombia-first ADS deployment, Brazil-first AV governance (LATAM, and it reverses the usual order)

**Region: LATAM.** Five passes of this KB treated LATAM as a regulatory blank and defaulted every
conversation to Brazil. **One measured fact reverses that for one of the two work types** — see
`intel/trends.md` **N15**.

**The asymmetry:** **Colombia already regulates the circulation of automated driving systems up to SAE
Level 3** (CMS, *Automotive Outlook 2026*) but has **no AI bill and is not debating one federally**.
**Brazil has the inverse**: no operating ADS rule, but **Bill 2,338/2023** would classify AVs as
**high-risk AI systems** with **risk-management, transparency, cybersecurity and human-supervision**
duties.

**So run two different plays, and do not mix them up:**

**Play A — deployment/homologation, in Colombia.** Something is already permitted, so the engagement is
to operate inside it: an L3-bounded ODD definition, the evidence pack for it, and the vehicle-side stack.
Wire [commaai/openpilot](https://github.com/commaai/openpilot) (**MIT**, 64,192★) or
[autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) (**Apache-2.0**) as
the L2/L3 base per **P11**, with `esmini` (**MPL-2.0**, 954★) +
[carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) (**MIT**, 687★)
driving the scenario regression factory of **P1** to produce ODD-bounded evidence.

**Play B — governance, in Brazil.** Bill 2,338 **names its own four work packages**, so build to them
directly: risk management, transparency, cybersecurity, human supervision. Use the **P14** assurance
artefact factory (`automotive-skills-suite`, **MIT**) to emit the four as versioned artefacts with named
owners, and keep **LGPD** as the binding constraint today (per **P5**) rather than the un-passed AI bill.

**Sequencing advice that follows from the asymmetry:** **a client wanting to *drive* something in LATAM
should be pointed at Colombia; a client wanting to *govern* AVs across LATAM should be anchored in
Brazil.** Pitching Brazilian deployment or Colombian AI governance is pitching into the half of each
regime that does not exist.

⚠️ **Two hard caveats before this is used commercially.** **(1) CMS names no Colombian decree or
resolution**, the analysis dates to ~March 2026, and no primary Colombian source resolved from this
environment — **confirm the instrument at the Ministerio de Transporte / Diario Oficial first.**
**(2) Baker McKenzie: no Latin American country has a fully mature, harmonised AI regime**, so neither
play should be sold as compliance with a settled framework. Supply-side reality is unchanged:
**zero LATAM-origin automotive repos across six consecutive passes** (`intel/market.md` → `### LATAM`),
so the engineering is imported and the **regulatory and integration work is the local value** — which
matches the buyer's own stated problem (**KPMG**: the obstacle is integrating data across fragmented
systems and supply-chain players).

---

## P22 🆕 — VDA-5-qualified plant-floor inspection (every region; the ROI argument is rework-vs-scrap)

**Regions: Global**, with a different unblocker per region (`intel/market.md` → Opportunities by region).
**This is the first pattern in this file that is not about vehicles.** It is about the plant that builds
them, which is where the non-AV automotive money is and the only automotive layer with world-scale
installed capacity in **every** region including LATAM.

**Why it is now buildable:** `repos/foundations.md` **Layer G** — a live, permissive anchor exists.

### The stack

| Layer | Repo / artefact | Licence | Role |
|---|---|---|---|
| Detection core | [`open-edge-platform/anomalib`](https://github.com/open-edge-platform/anomalib) | **Apache-2.0** (byte-read, 11,357 b) | 20+ algorithms (PatchCore, PaDiM, EfficientAD). **Choose the algorithm on the client's own images, not on a paper's table** |
| Edge runtime | OpenVINO export path, built into `anomalib` | Apache-2.0 | On-line inference on plant hardware; no cloud round-trip on the line |
| Signal plumbing | [`nanomq/nanomq`](https://github.com/nanomq/nanomq) (**MIT**, 2,666★) | MIT | MQTT broker between line cameras/PLCs and the detector — already in this KB's Layer A |
| Prior art only | [`sundyCoder/DEye`](https://github.com/sundyCoder/DEye), [`awslabs/sagemaker-defect-detection`](https://github.com/awslabs/sagemaker-defect-detection) | Apache-2.0 | **Dormant (2023 / 2022). Cite, do not build on** |
| Assurance output | [`jherrodthomas/automotive-skills-suite`](https://github.com/jherrodthomas/automotive-skills-suite) (**MIT**, 2,907★) | MIT | Already covers **AIAG-VDA**; the generator for the qualification pack in step 3 |

### Wiring

1. **Train on the client's line, never on the benchmark.** 🔴 **`anomalib` is Apache-2.0; MVTec AD is
   CC BY-NC-SA 4.0 — non-commercial** (`intel/trends.md` **N17**). Use MVTec AD **only** to shortlist an
   algorithm internally. **Shipping MVTec-trained weights, or quoting an MVTec score in the proposal, is
   commercial use of a non-commercial dataset** — and the proposal is where it actually happens, because
   the benchmark table is the first thing anyone copies.
2. **Anomaly detection first, classification later.** The plant has thousands of good parts and almost no
   labelled defects. Unsupervised/one-class is the only architecture that fits the data the client
   actually has, which is why this layer is built the way it is. **Defect *classification* is a phase-2
   upsell after enough true positives have accumulated.**
3. 🟢 **Make VDA QMC Volume 5 Part 3 qualification the deliverable, not accuracy.** Audi's AI spot-weld
   inspection **qualified as an inspection tool under VDA 5 Part 3** (optical sensors / image
   processing) — `intel/market.md` → EMEA. **Audit acceptance, not F1, is what lets the system actually
   gate parts.** Deliver a measurement-capability pack: repeatability/reproducibility on the optical
   system, decision thresholds, drift monitoring, and the human-adjudication path. **This is the step a
   generic CV vendor cannot do and it is the reason the engagement is worth automotive rates.**
4. **Price it on rework-versus-scrap.** The lever a plant controller already tracks is whether a
   defective part **can be reworked instead of scrapped** (`intel/market.md` → LATAM). **Quote
   cash-per-part recovered, not detection accuracy** — accuracy is a number the client cannot bank.
5. **Keep the inspector in the loop and say so.** Plants face a **shortage of certified NDT inspectors
   and experienced quality technicians**; the framing that lands is **extending scarce certified
   talent**. Route uncertain parts to human review rather than auto-passing them — which is also what
   step 3's audit pack requires. **Never pitch this as replacing operators**; in Mexico specifically the
   automation argument has already shifted from labour savings to **process stability**.
6. **Regional entry point — same stack, different first conversation:**
   - **NA:** industrialise a pilot that already exists (42% already use AI in quality, ~half still
     self-report "awareness-stage" digitalisation). Frame as **tariff-era margin defence**.
   - **EMEA:** lead with step 3. The qualification *is* the product.
   - **APAC:** robot density is already world-leading; sell **inspection judgement** on top of arms that
     are installed.
   - **ASEAN:** time it to the **subsidy withdrawal** (Indonesia's EEAI ends **31 Dec 2026**) — that is
     when cost-per-unit work gets funded.
   - **LATAM:** a **retrofit pilot on an installed Bajío line**; **89% of Mexico's H1-2026 FDI is
     reinvestment into existing plants**, so the budget owner is the plant, not a site-selection team.

**Why it sells:** it needs **no autonomy claim, no homologation, and no vehicle** — so it closes in
quarters rather than years, and it is the only pattern in this file that is **equally deliverable in all
five regions**. The entire regional difference sits in the evidence-and-economics wrapper, not the model
— the **second** independent instance of the *"one artefact factory, N regional buyers"* shape this KB
first recorded as **N9**, which is what makes that shape structural rather than coincidental.

🔴 **Honest limits.** No measured AI-adoption rate exists for any LATAM country in this KB (investment
flows and labour-market facts only). The VW "99.7% accuracy" figure is vendor-adjacent. Market size for
this sub-segment disagrees **4×** ($829M vs $3.26B for 2026) — **quote the VDA gate and the scrap
economics, never the market size.**

---

## P23 🆕 — The fully-permissive UDS diagnostics bench (every region; the licence story is clean end to end)

**Why this pattern is new:** this KB has carried diagnostics patterns before (**P10** on a published MCP
contract, **P12** for J1939 freight), but both had to route around the fact that the *protocol toolchain*
underneath was unverified. The fourth pass found it, byte-read it, and **it is permissive nearly
throughout** (`repos/foundations.md` → **Layer H**). This is the pattern where *nothing in the stack
needs a legal conversation* — which is itself the sellable property.

**The stack, with grants attached:**

| Role | Component | Grant (byte-read 2026-11-21) |
|---|---|---|
| UDS protocol, bench side | [pylessard/python-udsoncan](https://github.com/pylessard/python-udsoncan) | **MIT**, 1,074 b |
| Protocol constants, edge side | [oxibus/automotive_diag](https://github.com/oxibus/automotive_diag) (UDS, KWP2000, OBD-II, DoIP) | **MIT**, 1,139 b |
| ECU bench / HIL / DoIP+LIN | [ecubus/EcuBus-Pro](https://github.com/ecubus/EcuBus-Pro) | ⚠️ **Apache-2.0 in `package.json` only — no `LICENSE` file** |
| Bus triage UI | [Chanchaldhiman/CANviz](https://github.com/Chanchaldhiman/CANviz) | **MIT**, 1,076 b |
| Log ingest | [COVESA/dlt-viewer](https://github.com/COVESA/dlt-viewer) | **MPL-2.0** (file-level copyleft) |
| Technician app surface | [surendranb/CarDash](https://github.com/surendranb/CarDash) (Android) / [kkonteh97/SwiftOBD2](https://github.com/kkonteh97/SwiftOBD2) (iOS) | **MIT** / **MIT** |

**Wiring.** `automotive_diag` supplies the ISO-14229/14230/9141/13400 enums to a Rust edge collector on
the vehicle; `python-udsoncan` drives the same services from the bench, so **one protocol vocabulary
spans edge and bench**. `EcuBus-Pro` replaces a CANoe seat for DoIP/LIN/HIL scripting (TypeScript, not
CAPL). Session logs land as DLT and are read with `dlt-viewer`. The **agent sits above
`python-udsoncan`, never on the bus**: it proposes a service call, a deterministic allow-list executes
it, and `CarDash`/`SwiftOBD2` is the technician surface. Reuse **P10**'s MCP contract for the interface
and **P12**'s technician confirmation gate unchanged — an LLM must never emit a raw UDS write.

**Two things to put in the SOW, both discovered this pass:**
1. 🔴 **`EcuBus-Pro`'s grant is a `package.json` field with no licence text in the tree.** Probed five
   filenames on two branches: all 404. **Open a PR or an issue asking for a `LICENSE` file as task
   zero** — it is a ten-minute ask that converts the most valuable tool in the stack from
   "evaluation-only" to "deliverable-safe", and the answer is also a maintainer-responsiveness signal.
2. 🔴 **Licence-check the dev dependencies, not just the shipped artefact.** `Automotive-AI` is MIT and
   its README sends you to `Ircama/ELM327-emulator`, which is **CC-BY-NC** — non-commercial, so the
   documented no-car test path is unusable in a paid engagement. **Substitute
   [the-can-opener/simple-elm](https://github.com/the-can-opener/simple-elm) (MIT) or real ELM327
   hardware**, and add a dev-dependency licence scan to the gate in **P13**.

**Sell it as:** a diagnostics capability with a **complete, byte-read provenance table** (the P13
artefact) delivered alongside the code. The table is the differentiator — most competitors cannot
produce one, and this KB can now generate it from Layer H in an afternoon.

---

## P24 🆕 — Privacy-first consumer vehicle agent: local ledger, LLM on demand (LGPD / GDPR)

**The pattern exists as working MIT code, which is the whole point.**
[surendranb/CarDash](https://github.com/surendranb/CarDash) (**MIT**, 1,079 b byte-read, 61★, pushed
2026-08-03) implements it: an Android/Kotlin + Jetpack Compose OBD-II dashboard holding a **persistent
local vehicle-health ledger in Room/SQLite**, with **Google Gemini invoked only on demand** as an
assistant. Its README states the posture plainly — *"No Account Required"*, *"No Data Collection"*,
*"No Analytics"*, *"No Advertisements"*, *"100% Local Storage … Your vehicle data belongs to you alone."*

**Distinct from P5**, which is LGPD-compliant *fleet* telematics (an operator processing driver data for
its own purposes). This is the **consumer-owned-vehicle** case, where the data subject is the buyer.

**Why the architecture is the compliance argument.** Under **LGPD** and **GDPR**, most of the consent,
retention, cross-border-transfer and DSAR surface is created by *the telemetry leaving the device*.
Keep the ledger local and that surface largely does not arise; only the on-demand inference call does,
and it carries a single trip's context rather than a history. 🟢 **The reviewable claim becomes "by
default, nothing leaves the vehicle" — demonstrable in code, not asserted in a DPIA.**

**Wiring for a client build.** Fork the `CarDash` shape, not the app: (1) local Room/SQLite ledger as
system of record; (2) **on-device inference first** via
[OpenSparX/MasterAgent](https://github.com/OpenSparX/MasterAgent) (Apache-2.0, *"zero cloud
dependency"*, sub-100 ms on Qualcomm NPU) so the common path never leaves the device at all;
(3) cloud LLM as an **explicit, per-invocation, user-initiated escalation** — never a background sync;
(4) [kkonteh97/SwiftOBD2](https://github.com/kkonteh97/SwiftOBD2) (MIT) for the iOS half;
(5) the technician/service escalation path reuses **P23**'s allow-list — a consumer app must never
write to the bus.

**Where it sells.** **North America:** Deloitte's 2026 consumer study finds buyers wanting advanced
features while **privacy concerns loom large** and resisting paying extra — this answers the objection
that kills the upsell. **LATAM:** it removes most of the LGPD consent surface before legal review opens.
**EMEA:** it is the cleanest GDPR data-minimisation story available for a connected feature.
🟢 **And because it is MIT, the client can be shown the pattern as running code in the first workshop.**

---

## P25 🆕 — ARXML as data: programmatic AUTOSAR configuration with a review gate

**The gap this closes.** **P14** industrialises the *assurance* artefacts (ISO 26262 / 21434 / 21448 /
ASPICE) out of
[jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite)
(**MIT**, 76 builder + 76 reviewer skill pairs — the README now headlines **152 installable skills**).
But the suite's **ARXML / DBC / LDF / K-Matrix** skills emit `.xlsx` deliverables, and ARXML is the
format an AUTOSAR toolchain actually consumes. **Nothing in this KB previously connected the two.**
[cogu/autosar](https://github.com/cogu/autosar) (**MIT**, 1,088 b byte-read, 503★, pushed 2026-10-16)
is the missing link: Python modules that **read and write AUTOSAR XML**.

**Wiring.**
1. The suite's communication-matrix skill produces the K-Matrix / signal mapping as reviewed `.xlsx` —
   the human-auditable source of truth, with its paired **reviewer skill** as the confirmation step.
2. `cogu/autosar` **generates ARXML from that sheet**, deterministically. The sheet is the input; the
   ARXML is a build output, not a hand-edited artefact.
3. **The gate that makes this sellable:** `cogu/autosar` also *parses* ARXML, so the pipeline runs in
   reverse to **diff generated ARXML against what the OEM's toolchain actually returns.** A signal that
   drifted in integration shows up as a diff, not as a bus fault three months later.
4. Model-level traceability upstream via [de4sdv/DE4SDV](https://github.com/de4sdv/DE4SDV)
   (Apache-2.0, **SysML v2**, Layer D), so a requirement reaches a signal definition by a traced path.
5. Runtime side: [COVESA/vsomeip](https://github.com/COVESA/vsomeip) (**MPL-2.0**) for SOME/IP service
   deployment and `dlt-viewer` for the logs. ⚠️ **MPL-2.0 is file-level copyleft — modified `vsomeip`
   files stay MPL; linking proprietary code alongside is fine. Respect the file boundary in the build.**

**The deliverable is the diff, not the ARXML.** Any Tier-1 can hand-produce ARXML. **What they cannot
cheaply produce is continuous evidence that the deployed configuration still matches the reviewed
communication matrix** — that is the billable artefact, it recurs every integration cycle, and it is
built entirely from MIT + Apache + MPL parts.

⚠️ **Scope honestly:** `cogu/autosar` is an ARXML *library*, not an AUTOSAR authoring tool. It will not
replace DaVinci or EB tresos. **Position it as the automation and verification layer beside the
client's existing toolchain** — which is also why it is adoptable without displacing a vendor.

---

# 🆕 Added 2026-11-24

> Five patterns. **P26** is the one to read first: it is the pattern the 2026-11-24 supply findings most
> directly enable, and it changes an ISO 26262 engagement from assertion to pipeline.

## P26 🆕 — Compliance as CI output: MISRA/AUTOSAR evidence that regenerates on every commit

**The problem.** A client's ISO 26262 coding-standard compliance is today an **assertion** — a report
produced periodically by a paid static analyser, stale the moment it is written, and re-bought every
audit cycle. **P14** generates the *documents* via agent skills but never checks the *code*.

**What's new that makes this buildable:** a permissive MISRA/AUTOSAR checker maintained by GitHub.

**The stack, all byte-read permissive:**

| Role | Component | Grant |
|---|---|---|
| **Standard checking** | [github/codeql-coding-standards](https://github.com/github/codeql-coding-standards) — MISRA C/C++ **and AUTOSAR C++14** as CodeQL queries, 235★ | **MIT** |
| **MISRA C second opinion** | [WinterLabsHQ/maisha](https://github.com/WinterLabsHQ/maisha) — MISRA C / CERT C / BARR-C, 8★ ⚠️ young | **MIT** |
| **Requirement↔code↔test traceability** | [useblocks/sphinx-needs](https://github.com/useblocks/sphinx-needs) — 329★ | **MIT** |
| **Doxygen-native alternative** | [QuantumLeaps/spexygen](https://github.com/QuantumLeaps/spexygen) — 43★ | **MIT** |
| **Document generation** | `jherrodthomas/automotive-skills-suite` (76 builder/reviewer pairs) — **P14** | MIT |

**How to wire it:**

1. **Run CodeQL's coding-standards pack in the client's CI** against the ECU codebase. Output: a
   per-rule, per-file deviation set — machine-readable, regenerated per commit.
2. **Model requirements as `sphinx-needs` objects** in the repo. Each requirement gets an ID; each
   links to the code symbols implementing it and the tests covering it.
3. **Join the two.** A deviation now resolves to *which requirement it endangers*, which is the
   question an assessor actually asks — not "how many MISRA violations" but "which safety requirement
   is unevidenced."
4. **Hand the join to the P14 skill pair** to draft the deviation justification and the safety-case
   fragment. **A named human engineer signs each one** — the P14 rule is unchanged and non-negotiable.
5. **Publish the traceability matrix as a build artefact.** It regenerates; it does not get re-bought.

🔴 **The boundary you must state in the SOW, because it is where this pattern can mislead a client:**
**CodeQL is not a qualified tool under ISO 26262-8.** A qualified analyser's output is admissible to an
assessor on the strength of its qualification; CodeQL's output is **engineering evidence that still
needs a tool-qualification argument**, or confirmation by a qualified tool at the gate. **Sell this as
continuous evidence generation that collapses the cost of the qualified run — never as a replacement for
it.** Promising otherwise is the one way this pattern fails an audit (**N21**).

**Regions:** every region. **Strongest in EMEA**, where it feeds the **P20** duty map directly (an
automated MISRA/AUTOSAR evidence stream is exactly the "already discharged by existing evidence"
argument CLEPA makes), and in **APAC**, where GB 44721-2026's dated effect makes a regenerating
evidence pipeline worth more than a one-off report.

## P27 🆕 — Plant-floor asset-ops agent, bought as a harness

**The problem.** Plant-floor AI pilots stall because nobody can say whether the agent is *good*. **P22**
builds VDA-5-qualified inspection; it does not evaluate an agent that *acts* on inspection output.

**The stack:**

| Role | Component | Grant |
|---|---|---|
| **Agent harness + benchmark** | [IBM/AssetOpsBench](https://github.com/IBM/AssetOpsBench) — Industry 4.0 agent orchestration **and evaluation**, 2,483★ | **Apache-2.0** |
| **Vision / anomaly detection** | `open-edge-platform/anomalib` — 20+ algorithms, OpenVINO export, 6,414★ | Apache-2.0 |
| **Condition-monitoring tool surface** | [LGDiMaggio/predictive-maintenance-mcp](https://github.com/LGDiMaggio/predictive-maintenance-mcp) — MCP server, 118★ | **MIT** |
| **Datasets** | [kokikwbt/predictive-maintenance](https://github.com/kokikwbt/predictive-maintenance) — 177★ | **MIT** |

**How to wire it:** expose the client's historian, work-order system and `anomalib` inference endpoint
as **MCP tools** (the `predictive-maintenance-mcp` server is the reference shape). Run the agent inside
**AssetOpsBench**'s orchestration so that every proposed action — raise a work order, flag a batch, stop
a line — is **scored against the benchmark before it is wired to anything that acts.** Ship the
evaluation report as the pilot's deliverable, not a demo.

⚠️ **Two warnings.** First, **the line-stop action must be confirmation-gated** — the **P16** rule
applies on the plant floor exactly as in the cockpit: the agent's reasoning must not reach the actuator.
Second, **the dataset grant is a separate axis** (**N17**): check the licence of any benchmark data
before it touches a client deliverable.

**Regions:** **every region, and this is the one pattern that is equally sellable in all five** —
manufacturing is where the non-AV automotive money is, and LATAM has the installed base without the
regulatory overhead.

## P28 🆕 — Permissive EV battery estimator, simulator-trained

**The problem.** A client wants SOC/SOH/RUL estimation. The ML layer is 🟡 an **unmaintained long tail**
— 98 permissive repositories, none maintained (**N19**) — so there is nothing to adopt. But the
*expensive* parts, the physics and the embedded platform, are free.

**The stack:**

| Role | Component | Grant |
|---|---|---|
| **Physics simulator (training-data generator)** | [pybamm-team/PyBaMM](https://github.com/pybamm-team/PyBaMM) — DFN/P2D, SPM, SPMe, 1,742★ | **BSD-3-Clause** |
| **Embedded BMS platform** | [foxBMS/foxbms-2](https://github.com/foxBMS/foxbms-2) — Fraunhofer IISB, hw+sw, 512★ | **BSD-3** (sw) + CC-BY-4.0 (docs) |
| **Pack protocol corpus (brownfield)** | [patman15/BMS_BLE-HA](https://github.com/patman15/BMS_BLE-HA) ~20 vendors, 380★ · [fl4p/batmon-ha](https://github.com/fl4p/batmon-ha) 536★ | Apache-2.0 · MIT |
| **EV PID maps / field telemetry** | [nickn17/evDash](https://github.com/nickn17/evDash) — Hyundai/Kia/Renault EV, 186★ | **MIT** |
| **Model selection reference** | [FrankSuperG/electrochemical-battery-model-atlas](https://github.com/FrankSuperG/electrochemical-battery-model-atlas) | CC-BY-4.0 ⚠️ docs grant |

**How to wire it:**

1. **Parameterise a PyBaMM cell model** to the client's chemistry and form factor.
2. **Sweep it** — temperature, C-rate, depth-of-discharge, ageing — to synthesise a labelled degradation
   corpus. *This is the step that replaces the field data the client does not have, and it is the
   reason the long-tail gap is survivable.*
3. **Fit the estimator** on synthetic data; **calibrate on whatever real cycling data exists** (field
   data via `evDash`-style OBD/CAN logging, or the pack's own BMS via the protocol corpora).
4. **Deploy either greenfield on foxBMS** (BSD-3, so the estimator ships inside the BMS firmware) **or
   brownfield as a read-only estimator** alongside the incumbent BMS using the vendor protocol corpus.
5. **Validate against held-out real cycles, never against the simulator.** A simulator-trained
   estimator validated on simulator output measures nothing.

⚠️ **Quote this as a build, not an integration.** The simulator and platform are free and mature; the
estimator is bespoke work. **Say the split in the proposal** — it is the difference between a credible
estimate and a surprised client.

**Regions:** **EMEA first** — both anchors are EMEA-origin (Fraunhofer IISB; PyBaMM's community is
UK-centred), which answers a sovereignty question before it is asked. **APAC** second, where the
battery supply chain is.

## P29 🆕 — C-ITS message-layer deliverable, with the copyleft boundary drawn on purpose

**The problem.** This KB told you three days ago that all V2X work needs legal review in the SOW. That
was wrong (**`agents/top.md` W1**) and it was over-pricing a clean deliverable.

**The permissive core:**

| Role | Component | Grant |
|---|---|---|
| **ETSI ITS message encode/decode (CAM, DENM, CPM, VAM)** | [ika-rwth-aachen/etsi_its_messages](https://github.com/ika-rwth-aachen/etsi_its_messages) — ROS 2, RWTH Aachen **ika**, 83★ | **MIT** |
| **Cooperative-perception validation data** | [VjiaLi/V2U4Real](https://github.com/VjiaLi/V2U4Real) — CVPR 2026, vehicle-to-UAV, 75★ | **MIT** |
| **Standards-conformance agent surface** | [Nemeson/C-ITS-Expert](https://github.com/Nemeson/C-ITS-Expert) — validator, CLI + MCP, ⚠️ 1★ | **MIT** |
| **Transport** | `nanomq/nanomq` — MQTT for edge/SDV, 2,667★ *(held)* | MIT |

**How to wire it:** build the client's **message handling, validation and cooperative-perception fusion**
on `etsi_its_messages` inside ROS 2, transport over `nanomq`, validate against `V2U4Real`, and use
`C-ITS-Expert`'s validator **as a design reference for conformance checks you implement yourself** (1★
— do not take it as a dependency).

🔴 **Draw the boundary explicitly in the SOW, and put it in the architecture diagram:**

- ✅ **Message, validation, fusion, transport — MIT/permissive.** No legal review. Quote as
  build-on-open-source.
- ⛔ **Protocol stack — `vanetza` is CC-BY-NC.** Non-commercial. **Not a review item, a prohibition.**
  If the client needs a full ETSI stack, it is a commercial licence or a clean-room implementation, and
  that is a different project with a different price.
- ⚠️ **Simulation — `artery`, `veins`, `VaN3Twin` GPL-2.0; `mosaic` EPL-2.0.** Copyleft, but these are
  **tools, not shipped product**. Internal validation use is normally fine; **shipping or hosting a
  derivative is not.** This is the only part that needs legal review, and it is the cheap part.

**Regions:** **EMEA first** — ETSI C-ITS is the European standard and the anchor is a German
institute's, so the whole permissive core is EMEA-authored. Useful in **APAC** where China's V2X
deployment is large, with the caveat that Chinese C-V2X message sets differ from ETSI's.

## P30 🆕 — Licence remediation as a LATAM entry engagement

**The problem, measured.** **95 of the first 100 Hispanophone `automotriz` repositories carry no licence
file at all** (**N20**). No licence means **all rights reserved** — legally *less* usable than GPL. The
same statistic almost certainly describes a LATAM client's **internal** repositories, because it
describes the regional development culture, not just its public output.

**Why this is the right first engagement in the region:** it needs no regulatory trigger (LATAM has no
dated AI obligation — see `intel/market.md` → LATAM), it is cheap, it is fast, and it produces a finding
the client cannot dismiss: *their own code cannot be lawfully reused inside their own group.*

**The stack — the method is already built as P13, which this reuses rather than reinventing:**

| Step | Instrument | Note |
|---|---|---|
| **1. Enumerate** | `gh api -X GET search/repositories` + the client's own forges | 🔴 **Query in Spanish and Portuguese.** English-only enumeration is what hid 2,458 repositories from this KB for six passes. |
| **2. Liveness** | `git ls-remote --symref` | Returns the **default branch**, which step 3 needs |
| **3. Byte-read the grant** | `raw.githubusercontent.com/<o>/<r>/<branch>/<file>` | Probe `LICENSE`, `LICENSE.md`, `LICENSE.txt`, **`LICENCE`**, `COPYING`, **`LICENSE-MIT`**. ⚠️ **The British spelling and the Rust convention are both real and both produce false "no licence" verdicts.** |
| **4. Classify** | **none / permissive / weak copyleft / strong copyleft / non-commercial / dual-per-file** | ⚠️ Match **LESSER first** — LGPL's own text contains the string "GNU GENERAL PUBLIC LICENSE". ⚠️ A metadata-only grant (`package.json` with no LICENSE file) is **"declared", not "byte-read"** |
| **5. Remediate** | Add grants with author consent; quarantine what cannot be cleared | The deliverable |

**The deliverable:** a per-repository grant register, a remediation plan, and a **permissive baseline
policy** for new work. **Then the diligence relationship is in place before the AV/ADAS conversation
starts** — which, given Brazil's PL 2338/2023 will not be in force before 2027–2029, is the realistic
sequence.

⚠️ **Honest limit:** `gh api users/{login}` is **403** in this environment, so **author
location/affiliation cannot be verified programmatically here**. Origin is inferred from language and
institution. For a real engagement the client supplies the authorship facts — do not infer them in a
deliverable.

**Regions:** **LATAM** primarily. The *method* is global (**P13**), but the 95%-unlicensed statistic is
what makes it a door-opener specifically here.

---

## P31 🆕 — Charging conformance-and-evidence factory (NA + EMEA)

**Why this is the first recipe in the plane.** The regulation names protocol versions and a numeric uptime
target (**N29**), so the deliverable is not firmware — it is **a reproducible evidence file** that a named
duty is met. That is quotable as fixed scope.

**The duties this discharges.** 23 CFR 680.108 (**OCPI 2.2.1** network-to-network), 23 CFR 680.116
(**>97% average annual uptime** per port), California CEC (**OCPP 2.0.1** reporting for ports installed
on/after 2026-09-28), AFIR (**ISO 15118-20** by 2027-01-01, contested — scope against the duty, not the date).

**Wiring — all Apache-2.0, all byte-read (see `repos/foundations.md`):**

1. **Station side** — `EVerest/everest-core` (Apache-2.0, 11,356 B). The modular runtime. *Note its star
   count is unavailable: `search/repositories` 422s on this slug. Do not let that read as "small".*
2. **ISO 15118 -2/-20/-8** — `ecog-io/iso15118` (Apache-2.0, 250★) and SLAC via `ecog-io/pyslac`
   (Apache-2.0, 56★) or `EVerest/libslac` (Apache-2.0, 19★). **-20 is the piece the EMEA 2027 duty turns on.**
3. **Back office** — `citrineos/citrineos-core` (Apache-2.0, 311★), OCPP 2.0.1-native, LF Energy governed.
4. **Roaming duty** — `citrineos/citrineos-ocpi` (Apache-2.0, 23★). Small repo, but it is the one that
   maps onto 680.108.
5. **Schema gate in CI** — `solidstudiosh/ocpi-schema` (Apache-2.0, 20★) generates JSON-Schema for
   OCPI 2.1.1+. Fail the build on a non-conforming payload; the CI log *is* the evidence.
6. **Fleet you do not own** — `SAP/e-mobility-charging-stations-simulator` (Apache-2.0, 231★) and
   `monta-app/ocpp-emulator` (Apache-2.0, 182★) to generate load and uptime series at scale.
7. **Wire-level proof** — read the V2G exchange with `Sevenstax/FreeV2G` (**MIT**, 1,181 B — the API hides
   this grant). ⚠️ **Do not ship the Wireshark dissectors in the product**: `dsV2Gshark`'s `Wireshark/`
   directory is **GPL-2.0** and `ChargePoint/wireshark-v2g` resolves to **LGPL-3.0** via `openv2g`. Use
   them as **engineers' desk tools**, outside the deliverable boundary.

**Explicitly excluded from the fork.** `steve-community/steve` (GPL-3.0, 1,154★) and
`dallmann-consulting/OCPP.Core` (GPL-3.0, 304★). If a client already operates SteVe, integrate it
**across a process boundary** and do not derive from it.

**Deliverable.** A signed evidence pack: protocol-version conformance matrix, OCPI schema CI run,
simulated-fleet uptime series against the 97% line, and a duty→artefact mapping table. **Not** a charger.

**Stated assumption.** AFIR enforcement is per member state and this pass found **no national penalty
amounts and no 2026 enforcement cases**; price the evidence pack on the duty text, not on an expected fine.

---

## P32 🆕 — The operator-side charging agent (build, because it does not exist)

**This recipe exists because of a measurement, not a hunch.** `charging station agent license:apache-2.0`
returns **0**. The nine real MCP servers in this plane are all **driver-side**, median 1★ (**N24**). There
is nothing to compose on the operator side — so this is a build, on top of a protocol layer that is
already permissive and already solid.

**Wiring:**

1. **Device abstraction** — `evcc-io/evcc` (**MIT**, 7,654★). The single most valuable artefact in the
   plane for this purpose: it already normalises wallboxes, inverters, meters and vehicles across vendors.
   Do not rebuild this.
2. **Protocol spine** — `citrineos/citrineos-core` (Apache-2.0) for OCPP 2.0.1, or a language-matched
   library: `mobilityhouse/ocpp` (MIT, 1,052★, Python), `lorenzodonini/ocpp-go` (MIT, 376★, Go),
   `ChargeTimeEU/Java-OCA-OCPP` (MIT, 380★, Java), `matth-x/MicroOcpp` (MIT, 547★, embedded).
   ⚠️ `c-jimenez/open-ocpp` is **LGPL-2.1 on branch `develop`** — dynamic linking only.
3. **The decision core is NOT a language model.** Setpoints come from the optimization tier:
   `StavrosOrf/EV2Gym` (MIT, 250★) for the V2G/large-scale environment, `StavrosOrf/DT4EVs` (MIT, 23★)
   for offline RL, `StavrosOrf/EV-GNN` (MIT, 34★) for scaling, `TUMFTM/REVOL-E-TION` (Apache-2.0, 17★)
   for site-level energy optimization. **The model never chooses a current or a price**; it explains,
   drafts and routes. This follows the KB's standing rule that every credible automotive agent design has
   a human gate — here the gate is on **anything that moves power or money**.
4. **Agent surface** — model the MCP tool boundary on the nine byte-read-MIT driver-side servers
   (`javierojan/askacharge-mcp` is the only one that *operates* chargers rather than reading them).
   Treat them as **interface references, not dependencies** — single-author, median 1★.
5. **Test harness** — `shiv3/ocpp-cp-simulator` (Apache-2.0, 48★), written for exactly this: testing AI
   agents against OCPP. Build the eval before the agent.

**Hard exclusion.** `nader0913/ocpp-rag` (48★) is the most-starred OCPP knowledge/RAG/MCP repo and is
**PolyForm Noncommercial 1.0.0** — the API reports `NOASSERTION`, so nothing warns you. If the client's
team has already vendored it, that is a remediation finding.

**Risk to state in the SOW.** Three of the four optimization repos have the **same single maintainer**.
Fork-and-own them at the start of the engagement; do not treat them as an upstream.

---

## P33 🆕 — Chile interoperability registration, as a LATAM entry engagement

**Why Chile and why now.** LATAM is usually the advisory-shaped region in this KB. In *this* plane it is
the opposite: Chile has a **named protocol mandate, a registration platform and a dated 2026 instructivo**
— the hardest fact pattern of the four regions (**see `intel/market.md` → LATAM**).

**The instruments.** Ley 21.305 empowers the Ministry of Energy to regulate charging interoperability.
**Reglamento de Interoperabilidad DS 12** (Diario Oficial, May 2023) establishes the platform and rules
that **private-access chargers may not be used to provide charging service, nor be registered**. SEC's
instructivo — **Resolución 27547 EXENTA** (Oct 2024), superseded by **Resolución Exenta N°41458** (2026) —
fixes how to register and integrate. **Pliego Técnico 15 requires the communication protocol to be
OCPP 1.6 or higher.**

**Wiring:**

1. **Protocol floor is 1.6, not 2.0.1** — so `ChargeTimeEU/Java-OCA-OCPP` (MIT, 380★),
   `mobilityhouse/ocpp` (MIT, 1,052★) or `lorenzodonini/ocpp-go` (MIT, 376★) all clear the bar.
   `citrineos/citrineos-core` (Apache-2.0, 311★) clears it too and leaves 2.0.1 headroom —
   **recommended** where the client expects to grow into California-style 2.0.1 reporting.
2. **The platform feed** — DS 12 requires current charge-point information: operating status, hours,
   payment means, tariffs and available connectors. That is an OCPP→registry adapter plus a
   status/tariff projection, not an AI problem. Build it deterministically.
3. **Scoping rule that cuts in the client's favour** — the **private-charger exclusion** bounds the
   estate that must be registered. Establish which of the client's sites are public-access *first*; it
   is usually the single biggest lever on project size.
4. **AI layer, where it earns its place** — tariff/status reconciliation across sites, and a Spanish-language
   operator assistant over the registry. ⚠️ Note the fleet-wide finding that Spanish-language repo supply
   is persistently near zero: **choose embeddings by the language of the operator's own data**, not by
   benchmark rank.

**Deliverable.** A registration dossier against Resolución Exenta N°41458 + the conforming data feed.
**Target context:** the national roadmap targets **≥6,500 public charge points** (BCN, July 2026).

**Declared gap, stated to the client up front.** For **Brazil**, this pass found **zero** charging
interoperability regulation across its search legs; Mexico's **CRE A/108/2024** reached us only through a
*Chilean* parliamentary document (secondary). Neither is a basis for a fixed-scope registration project
yet. **Chile is the only LATAM country in this plane with a quotable compliance deliverable today.**

---

## P34 🆕 — Battery-passport readiness on Tractus-X, with the 18 Feb 2027 date as the scope boundary (EMEA-first, global supply)

**The duty, stated precisely.** Art. 77 of **Reg. (EU) 2023/1542** requires a digital battery passport
from **18 February 2027** for **EV batteries, LMT batteries and industrial batteries above 2 kWh**. The
responsible party is **the economic operator that places the battery on the EU market or puts it into
service** — so a Mexican or Brazilian cell/pack supplier selling into an EU OEM is inside the scope of
its customer's duty even though the regulation does not bind it directly. Two facts bound the work
usefully: there is **no retroactivity** (a battery placed on the market before 18 Feb 2027 never needs a
passport), and the **initial 2027 content set is thin** — identification, type, model and key technical
characteristics, with delegated acts to expand it later. Commission guidance **v3.2** currently marks
certain information groups *not to be filled in* at launch, pending the Omnibus provisions.

**Why that shape is commercially attractive:** the deadline is hard, the first-wave data requirement is
small, and the expansion is guaranteed. That is a **phase-1 fixed-price, phase-2 retainer**.

**The stack — every row byte-read Apache-2.0 or MIT:**

| Layer | Repo | Licence |
|---|---|---|
| Dataspace connector | [`eclipse-tractusx/tractusx-edc`](https://github.com/eclipse-tractusx/tractusx-edc) | Apache-2.0 |
| Whole-stack install | [`eclipse-tractusx/tractus-x-umbrella`](https://github.com/eclipse-tractusx/tractus-x-umbrella) | Apache-2.0 |
| Passport app | [`eclipse-tractusx/digital-product-pass`](https://github.com/eclipse-tractusx/digital-product-pass) | Apache-2.0 |
| Twin registry | [`eclipse-tractusx/sldt-digital-twin-registry`](https://github.com/eclipse-tractusx/sldt-digital-twin-registry) | Apache-2.0 |
| Semantic models | [`eclipse-tractusx/sldt-semantic-models`](https://github.com/eclipse-tractusx/sldt-semantic-models) | CC-BY-4.0 (non-code, house rule) |
| AAS runtime | [`eclipse-basyx/basyx-java-server-sdk`](https://github.com/eclipse-basyx/basyx-java-server-sdk) | MIT |
| Conformance proof | [`admin-shell-io/aas-test-engines`](https://github.com/admin-shell-io/aas-test-engines) | Apache-2.0 |
| Passport validation | [`artiso-ai/dppvalidator`](https://github.com/artiso-ai/dppvalidator) | MIT |
| Integration surface | [`tractusx-sdk`](https://github.com/eclipse-tractusx/tractusx-sdk) (PyPI) | Apache-2.0 |

**Wiring.**
1. `helm install` the **umbrella** chart → a working connector + registry + portal in one namespace. This
   is the demo environment; do not hand-assemble it.
2. Model the battery as an **AAS submodel** using `sldt-semantic-models` + `admin-shell-io/submodel-templates`.
   Register the twin in the **Digital Twin Registry**.
3. Expose it through `tractusx-edc` under a Catena-X policy; consume it in `digital-product-pass`.
4. **Gate the pipeline on `aas-test-engines` + `dppvalidator` in CI** — this is the P26 "compliance as CI
   output" principle applied to a passport: the client's evidence is a regenerated test report, not a
   consultant's memo.
5. The **state-of-health** field is where this stops being a data-modelling job: SoH must be computed and
   refreshed over life. Reuse Layer H (`foxBMS`, EV/battery modelling) from `repos/foundations.md` for the
   estimator and feed it in as a dynamic submodel property.

**Two risks to put in the SOW in writing.**
- `digital-product-pass` was **last pushed 2025-09-18**. Verify it against the current release train
  (`R26.06`-style) before committing to a fixed scope; budget an upgrade spike.
- **Do not build on `sovity/edc-ce`** (96★, the most obvious "community edition"). Its default grant is
  **Elastic License 2.0**, which forbids offering the software to third parties as a managed service — a
  direct breach for a Globant-hosted deployment. Use `tractusx-edc`. See `agents/top.md` **T1**.

---

## P35 🆕 — Supplier-onboarding agent: PDF datasheet → AAS submodel → dataspace (the only agent row in this plane with real leverage)

**The problem, in the client's words.** Tier-2 and Tier-3 suppliers hold their part data in **PDF
datasheets and spreadsheets**. Catena-X needs it as typed AAS submodels. Today that conversion is manual,
and it is the single largest cost line in every onboarding programme —
`industry-core-hub`'s own pitch is *"onboarding to first data exchange in days, not months,"* which is an
admission that months is the status quo.

**The stack:**

| Role | Repo | ★ | Licence |
|---|---|---|---|
| PDF → AAS extraction | [`eclipse-basyx/basyx-pdf-to-aas`](https://github.com/eclipse-basyx/basyx-pdf-to-aas) | 17 | ✅ MIT |
| AAS tool surface for the agent | [`SAP/aas-mcp-server`](https://github.com/SAP/aas-mcp-server) | 9 | ✅ Apache-2.0 |
| AAS API specs (required input) | [`admin-shell-io/aas-specs-api`](https://github.com/admin-shell-io/aas-specs-api) `v3.2.0` | — | 📄 CC-BY-4.0 |
| AAS backend | [`basyx-java-server-sdk`](https://github.com/eclipse-basyx/basyx-java-server-sdk) or [`FA³ST`](https://github.com/FraunhoferIOSB/FAAAST-Service) | 84 / 94 | ✅ MIT / Apache-2.0 |
| Orchestration into the dataspace | [`industry-core-hub`](https://github.com/eclipse-tractusx/industry-core-hub) + [`tractusx-sdk`](https://github.com/eclipse-tractusx/tractusx-sdk) | 26 / 15 | ✅ Apache-2.0 |
| Human review UI | [`basyx-aas-web-ui`](https://github.com/eclipse-basyx/basyx-aas-web-ui) | 35 | ✅ MIT |
| Docs retrieval for the build team | [`artamrj/tractusx-rag-mcp`](https://github.com/artamrj/tractusx-rag-mcp) | 1 | ✅ Apache-2.0 |

**Wiring.**
1. `pdf2aas.convert('datasheet.pdf', eclass_id, 'submodel.json')` — pypdfium2 preprocessing, **ECLASS**
   dictionary for the property vocabulary, `PropertyLLMSearch` extractor, Technical Data submodel
   generator. Swap its default OpenAI client for the engagement's model.
2. Build the **AAS MCP server** from the IDTA Part 2 specs at tag `v3.2.0` (bundle one file per API) and
   point it at the AAS backend. The agent now reads and writes twins **through a standard API**, not a
   bespoke integration.
3. **Mandatory human gate.** Extracted properties land in `basyx-aas-web-ui` for supplier sign-off before
   publication. An extraction error here propagates into every consumer in the dataspace — treat it like
   P10's technician gate, not like a chatbot.
4. Publish via `industry-core-hub`; assert conformance with `aas-test-engines` in CI.

**Why this is the defensible bit.** The platform is settled and free; **this conversion step is where the
margin is**, and the agent tier here has a median of 3★ (see **N32**) — there is nothing to buy. Scope it
per-supplier-per-part-family with a measured extraction-accuracy SLA, since `pdf-to-aas` gives a testable
output and `tractusx-rag-mcp` demonstrates the norm of publishing an eval (100 % Hit@8, 98 % faithfulness,
80 % correctness on 60 questions) — **hold your own extraction agent to a published number too.**

---

## P36 🆕 — Tractus-X Accelerator: a funded, dated entry route for SMEs (EMEA, and it is a genuine filing counter)

**The opportunity, with dates.** The **Tractus-X Accelerator** entered its implementation phase on
**1 September 2026** and runs **2026–2029**, funded by the **German Federal Ministry for Economic Affairs
and Energy (BMWE)**, with **ARENA2036, Catena-X Automotive Network, Fraunhofer ISST and IDSA** as
partners. Its explicit target is **SMEs and mid-caps in automotive and adjacent sectors (including machine
building) that are not yet active in Catena-X**, and **applications are due by the end of December 2026.**

**Why this matters more than a market-size figure.** This KB's standing complaint about EMEA is that the
AI Act gives **duties without a filing counter** — nothing with a date and a queue to join. The
Accelerator *is* that counter: a named programme, a named funder, a closing date **five weeks out**, and a
cohort of exactly the companies that need integration help and cannot staff it. Pair it with **N33**'s now-dated
AI Act timeline and EMEA has, for the first time in this KB, both a duty calendar and an entry queue.

**The deliverable Globant can quote this quarter:** a **two-week Catena-X readiness assessment** producing
(a) the client's data-sharing use case mapped to a named CX standard — `puris` demonstrates the
vocabulary: *CX-0118, CX-0120, CX-0121, CX-0122, CX-0145, CX-0146, CX-0018*; (b) a running **umbrella**
deployment as proof of technical feasibility; (c) the gap list between their PLM/ERP data and the required
AAS submodels — i.e. the P35 backlog, priced.

**Demo environment, cheapest legitimate route:**
[`awslabs/minimum-viable-dataspace-on-aws`](https://github.com/awslabs/minimum-viable-dataspace-on-aws)
(**MIT-0** — *no attribution condition at all*, 945 B) or
[`awslabs/dataspace-connector-on-aws`](https://github.com/awslabs/dataspace-connector-on-aws)
(Apache-2.0, pushed 2026-11-21). For a non-automotive mobility variant, the same protocol stack runs under
[`Mobility-Data-Space/mds-edc`](https://github.com/Mobility-Data-Space/mds-edc) (Apache-2.0).

**Honest limits.** Catena-X's own scale figures — *21 KITs and >40 certified services* — are **as of
12/2025** and come from a partner presentation; **no independent 2026 data on how many companies are
actively exchanging data was reachable this pass.** Quote the programme's dates (primary, specific) and the
repository counts (measured: 83 repos in `org:eclipse-tractusx`), **not** the ecosystem adoption claims.
