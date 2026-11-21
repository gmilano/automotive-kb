---
industry: automotive
region: Global
updated: 2026-11-21
---

# 🏭 Vertical platforms — Automotive

> Real, running open-source systems that can be customised with an AI layer on top.
> Model: start from something that already works, add the agentic layer above it.
> **Verified 2026-11-21:** licences **byte-read** from `raw.githubusercontent.com` (HTTP 200), liveness
> via `git ls-remote`, stars/push dates via `gh api -X GET search/repositories`.
>
> *Superseded note —* verified 2026-11-13 (`curl -sI` on `github.com` and `api.github.com` both return **HTTP 403** through
> this session's proxy, re-tested today, so licences and stars are read from the rendered repository page;
> 🆕 = new this pass, 🔄 = licence/stars re-read today, ⏸ = carried forward and labelled).

## 🆕 2026-11-21 (third pass, 13:40Z) — the manufacturing / plant-floor gap is CLOSED, and the DMS gap is confirmed an eighth time

### ✅ Gap closed — the plant-floor layer has a customisable base after all

This file declared **"Manufacturing / plant floor — a declared gap, stated with its query"** on
2026-11-19 (section below, preserved). **The query was the problem.** The base exists, it is mature, and
it is permissive — it simply does not describe itself as automotive.

