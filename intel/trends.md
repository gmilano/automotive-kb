---
industry: automotive
region: Global
updated: 2026-10-31
---

# 📡 Trends — Automotive

> Current trends, updated 2026-10-31. Project and vendor self-reported performance figures are labelled
> as such. Dates name their instrument.

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
