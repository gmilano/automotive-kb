---
industry: automotive
region: Global
updated: 2026-11-19
---

# 📡 Trends — Automotive

> Current trends, updated 2026-10-31. Project and vendor self-reported performance figures are labelled
> as such. Dates name their instrument.

## 🆕 New on 2026-11-19 — four trends, and the first one corrects a claim this file has made three times

### N6 — The automotive agent layer is 2,907★, and it lives in the engineering office, not the vehicle

**Supersedes:** the "0–8★", then "0–26★" ceiling recorded in **N2** (2026-10-31) and carried forward on
2026-11-13. Those numbers were correctly counted and wrongly scoped.

[`jherrodthomas/automotive-skills-suite`](https://github.com/jherrodthomas/automotive-skills-suite) —
**MIT, 2,907★, 141 forks** — is 76 builder+reviewer agent-skill pairs that emit the **ISO 26262 /
ISO/SAE 21434 / ISO 21448 SOTIF / Automotive SPICE / AIAG-VDA (APQP, DFMEA, PFMEA, control plans, PPAP)**
artefact pack as `.xlsx`, plus CAN/LIN/FlexRay/Ethernet and K-Matrix work, UDS/ODX/DEM diagnostics,
AUTOSAR Classic and Adaptive, A2L/DCM calibration, MBSE/SysML and V&V traceability matrices.

**Why every prior pass missed it:** the searches were all shaped like the *vehicle* — "in-car agent",
"diagnostics MCP", "driving policy". The query that finds it is shaped like the *standard*:

```
AUTOSAR OR ISO26262 OR "ISO 21434" in:name,description,readme pushed:>2026-08-01 stars:>15
```

**Method change for every future pass of this KB: search the standard, not only the protocol, and never
the buzzword.** The same query also returned `iDoka/awesome-canbus` (CC0, 3,571★),
`ebroecker/canmatrix` (BSD-2, 1,093★), `eclipse-iceoryx/iceoryx` (Apache-2.0, 2,212★) and `autoas/as`
(965★) — four more repos above 900★ that five previous passes never surfaced.

**The commercial reading:** the open automotive agent value is in the **artefact pack a programme
ships**, not in the car. That is consultable, reviewable, billable work with no vehicle access required
— and it is the same deliverable in all four regions (see **N9**).

⚠️ **And the risk, stated once:** the repository page carries **no "not certified" disclaimer** and no
requirement that a qualified engineer validate outputs, while advertising coverage of six standards and
the word "compliance". A generated safety case is a **draft with a named owner**, or it is a liability.

### N7 — "Assurance-as-code" became a category in six weeks, and the honest one is the small one

Three independent MIT projects, none older than 2026-05-01:

| Project | ★ | Epistemic posture |
|---|--:|---|
| `jherrodthomas/automotive-skills-suite` | 2,907★ | Advertises coverage of six standards. **No disclaimer.** |
| `jherrodthomas/LionDriver` | 65★ | **Publishes 42 unresolved defeaters against its own safety case** and states no compliance is claimed because no assessment was performed |
| `Lieubk/automotive-safety-security-assurance-kit` | 2★ | *"The toolkit drafts and checks; people decide"* — created **2026-11-19** |

**LionDriver is the template; the skills suite is the tool.** LionDriver ships a living safety case of
**36 claims and 50 evidence items with 0 accepted and 42 open defeaters**, **89 V-cycle work products
(85 draft, 4 skeleton)**, citations to ISO 26262 / ISO 21448 / ISO/SAE 21434 / **ISO/PAS 8800** /
**UL 4600** / Automotive SPICE, a statement that no release build exists and that development builds
must not be used on public roads outside a controlled test regime, a named first *evaluated*
configuration (**Toyota Corolla E210**) with **no configuration yet assurance-supported**, automated
checks of inherited openpilot safety code running in CI but **not yet reviewed as evidence**, and a
field-monitoring process whose first live case is tied to **NHTSA PE26007**.

**The trend is not that the tooling exists. It is that publishing your own open defeaters has become a
credibility move.** Expect clients to start asking for the defeater list, and expect the vendors who
cannot produce one to lose on that question. Globant should arrive with one.

**Two data points is coincidence; three in six weeks is a category.** Watch for a fourth.

### N8 — Agents now actuate real vehicles, and the safety envelope — not the model — is the published artefact

[`aditya-ramabadran/drivingbench_harness_code`](https://github.com/aditya-ramabadran/drivingbench_harness_code)
— **MIT, 63★** — closes the gap recorded in earlier passes ("no benchmark where an LLM agent actually
controls a vehicle"). An MCP server named `drivingbench_sandbox` exposes exactly three tools —
`observe()`, `set_motion()`, `stop_now()` — and **chat models (Codex, Claude Code, Cursor), API models
(OpenRouter, Gemini) and trained VLA policies served over HTTP all drive the same course through the
same interface.** Real platforms: **comma four** on pinned openpilot `59fcd340`, **Toyota TSS2**,
**Tesla Model 3 HW3**. The simulator is the course as a **Gaussian splat** running the real control
stack, scored identically to the car.

**The three design decisions worth copying into any Globant vehicle-agent architecture:**
1. **The `reason` string is logged for the operator and never sent to the controller.** Prompt text
   cannot become actuation. This is the cleanest statement of the agent/actuator boundary found in this
   KB.
2. **`observe()` returns image age.** Staleness is an input, not an assumption.
3. **Layered limits:** operator-set ceiling (default **3 m/s**), **hard cutoff at 6 m/s**, command
   expiry, and cancellation on brake / gas / steering override / disengagement. Four independent
   stoppers, not one.

⚠️ **No scores and no leaderboard are published; Releases is empty.** So **N8 is a feasibility trend,
not a capability trend.** Do not quote a DrivingBench result; `drivingbench.com` was not fetched this
pass.

**Corollary, and it is the one with budget attached:** this is the shape of the *evaluation harness*
that every ADAS client will need once a safety case is a regulatory deliverable (**see N9**). The
harness is more sellable than the model.

### N9 — One artefact factory, four regional buyers: regulation diverged in form and converged in output

For five passes this file treated regional regulation as four separate compliance stories. 2026 ended
that. **UNECE WP.29's approval of the ADS Global Technical Regulation (22–26 June 2026, all contracting
parties, co-developed by China, the EU, the UK, the US, Canada and Japan)** means the *technical target*
is now shared, while **authorisation stays national**. Layer that over what each region is actually
buying:

| Region | The instrument that pays for it | The deliverable |
|---|---|---|
| **North America** | **15 of the 2026 NHTSA/FMCSA rulemakings are AV-focused**; SELF DRIVE Act 2026 (H.R. 7390) reported to require a **safety case for SAE L3–L5**; NHTSA **EA26002** (~3.2M vehicles) shows enforcement is live; Zoox's first-ever FMVSS robotaxi exemption shows the exemption path works | Safety case + **field-monitoring evidence** |
| **EMEA** | EU AI Act (timeline contested), absorbed through **UNECE type-approval**; OEMs with **UNECE R151** docs must add **bias testing and AI Act risk-management language** | The **delta** on top of existing type-approval |
| **APAC** | The GTR China co-led, **plus stricter domestic rules**: public-beta ban, marketing-terminology limits, **heavily regulated OTA**; **Japan requires remote monitoring for all L4**; **Korea has issued accident-decision ethics guidelines** | Release-engineering evidence, OTA governance, remote-ops software, an **ethics rationale document** |
| **LATAM** | **Nothing mandates it.** Binding constraints are **LGPD** and **USMCA (review July 2026)** | **Export-readiness** for suppliers shipping into the other three regions |

**The trend: the artefact is the same in all four; only the buyer's reason differs.** That makes the
assurance factory of **N6/N7** a single reusable asset rather than four regional builds — and it makes
**LATAM sellable on a compliance story even though LATAM has no compliance mandate**, because the
Bajío's customers are in North America.

⚠️ **Source discipline:** every regulatory date above is from a law-firm briefing, a compliance-vendor
page or a trade outlet. **No primary register was fetched this pass.** Confirm once before any client
deck. The EU AI Act timeline specifically remains **three-way contested** (2 Aug 2026 / Annex III to
2 Dec 2027 via Regulation (EU) 2026/1744 / Omnibus adopted June 2026) — six days after this file first
recorded the conflict, it has not resolved.

### 🆕 Three smaller movements worth recording

- **The research tier became licence-safe by convention.** Of the 14 new driving-policy / world-model
  rows admitted this pass, **11 are Apache-2.0**, 1 is MIT, 2 have none. Two passes ago the no-licence
  rate in this tier was the single largest obstacle to using it. It is now the exception. **This
  materially lowers the cost of a model-selection engagement** (**P9**).
- **openpilot is unbundling from comma's hardware.** `zoompilot/jetlink` (MIT) runs openpilot's large
  driving model on **Jetson Orin Nano, macOS, iOS, Android and CUDA laptops** with only a comma device
  and a USB3 cable — and carries **40 forks on 57 stars**, a build signal rather than a bookmark
  signal. With `YassineYousfi/openpilot.distill` (MIT) and `Sherin-SEF-AI/Lyne-ADAS` (MIT, on-device
  Android ADAS), "can a real driving model run on the client's compute?" has become an integration
  question. **This is the supply-side mirror of the Mercedes × Liquid AI on-device programme** — the
  direction of travel in both the OEM tier and the open tier is **small, local, no cloud fallback**.
- **The vehicle-data MCP convention is now in the code, not just the README.** `wtfault-scanner`
  (*"never makes anything up"*, every number clickable to raw bytes) and `CanLab` (**injection is
  bench-only and stays disarmed until armed**) are the reference implementations. `cobanov/teslamate-mcp`
  (MIT, **142★**) is now the category leader at 5× the previous high. **T8** (every credible automotive
  agent has a human gate) is confirmed from the supply side.

### 🔴 Gaps opened or closed on 2026-11-19

**Closed:**
- *"No benchmark where an agent actually actuates a vehicle"* → **closed** by DrivingBench (**N8**),
  with the caveat that no scores are published.
- *"The automotive agent category has no large repo"* → **closed, and the earlier claim corrected**
  (**N6**).
- *"No open SysML v2 automotive systems-engineering base"* → **closed** by `de4sdv/DE4SDV`
  (Apache-2.0).

**Still open, re-measured this pass with the query stated:**
- **EV charging / battery AI:** `EV battery charging AI … stars:>15 pushed:>2026-08-01` → **0 repos.**
- **Plant-floor quality / inspection AI:** `… stars:>3 pushed:>2026-06-01` → **0 repos.** The nearest
  asset is `aws-samples/sample-manufacturing-automotive-ai-toolkit` (**MIT-0**, 19★) — samples, not a
  platform.
- **Fleet telematics:** **2 repos** above 5★ in the last quarter. Fifth pass.
- **DMS:** 408 repos, **top star count 5**, nearly all unlicensed. Fifth pass. Now a measured finding.
- **LATAM-origin supply:** **zero** across eleven queries. Fifth consecutive snapshot.
- **Model weight licences:** `huggingface.co` unreachable from this session. **None verified
  first-hand**, this pass or any previous pass.

**Newly opened:**
- **Primary-register verification is now the binding constraint on this file's regulatory content, not
  search coverage.** Three incompatible AI Act timelines have survived two passes. The next pass should
  spend its budget on one primary source (Official Journal for Regulation (EU) 2026/1744) rather than
  on more secondary reading.
- **Licence-unclassified high-star repos are accumulating:** `AtsushiSakai/PythonRobotics` (**30,951★**,
  `NOASSERTION`), `autoas/as` (965★, the only substantial open AUTOSAR BSW), `autowarefoundation/AWSIM`
  (765★, confirmed **bespoke licence**, *not* Apache-2.0), `openremote/fleet-management` (51★,
  unclassified for five passes). **A licence-resolution pass on these four would unblock more
  engagement surface than any new search.**

## 🆕 New on 2026-11-13 — three trends, and the first one supersedes a standing conclusion

### N3 — Open automotive AI crossed from "research models" to "a shippable product stack"

**The evidence.** In three days (10–12 Nov 2026) the Autoware Foundation published
[`vision_pilot`](https://github.com/autowarefoundation/vision_pilot) — **Apache-2.0, 927★, 196 forks,
4,282 commits** — described in its own README as *"a productionizable and safety certifiable
implementation of an open-source L2 ADAS system."* It ships **ACC, FCW, AEB, LKAS, LDW, ISA and
single-lane hands-free highway Autopilot**, **mapless**, from **a single 1–2 MP monocular camera** on
**ONNX Runtime, GPU or CPU**. Around it: `agnocast` (zero-copy ROS 2 IPC, 212★, 1,258 commits),
`autoware-safety-island` (ARM SoC, 608 commits), `scene_3d` and `ego_lanes` (perception),
`autoware.trucks` (freight charter), `alpamayo-autoware` (foundation-owned Alpamayo fork).

**What it supersedes.** Four passes of this KB concluded that *"the buildable open assets in automotive are
driving policies and SDV infrastructure"* — i.e. **research models and middleware, with the product layer
closed.** That conclusion is now obsolete at the L2 tier. There is an open product layer.

**Why it is a trend and not a release.** Three signals distinguish them: a **feature list expressed in
regulatory vocabulary** (AEB, ISA, LDW are homologation terms, not research terms); a **certification
roadmap** naming **ISO 26262 and ISO 8800**; and **silicon board support** (`openadkit-rcar-x5h`, Renesas
R-Car X5H). Research projects do not publish board support for mainstream automotive SoCs.

**Implication for an engagement.** The answer to *"can we build ADAS on open source?"* changes from "only
the research scaffolding" to "there is a stack with the features, and the gap is integration,
homologation evidence and your sensor set." ⚠️ **"Certifiable" is aspiration, not status** — and the
current input is one narrow-FOV camera with no radar until the roadmap lands. Pitch an **L2 base**, never
an L3 shortcut.

### N4 — The open automotive AI supply chain is APAC-led, which reframes every region's engagement

Every pass of this KB has placed **APAC as the largest automotive AI market**. This pass places it as the
**producer of the open supply**: the entire release wave above comes from the **Autoware Foundation**,
anchored by **TIER IV (Japan)**; **Qwen-Drive-1.0** is Alibaba's; **Senna (IJCV 2026)** is HUST's. Against
that, NVIDIA's Alpamayo line is now **forked into the foundation** (`alpamayo-autoware`) rather than
consumed from the vendor.

**Why Japan specifically.** Three things coincide: a **light-touch domestic regime** (the AI Promotion Act,
in force since June 2025, is a framework law **with no penalties**), a national industrial strength in
**safety-critical engineering and Tier-1 integration**, and a vendor-neutral foundation with OEM
membership. `autoware-safety-island` plus an ISO 26262/8800 roadmap is that combination expressed as code.

**Implication.** Upstream partnership and contribution strategy belongs in APAC **regardless of where the
client sits**. A North American or EMEA ADAS engagement now has an APAC dependency in its supply chain —
which is a governance fact to put in front of a client before they discover it, and an argument for
contributing upstream rather than forking privately.

### N5 — The licence-defect rate in this industry is high enough to be a service line, and it fails in both directions

This pass probed 19 repositories and **six carried a licence defect** — roughly a third:

| Defect | Specimen | Shape |
|---|---|---|
| **No licence at all, inside a major foundation** | `autoware_latent_drive` (42★) | No field, no README statement, `LICENSE`/`.md`/`.txt`/`license.rst` **all 404** |
| **README claims MIT, no file** | `petrpatek/obd2-mcp-server` (12★) | Third instance of this exact defect in this KB |
| **No licence + gated on proprietary software** | `tars-car-mcp` (0★) | Needs the closed TARS desktop app |
| **Secondary source claims MIT; repo is AGPL-3.0** | `idurar/idurar-erp-crm` (9.0k★) | Strong copyleft presented as permissive |
| **Secondary source claims Apache-2.0; repo is EPL-2.0 *and frozen*** | Huly / `hcengineering/platform` (28.1k★) | Wrong licence **and** abandoned |
| **MIT badge with an undisclosed commercial carve-out** | `open-mercato` (1.9k★) | `packages/enterprise` is not MIT |

**And the inverse defect, which is new and just as expensive.**
[`autoware-safety-island`](https://github.com/autowarefoundation/autoware-safety-island) shows as
**"Other"** in GitHub's org listing purely because its licence file is named **`license.rst`**. Read raw,
it is **verbatim Apache-2.0**. A pipeline that trusts the label **silently discards** a usable, 608-commit
safety repository — and silent loss is harder to catch than a false positive, because nothing looks wrong.

**The operational rule this hardens into:** *fetch the file; the README is not a grant, the search summary
is not a grant, the org's reputation is not a grant, and GitHub's label is not a verdict in either
direction.* **Of four ERP/CRM licence claims probed this pass, exactly one held as stated.**

**Commercially:** three of four ERP/CRM bases and one in three repos overall carrying a licence defect is
not a curiosity, it is a diligence service a client can verify and a reason to be the firm that reads
licences.

---

## 🆕 New on 2026-10-31 — two trends that sit above the numbered list below

The numbered T0–T8 sections that follow are kept as written on 2026-10-26 and are **not renumbered**, so
the record stays comparable pass to pass. These two are new.

### N1 — The open end-to-end driving model became a three-supplier commodity, and NVIDIA is no longer top of the table

For three passes this KB has described **one** open AV reference line: NVIDIA's Alpamayo. As of this pass
there are **three independent Apache-2.0 suppliers**, and on the only published multi-model comparison the
NVIDIA model is **third**:

| Model | Supplier | Params | Licence | ★ | ADE @ 3 s | FDE @ 3 s |
|---|---|---|---|--:|--:|--:|
| **Qwen Drive 1.0** | Alibaba | 4B | Apache-2.0 | 537 | **0.565 m** | **1.397 m** |
| **AutoE2E v1.0** | Autoware Foundation | **79.9M** | Apache-2.0 | 184 | 0.744 m | 1.980 m |
| **Alpamayo 1.5** | NVIDIA | 10B | Apache-2.0 code · **OpenMDW-1.1 weights** | 370 | behind AutoE2E | — |

Source: AutoE2E's own README, read 2026-10-31, on **KITScenes-Multimodal** validation, open-loop, 3 s
horizon, eight open-weights models compared (SimForge and METEOR also behind AutoE2E).

🔴 **It is not a clean ranking and must not be sold as one.** The README states that **inputs differ by
model** — AutoE2E itself receives an HD map and the route — and the Qwen Drive row uses a **different
evaluation setting** (first-of-6-trajectories checkpoint, 202 keyframes). What it *is*: the **first
vendor-neutral multi-model comparison in open AV**, published by a foundation that sells no model, and
**reproducible** (issue **#210** coordinates the community benchmark; PRs **#220** and **#229** added the
Qwen Drive and Alpamayo evaluation scripts).

**Three commercial reads:**
1. **Parameter count is not the axis.** AutoE2E beats a 10B model with **79.9M parameters** and runs at
   **~76 FPS on an RTX 5080** (project figure). For a client who must ship on automotive silicon rather
   than a datacentre GPU, that is the more important number than any benchmark row.
2. **Vendor neutrality is now purchasable.** An OEM that does not want to look captured by NVIDIA has a
   foundation-governed option with the same licence. Expect this to come up in procurement before it comes
   up in engineering.
3. **"Model-agnostic" stops being a slide and becomes a deliverable.** With three free suppliers whose
   relative quality is contested, the defensible architecture puts the policy behind an interface and
   swaps it — which is what the revised P6 and the new P9 below do.

### N2 — The automotive agent layer finally appeared, as MCP servers, at 0–8 stars

Three passes recorded *"no permissively-licensed automotive AI agents exist."* That is **no longer true**,
and the correction has to carry its own scale: `Vehicle-Diagnostic-Assistant` (MIT, **8★**), `obd2-mcp`
(MIT, **2★**), `automotive-ai-skills` (MIT), `j2534-mcp-server` (**0★**, and **no LICENSE file**),
`carvector-mcp` (MIT client, **1★**, keyed proprietary API). The one real-traction project in the space is
a **protocol, not an agent**: **Auto Agent Protocol** (Apache-2.0, **110★**, v3.1).

**The signal is the convergence, not the stars.** Every project is an **MCP server**. The physical layer
has settled: **ELM327/OBD-II** for consumer-grade access, **J2534 PassThru** for professional-grade
(UDS, KWP2000, DTC lookup, PID decoding). Independently, two of these projects arrived at the **human
approval gate before any vehicle action** that this KB has recommended since July.

**Why this is the favourable shape of a market for a services firm:** the integration contracts are
standardised and free, and **the differentiated product does not exist yet**. Compare the LMS-agent cluster
in the education KB — same MCP-first shape, same small star counts, same conclusion. 🟡 **Caveat worth
stating internally:** a 0–8★ category is a *watch* item. It justifies a demo and a point of view; it does
not yet justify a practice. Re-measure next pass — these numbers are the baseline.

## T0 — The open SDV *core* arrived (recorded 2026-10-26)

The previous pass tracked the SDV **data layer** (VSS, Kuksa, Ankaios) and missed the **platform core**.
**Eclipse S-CORE** (*Safe Open Vehicle Core*, Apache-2.0) is the first open-source-based SDV platform
designed against **ASIL-B** functional-safety requirements — a design target, not a certification, and that
distinction belongs in any client conversation.

Why it is credible rather than aspirational:
- **It ships.** Ten releases are listed on its GitHub releases page, latest **`v0.7.3` on 07 Oct 2026**,
  roughly monthly since `v0.5.5` in April.
- **Dual-language, safety-grade.** `0.6.0` introduced full **C++ and Rust** support including the
  **Ferrocene** safety-critical Rust toolchain, plus Baselibs Rust and Lifecycle & Health Management.
- **The OEM bloc is behind it.** The Eclipse SDV ↔ **VDA** memorandum expanded to **32 companies**
  (Jan 2026); **Hyundai Mobis joined the SDV Working Group** (May 2026).
- **It has a commercial escape hatch.** Founding member **Qorix** sells a commercial middleware
  distribution built on S-CORE — which removes the "unsupported open source" procurement objection.
- **Its process is a repository.** `eclipse-score/process_description` publishes the development process
  itself; for a safety argument that artefact is worth as much as the code.

⚠️ **Do not quote a 1.0 date.** The Eclipse project page lists **v1.0.0 at 2026-12-14**, the Eclipse
newsroom says a full release is planned for 2026 targeting vehicle programmes reaching market by 2030, and
an ETAS presentation says a complete solution is on track for **2028**. Three sources, three horizons.
Separately, trade press dates 0.6.0 to Feb 2026 and 0.7.0 to May 2026 while **the GitHub releases page
says 26 Jun and 24 Aug** — prefer the releases page.

**Commercial read:** 111 stars on the platform a VDA-backed, 32-company bloc is standardising on. The
mindshare gap between the repository's visibility and its industrial weight is the clearest arbitrage in
this KB.

## T1 — A global AV regulation now sits above the regional patchwork

🆕 **UNECE adopted the first global technical regulation for automated driving systems on 24 June 2026**,
reported as **UN GTR No. 26** with **UN Regulation No. 185**, endorsed by Canada, China, the EU, Japan, the
UK and the US; NHTSA voted in favour for the US in June 2026. China's forthcoming mandatory L3/L4 standard
is reported to reference it.

This changes the shape of multi-region compliance work: the regions are no longer purely divergent, so the
offering shifts from "translate between four regimes" toward "map one global baseline onto four national
implementations" — with the national deltas, not the baseline, as the billable surface.
⚠️ The GTR and regulation numbers come from secondary/vendor sources. **Confirm against UNECE publications
before putting them in a deliverable.**

## T2 — The open reference AV stack is vendor-published, Apache-2.0, and now 34B

**NVIDIA's Alpamayo family** remains the defining open AV model line. Verified state on 2026-10-26:
**Alpamayo 2 Super** (`NVlabs/alpamayo2`, Apache-2.0, 287★) is an open **34B** multi-task foundation model
— a 32B VLM backbone plus a 2B diffusion expert. **Alpamayo 1.5** (370★) remains the practical entry point
and the one the published recipes target. **Alpamayo 1 Nano** (2.1k★) now carries an explicit banner:
*"no longer under active development … limited maintenance updates."*

🔴 **Licence nuance the previous pass missed:** the Alpamayo 1.5 repository is Apache-2.0, **but its README
states the model weights are OpenMDW-1.1.** Code licence ≠ weight licence. Read OpenMDW-1.1 before
distributing fine-tuned derivatives.

🆕 **A second open VLA line now exists:** `DriveVLA/OpenDriveVLA` (Apache-2.0, 824★, **AAAI 2026**) with a
**0.5B checkpoint on Hugging Face**. That matters practically — Alpamayo 1 Nano alone wants ≥24 GB VRAM, so
a 0.5B open VLA is the realistic candidate for on-target experiments and for teaching.

**Why it matters commercially:** NVIDIA positions Alpamayo as a **teacher model, not in-car software**. The
weights are free; integration, distillation, quantization, validation and homologation are not. That is the
billable surface.

## T3 — Post-training, not pre-training, is where AV capability is won

**OpenDriveLab's WorldEngine** (Apache-2.0, 528★, stable checkpoints 2026/09/15) frames this directly:
imitation-learn a base policy, run open-loop rollouts over real logs to **automatically surface
failure-prone scenarios**, rebuild those scenes with **3D Gaussian Splatting**, refine with RL under a
shaped safety/efficiency/comfort reward. Project's own figures: post-training from a 50k-scene base gives
gains equivalent to **~14× more pre-training data**, simulated collision rate down up to **45.5%**, zero
disengagements over a 200 km on-road test — **not independently verified**.

Paired with **AlpaGym** (RL on AlpaSim), the closed-loop post-training pipeline is fully open-source. The
scarce input is no longer compute or architecture — it is **failure-case data and the pipeline to mine it**.
🆕 And NHTSA is now **explicitly assessing AI training and validation strategies** within ADS, which turns
that pipeline from an engineering nicety into a regulatory artefact.

## T4 — "Software-defined" is being restated as "AI-defined"

🆕 **At CES 2026, automakers emphasised AI rather than electrification** as EV demand softened (S&P
Global), positioning vehicles as software-defined rather than fixed hardware. Perforce's 2026 survey:
**71% implementing AI in their vehicles**, **57% currently working on SDV architectures**, **70%** using AI
for SDV optimisation (vendor survey — directional).

The open plumbing matured to match: **Kuksa Databroker** at 0.6.1 with a **Quarkslab security audit**
(82★), **Ankaios** at 125★, **COVESA VSS** at 451★ with 100+ companies around it, and 🆕 a **runnable
`eclipse-sdv-blueprints/fleet-management` reference** wiring Kuksa → FMS Forwarder → **Eclipse uProtocol**
→ InfluxDB → Grafana with an **rFMS API** server. Published topology, not an architecture slide.

**The signal to read:** these repos carry 7–451 stars. **Star count is a terrible proxy for importance in
this industry.**

## T5 — Compliance is the 2026 budget line in EMEA, and the calendar got denser

Dated obligations inside a 12-month window: **EDR mandatory 7 Jan 2026** · **ADDW mandatory 7 Jul 2026** ·
**EU AI Act general application 2 Aug 2026** · **UNECE R155/R156 for new types from 1 Jun 2026** (GB) ·
🆕 **UK Automated Vehicles (Permits for Automated Passenger Services) Regulations 2026 in force since
15 May 2026** · 🆕 **UN GTR No. 26 adopted 24 Jun 2026**.

**ISO/PAS 8800** (AI safety for road vehicles) complements ISO 26262 and ISO 21448/SOTIF without replacing
them; the AI Act adds governance on top — risk management, data quality, transparency, human oversight,
robustness, cybersecurity, post-market monitoring, with a technical file and serious-incident pipeline per
high-risk system, and it does not displace ISO/SAE 21434, UN R155 or UN R156.

⚠️ **The timeline is genuinely contested.** Safety-component AI (most ADAS/AD) appears to start **Aug
2027**, and one source cites **2 Dec 2027** for standalone Annex III systems via the Digital Omnibus —
unverified against the Official Journal. **Do not put a single date in a client deliverable.**

## T6 🆕 — APAC's rules became binding in 2026, not "coming"

Three state changes the previous pass had as future tense:
- **South Korea's AI Basic Act took effect 22 January 2026** (transparency for generative/high-impact AI,
  safety duties for frontier models, governance duties for high-impact systems in sensitive sectors;
  decree and ministry guidelines are **interpretive, not binding**).
- **China issued mandatory standards for combined driving assistance and automated driving** (reported
  July 2026), after an April 2026 analysis found no nationwide mandatory rule and **Beijing among
  municipalities pulling back** from unfettered autonomous operation. **L2 penetration is past 70% of new
  passenger vehicles** (MIIT). A mandatory **L3/L4 standard referencing the UN GTR from 1 Jul 2027** is
  reported — ⚠️ unverified.
- **India**: BNCAP incentivises camera ADAS and **BNCAP 2.0 is reported to require multiple ADAS features**
  for a high rating; Mobileye calls **2026–2027 the defining years for ADAS in India**.

Industry signals from the 2026 World Intelligent Connected Vehicles Conference: **BYD announced a 4nm
intelligent-driving chip in mass production** claimed to support L3/L4, and **XPeng's CEO said the company
would "skip L3"** — i.e. the region is not converging on a single autonomy ladder even as its regulation
centralises.

## T7 — Aftersales and warranty remains the commercial beachhead, and it is agentic

**43% of dealers** already deploy AI. The use cases are unglamorous and high-volume: warranty eligibility
checks, claim submission and validation against repair orders and OEM rules, parts substitution, fraud and
anomaly detection on claim patterns, service scheduling. Vendors integrate into **CDK, Reynolds &
Reynolds, Tekion and DealerSocket** at VIN level.

🆕 **The "no open-source DMS" finding is now precise rather than absolute:** open-source *repair-shop*
managers do exist — `winterautollc/OpenAutoCore` (**GPL-3.0**, 9★, live), `GarageBuddy` (work in progress),
and the most complete one, `ChanMeng666/Automotive-Repair-Management-System`, **archived by its owner on
2026-07-08**. None scales into a DMS, and the one that is alive is GPL. **Automotive retail AI is an
integration market and will stay one.** See `verticals/solutions.md`.

## T8 — Every credible automotive agent design has a human gate

Consistent across every agent implementation reviewed in this KB: the architecturally serious ones put a
**human sign-off between the model and the vehicle**. The clearest example calls it
"Technician-in-the-Loop" — low-confidence or safety-critical cases route to a technician before any
over-the-air action. Treat the gate as a required architectural element, not a nice-to-have; it is also
what makes the AI Act's human-oversight requirement **demonstrable** rather than asserted.

## T9 — Market-size numbers are still not trustworthy; adoption numbers are

2026 "AI in automotive" estimates now span **$5.80B** (Precedence) to **$26.98B** (TBRC) to **$38.45B by
2030** (MarketsandMarkets) — while a separate report puts **China alone at ~$4.9B** and **India at
~$0.96B** for 2026. Those cannot all be true of the same market. Use adoption figures (71% in-vehicle AI,
47%→72% by 2030 per PwC, ~26% sector-leading adoption) and cite market size only with its source attached.
Detail and the full conflict table in `intel/market.md`.

## T10 — Declared gaps this pass

Recording these because an unstated gap is indistinguishable from coverage.

1. 🟢 **Closed since last pass:** the LATAM regulatory question. Searching in **Portuguese and Spanish**
   (the channel the previous pass named as missing) established that **Brazil's PL 2338/2023 is not law**
   (Senate 10 Dec 2024; Câmara *"Aguardando Parecer"*, last movement 2 Sep 2026) and **Mexico has no
   general AI law** (85 initiatives since Apr 2023, 67 pending). **A LATAM "AI compliance" pitch has no
   legal hook; a data-protection one (LGPD/Anatel) does.**
2. 🔴 **Still missing in LATAM:** any **CONTRAN** resolution on AVs in Brazil, any **NOM** for AVs in
   Mexico, any AMIA/ANFAVEA position, and **any AI-adoption data for Mexican or Brazilian auto plants**.
   Closing it needs Diário Oficial / DOF / CONTRAN / industry-body primary sources, not web search.
3. 🔴 **No open-source Dealership Management System** — re-searched and re-confirmed, now with the
   repair-shop near-misses named (T7) so the search is not repeated from scratch.
4. 🟡 **No mature, permissively-licensed automotive-specific *agent* framework.** Re-confirmed: the top
   search hits are general-purpose agent frameworks with no automotive content, plus 0-star unlicensed
   hobby projects. The buildable layer is policies/VLAs and SDV infrastructure.
5. 🟡 **GitHub trending still cannot be filtered for automotive.** `github.com/trending` has no automotive
   topic filter and the topic pages surface mostly 0–5 star projects. Trend detection here has to come
   from foundations and vendor releases — see `repos/trending.md` for the method note.
6. 🔴 **Two channels are blocked, which constrains everything above:** `api.github.com` returns **HTTP 403**
   for repositories not attached to this session (so licences and stars are read from rendered repository
   pages), and **`eclipsesdv.org` failed DNS resolution** this pass (so S-CORE release notes came from the
   GitHub releases page plus trade press rather than the project's own announcements).
7. 🟡 **Japan is the thinnest major market in this KB.** Beyond "first to permit L3" and "remote monitoring
   required for all L4", searches returned almost nothing dated 2026. Named here so the next pass targets
   MLIT/METI sources directly.

---
*Updated 2026-10-31 (previous pass 2026-10-26). N1–N2 are new this pass; T0–T8 are preserved as written on
2026-10-26 and deliberately not renumbered. ⚠️ marks a claim this pass could not verify against a primary
source; 🔴 an open gap; 🟢 a gap closed since the previous pass.*

## 🆕 Gaps opened or closed on 2026-10-31

- 🟢 **Closed — China's mandatory standards have numbers.** **GB 44721-2026** (L3/L4, effective
  **1 July 2027**, MIIT, Class M and N, one-year transition) and **GB 47955-2026** (combined driver
  assistance, effective **1 January 2027**). The 2026-10-26 pass carried this as "⚠️ unverified".
- 🟢 **Closed — the AutoE2E licence conflict.** Secondary sources said OpenMDW-1.1; the repository's
  `LICENSE`, fetched raw, is **verbatim Apache-2.0**. Settled by reading the file.
- 🟢 **Partially closed — Japan, previously "the thinnest major market in this KB".** Now dated and named:
  **Phase II AI Basic Plan** (non-binding national strategy) and **AI Business Guidelines v1.2**, which
  cover **AI agents and physical AI** specifically. Level 4 remains **ODD-bounded**. MLIT/METI primary
  sources still not read directly.
- 🟢 **Partially closed — Brazil's AV instrument.** **PL 1317/2023** would add licensing, reporting and AI
  governance duties to the **Código de Trânsito** — distinct from PL 2338/2023 and previously missed here.
  Still no CONTRAN resolution; still no regulation of AV testing or circulation on any Brazilian road.
- 🔴 **Opened — model weights cannot be verified from this session.** `huggingface.co` **does not resolve**
  (DNS failure, consistent with the proxy's allowed-domain policy). Given the Alpamayo code/weights split
  this KB already caught, the weights licences for **AutoE2E** and **Qwen-Drive-1.0** are **unresolved**.
  Next pass: request `huggingface.co` in the session's allowed domains before relying on either.
- 🔴 **Opened — EU AI Act automotive date may have moved to 2 August 2028** via the **Digital Omnibus**
  (reported adopted June 2026, Annex I type-approval route). Two independent sources agree; **neither is the
  Official Journal.** Article 50 transparency reported as applying since **2 August 2026**.
- 🔴 **Open — Auto Agent Protocol adoption is unverified.** The spec, licence split and version are
  verified; **how many dealerships serve the endpoints is not.** Highest-value question for the next pass.
- 🔴 **Open, and now with a US instrument attached — LATAM.** The **Connected Vehicle Security Act of
  2026** advanced unanimously from Senate committee in July 2026 and is expected to reach EV imports
  **assembled in Brazil**. No LATAM-origin automotive repository has been found in any pass.
- 🟡 **Watch — North America AV transparency is narrowing.** One analysis notes 2025's reporting changes
  imply **decreasing public visibility of AV failure modes as fleets grow**, which shrinks the public
  corpus a scenario-mining offering can draw on and raises the value of a client's own logs.

## 🆕 Gaps opened or closed on 2026-11-13

**Closed:**
- 🟢 *"Is there any open automotive product-tier software, or only research code?"* — **closed by
  `vision_pilot`.** There is an Apache-2.0 L2 ADAS stack with 927★ and 4,282 commits.
- 🟢 *"Does the diagnostics-agent category have anything above single-digit stars?"* — **closed.**
  `farzadnadiri/Peykan` (MIT, 26★), which also covers **J1939**, the commercial-vehicle bus no other
  agent in this KB touches. ⚠️ It is reachable at `farzadnadiri/mcp-can` in every search result; that
  address is a **rename** and will eventually rot.

**Opened:**
- 🔴 **Can `vision_pilot`'s safety claim be substantiated?** The roadmap names ISO 26262 and ISO 8800;
  nothing published shows progress against them. This is the question that decides whether it is an OEM
  conversation or a prototype conversation.
- 🔴 **No benchmark exists for any model in the new release wave.** `vision_pilot` publishes none;
  `autoware_latent_drive` explicitly publishes none and offers only qualitative open-loop replays. The
  eight-model ADE/FDE table carried from AutoE2E's README (2026-10-31) is **still the only published
  multi-model open comparison in this field**, was never like-for-like, and now covers a **minority** of
  available models. **It is ageing badly.**
- 🔴 **Model weights remain unverified for a fourth consecutive pass** (`huggingface.co` does not resolve).
  This now blocks a specific decision: `autoware_latent_drive` has **no repository licence**, and its two
  ONNX models and all training detail live **only** on Hugging Face — so the model card is the **only**
  place a grant could exist, and it cannot be read.
- 🔴 **`autoware.trucks` is a charter, not a codebase** (9 commits). North American freight demand is
  visible (Kodiak in Indiana and Ohio; California's heavy-duty AV rules of 28 April 2026) and the open
  supply is not there yet. **That gap is the opportunity, and it has a clock on it.**

---
*Updated 2026-11-13 (previous passes 2026-10-31, 2026-10-26). Every repository claim in this file was read from the rendered repository page
or a raw licence file today; `curl` and `api.github.com` are both HTTP 403 in this session. Regulatory and
market claims are secondary-sourced unless stated otherwise, and the 🔴 markers flag what could not be verified.*