| Platform | Repo | Licence (byte-read) | ★ | Stack | Why it belongs in this file |
|---|---|---|--:|---|---|
| 🆕 **Anomalib** | [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | **Apache-2.0** — `LICENSE`, 11,357 b, canonical | **6,414** / 1,047f | Python / PyTorch / OpenVINO | **The customisable base for plant-floor visual inspection.** Intel-maintained, 20+ industrial anomaly-detection algorithms, edge export built in, **pushed 2026-11-20**. Paint, weld, panel-gap, battery-module inspection. **This is the Odoo of the plant floor for this KB** — a real system to customise with AI on top, not a research drop |
| ⏸ DEye | [sundyCoder/DEye](https://github.com/sundyCoder/DEye) | **Apache-2.0** — 11,357 b | 885 / 367f | C++ | Surface/semiconductor defect inspection. **Dormant since 2023-03-14 — prior art only** |
| ⏸ SageMaker Defect Detection | [awslabs/sagemaker-defect-detection](https://github.com/awslabs/sagemaker-defect-detection) | **Apache-2.0** — 10,142 b | 62 / 25f | Python / SageMaker | Supervised steel-surface detection (NEU dataset). **Dormant since 2022-12-21, AWS-coupled — architecture reference for an AWS client** |

**What makes it a *vertical platform* rather than a model:** the engagement is to customise it against
one plant's lines and then **qualify it as an inspection tool under VDA QMC Volume 5 Part 3** — the route
Audi took for AI spot-weld inspection (`intel/market.md` → EMEA). **The audit qualification is the
deliverable; the detector is the commodity.** Full recipe: `compose/patterns.md` **P22**.

🔴 **The one trap, and it is not in any `LICENSE` file.** `anomalib`'s code is Apache-2.0. **MVTec AD —
the benchmark this entire layer reports against — is CC BY-NC-SA 4.0, non-commercial.** Train on the
client's own line images; use MVTec AD only to shortlist an algorithm internally. **Never ship
MVTec-trained weights or quote an MVTec score in a commercial proposal** (`intel/trends.md` **N17**).

### 🔴 The DMS gap — eighth consecutive confirmation, now with the reason rather than the count

A leg aimed directly at open DMS (gaze + drowsiness, permissive, automotive-grade) returned **one**
framework-grade project and it fails twice over:

| Candidate | Measured | ★ | Pushed | Verdict |
|---|---|--:|---|---|
| [kiralygomba/nottired_guard](https://github.com/kiralygomba/nottired_guard) | 🔴 **GPL-3.0** — `LICENSE`, 35,149 b | **1** | ⚠️ **2024-03-08** | **Rejected: copyleft *and* abandoned 20 months.** Head pose + gaze + blink + yawn, with a 2025 peer-reviewed preprint behind it — the only one with a method paper |

Everything else is a **single-file eye-aspect-ratio demo** (MediaPipe/dlib, 0–3★, no temporal model, no
gaze, no standards claim). One listing advertised **"EU regulation C(2023)4523-compliant gaze-zone
detection"** without naming a repo — **unverifiable, not recorded.**

🟢 **Stop filing this as research debt and start selling it.** Driver monitoring is **regulatorily
mandated in the EU** and has **no adoptable open implementation.** Every other recommendation in this
file is "adopt the open base" — which a client can do without us. **DMS is the one place where build is
the honest answer**, and it is therefore the strongest build-versus-adopt case in this KB
(`intel/trends.md` **N18**).

---

## 🆕 2026-11-21 (second pass, verification 12:45Z) — the ERP/CRM shelf re-measured; the DMS gap survives a leg aimed straight at it

**Verification pass.** The dealership/ERP leg was re-run specifically to attack the DMS gap recorded
below. **It produced no new permissive platform — the eighth consecutive negative result on this
question** — but it did produce **fresh measurements** for the candidates, which is what the gap statement
needs to stay credible.

### 🔄 ERP/CRM candidates re-measured 2026-11-21

| Platform | Measured licence | ★ | Last push | Verdict for Globant |
|---|---|--:|---|---|
| [Dolibarr/dolibarr](https://github.com/Dolibarr/dolibarr) | **GPL-3.0** | 7,889 | **2026-11-21** | ❌ **Strong copyleft.** Very much alive — pushed the same day as this pass — and still unusable as a base a client ships proprietary work on. Correctly held as copyleft in this file. |
| [open-mercato/open-mercato](https://github.com/open-mercato/open-mercato) | **MIT** | **1,953** | **2026-11-21** | ✅ **The only permissive option, and it is a framework — not a dealership product.** Pushed the same day; genuinely active. Building a dealer layer on it is **P17** below, and it remains a *build*, not a *configure*. |
| [YetiForceCompany/YetiForceCRM](https://github.com/YetiForceCompany/YetiForceCRM) | **`NOASSERTION`** | 1,788 | 🔴 **2024-09-13** | ❌ **Rejected on two counts:** no resolvable SPDX grant **and unpushed for over two years.** Named here because listicles still recommend it as an open ERP/CRM for dealerships. |
| SuiteCRM | **did not resolve** | — | — | ❌ Named by a comparison page; **the slug did not resolve to a repository.** Not a finding. |

**The gap statement, restated with this pass's evidence:** a search aimed directly at permissive
dealership ERP/CRM returns **general-purpose business software, one permissive framework, and one
abandoned CRM.** **There is still no open-source DMS**, and the two live candidates split exactly the
wrong way — **the mature one is copyleft and the permissive one is a framework.** That is a stable,
well-measured finding across eight passes, not an absence of searching.

⚠️ **Watch the "MIT" trap in this layer specifically.** The education KB recorded *licence-by-association*
(a platform described as "founded by Harvard and MIT" rendered elsewhere as "under Apache 2.0"). The same
shape is live here: comparison pages describe permissive licences generically as "commonly MIT or Apache
2.0" in the same breath as naming dealership products. **Measure the repo; never inherit a licence from a
sentence about licences.**

---


## 🆕 2026-11-21 — Huly moves from *rejected* to *viable*, and Odoo's LGPL grant is byte-confirmed

> **Verification this pass:** licences **byte-read** from `raw.githubusercontent.com` (HTTP 200 — it
> works), liveness via `git ls-remote`, metadata via `gh api -X GET search/repositories`. The
> rendered-page channel earlier passes relied on is no longer the best available. See
> `agents/top.md` → *"What changed on 2026-11-21"*.

### 🔄 Correction: Huly's *hosted service* is discontinued — its *repository* is not frozen

The rejection table below (2026-11-19) excludes
[hcengineering/platform](https://github.com/hcengineering/platform) partly because *"the page states it
is frozen and is no longer actively maintained."* **The licence call was right; the liveness call was
not.** The README banner actually says:

> *"The hosted Huly service is being discontinued because its hosting is no longer being funded. If you
> keep important data on the hosted platform, export and back it up, and migrate as soon as possible —
> we can help you move to either a self-hosted setup or a hosted option."*

That is a **SaaS wind-down with a vendor-recommended migration to self-hosting**, not an abandoned
codebase. First-hand repository state today:

| Field | Value (read 2026-11-21) |
|---|---|
| Stars | **28,161** |
| `pushed_at` | **2026-11-09** |
| `archived` | **false** |
| Last commits | `fix(github): do not persist the Octokit client in the user integration secret` (2026-11-05), `fix(gantt)` (2026-11-04), `fix(contact)` (2026-11-02) |
| Licence (byte-read) | **EPL-2.0** — weak, file-level copyleft |

**Revised verdict: viable for a self-hosted engagement.** EPL-2.0 does not reach proprietary modules kept
in separate files, the code is actively fixed, and self-hosting is the upstream's own recommended path.
The real risk is **commercial sustainability of the vendor**, which is a diligence question, not a
licence or liveness blocker. The **Apache-2.0 claim remains false** — it is EPL-2.0, and today's search
results repeated the Apache claim again, so the secondary-source error is upstream and persistent.

**Method note worth keeping:** *"hosted service shutting down"* and *"project dead"* are different
findings, and the first is routinely published in language that reads like the second. **Check
`pushed_at` and `archived` before converting a service notice into a project obituary.**

### ✅ Odoo — the LGPL-3.0 grant, byte-confirmed

The rotation brief names Odoo as the ERP exemplar, so this is worth settling first-hand rather than
citing. `odoo/odoo` `LICENSE`, read byte for byte today, opens:

> *"Odoo is published under the GNU LESSER GENERAL PUBLIC LICENSE, Version 3 (LGPLv3), as included
> below. Since the LGPL is a set of additional permissions on top of the GPL, the text of the GPL is
> included at the bottom as well. Some external libraries and contributions bundled with Odoo may be
> published under other GPL-compatible licenses."*

**LGPL-3.0, confirmed.** This is exactly why proprietary Odoo modules are viable where they would not be
under GPL or AGPL — and why an automated classifier that sees the appended GPL text and reports "AGPL-3.0"
(as one did against this shelf today) would wrongly disqualify the single most useful ERP base in this file.

### 🆕 ERP bases — one dead, one live-but-copyleft

| Platform | Repo | Licence (byte-read) | ★ | Last push | Verdict |
|---|---|---|--:|---|---|
| **XTuple** | `xtuple/xtuple` | — | — | — | 🔴 **GONE** — 404 via `git ls-remote`. Still cited in current ERP roundups. **Any shortlist naming XTuple is stale.** |
| **iDempiere** | [idempiere/idempiere](https://github.com/idempiere/idempiere) | ⚠️ **GPL-2.0** (API says `NOASSERTION`; `LICENSE.md` is the GPL-2.0 text) | 678 | 2026-11-20 | ⚠️ **Live and genuinely maintained**, but strong copyleft. Usable only where the deliverable can be GPL — not for a proprietary dealer module. |

Both were returned by this pass's `open source platform automotive ERP CRM dealership MIT Apache` query.
Neither closes the DMS gap.

### 🔴 The DMS gap — seventh consecutive confirmation

Still **no open-source dealer management system** with inventory, F&I and deal-desk modules. Today's
query returned only general-purpose ERP/CRM: OFBiz (Apache-2.0), Huly (EPL-2.0), Krayin (MIT), iDURAR
(AGPL-3.0), Open Mercato (MIT core + commercial enterprise package), Dolibarr (GPL-3.0), iDempiere
(GPL-2.0), ERPNext (GPL-3.0). **The gap is structural, not a search failure** — a DMS is a regulated,
OEM-integrated product category, and no one has open-sourced one.

What *did* appear this pass is the first **MIT-licensed dealer-operations agent layer**:
[arielcoro/dealer-ai-skills](https://github.com/arielcoro/dealer-ai-skills) (MIT, 3★, pushed 2026-10-21)
— SEO/AEO/GEO, BDC, F&I, fixed ops, equity mining as installable agent skills. It is small and
single-author, but it is the first thing in this base that speaks **dealer retail** with a real grant.
See `compose/patterns.md` for how to pair it with a permissive ERP instead of waiting for a DMS.

---

## 🆕 2026-11-19 — the DMS gap re-measured, and the first *shop-management* contract appears

### The DMS gap, now with a number instead of an impression

Four previous passes recorded "there is no open dealer management system". This pass the claim was
turned into a measurement. Query run through the GitHub REST API:

```
gh api -X GET search/repositories -f q='car dealership management in:name,description,topics pushed:>2026-01-01' -f sort=stars
```

**Result: 408 repositories. The highest star count in the entire result set is 5.** The top twenty, read
row by row, are: `mohammadumar-dev/carventory` (MIT, 5★), `ArmanAmreliya/car-dealership-inventory-system`
(no licence, 3★), `Het10-Lb/Car-Dealership-Inventory-System` (no licence, 3★), then a long tail of
1–2★ MERN/Spring Boot/PHP coursework projects, **the overwhelming majority with no licence at all**.

**This is now a hard finding, not a soft one.** There is no open-source DMS, there is no candidate that
could become one, and the 408 results are a *student-project corpus*, not a market. Any engagement
touching dealer operations integrates a commercial DMS (CDK, Reynolds & Reynolds, Tekion, Dealertrack)
or builds on a general ERP/CRM base — it does not fork an open DMS, because none exists.

⚠️ **Procurement trap:** a search for "open source DMS" will return results with real-looking READMEs.
Every one of the 408 is a coursework project. **Star count and licence are the filter**; apply both.

### 🆕 But the *shop-management* layer just got an open contract

The aftersales side is where the first real integration surface appeared — not a platform, an **API
contract wrapped for agents**:

| Platform / contract | Repo | Licence | ★ | What it gives you |
|---|---|---|--:|---|
| **Shopmonkey** (commercial SaaS; the MCP wrapper is open) | [AbbottDevelopments/shopmonkey-mcp-server](https://github.com/AbbottDevelopments/shopmonkey-mcp-server) | **MIT** | 3★ / 8f | **69 tools over the Shopmonkey REST API v3**: work orders, customers, vehicles, inventory, appointments, labour. The first repair-shop management system reachable by an agent through a permissively licensed wrapper. |
| **TeslaMate** (self-hosted vehicle data logger) | [cobanov/teslamate-mcp](https://github.com/cobanov/teslamate-mcp) | **MIT** | **142★** / 25f | Queries the TeslaMate database — drive and charge history, analytics. **The largest automotive MCP server in this KB.** Pairs with a self-hosted TeslaMate instance to give an agent a real vehicle-history corpus. |
| **NHTSA public data** | [cyanheads/nhtsa-vehicle-safety-mcp-server](https://github.com/cyanheads/nhtsa-vehicle-safety-mcp-server) | **Apache-2.0** | 3★ | VIN decode, recalls, complaints, crash ratings, investigations. STDIO or Streamable HTTP. **Free, authoritative, US-scoped** — the cheapest trust anchor for any North America aftersales agent. |
| **OEM service documentation** | [bpawnzZ/lemonwrench](https://github.com/bpawnzZ/lemonwrench) | **MIT** | 21★ | Free OEM service manuals → procedure, torque table, labelled figures. **69 makes, 1960–2025.** Turns "what is the torque spec" into a tool call instead of a hallucination. |
| **Auto.dev** (commercial data API) | [auto-dot-dev/sdk](https://github.com/auto-dot-dev/sdk) | 🔴 **no licence** | 3★ | VIN decode, listings, specs, OEM build data, recalls, payments, taxes. **Licence blocks use** — recorded so it is not re-found. |
| **Vehicle reference data** | [vehiclesdb/vehicles](https://github.com/vehiclesdb/vehicles) | ⚠️ `NOASSERTION` (data **CC-BY-4.0**) | 5★ | Makes and models for Rails apps with a bundled MCP server, no API keys. Settle the code licence; the *data* licence is stated as CC-BY-4.0. |

**The pattern to take to a client:** the aftersales opportunity is not "replace the DMS". It is
**wrap the systems the shop already pays for in an MCP contract, add the free authoritative sources
(NHTSA recalls, OEM torque specs) as separate tools, and gate every write behind a named human**. That
is `compose/patterns.md` → **P10**, now with four real, licence-checked tool sources instead of two.

### Fleet and telematics — fifth pass, still two repos

```
gh api -X GET search/repositories -f q='fleet management telematics in:name,description pushed:>2026-08-01 stars:>5'
```
**Total: 2.**

| Repo | Licence | ★ | Note |
|---|---|--:|---|
| [openremote/fleet-management](https://github.com/openremote/fleet-management) | ⚠️ `NOASSERTION` | 51★ | Telematics on top of the OpenRemote IoT platform. **Licence still unclassified by GitHub** after five passes — settle it from the file before any deliverable. |
| [santoshiimind/fleet-management-system](https://github.com/santoshiimind/fleet-management-system) | **Apache-2.0** | 8★ | FastAPI + SQLAlchemy: **OBD-II diagnostics, GPS tracking, CAN bus decoding, DTC analysis, driver-behaviour monitoring, fuel analytics, live dashboard.** The only permissively licensed open fleet stack found — and it is a **one-person project**, so treat it as a reference implementation, not a base. |

[traccar/traccar](https://github.com/traccar/traccar) (Apache-2.0) remains the real answer for GPS
telematics and is unchanged. The *AI* layer on fleet data still has to be built; nobody has published it.

### 🆕 The customisable base nobody expected: assurance, not an ERP

For four passes this section has asked "what is automotive's Odoo?" — a real system a studio can
customise. The honest 2026-11-19 answer is that the best-adopted customisable automotive base is **not
an operations platform at all**. It is
[jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite)
(**MIT, 2,907★, 141 forks**): 76 builder+reviewer skill pairs that generate the ISO 26262 / ISO 21434 /
ISO 21448 / ASPICE / AIAG-VDA artefact pack as `.xlsx`.

Its **141 forks** are the signal — that is a customisation rate, which is exactly what "a base you can
customise" means in practice.

⚠️ **Two caveats before it goes near a client:**
1. The page carries **no statement that outputs are uncertified** and no requirement that a qualified
   engineer validate them, while advertising coverage of six standards and the word "compliance".
   Generated artefacts must be **owned by a named responsible engineer**, not shipped as found.
2. Installation is **"Save skill" in Cowork or Claude Desktop**; the page names **no Claude Code or
   non-Claude runtime**. If a client's agent platform is something else, the packaging is work.

The counterpart to customise *alongside* it is
[jherrodthomas/LionDriver](https://github.com/jherrodthomas/LionDriver) (MIT, 65★), which shows what an
honest assurance repository looks like: 36 claims, 50 evidence items, **42 open defeaters, 0 accepted**,
89 V-cycle work products, and an explicit statement that **no compliance is claimed because no
assessment has been performed**.

### 🆕 In-vehicle and SDV bases added this pass

| Base | Repo | Licence | ★ | Customisation story |
|---|---|---|--:|---|
| **Smart-cockpit agent framework** | [yancent-dao/cockpit-agent-sim](https://github.com/yancent-dao/cockpit-agent-sim) | **MIT** | 98★ | Zero-backend, **tiered permissions, confirmation flow, card orchestration, fast/slow dual layer**, real third-party integrations. Its own design rule is *"add a capability = add data, not code"* — i.e. built to be extended by configuration. The most reusable in-vehicle HMI agent base found. |
| **SDV reproducible image** | [eclipse-leda/leda-distro](https://github.com/eclipse-leda/leda-distro) | **Apache-2.0** | 21★ | Yocto build setup for Eclipse SDV.EDGE. This is what makes Kuksa / Velocitas / Ankaios boot on real target hardware. Low stars, high leverage. |
| **SDV systems engineering** | [de4sdv/DE4SDV](https://github.com/de4sdv/DE4SDV) | **Apache-2.0** | 13★ | **SysML v2**, MBSE, product-line engineering, digital continuity, continuous compliance. The only open SysML v2 automotive base found; pairs with the assurance layer above. |
| **Edge message bus** | [nanomq/nanomq](https://github.com/nanomq/nanomq) | **MIT** | 2,666★ | MQTT broker built for **Edge & SDV**. The transport under a connected-vehicle deployment. |
| **Zero-copy IPC** | [eclipse-iceoryx/iceoryx](https://github.com/eclipse-iceoryx/iceoryx) | **Apache-2.0** | 2,212★ | For hard latency budgets in AUTOSAR Adaptive / ROS 2 stacks. |

### 🆕 Manufacturing / plant floor — a declared gap, stated with its query

```
gh api -X GET search/repositories -f q='automotive manufacturing quality inspection AI in:name,description pushed:>2026-06-01 stars:>3'
```
**Total: 0 repositories.**

There is **no open-source automotive plant-floor quality/inspection AI** above 3★ pushed in the last six
months. The one adjacent asset is
[aws-samples/sample-manufacturing-automotive-ai-toolkit](https://github.com/aws-samples/sample-manufacturing-automotive-ai-toolkit)
(**MIT-0**, 19★/7f) — *"a collection of sample AI agents for Automotive and Manufacturing use cases"*,
the **first hyperscaler-published** automotive agent sample set in this KB. **MIT-0 requires no
attribution**, which makes it the most permissively licensed asset recorded here and the natural
starting point for a plant-floor proof of concept. It is samples, not a platform — size the work
accordingly.

### 🔴 Still rejected, carried forward

The 2026-11-13 rejections stand and were **not** re-probed this pass (no new information):
`idurar/idurar-erp-crm` (claims MIT, is **AGPL-3.0**, 9.0k★) and `hcengineering/platform` / Huly
(claims Apache-2.0, is **EPL-2.0**, 28.1k★, **and declared frozen / no longer actively maintained**).
New this pass, same category of error: [`aureuserp/aureuserp`](https://github.com/aureuserp/aureuserp)
and [`open-mercato/open-mercato`](https://github.com/open-mercato/open-mercato) are described in
secondary sources as fully open while **Open Mercato's own description states the core is MIT with
enterprise modules licensed separately** — a dual-licence structure, not a permissive one. Verify the
module you actually need, not the repository root.

## 🆕 2026-11-13 — a new customisable base appeared, and it is not an ERP: an open L2 ADAS stack

The premise of this file is *"start from something that already works, add the agentic layer above it."*
Until today every base here was a **business** system — fleet, ERP, CRM, telematics. This pass adds the
first credible base that is a **vehicle** system.

| Platform | Repo | Licence | ★ | What you customise |
|---|---|---|--:|---|
| 🆕 **Vision Pilot** | [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) | **Apache-2.0** | **927** | *"Free and fully open-source L2 ADAS stack powered by End-to-End AI technology"*; README: *"a productionizable and safety certifiable implementation."* Ships **ACC, FCW, AEB, LKAS, LDW, ISA and single-lane hands-free highway Autopilot**, **mapless**, from **one front monocular camera (52–55° HFOV, 1–2 MP)** on **ONNX Runtime, GPU or CPU**, with Docker, an optional ROS 2 interface and CARLA 0.9.16 closed-loop simulation. Three swappable models — **AutoSpeed**, **AutoSteer**, **AutoDrive**. 196 forks, 4,282 commits. Roadmap: radar fusion, 8 MP/120° camera, **ISO 26262 + ISO 8800**. |

**Why this belongs in *verticals* and not only in `repos/foundations.md`.** It is the "Odoo for ADAS" shape
this KB has never had: a running system a client already recognises, which you extend rather than invent.
The customisation surface is concrete — swap or retrain **AutoSpeed/AutoSteer/AutoDrive**, add the client's
own sensor set, retarget the hardware, keep the feature set. And because the camera requirement is a
**single 1–2 MP monocular camera on CPU-capable inference**, a proof of concept is affordable in a way an
Alpamayo-class engagement is not.

⚠️ **Two honest limits to state before a client hears "certifiable".** Certification is a **roadmap item,
not a status** — "safety certifiable" is the project's own aspirational wording. And the current input is
**one narrow-FOV camera**: no radar, no surround view, until the roadmap lands. It is a genuine L2 base,
not an L3 shortcut.

**Pair it with** [autoware-safety-island](https://github.com/autowarefoundation/autoware-safety-island)
(Apache-2.0 — licence read from `license.rst` after GitHub mislabelled it "Other"; 608 commits) and
**Eclipse S-CORE** below. Those three are the first open answer to *"how would we ever certify this"*.

---

## 🆕 2026-10-31 — the DMS gap now has an open *contract*, though still no open DMS

**This is the most consequential change to this file since it was written.** For four passes the conclusion
has been: the dealership layer is a closed oligopoly, there is no "Odoo for dealerships" to fork, and
engagement work is therefore bespoke integration against proprietary DMS APIs. **The first two still hold.
The third no longer does.**

| Project | Repo | Licence | Stars | What it specifies |
|---|---|---|--:|---|
| 🆕 **Auto Agent Protocol** | [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | **Apache-2.0** (spec, schemas, code) · docs **CC BY 4.0** | 110 | *"The open automotive contract for MCP, A2A and Personal Agent Protocol: dealer discovery, inventory, evidence, pricing and consented inquiries."* **v3.1** per README, additive over the published **3.0** contract (AAP 2.x must migrate to 3.0 first). Dealer domains advertise capability by publishing an **Agent Card**, a **Poppy document** and **`llms.txt`** pointing at live **MCP**, **A2A** and **PAP** endpoints; the MCP tool catalogue and A2A OpenAPI are served from versioned **`/v3.0/`** paths. Independent project, built on Google's A2A (Apache-2.0, Linux Foundation). |

**What it changes for scoping an engagement.** The integration target becomes a **published, versioned
contract** rather than a per-vendor negotiation. A dealer-group client can be made agent-reachable —
discoverable inventory, verifiable vehicle facts, consented lead capture — **without replacing their DMS**,
which is the objection that has killed this conversation historically. The consent model is in the spec
("consented inquiries"), which is also the part a LATAM/LGPD or EU engagement will be asked about first.

🔴 **The honest caveat, and it is a big one: adoption is unverified.** The specification's existence,
licence and version are verified first-hand. **How many dealerships actually serve these endpoints today is
unknown** — nothing found this pass establishes it. Pitch it as *"an open contract exists and we can
implement both sides of it"*, **not** as *"the industry has standardised"*. Confirming real deployments is
the single highest-value question for the next pass.

## The DMS gap — the underlying finding, unchanged across four passes

The 2026-10-15 pass recorded *"no open-source Dealership Management System exists."* This pass searched
again (`open source dealership management system 2026 automotive aftersales repair shop GitHub`) and the
finding is **more precise, and more useful**:

**There is no open-source DMS. There *are* open-source independent-repair-shop managers — and they are
small, copyleft, or abandoned.** Named, so nobody re-searches this next pass:

| Project | Repo | Licence | Stars | State |
|---|---|---|---|---|
| 🆕🔄 OpenAuto | [winterautollc/OpenAutoCore](https://github.com/winterautollc/OpenAutoCore) | ⚠️ **GPL-3.0** | 9 | *"Automotive Shop management Software."* Python + PyQt6 + MySQL; customers, estimates/invoices, scheduling, custom pricing matrix. 71 commits, README screenshots dated Sep 2025. **Live, tiny, and GPL — unusable as a base for a proprietary deliverable.** |
| 🆕 RepairOS | [ChanMeng666/Automotive-Repair-Management-System](https://github.com/ChanMeng666/Automotive-Repair-Management-System) | not read | — | The most feature-complete hit (Flask + multi-tenant SaaS, RBAC, Stripe billing, work orders) — **archived by its owner on 2026-07-08**. Dead end; recorded so it is not rediscovered as a candidate. |
| 🆕 GarageBuddy | [dimitar-grigorov/GarageBuddy](https://github.com/dimitar-grigorov/GarageBuddy) | not read | — | ASP.NET Core MVC garage management, service history. README marks features "work in progress". |

**Conclusion unchanged, evidence stronger:** the automotive retail layer is a closed oligopoly — **CDK,
Reynolds & Reynolds, Tekion, DealerSocket** — and dealership AI vendors integrate *into* those systems
rather than replacing them. There is no "Odoo for dealerships" to fork, and the repair-shop projects above
do not scale into one.

Two consequences for pricing an engagement:
1. Dealership/aftersales work is **integration against proprietary DMS APIs**, not customisation of an
   open base. Scope the API-access negotiation as its own line item.
2. A generic ERP/CRM base (below) plus a VIN/parts/service-order domain model is the only open starting
   point — and that modelling work is the differentiator, not commodity.

## Fleet, telematics & connected-vehicle platforms

| Platform | Repo | Licence | Stars | Stack | Use case |
|---|---|---|---|---|---|
| 🔄 **Traccar** | [traccar/traccar](https://github.com/traccar/traccar) | Apache-2.0 | 7.9k | Java | *"Open source GPS tracking platform - self-hosted or managed, 200+ device protocols."* Multi-tenant user/permission management, so several client accounts run on one server. **The best permissive starting point in this KB for fleet work.** |
| 🆕🔄 **Eclipse SDV fleet-management blueprint** | [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management) | Apache-2.0 | 27 | Rust/containers | Not a product — a **runnable reference fleet stack**: Kuksa CSV Provider → Kuksa Databroker → FMS Forwarder → Eclipse uProtocol → FMS Consumer → InfluxDB → Grafana, with an **FMS Server exposing the rFMS API**. Use it when the client is an OEM/truck maker who wants fleet data *from the vehicle's own SDV stack* rather than from an aftermarket tracker. |
| ⏸ **Fleetbase** | [fleetbase/fleetbase](https://github.com/fleetbase/fleetbase) | ⚠️ **AGPL-3.0** | 4.3k | PHP/Laravel + Ember | Modular logistics operating system; fleet and transport management, extension-based. Far richer than Traccar — but AGPL, so a hosted client deliverable triggers source obligations. Legal sign-off required. |
| 🆕 **Fleet Management System** (Navari) | [navariltd/Fleet-Management-System](https://github.com/navariltd/Fleet-Management-System) | ⚠️ **GPL-3.0** | 12 | Python / **Frappe** | *"Open-source fleet management solution built on the Frappe framework, designed for transportation companies, logistics providers, and organizations managing vehicle fleets."* Interesting only because it rides **Frappe/ERPNext**, so a client already on that stack gets fleet inside their ERP. **GPL-3.0** (README + badge; the GitHub sidebar shows a License link but does not name it, so the README is the source) — copyleft, excluded as a base. 18 forks, default branch `develop`. |
| ⏸ **OpenRemote** | [openremote/openremote](https://github.com/openremote/openremote) | ⚠️ **AGPL-3.0** | 1.9k | Java | 100% open IoT platform — device integration, rules, custom apps; fits connected-vehicle/charging telemetry. Sidebar shows no licence name; `LICENSE.txt` read directly (2026-10-15) = **AGPL v3, © 2016 OpenRemote Inc.** |

## ERP / CRM bases for aftersales, parts and dealer operations

| Platform | Repo | Licence | Stars | Stack | Use case |
|---|---|---|---|---|---|
| ⏸ **Odoo** | [odoo/odoo](https://github.com/odoo/odoo) | ⚠️ **LGPL-3.0** | 55.0k | Python | Ships a **Fleet** module out of the box plus inventory, purchasing, maintenance and CRM — shortest path to a working parts/service/fleet back office. `LICENSE` read directly (2026-10-15) = **LGPL v3**. Community edition only; Enterprise is proprietary. |
| ⏸ **Apache OFBiz** | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1.1k | Java | ERP + CRM + e-commerce + supply-chain and manufacturing resource planning in one Apache-2.0 framework. **The most permissive full ERP base**; strongest fit for parts distribution and manufacturing-side work. Heavier to learn than Odoo. |
| 🆕 **Dolibarr** | [Dolibarr/dolibarr](https://github.com/Dolibarr/dolibarr) | ⚠️ **GPL-3.0** | 7.8k | PHP | *"Dolibarr ERP CRM is a modern software package to manage your company or foundation's activity."* Surfaced this pass as an ERP/CRM base for aftersales. **GPL-3.0 read from the sidebar — ruled out**, and recorded so it is not rediscovered: Odoo (LGPL-3.0) is the softer-copyleft option and **OFBiz (Apache-2.0) is the permissive one**. Default branch `develop`. |
| ⏸ **Krayin CRM** | [krayin/laravel-crm](https://github.com/krayin/laravel-crm) | MIT | 24.0k | PHP/Laravel | Open-source CRM for customer, lead and sales management. MIT — cleanest licence of any CRM here. Good base for a dealer-lead / test-drive-booking front end. ⚠️ Some advanced features (e.g. multi-tenancy) are paywalled. |
| 🆕 **AureusERP** | [aureuserp/aureuserp](https://github.com/aureuserp/aureuserp) | **MIT** | 12.2k | PHP/Laravel + **FilamentPHP** | *"Free and Open Source ERP software."* **The cleanest-licensed full ERP in this file** — MIT, where Odoo is LGPL-3.0 and OFBiz is Apache-2.0 but heavy. Modules for accounting, inventory, HR and CRM. For an aftersales/parts back office that must ship as a proprietary client deliverable, this is now the **first** base to evaluate: Laravel+Filament is fast to extend and the grant has no carve-out. 12.2k★ means real adoption, unlike most MIT ERP claims. |
| 🆕 **Open Mercato** | [open-mercato/open-mercato](https://github.com/open-mercato/open-mercato) | ⚠️ **MIT core + separate commercial licence for `packages/enterprise`** | 1.9k | TypeScript / Next.js / PostgreSQL | *"The AI-Engineering Foundation Framework for business apps."* Ships CRM and ERP modules with multi-tenancy, RBAC, events and domain modules decided as conventions — explicitly designed so coding agents extend it rather than re-deciding architecture, which is an unusual and genuinely useful fit for a Globant engagement. ⚠️ **Read the carve-out before scoping:** the repo badge says MIT, but `packages/enterprise` is **not** MIT. Verify which modules a client needs fall inside the MIT boundary. |

### 🔴 Rejected this pass — two "open source" ERP/CRM claims that failed verification

Both were returned by `open source platform automotive ERP CRM dealership MIT Apache` as permissively
licensed. **Neither is.** Recorded so no future pass re-admits them.

| Repo | Search summary claimed | **Repository page says (read 2026-11-13)** | Why excluded |
|---|---|---|---|
| [idurar/idurar-erp-crm](https://github.com/idurar/idurar-erp-crm) | *"fully open-source under the MIT license"* | 🔴 **AGPL-3.0**, 9.0k★ | **Strong network copyleft.** A hosted client deliverable triggers source obligations. The claim was simply false. |
| [hcengineering/platform](https://github.com/hcengineering/platform) (**Huly**) | *"licensed under Apache License 2.0"* | 🔴 **EPL-2.0**, 28.1k★ — **and the page states it is "frozen and is no longer actively maintained"** — 🔄 **see 2026-11-21 above: the licence call stands, the "frozen" call does not. Hosted *service* discontinued; repo pushed 2026-11-09, `archived: false`. Revised to VIABLE self-hosted.** | **Wrong on two counts**, and the second is worse: a 28.1k-star project that looks alive in every search result is **dead upstream**. Never base an engagement on it. |

**The lesson, stated plainly because it keeps recurring.** Four ERP/CRM licence claims were probed this
pass and **three were wrong or incomplete** — one false MIT, one false Apache-2.0 on an abandoned repo, one
MIT with an undisclosed commercial carve-out. Only AureusERP's claim held exactly as stated. **For this
layer in particular, a search summary is a lead and the repository page is the source.**

## In-vehicle platform — the base for OEM/Tier-1 SDV engagements

For OEM work the customisable base is **not** an ERP. It is, bottom to top:

**COVESA VSS** (signal vocabulary, MPL-2.0) → **Eclipse Kuksa Databroker** (in-vehicle data layer,
Apache-2.0) → **Eclipse Ankaios** (workload orchestration on automotive HPCs, Apache-2.0) →
🆕 **Eclipse S-CORE** (Apache-2.0, ASIL-B-targeted platform core, releasing ~monthly, latest `v0.7.3`
07 Oct 2026, dual C++/Rust with the Ferrocene toolchain).

The ready-made topologies are published, not hypothetical: the
[fleet-management blueprint](https://github.com/eclipse-sdv-blueprints/fleet-management) above, and the
wider [eclipse-sdv-blueprints](https://github.com/eclipse-sdv-blueprints) organisation (an **org** URL,
not a repo — `git ls-remote` cannot probe it and plain page fetches return HTTP 403 through this session's
proxy, so it is the one link here verified only indirectly, via its `fleet-management` repository above).
**Do not invent
this architecture for a client — adopt the blueprint and spend the budget on their domain.**

🆕 **Commercial-support answer for a risk-averse OEM:** founding member **Qorix** sells a commercial
middleware distribution built on S-CORE. That matters in a procurement conversation — the open project has
a paid-support path, so "unsupported open source" is not a valid objection.

## How to add the AI layer

1. **Pick the base by licence constraint first**, not by features. If the client needs a proprietary hosted
   product, the clean bases here are Traccar (Apache-2.0), OFBiz (Apache-2.0), Krayin (MIT),
   the SDV blueprint (Apache-2.0), 🆕 **AureusERP (MIT)** and 🆕 **Vision Pilot (Apache-2.0)** — with
   🆕 **Open Mercato (MIT)** usable only outside `packages/enterprise`. Odoo, Fleetbase, OpenRemote and
   OpenAutoCore all carry copyleft obligations, and 🆕 **idurar-erp-crm (AGPL-3.0)** and 🆕 **Huly
   (EPL-2.0, frozen)** are excluded outright.
2. **Expose the domain over MCP or a typed tool API** — vehicle, VIN, repair order, parts, telemetry signal.
   Use **VSS names** for anything vehicle-signal-shaped so the model's vocabulary matches the industry's.
   🆕 **And do not invent the outward-facing contract either:** for anything dealer-facing (discovery,
   inventory, pricing, consented inquiries) implement **Auto Agent Protocol v3.x** above rather than a
   bespoke schema. 🆕 For diagnostics, the MCP servers in [`../agents/top.md`](../agents/top.md) already
   define the tool shape — `obd2-mcp` (MIT) even **bundles a mock vehicle**, so the integration can be
   demonstrated to a client before any hardware exists.
3. **Wrap existing workflows with agents** rather than replacing them: eligibility checks, claim validation
   against repair orders, parts substitution, service scheduling.
4. **Put a human gate on anything that actuates a vehicle or commits money.** Still the one consistent
   design feature across every credible automotive agent reviewed in this KB — and it is what makes the
   EU AI Act's human-oversight duty demonstrable rather than asserted.
5. **Conversational UI / API last.** The value is in the domain model and the gate, not the chat box.

---
*Verified 2026-11-13 (previous passes 2026-10-31, 2026-10-26). 🆕 = new this pass. 🔄 = licence/stars read today. ⏸ = carried forward and
labelled. Where a licence is listed as "not read", the URL is confirmed live and the licence was deliberately left blank rather than guessed.
`curl` and `api.github.com` are both HTTP 403 in this session, so the rendered repository page is the verification channel.*

---

## 🆕 2026-11-21 (fourth pass) — the dealership-DMS question is now CLOSED, and with better evidence

This KB has recorded **seven consecutive negative results** on "is there a permissive open-source
dealership DMS / automotive ERP-CRM". Every one of those came from **web search and listicles**, which
can only ever support *"we did not find one."* This pass asked the **licence-filtered GitHub index**
directly, which supports a much stronger claim.

**Queries and the complete result sets — not a sample, the whole return:**

| Query | Every repository returned |
|---|---|
| `dealership management system DMS license:mit` | `Defcon27/Autorizz-…-NodeJS-Express-MongoDB` **88★, last push 2022-11-21**; `imtutul/dms` **0★, 2019-03-03**; `timsa-m/ebenezar-dms` **0★, 2026-11-20** |
| `car dealership inventory management license:apache-2.0` | `Casey-Jeremy/car_dealership` **0★, 2025-09-19** (a dealership *website*, not a DMS) |

**The finding, stated at the strength the evidence now supports: there is no maintained permissive
open-source Dealer Management System on GitHub.** Not "none found" — the licence-filtered index over
all of GitHub returns **nothing above 88★, and the 88★ entry is a student project abandoned in 2022.**
This is the **8th negative and the first authoritative one.** It is now safe to tell a client, in
writing, that a dealership build starts from a framework and not from a product.

**What that means for an engagement, unchanged but now defensible:**
- [open-mercato/open-mercato](https://github.com/open-mercato/open-mercato) (**MIT**, 1,953★) remains
  the only permissive option and is a **framework, not a dealership product** — budget the domain model.
- The copyleft suites are real but carry obligations: **ERPNext GPL-3.0**, **Dolibarr GPL-3.0**
  (7,889★), **Opentaps GPL-2.0**. `YetiForceCRM` is `NOASSERTION` and unpushed since 2024-09;
  `SuiteCRM` did not resolve.
- 🆕 **Say the quiet part in the proposal:** the DMS market (Tekion, CDK, Reynolds) is proprietary with
  no open flank. **The open opportunity is not replacing the DMS — it is the agent layer beside it**,
  which is why `agents/top.md`'s Auto Agent Protocol row matters more than any ERP fork would.

## 🆕 ECU development benches — a real vertical tool category, newly recorded

Not ERP, but the platform category a studio most often needs to sit beside: the **ECU development and
test bench**, where the commercial incumbents (Vector CANoe/CAPL, ETAS) run five figures per seat.

| Platform | Licence | ★ | What it replaces |
|---|---|--:|---|
| [ecubus/EcuBus-Pro](https://github.com/ecubus/EcuBus-Pro) | ⚠️ **Apache-2.0 in `package.json` only — no `LICENSE` file in the tree** | **914** | **CANoe/CAPL-class bench.** UDS, CAN-TP, DoIP, LIN, TypeScript scripting *"like CAPL"*, HIL test. Functionally the strongest open option; **get the licence file added before it carries a deliverable.** |
| [TOSUN-Shanghai/TSMaster](https://github.com/TOSUN-Shanghai/TSMaster) | **LGPL-2.1** (byte-read, 26,526 b) | 442 | *"A powerful open environment for automotive bus monitoring, simulation, testing."* **APAC-origin (Shanghai)** — relevant where a client's supply chain already runs TOSUN hardware. ⚠️ LGPL: link, don't absorb. |
| [COVESA/dlt-viewer](https://github.com/COVESA/dlt-viewer) | **MPL-2.0** (372 b short form) | 557 | AUTOSAR **Diagnostic Log and Trace** viewing — the log side of the same bench. |

⚠️ **Licence-classifier correction worth carrying:** the first read of `TSMaster` and `autoas/as`
reported plain "GPL". **LGPL's own text contains the string "GNU GENERAL PUBLIC LICENSE"**, so a naive
grep mislabels LGPL as GPL — and the difference decides whether a client can link against it. Match
`LESSER` first. Re-read: **TSMaster = LGPL-2.1**, **`autoas/as` = GPL-3.0** (*"Version 3, 29 June 2007"*).
