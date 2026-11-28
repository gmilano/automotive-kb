---
industry: automotive
region: Global
updated: 2026-11-28
---

# 🏗️ Foundational repos — Automotive

> The bases to build on. Open licence, active community. Grouped by layer, because "automotive open source"
> is four unrelated stacks that are routinely confused.
> **Verification (2026-11-21):** liveness via `git ls-remote`, licences **byte-read** from
> `raw.githubusercontent.com` (HTTP 200), metadata from `gh api -X GET search/repositories`. All 174 KB
> URLs probed; 152 LICENSE files read. `github.com` and `api.github.com` remain **403**, but they are no
> longer needed.
>
> *Superseded note —* **2026-11-13:** `curl -sI` on `github.com` returns **HTTP 403** through this session's
> proxy — re-tested today on three URLs including `api.github.com`, all 403 — so figures are read from
> rendered repository pages. Where the licence was the point, the file was fetched raw from
> `raw.githubusercontent.com`; that is how `autoware-safety-island` was reclassified from GitHub's
> **"Other"** label to **verbatim Apache-2.0** (its file is `license.rst`) and how
> `autoware_latent_drive` was confirmed to have **no licence at all**.
> 🔴 **`huggingface.co` still does not resolve from this session**, so no model-weight licence was verified.
> 🆕 = added 2026-11-13. 🔄 = licence/stars re-read today. ⏸ = URL re-probed, figures carried forward.
> ⚪ = URL live, licence/stars deliberately left blank rather than guessed.

## 🆕 Added 2026-11-28 — **Layer O: the diagnostic-access plane (SOVD)**, 20 repos, and it was the gap under this KB's own beachhead

**Why this layer.** Layers A–N cover the AV stack, the SDV core, charging, data spaces and digital twins.
None of them covers **how a service bay talks to a software-defined vehicle**. Control grep across all
nine files: `SOVD` 0, `ISO 17978` 0, `openxc` 0, `ros2_medkit` 0, `MDD` 0. Meanwhile `intel/trends.md`
`T7` has asserted three times that aftersales is the commercial beachhead. **This layer is the plumbing
that beachhead stands on**, and it was absent.

**All 20 slugs below: `git ls-remote` live, licence byte-read from `raw.githubusercontent.com`. 0 dead.**

### 🆕 Layer O1 — Eclipse OpenSOVD (the SOVD reference stack, Rust-dominant)

ASAM SOVD is the REST/HTTP successor to UDS for SDVs; ASAM reports it is **being transferred to ISO**
(cited as **ISO 17978**) and that **SOVD 1.2.0** kicked off Nov 2025 for a **March 2028** release
(secondary: ASAM conference material). Eclipse OpenSOVD is its open implementation.

| Repo | ★ | Licence (byte-read) | Lang | Role in the stack |
|---|---|---|---|---|
| [eclipse-opensovd/opensovd](https://github.com/eclipse-opensovd/opensovd) | 50 | ✅ Apache-2.0 (9,792 B) | — | Umbrella / entry point. Start reading here. |
| [eclipse-opensovd/classic-diagnostic-adapter](https://github.com/eclipse-opensovd/classic-diagnostic-adapter) | 31 | ✅ Apache-2.0 (10,279 B) | Rust | **The commercially important one.** Fronts *legacy UDS ECUs* with a SOVD interface — i.e. it makes a mixed-age fleet addressable by one API. Pushed **2026-11-28**. |
| [eclipse-opensovd/opensovd-core](https://github.com/eclipse-opensovd/opensovd-core) | 22 | ✅ Apache-2.0 (10,176 B) | Rust | Server, client and gateway. Pushed 2026-11-28. |
| [eclipse-opensovd/odx-converter](https://github.com/eclipse-opensovd/odx-converter) | 13 | ✅ Apache-2.0 (10,279 B) | Kotlin | **ODX → MDD converter.** Decides whether a project is affordable: it reuses the OEM's *existing* ODX diagnostic data instead of re-authoring it. |
| [eclipse-opensovd/fault-lib](https://github.com/eclipse-opensovd/fault-lib) | 9 | ✅ Apache-2.0 (9,792 B) | Rust | Fault library. |
| [eclipse-opensovd/uds2sovd-proxy](https://github.com/eclipse-opensovd/uds2sovd-proxy) | 5 | ✅ Apache-2.0 (11,356 B) | Rust | Maps UDS requests onto SOVD ones. The migration component. |
| [eclipse-opensovd/mdd-ui](https://github.com/eclipse-opensovd/mdd-ui) | 2 | ✅ Apache-2.0 (10,764 B) | Rust | Viewer **and MCP server** for MDD files. The agent-facing surface — see `agents/top.md` **A1**. |
| [eclipse-opensovd/dlt-tracing-lib](https://github.com/eclipse-opensovd/dlt-tracing-lib) | 2 | ✅ Apache-2.0 (10,279 B) | Rust | DLT (AUTOSAR diagnostic log & trace) appender. |
| [eclipse-opensovd/mbedtls-rs](https://github.com/eclipse-opensovd/mbedtls-rs) | 0 | ✅ Apache-2.0 (10,259 B) | Rust | Patched Mbed TLS + Rust bindings. The transport-security dependency. |
| [eclipse-opensovd/demo](https://github.com/eclipse-opensovd/demo) | 1 | ✅ Apache-2.0 (10,279 B) | Kotlin | Runnable demos for all subprojects. The fastest honest estimate of effort. |
| [eclipse-opensovd/cicd-workflows](https://github.com/eclipse-opensovd/cicd-workflows) | 0 | ✅ Apache-2.0 (10,279 B) | Python | Reusable GitHub Actions workflows. |

🔴 **Per-repo IP clearance caveat.** 5 of the org's 17 repos carry **no `LICENSE` file**:
`cpp-bindings`, `cand-relay` (both **code**, both pushed within three weeks), `cda-addons`, `.github`,
`.eclipsefdn`. Eclipse's house convention is Apache-2.0 but clearance is per-repo — **check the repo you
vendor, not the org you found it in.**

### 🆕 Layer O2 — the most-starred SOVD implementation is **not automotive**

| Repo | ★ | Licence (byte-read) | Why it is here |
|---|---|---|---|
| [selfpatch/ros2_medkit](https://github.com/selfpatch/ros2_medkit) | 291 | ✅ Apache-2.0 (11,356 B) | **SOVD diagnostics gateway for ROS 2 robots** — faults, live data, operations, scripts. Pushed 2026-11-28. At 291★ it is **~6× the stars of the automotive reference stack's umbrella repo**. |
| [selfpatch/ros2_medkit_web_ui](https://github.com/selfpatch/ros2_medkit_web_ui) | 9 | ✅ Apache-2.0 (11,356 B) | SOVD web UI: discovery and entity hierarchies as an SPA. |
| [selfpatch/ros2_medkit_mcp](https://github.com/selfpatch/ros2_medkit_mcp) | 6 | ✅ Apache-2.0 (11,356 B) | MCP server bridging LLM agents to the SOVD REST API. |
| [MauroCerrato/sovd-lab](https://github.com/MauroCerrato/sovd-lab) | 3 | ✅ Apache-2.0 **by reference** (810 B short-form header — see `agents/top.md` **A3**) | YAML/JSON capability descriptions, `/docs` endpoint, OpenAPI specs. Useful as a *conformance fixture*. GitHub reports `NOASSERTION`; the prose read says otherwise. |

**The transferable finding:** an automotive standard's best open implementation came out of **robotics**,
and it arrived with an MCP bridge already attached. When an automotive layer looks like it has no agent
tier, **search the standard's name outside the industry** before declaring the gap.

### 🆕 Layer O3 — the vehicle-data-interface layer: BSD-3, Ford-originated, and **half of it is stale**

| Repo | ★ | Licence (byte-read) | Last push | Note |
|---|---|---|---|---|
| [openxc/openxc-android](https://github.com/openxc/openxc-android) | 248 | ✅ BSD-3-Clause (1,503 B) | 2026-08-08 | Android library for reading vehicle data from an OpenXC interface. **Maintained.** |
| [openxc/vi-firmware](https://github.com/openxc/vi-firmware) | 211 | ✅ BSD-3-Clause (1,503 B) | 2026-03-27 | Vehicle-interface firmware (PIC32, LPC1768). **Maintained.** |
| [openxc/openxc-message-format](https://github.com/openxc/openxc-message-format) | 107 | ✅ BSD-3-Clause (1,503 B) | 2026-02-05 | The JSON message-format spec. The piece you actually depend on. |
| [openxc/openxc-python](https://github.com/openxc/openxc-python) | 119 | ✅ BSD-3-Clause (1,503 B) | **2022-03-24** | ⚠️ **~4.7 years stale.** Do not plan a Python integration on it without budgeting a fork. |
| [openxc/openxc-vehicle-simulator](https://github.com/openxc/openxc-vehicle-simulator) | 71 | ✅ BSD-3-Clause (1,503 B) | **2021-03-19** | ⚠️ **~5.7 years stale.** |

All five are `Copyright (c) 2012 Ford Motor Company`. **BSD-3-Clause is the most permissive licence family
in this KB's automotive shelf** — no copyleft, no patent clause to argue about, attribution only.
See `agents/top.md` **A3** for why a name-based licence detector cannot see any of them.

### 🆕 Layer O4 — workshop / repair-side bases (small, but real and permissive)

| Repo | ★ | Licence (byte-read) | Note |
|---|---|---|---|
| [aon082910/repair-hub](https://github.com/aon082910/repair-hub) | 3 | ✅ MIT (1,065 B) | Self-hosted repair reference: vehicles, DTC lookup, wiring diagrams, estimates. Pushed 2026-11-16. |
| [srmming/repairnote-open-source](https://github.com/srmming/repairnote-open-source) | 4 | ✅ MIT (1,079 B) | Repair-shop management on Next.js + Prisma + MySQL/MariaDB. Pushed 2026-09-18. |
| [LoganCarter08/Open_CAN_Bus_Hub](https://github.com/LoganCarter08/Open_CAN_Bus_Hub) | 13 | ✅ MIT (1,068 B) | Open-source CAN-bus hub — the aftermarket hardware interface. |
| [ETSoftwareStudio/obd-scanner-android](https://github.com/ETSoftwareStudio/obd-scanner-android) | 8 | ✅ Apache-2.0 (11,356 B) | Kotlin/Compose/Hilt OBD-II scanner sample. Pushed 2026-11-22. A clean modern starting point. |
| [tronikos/elm327_obdii](https://github.com/tronikos/elm327_obdii) | 2 | ✅ Apache-2.0 (11,356 B) | Python ELM327 BLE reader. Pushed 2026-11-12. |
| [Kukun7610/Vehicle_CAN_Diagnostic_tool](https://github.com/Kukun7610/Vehicle_CAN_Diagnostic_tool) | 3 | ✅ Apache-2.0 (11,356 B) | CAN-bus diagnostic + data-logging tool. Pushed 2026-11-27. |

🔴 **What is *not* here, measured.** No permissive anchor exists for: **warranty-claim processing**
(`warranty claim` = 830 repos, top hits are ToS text spam), **mileage/odometer integrity**
(`odometer fraud detection` = **0**), **SERMI** accreditation tooling (**0**), or **parts-catalogue data**
(`tecdoc parts catalog` = 4 repos, all 0★ and unlicensed). Full table in `agents/top.md` **A5**. The
workshop *application* layer above is genuine but thin — **nothing here is Odoo-shaped**, and
`verticals/solutions.md` says so plainly.

## 🆕 Added 2026-11-24 (third pass) — **Layer L: the data-space / digital-twin plane**, 30 repos, and it was a total blind spot

A control grep for `Catena-X`, `Tractus-X`, `dataspace`, `data space` and `battery passport` returned
**0 hits across all nine files** before this pass. This is the layer the EU's **battery passport
(18 Feb 2027)** and supply-chain due-diligence duties physically land on, and it is **overwhelmingly
Apache-2.0 / MIT** — the most permissive layer this KB has yet measured.

**All licences below byte-read from `raw.githubusercontent.com`; all addresses live via `git ls-remote`
(control: fabricated slug = DEAD).**

### 🆕 Layer L1 — Dataspace connectors (the Dataspace Protocol plane)

| Repo | ★ | Licence (byte-read) | Role |
|---|---|---|---|
| [eclipse-edc/Connector](https://github.com/eclipse-edc/Connector) | **429** | ✅ Apache-2.0 (10,172 B) | **The anchor.** Eclipse Dataspace Components — reference implementation of the Dataspace Protocol (DSP) and Decentralized Claims Protocol (DCP). Pushed 2026-11-23. |
| [FraunhoferISST/DataspaceConnector](https://github.com/FraunhoferISST/DataspaceConnector) | 106 | ✅ Apache-2.0 (10,796 B) | The original IDS connector. ⏸ **Stale — last push 2022-03-31.** Historically important, superseded by EDC. Do not start here. |
| [eclipse-tractusx/tractusx-edc](https://github.com/eclipse-tractusx/tractusx-edc) | 96 | ✅ Apache-2.0 (11,356 B) | **The automotive distribution of EDC** — EDC plus Catena-X policy/identity extensions. This, not plain EDC, is the automotive starting point. |
| [FIWARE/data-space-connector](https://github.com/FIWARE/data-space-connector) | 61 | ✅ Apache-2.0 (11,356 B) | FIWARE's connector; the alternative lineage. Pushed 2026-11-23. |
| [eclipse-edc/IdentityHub](https://github.com/eclipse-edc/IdentityHub) | 46 | ✅ Apache-2.0 (10,172 B) | Verifiable-credential wallet / DCP identity. |
| [eclipse-edc/Samples](https://github.com/eclipse-edc/Samples) | 86 | ✅ Apache-2.0 (10,172 B) | Runnable EDC samples — the actual on-ramp for an engineer. |
| [eclipse-edc/FederatedCatalog](https://github.com/eclipse-edc/FederatedCatalog) | 12 | ✅ Apache-2.0 (10,172 B) | Cross-participant catalogue crawling. |
| [Prometheus-X-association/dataspace-connector](https://github.com/Prometheus-X-association/dataspace-connector) | 17 | ✅ **MIT** (1,059 B) | Non-EDC lineage, MIT. Pushed 2026-11-23. |
| [Mobility-Data-Space/mds-edc](https://github.com/Mobility-Data-Space/mds-edc) | 8 | ✅ Apache-2.0 (11,356 B) | **Mobility Data Space** EDC build — the mobility-sector sibling of Catena-X. |
| [awslabs/dataspace-connector-on-aws](https://github.com/awslabs/dataspace-connector-on-aws) | 11 | ✅ Apache-2.0 (10,141 B) | AWS reference deployment. Pushed 2026-11-21. |
| [awslabs/minimum-viable-dataspace-on-aws](https://github.com/awslabs/minimum-viable-dataspace-on-aws) | 11 | ✅ **MIT-0** (945 B) | **Minimum viable dataspace** on AWS — MIT-0 means *no attribution condition at all*. The cheapest legitimate way to stand up a demo. |

### 🆕 Layer L2 — Catena-X / Tractus-X business applications (Eclipse Tractus-X)

**Measured today: `org:eclipse-tractusx` = 83 repositories.** Secondary (IDSA): >330 active contributors,
quarterly releases. Release train naming is `R26.06`-style (read from `puris`'s dependency table).

| Repo | ★ | Licence (byte-read) | Role |
|---|---|---|---|
| [eclipse-tractusx/sldt-semantic-models](https://github.com/eclipse-tractusx/sldt-semantic-models) | 58 | 📄 CC-BY-4.0 (16,677 B, **no NC/ND**) | The Catena-X semantic models. Non-code → CC-BY is the **house convention**, not a risk. |
| [eclipse-tractusx/digital-product-pass](https://github.com/eclipse-tractusx/digital-product-pass) | 50 | ✅ Apache-2.0 (11,504 B) | **Digital Product Passport / battery passport viewer.** The direct open-source answer to the 2027 duty. ⏸ last push 2025-09-18 — verify currency before quoting. |
| [eclipse-tractusx/tractus-x-umbrella](https://github.com/eclipse-tractusx/tractus-x-umbrella) | 27 | ✅ Apache-2.0 (11,357 B) | **Umbrella Helm chart — the whole dataspace in one `helm install`.** Start demos here. Pushed 2026-11-20. |
| [eclipse-tractusx/industry-core-hub](https://github.com/eclipse-tractusx/industry-core-hub) | 26 | ✅ Apache-2.0 (11,559 B) | Data provision/consumption orchestrator; its own pitch is **"onboarding to first data exchange in days, not months"**. The highest-leverage repo for a supplier-onboarding engagement. |
| [eclipse-tractusx/puris](https://github.com/eclipse-tractusx/puris) | 21 | ✅ Apache-2.0 (11,532 B) | **PURIS** — short-term demand & capacity management. Declares compliance against named standards: **CX-0118, CX-0120, CX-0121, CX-0122, CX-0145, CX-0146, CX-0018**. Pushed 2026-11-23. |
| [eclipse-tractusx/sldt-digital-twin-registry](https://github.com/eclipse-tractusx/sldt-digital-twin-registry) | 19 | ✅ Apache-2.0 (11,357 B) | Digital Twin Registry (AAS discovery). |
| [eclipse-tractusx/traceability-foss](https://github.com/eclipse-tractusx/traceability-foss) | 17 | ✅ Apache-2.0 (11,356 B) | **Parts traceability / quality notifications** — the recall-and-defect use case. |
| [eclipse-tractusx/tractusx-sdk](https://github.com/eclipse-tractusx/tractusx-sdk) | 15 | ✅ Apache-2.0 (11,559 B) | Python SDK, published on PyPI. **The integration surface an agent should call.** Pushed 2026-11-20. |
| [SAP/ssi-dim-middle-layer](https://github.com/SAP/ssi-dim-middle-layer) | 5 | ✅ Apache-2.0 (11,356 B) | SAP's self-sovereign-identity middle layer for the Catena-X onboarding flow. |

### 🆕 Layer L3 — Asset Administration Shell (the digital-twin standard, IDTA)

The AAS is **the** industrial digital-twin metamodel, and this sub-layer is **MIT-dominant**:

| Repo | ★ | Licence (byte-read) | Role |
|---|---|---|---|
| [admin-shell-io/aasx-package-explorer](https://github.com/admin-shell-io/aasx-package-explorer) | **139** | ✅ Apache-2.0 (**75,733 B**) | The reference AAS authoring tool. API said `NOASSERTION`; the file is a 75 KB **bundled-dependency notice** — a *long* file is the mirror image of the `sovity` trap. ⏸ last push 2024-04-16. |
| [eclipse-basyx/basyx-python-sdk](https://github.com/eclipse-basyx/basyx-python-sdk) | 108 | ✅ **MIT** (1,086 B) | Eclipse BaSyx Python SDK. Pushed 2026-11-23. |
| [admin-shell-io/submodel-templates](https://github.com/admin-shell-io/submodel-templates) | 95 | 📄 CC-BY-4.0 (18,649 B, no NC/ND) | The official submodel templates. Pushed 2026-11-20. |
| [FraunhoferIOSB/FAAAST-Service](https://github.com/FraunhoferIOSB/FAAAST-Service) | 94 | ✅ Apache-2.0 (11,356 B) | **FA³ST** AAS runtime — the Java server alternative to BaSyx. Pushed 2026-11-23. |
| [eclipse-basyx/basyx-java-server-sdk](https://github.com/eclipse-basyx/basyx-java-server-sdk) | 84 | ✅ **MIT** (1,024 B) | The AAS server most deployments actually run. Pushed 2026-11-23. |
| [admin-shell-io/aas-specs-metamodel](https://github.com/admin-shell-io/aas-specs-metamodel) | 78 | 📄 CC-BY-4.0 (18,650 B, no NC/ND) | The metamodel specification itself. |
| [eclipse-basyx/basyx-aas-web-ui](https://github.com/eclipse-basyx/basyx-aas-web-ui) | 35 | ✅ **MIT** (1,081 B) | Web UI for browsing twins. Pushed 2026-11-23. |
| [admin-shell-io/aas-test-engines](https://github.com/admin-shell-io/aas-test-engines) | 30 | ✅ Apache-2.0 (11,356 B) | **Conformance test engines** — turns "we support AAS" into a test report. |
| [admin-shell-io/aas-specs-api](https://github.com/admin-shell-io/aas-specs-api) | — | 📄 CC-BY-4.0 (18,650 B, no NC/ND) | The IDTA **Part 2 API** specs; the required input for `SAP/aas-mcp-server` (tag `v3.2.0`). |

### 🆕 Layer M — one genuine foundational gap closed: the **map format**

| Repo | ★ | Licence (byte-read) | Role |
|---|---|---|---|
| [fzi-forschungszentrum-informatik/Lanelet2](https://github.com/fzi-forschungszentrum-informatik/Lanelet2) | **979** | ✅ **BSD-3-Clause** (1,476 B) | **Lanelet2** — the HD-map library and format that **Autoware consumes**. This KB has carried Autoware since cycle 2 and `HD map` appeared in 11 lines of prose, yet **`Lanelet2` had 0 mentions**: the map layer under the AV stack was never named. BSD-3 (default branch `master`). |

> **Method note on how this was missed for 9 passes:** the gap was not a supply gap, it was a
> **vocabulary** gap. The KB searched for `HD map` (a *description*) and never for `Lanelet2` (the
> *artefact name*). Same failure shape as the `automotive`-word finding (**N16**) and the `CarDash`
> finding — **search the name of the thing, not the category it belongs to.**

### 🔴 Layer N — the CAN **intrusion-detection** layer: measured, and it has essentially no permissive anchor

`automotive intrusion detection` → 114 repos; the **entire** top tier by stars is 12★ and below, and
licence-bearing rows are almost absent:

| Repo | ★ | Licence (byte-read) | Verdict |
|---|---|---|---|
| [lorenzo9uerra/CAN-IDSs-on-the-ROAD](https://github.com/lorenzo9uerra/CAN-IDSs-on-the-ROAD) | 12 | ✅ **MIT** (1,070 B) | **The only permissive, licensed CAN-IDS repo found.** Benchmarks CAN IDSs on the ROAD dataset. Pushed 2026-09-30. |
| `sececter/CAN-control` | 6 | ⚠️ GPL-3.0 | Copyleft, and stale since 2017. |
| 4 further CAN-IDS repos at 3–6★ | — | 🔴 **no licence** | `dankimh/…LSTM`, `Mostafa-Noshy/CAN_intrusion`, `Zhou-CyberSecurity-AI/CAN-BERTtoDNN`, `AlCodes808/CAN-Bus-Sentinel-IDS`. |

**This extends this KB's layered-licence-risk finding to a third layer.** Diagnostics = permissive
throughout; V2X/C-ITS = no permissive anchor (later corrected, see `agents/top.md` W1); **intrusion
detection = one MIT repo at 12★ and nothing else.** R155 requires a CSMS and detection capability, so
**the IDS layer must be quoted as build-from-scratch or commercial-licensed — never as "build on open source."**

### 🔴 The insurance-telematics / UBI layer: **no open-source anchor exists**

`usage based insurance` and `insurance telematics` both return **Damoov's commercial SDK wrappers** as the
top results (`Mobile-Telematics/TelematicsApp-Android` 76★, iOS 40★, Flutter 25★) — byte-read as
**"Damoov Service Terms"**, a commercial agreement, not a licence. Everything else in the top tier is
Kaggle-competition code (2016) or unlicensed student work. **Declared gap, with the reason: the UBI layer
is a commercial-SDK market, not an open-source one.**

### ✅ Fairness re-probe — and the short-query rule holds for a **third** time

Per the standing rule that *"a 0-repos cell is a claim about the instrument until a short query has been
tried"*, this pass deliberately re-probed its own negative:

| Query | Terms | Result |
|---|---|---|
| `manufacturing quality inspection license:apache-2.0` | 4 | **2 repos**, both 1★ |
| `defect detection license:apache-2.0` | 3 | **210 repos** |
| `visual inspection license:mit` | 3 | **398 repos** |
| `anomaly detection license:apache-2.0` | 3 | **1,525 repos** — top row [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) at **6,420★**, Apache-2.0, pushed 2026-11-21 |

**Had this pass written its 4-term result down, it would have published a fabricated gap** over a layer
whose anchor has 6,420 stars and was already in this KB (Layer G). Third confirmation; the rule is now
load-bearing and should be applied to every `0-repos` cell in this fleet.

## 🆕 Added 2026-11-24 — the EV/battery gap is CLOSED, and it was the **industry word** again (third instance)

**This KB has carried `EV / battery AI = 0 repos` since 2026-11-19.** It is not a gap. The anchors are
mature, permissive, maintained — and **neither of them says "automotive" anywhere in its pitch**, which
is exactly the failure mode trend **N16** named for the plant floor. *That makes three: plant-floor
inspection (N16), EV/battery (here), and the assurance tool tier (Layer I below). The industry word is
this KB's single biggest discovery defect.*

### 🆕 Layer H — EV / battery modelling and management

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [pybamm-team/PyBaMM](https://github.com/pybamm-team/PyBaMM) | **BSD-3-Clause** — `LICENSE.txt`, 1,494 B, *"Copyright (c) 2018, the PyBaMM team"* | **1,742** | **2026-11-23** | **The anchor of this layer.** Fast, flexible **physics-based** battery models (DFN/P2D, SPM, SPMe) in Python. Permissive, actively maintained, the de-facto standard in battery simulation. For range, degradation, thermal and fast-charge work this is the base — **do not start from a dissertation notebook.** |
| [foxBMS/foxbms-2](https://github.com/foxBMS/foxbms-2) | **BSD-3-Clause (software)** + **CC-BY-4.0 (hardware & docs)** — split grant, byte-read `LICENSE.md`, 1,185 B | **512** | 2026-10-08 | **The only automotive-grade open BMS platform found.** From **Fraunhofer IISB (Erlangen, Germany)** — free, open, flexible BMS *hardware and software* platform. EMEA-origin. See the split-grant note below before quoting it. |
| [patman15/BMS_BLE-HA](https://github.com/patman15/BMS_BLE-HA) | **Apache-2.0** — index-reported | 380 | 2026-11-22 | Monitors BLE battery-management systems from ~20 vendors. **Not automotive-grade** — a Home Assistant integration — but it is the broadest open **BMS protocol corpus** in existence, which is the expensive part of any pack-diagnostics build. |
| [fl4p/batmon-ha](https://github.com/fl4p/batmon-ha) | **MIT** — index-reported | 536 | 2026-11-23 | Same shape: JK, JBD, Daly, ANT, SOK, Supervolt BMS over Bluetooth. Pair with the row above as a **protocol reference**, not a product base. |
| [FrankSuperG/electrochemical-battery-model-atlas](https://github.com/FrankSuperG/electrochemical-battery-model-atlas) | **CC-BY-4.0** — index-reported ⚠️ *docs licence, not a software grant* | 51 | 2026-09-23 | Curated index of open electrochemical battery models with reproducibility notes. Use it to **choose** a model; it is not code you ship. |

#### 🔴 foxBMS is a **split grant**, and one line in it is a *request*, not a condition

Its `LICENSE.md` is three distinct things and a client diligence report must separate them:

1. **Software → BSD-3-Clause.** Permissive. Ship it.
2. **Hardware & documentation → CC-BY-4.0.** Attribution required; fine for schematics and docs.
3. **A trademark courtesy:** *"We kindly request you to use one or more of the following phrases…
   'This product uses parts of foxBMS®'."* **This is a request, not a licence condition** — it sits
   under *"Further Information"*, outside both grants, and uses "kindly request".

**New rule for this KB: distinguish an obligation from a request when reading a grant file.** Writing
foxBMS up as "BSD-3 with an attribution requirement" would over-constrain a client for no legal reason.
Writing it up as plain BSD-3 would miss that the docs are CC-BY. Both halves have to be said.

### 🆕 Layer I — The assurance / V-cycle tool tier (what **P14** was missing)

**P14 (the assurance artefact factory) has until now rested entirely on agent skill suites.** Skills
generate documents; they do not *check* code against a standard. These four do, they are all permissive,
and none of them markets itself as automotive:

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [github/codeql-coding-standards](https://github.com/github/codeql-coding-standards) | **MIT** — `LICENSE.md`, 1,062 B, *"Copyright (c) 2022 GitHub"* | **235** | 2026-11-20 | **The highest-value row in this section.** CodeQL queries and libraries implementing **MISRA C/C++ and AUTOSAR C++14** coding standards — maintained by **GitHub itself**. This turns "we comply with MISRA" from a consultant's assertion into **CI output**. Drops straight into **P14** as the automated-evidence leg. |
| [useblocks/sphinx-needs](https://github.com/useblocks/sphinx-needs) | **MIT** — `LICENSE`, 1,076 B, *"useblocks GmbH"* | **329** | 2026-11-23 | Requirements, specifications and **traceability links** as Sphinx objects — docs-as-code for the ISO 26262 work-product chain. The traceability matrix an auditor asks for, generated from the repo. EMEA-origin (Germany). |
| [QuantumLeaps/spexygen](https://github.com/QuantumLeaps/spexygen) | **MIT** — `LICENSE`, 1,160 B | 43 | 2026-11-19 | Traceable specifications via Doxygen — bidirectional requirement↔code↔test links. The lighter-weight alternative to the row above when the codebase is C/C++ and already Doxygen'd. |
| [WinterLabsHQ/maisha](https://github.com/WinterLabsHQ/maisha) | **MIT** — `LICENSE`, 1,392 B | 8 | 2026-11-20 | **MISRA C / CERT C / BARR-C compliance for embedded C — explicitly "the vendor-neutral alternative."** ⚠️ **8★ and a month old.** Recorded because the *category* (open MISRA checking) was previously empty except for the GitHub row; watch it. |

**Why this tier is strategically interesting:** the automotive assurance-tool market is dominated by
paid static analysers. A **permissive MISRA/AUTOSAR checker maintained by GitHub** changes the quote for
every ISO 26262 engagement — the evidence pipeline becomes a configuration deliverable rather than a
licence resale.

### 🆕 Layer J additions — AUTOSAR/ARXML and diagnostics, and a Tier-1 tool vendor shipping MIT

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [vectorgrp/XCPlite](https://github.com/vectorgrp/XCPlite) | **MIT** — `LICENSE`, 1,082 B, *"Copyright (c) 2026 **Vector Informatik GmbH**"* | **271** | 2026-11-21 | **The notable one.** ASAM **XCP** on Ethernet, published under MIT by **Vector Informatik** — the Tier-1 measurement/calibration tool vendor. The calibration layer was assumed vendor-locked (`TSMaster` is LGPL-2.1 and gated). It is not: the protocol implementation is MIT from the incumbent itself. |
| [mdabrowski1990/uds](https://github.com/mdabrowski1990/uds) | **MIT** — `LICENSE`, 1,074 B | 154 | 2026-11-23 | **UDS (ISO 14229)** in Python with a common API across transports. Joins `python-udsoncan` as a second permissive UDS implementation — **P23**'s fully-permissive diagnostics bench now has a choice, which matters for a client that must avoid a single-maintainer dependency. |
| [girishchandranc/autosarfactory](https://github.com/girishchandranc/autosarfactory) | **MIT** — `LICENSE`, 1,097 B | 132 | 2026-11-12 | Python package to **read/create/modify AUTOSAR ARXML** as objects. Direct input to **P25** (ARXML as data). |
| [DanielT/autosar-data](https://github.com/DanielT/autosar-data) | **MIT** — `LICENSE-MIT`, 1,080 B ⚠️ *filename is `LICENSE-MIT`, Rust dual-licence convention — check for a parallel `LICENSE-APACHE`* | 70 | 2026-11-15 | Rust crate for ARXML. The performant option for **P25** when the ARXML set is large enough that Python object graphs stop being viable. |
| [I-CAN-hack/automotive](https://github.com/I-CAN-hack/automotive) | **MIT** — `LICENSE`, 1,067 B | 109 | 2026-11-17 | Rust crate with **Python bindings** — CAN communication, UDS, diagnostics. The bridge row: Rust performance with a Python surface for the agent layer. |
| [AKJ7/CANExplorer](https://github.com/AKJ7/CANExplorer) | **MIT** — `LICENSE.md`, 1,060 B | 223 | 2026-11-22 | CAN bus GUI and toolkit, actively maintained. |
| [CANnectivity/cannectivity](https://github.com/CANnectivity/cannectivity) | **Apache-2.0** — `LICENSE`, 11,357 B | 206 | **2026-11-23** | Hardware-agnostic **USB-to-CAN adapter firmware** (Zephyr-based). Closes the last proprietary link in **P23**: the interface *hardware firmware* is now permissive too, so the bench is open end to end — host library, protocol, and dongle. |
| [nickn17/evDash](https://github.com/nickn17/evDash) | **MIT** — `LICENSE`, 1,065 B | 186 | 2026-11-17 | **EV** dashboard for dev boards over OBD2-BLE4 or CAN — Hyundai/Kia/Renault EV PIDs. The EV-specific counterpart to Layer J's ICE-oriented tools, and a rare source of **real pack-level PID maps**. |
| [nopnop2002/Arduino-STM32-CAN](https://github.com/nopnop2002/Arduino-STM32-CAN) | **MIT** — index-reported | 282 | 2026-11-23 | CAN examples for Arduino STM32 cores. Bench-rig plumbing. |

### 🆕 Layer K — Plant-floor asset operations (extends Layer G)

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [IBM/AssetOpsBench](https://github.com/IBM/AssetOpsBench) | **Apache-2.0** — `LICENSE`, 11,357 B | **2,483** | 2026-11-21 | **Industry 4.0 benchmark *and* framework for building, orchestrating and evaluating agents for asset operations** — IBM-maintained, 2,483★. This is **P15**'s "buy the harness, not the model" argument applied to the plant floor instead of the vehicle. Pairs with `anomalib` (Layer G) as the evaluation half. |
| [kokikwbt/predictive-maintenance](https://github.com/kokikwbt/predictive-maintenance) | **MIT** — index-reported | 177 | 2026-11-10 | Curated **datasets** for predictive maintenance. The data half of the above — and see **N17**'s warning: a dataset grant is a separate axis from the code grant. |
| [BaronTrump/AutoPartVision](https://github.com/BaronTrump/AutoPartVision) | **Apache-2.0** — index-reported | **1** | ⏸ 2026-06-17 | ⚠️ **1★.** Real-time defect inspection for **auto-parts lines** (RF-DETR/YOLOX + instance segmentation + ByteTrack). Listed **only** to document that it is the *entire* purpose-built population — see the licence-filtered measurement in `repos/trending.md`. **The finding is the count, not the repo.** |

### 🆕 Fleet — one addition

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [traccar/traccar-web](https://github.com/traccar/traccar-web) | **Apache-2.0** — `LICENSE.txt`, 11,358 B | **1,207** | **2026-11-23** | The web dashboard for Traccar (8,179★, Apache-2.0, 200+ device protocols — already held). Recorded separately because **the server and the UI are different repositories with different clone targets**, and **P5** deploys both. Takes the fleet-telematics layer from 2 repos to 3. |

### 🔴 Licence rejections this pass — five, and the biggest one is the most dangerous

| Repo | ★ | Licence (byte-read) | Verdict |
|---|--:|---|---|
| [Serial-Studio/Serial-Studio](https://github.com/Serial-Studio/Serial-Studio) | **7,335** | **Dual: `GPL-3.0-or-later` OR `LicenseRef-SerialStudio-Commercial`**, `LICENSE.md` 2,332 B | ⛔ **Not permissive, and the trap is the structure.** Telemetry dashboard (UART/BLE/MQTT/Modbus/**CAN**) — exactly what a vehicle-bench dashboard needs, and 7,335★ means clients *will* raise it. **The SPDX header of each individual file is authoritative**, declared per-file or via `REUSE.toml`. Default build (`BUILD_GPL3=ON`) is **GPLv3**. "Pro module" files are **proprietary-only** and the published binaries ship under an EULA, not the GPL. **Per-file licence determination required — budget it or decline it.** |
| [stuartpittaway/diyBMSv4](https://github.com/stuartpittaway/diyBMSv4) | **1,145** | **CC-BY-NC-SA-2.0-UK**, `LICENSE` 1,431 B | ⛔ **Non-commercial.** The most-starred DIY BMS. 1,145★ makes it a likely client suggestion for Layer H; it cannot be used commercially at all. |
| [openremote/core](https://github.com/openremote/core) | **2,185** | **AGPL-3.0**, `LICENSE.txt` **172,958 B** | ⛔ IoT platform pitched as "100% open-source"; the grant is **AGPL** — network copyleft. Excluded from the fleet layer. *(Note the 172 KB file: it is the licence plus a bundled third-party notices appendix — size alone does not identify a grant, read the opening lines.)* |
| [iUnreallx/ReDrive](https://github.com/iUnreallx/ReDrive) | 158 | **GPL-3.0**, `LICENSE` 682 B | ⛔ Open-source OBD2 dashboard, actively pushed. Copyleft — excluded from **P23**/**P24**. |
| [Lularible/from-sand-to-ruts](https://github.com/Lularible/from-sand-to-ruts) | 96 | **CC-BY-NC-ND-4.0**, `LICENSE` 19,121 B | ⛔ **The worst grant shape in this KB: non-commercial *and* no-derivatives.** A 33-chapter panorama of automotive embedded computing — genuinely good onboarding material that **cannot be excerpted, adapted or used commercially**. Link to it; never copy from it. |

#### 🔴 Two licence-detector facts learned this pass

1. **A grant file may be spelled `LICENCE`.** [Lyric0620/ETSAuto](https://github.com/Lyric0620/ETSAuto)
   (184★) is **MIT** — byte-read from `LICENCE`, 1,067 B, British spelling. A probe list of
   `LICENSE / LICENSE.md / LICENSE.txt / COPYING` reports **"no licence"** on an MIT repo. **`LICENCE`
   is now in this KB's probe list** (as is `LICENSE-MIT`, per `autosar-data` above).
2. **Licence is per-repository, not per-author.** `christoph2/pyxcp` is **LGPL-3.0** (283★) while
   `christoph2/pyA2L` is **GPL-2.0** (179★) — same maintainer, same ASAM domain, two different
   copyleft grants, neither usable. Never infer one repo's licence from a sibling's.

#### ⏸ Two MIT repos that are live, permissive and **stale** — stars are not maintenance

[vietanhdev/open-adas](https://github.com/vietanhdev/open-adas) — **MIT** (`LICENSE`, 1,073 B), **509★**,
pushed **2023-10-24**. [Lyric0620/ETSAuto](https://github.com/Lyric0620/ETSAuto) — **MIT**, 184★, pushed
**2024-03-12**. Both are live and permissively licensed; both have been untouched for 2–3 years. They
belong in a KB as *reference architectures* and nowhere near a proposal as a base. **This is the same
freshness trap recorded on 2026-11-21 for VIA-AI, arriving through a different door: there the listicle's
year misled, here the star count does.**

## 🆕 Added 2026-11-21 (third pass, 13:40Z) — Layer G: the plant floor, a gap this KB has carried at **zero repos for five passes**

**This closes the longest-standing supply gap in this KB.** Every prior pass measured
`plant-floor / manufacturing quality AI = 0 repos` and moved on. The gap was an artefact of **where we
were looking**: five passes searched `automotive` + `AI` + `agent`, and the plant-floor stack does not
describe itself as automotive at all — it is **industrial anomaly detection**, and it is mature,
permissive and maintained.

This matters disproportionately for this industry because **manufacturing is where the non-AV automotive
money is**, and it is the one automotive layer with a serious installed base in **every** region
including LATAM (see `intel/market.md` → Opportunities by region).

### 🆕 Layer G — Industrial visual inspection / anomaly detection (the plant-floor layer)

| Repo | Licence (byte-read) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [open-edge-platform/anomalib](https://github.com/open-edge-platform/anomalib) | **Apache-2.0** — `LICENSE`, 11,357 bytes, canonical | **6,414** / 1,047f | **2026-11-20** | **The anchor of this layer, and the only production-grade one.** Intel-maintained library of 20+ industrial anomaly-detection algorithms (PatchCore, PaDiM, EfficientAD…) with OpenVINO export. **Pushed yesterday**, 1,047 forks. For paint, weld, panel-gap and battery-module inspection this is the base to start from rather than build. ⚠️ **Read the dataset warning below before quoting a benchmark number.** |
| [sundyCoder/DEye](https://github.com/sundyCoder/DEye) | **Apache-2.0** — `LICENSE`, 11,357 bytes, canonical | 885 / 367f | ⚠️ **2023-03-14** | Surface-defect inspection, semiconductor-oriented. **Dormant 3.5 years — reference only, do not propose it as a base.** Listed because 885★/367f means client teams will have heard of it and will ask. |
| [awslabs/sagemaker-defect-detection](https://github.com/awslabs/sagemaker-defect-detection) | **Apache-2.0** — `LICENSE`, 10,142 bytes, canonical | 62 / 25f | ⚠️ **2022-12-21** | Supervised bounding-box defect detection on steel surfaces (NEU dataset). **Dormant 4 years and AWS-coupled** — useful as an architecture reference for a SageMaker-hosted client, not as a starting point. Default branch is `mainline`, not `main`. |

**The honest shape of this layer: one live anchor and two dormant references.** That is a finding, not a
shortfall — it means an engagement standardises on `anomalib` and treats everything else as prior art.

### 🔴 The dataset-licence trap, and it is the new error class from this pass

**`anomalib` is Apache-2.0. Its benchmark dataset is not.** **MVTec AD** — the dataset essentially every
industrial-anomaly-detection paper and tutorial reports against — is **CC BY-NC-SA 4.0: non-commercial.**

The code licence and the data licence are **independent axes**, and for an AI repo **the data licence is
usually the binding one**:

- ✅ Using `anomalib`'s **code** in a client deliverable: permitted by Apache-2.0.
- 🔴 Shipping **weights trained on MVTec AD** to a paying client: **commercial use of an NC dataset.**
- 🔴 Quoting an **MVTec AD benchmark number** in a commercial proposal: the same problem, and it is the
  form the mistake actually takes, because the benchmark table is the first thing a proposal copies.
- ✅ The clean path: train on **the client's own line images**, which is what the engagement should be
  doing anyway. The NC dataset is for *method selection*, never for the delivered model.

**Generalise this across every KB in this fleet:** a permissive SPDX on the repo says **nothing** about
the corpus the model was fitted to. Byte-reading `LICENSE` — the discipline this KB already enforces —
**does not catch this at all**, because the trap is not in `LICENSE`.

### 🔄 Two NOASSERTION rows resolved — and the resolution was already in `compose/patterns.md` P19

An internal inconsistency found by cross-reading this file against P19: **P19 records the byte-read answer
for both of these, while the rows below still tell the reader to "settle before any use."** A reader of
`foundations.md` was getting worse advice than a reader of `patterns.md`. Both rows are corrected in
place in Layer A / Layer 2 below, and the answers are:

| Repo | GitHub SPDX | Byte-read grant | What it means |
|---|---|---|---|
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | `NOASSERTION` | **MIT** — `LICENSE`, 1,170 bytes, *"The MIT License (MIT)"* | ✅ **Usable. Settled, not pending.** The largest repo in this file (**30,951★**) is cleanly permissive. |
| [autoas/as](https://github.com/autoas/as) | `NOASSERTION` | **Dual: GPL-3.0 OR Commercial** — `LICENSE`, 1,299 bytes, *"Dual License: GPLv3 and Commercial"*, © 2025 Parai Wang | 🔴 **Not usable under GPLv3 for proprietary client work — but a commercial grant exists and is offered by the author.** The "settle it" step is a **procurement conversation**, not a licence investigation. For the only substantial open AUTOSAR BSW, that is worth knowing before it is written off. |

### 🆕 The mechanism behind `NOASSERTION`, measured twice this pass — and it inverts the signal

Both NOASSERTION cases above are **verbatim licence text made non-matching by appending honest
information**. GitHub's classifier is near-exact-match, so *any* insertion drops the file to
`NOASSERTION`:

- `PythonRobotics` inserts a **contributors URL** after the copyright line.
- `MayankGangwal-code/ev-battery-soc-estimation` (probed this pass) appends a **dataset attribution**:
  *"The processed data in `data/` is derived from 'LG 18650HG2 Li-ion Battery Data' … Mendeley Data,
  doi:10.17632/cp3473x7xv.3, licensed CC BY 4.0."* Its MIT text is otherwise byte-identical to a
  canonical MIT file that GitHub classifies correctly.

**So `NOASSERTION` correlates with conscientious authorship, not with licence risk** — the careless
repos in this KB have **no licence file at all** and classify as `NONE`, not `NOASSERTION`. Sharpen the
standing rule: **`NOASSERTION` is not merely "a pointer" — it is frequently a pointer to a
*dataset* attribution**, which is exactly the axis the section above shows `LICENSE` cannot cover.

---

## 🆕 Added 2026-11-21 (second pass, verification 12:45Z) — one new reference repo, and the shelf re-measured

**This pass verified the 09:55Z base rather than rewriting it.** All 188 repo URLs across the eight files
were re-probed; **185 live, 3 dead — the same 3 already recorded as dead, none of them a recommendation.**
Every licence cell that disagreed with GitHub's measured SPDX was byte-read: **20 disagreements, 0 real
errors.** Details in `agents/top.md` §V1.

### 🆕 New reference repo — the survey layer gains a university-authored index

| Repo | Licence | ★ / forks | What it is |
|---|---|--:|---|
| 🆕 [TUM-AVS/FM-AD-Survey](https://github.com/TUM-AVS/FM-AD-Survey) | **Apache-2.0** — `LICENSE` byte-read 2026-11-21, **11,337 bytes, full canonical text** | **249★** | **Foundation-models-for-autonomous-driving survey from TU Munich's Autonomous Vehicle Systems chair (TUM-AVS).** Pushed **2026-11-19**, so it is tracking the layer in near-real time. **Prefer it over the anonymous `awesome-*` lists in "Index repos to track" below for anything client-facing**: it is attributable to a named academic group, which matters when a survey is the citation under a recommendation. Pair with `Thinklab-SJTU/Awesome-LLM4AD` (Apache-2.0, 1,906★) for breadth. |

### 🔴 This pass strengthens the standing warning about LICENSE-file-only probes — with a third example

The note below already records that `TrampolineRTOS/trampoline` and `navariltd/Fleet-Management-System`
state their grants outside a `LICENSE` file. **A third and sharper case was found this pass:**
**`autowarefoundation/autoware-safety-island` carries a full 10,894-byte Apache-2.0 text in
`license.rst`** — invisible to a probe of `LICENSE*`/`LICENCE`/`COPYING`/`NOTICE` across `main`,
`master` and `develop` (**18/18 404s**), and invisible to GitHub's matcher (`NOASSERTION`) because it is
reStructuredText. **Add `license.rst` and `LICENSE.rst` to every future probe list.** The existing row
for that repo already named `license.rst` as its evidence — **the base was right and the probe was wrong.**

### 🔴 Negative results settled 2026-11-21 (verification pass) — do not re-search these

- **No permissive dealership ERP/CRM exists — 7th consecutive negative.** Re-measured this pass:
  `Dolibarr/dolibarr` **GPL-3.0** (7,889★), `YetiForceCompany/YetiForceCRM` **`NOASSERTION`, unpushed
  since 2024-09-13**, `SuiteCRM` did not resolve. **`open-mercato/open-mercato` (MIT, 1,953★, pushed
  2026-11-21) is the only permissive option and it is a framework, not a dealership product.**
- **Two aggregator-sourced candidates evaporated under verification:** `SpaceDrive` (named as a CVPR 2026
  driving project) **resolves to no repository at all**, and the `carlover` slug cited by an ecosystems
  aggregator **does not exist** — the only matches are 0–3★ unlicensed projects. **Aggregator listings
  name papers and dead slugs as if they were repos; resolve the slug before writing the row.**
- **`huggingface.co`, `eur-lex.europa.eu`, `unece.org` and `www.federalregister.gov` are all DNS-dead from
  this environment — re-probed and re-confirmed this pass (6th consecutive).** Model **weights** licences
  therefore remain unverifiable here by construction. This is a channel limit, not a research gap.

---


## 🆕 Added 2026-11-21 — the canonical perception/benchmark layer, with honest dormancy labels

> **Verification:** `git ls-remote` for liveness, `raw.githubusercontent.com` for the byte-read licence,
> `gh api -X GET search/repositories` for stars/forks/`pushed_at`/`archived`. All first-hand.
> See `agents/top.md` → *"What changed on 2026-11-21"* for the channel table.

This base was strong on **stacks** (Autoware, Apollo, openpilot), **SDV middleware** (Eclipse) and
**bus tooling**, and thin on the **perception and benchmark repos that every ADAS engagement actually
reads**. Those are added here — **with the dormancy stated, because most of them are dormant, and that
is the finding.**

### 🆕 Layer F — Canonical perception, benchmark and dataset repos

| Repo | Licence (byte-read) | ★ | Last push | Liveness | What it is |
|---|---|--:|---|---|---|
| [waymo-research/waymo-open-dataset](https://github.com/waymo-research/waymo-open-dataset) | **Apache-2.0 *except* `src/waymo_open_dataset/wdl_limited`** (API: `NOASSERTION`) | 3,438 | 2026-01-08 | ⚠️ Slow | The reference AV dataset devkit. **Use the code, avoid that one directory**, treat the dataset as separately licensed. |
| [fundamentalvision/BEVFormer](https://github.com/fundamentalvision/BEVFormer) | **Apache-2.0** | 4,652 | 2024-08-15 | 🔴 **Dormant 2+ yrs** | Camera-only BEV perception (ECCV 2022). Still the most-cited BEV baseline — **read it, do not depend on it.** |
| [PJLab-ADG/SensorsCalibration](https://github.com/PJLab-ADG/SensorsCalibration) | **Apache-2.0** | 3,261 | 2024-06-17 | 🔴 **Dormant** | OpenCalib multi-sensor calibration toolbox. Calibration maths does not rot as fast as frameworks — **highest-value dormant repo here.** |
| [OpenDriveLab/End-to-end-Autonomous-Driving](https://github.com/OpenDriveLab/End-to-end-Autonomous-Driving) | **MIT** | 3,730 | 2025-07-02 | ⚠️ Slow | The E2E survey + curated paper list (IEEE T-PAMI 2024). MIT, so quotable in client material. |
| [hustvl/YOLOP](https://github.com/hustvl/YOLOP) | **MIT** | 2,258 | 2023-10-20 | 🔴 **Dormant 3 yrs** | Panoptic driving perception — detection + drivable area + lane in one head. Small, MIT, easy to port. |
| [daohu527/dig-into-apollo](https://github.com/daohu527/dig-into-apollo) | **MIT** | 2,457 | 2026-02-03 | ✅ Live-ish | Apollo architecture notes. **The fastest way to onboard an engineer onto Apollo** without reading 27k★ of C++. |
| [zhulf0804/3D-PointCloud](https://github.com/zhulf0804/3D-PointCloud) | 🔴 **No licence file** (API: `NONE`) | 2,949 | 2024-08-30 | 🔴 Dormant | Point-cloud papers/datasets index. **No grant — read-only reference, do not vendor it.** |
| [Ly0n/awesome-robotic-tooling](https://github.com/Ly0n/awesome-robotic-tooling) | **CC0-1.0** | 3,924 | 2023-11-20 | 🔴 Dormant | Robotics/AD tooling list. CC0 means **reusable verbatim** in internal docs. |
| [microsoft/AutonomousDrivingCookbook](https://github.com/microsoft/AutonomousDrivingCookbook) | **MIT** | 2,440 | 2025-08-25 | 🔴 **ARCHIVED** | Archived by Microsoft (`archived: true`). Tutorials only. **Listed so nobody proposes it as a base.** |

**Read this layer as a warning, not a shopping list.** Seven of the nine have not been pushed in over a
year; one is formally archived. The automotive perception commons is **largely frozen research code**,
while the *live* investment has moved to end-to-end/VLA models and the Autoware/Apollo stacks already in
this base. For an engagement that means: **take algorithms and calibration maths from Layer F; take
runnable infrastructure from Layers A–E and the stacks.** Proposing BEVFormer as a 2026 production base
would be a mistake this table exists to prevent.

### 🔄 Licence cells filled by byte-read this pass

| Repo | ★ | API `license.spdx_id` | **Byte-read grant** |
|---|--:|---|---|
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | 30,954 | `NOASSERTION` | **MIT** — *"The MIT License (MIT)"* |
| [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | 81 | `MPL-2.0` | **MPL-2.0** (was *"not read this pass"* here) |
| [autoas/as](https://github.com/autoas/as) | 965 | `NOASSERTION` | **GPL-3.0 OR Commercial (dual)** |
| [openremote/fleet-management](https://github.com/openremote/fleet-management) | 51 | `NOASSERTION` | **AGPL-3.0** |

**`PythonRobotics` at 30,954★ is plain MIT and the API could not say so.** That single row is the
argument for byte-reading licences in this base rather than trusting an SPDX field.

### 🔴 Negative results settled 2026-11-21 — do not re-search these

- **`xtuple/xtuple` is gone** (404 via `git ls-remote`). Any ERP shortlist citing XTuple is stale.
- **No open-source dealership DMS exists.** See `verticals/solutions.md` and `agents/top.md` §7.
- **No LATAM-origin automotive foundation repo** surfaced across four region-scoped searches.
- **18 of 170 live repos serve no LICENSE file.** All already labelled correctly in this base; two
  (`TrampolineRTOS/trampoline`, `navariltd/Fleet-Management-System`) carry grants stated only in the
  README/source headers, so **a LICENSE-file-only probe would wrongly downgrade them.**

---

## 🆕 Added 2026-11-19 — four layers this KB did not have: SDV middleware, bus tooling, the openpilot ecosystem, and assurance

> **Verification:** every row below was re-queried by exact `repo:owner/name` through
> `gh api -X GET search/repositories` (the GitHub REST API), so licence SPDX IDs, stars, forks and push
> dates are **first-hand API fields**. 39 of 39 resolved. `curl` to `github.com`/`api.github.com` is
> **HTTP 403** (host policy); LICENSE files were settled via `raw.githubusercontent.com`.

### 🆕 Layer A — SDV middleware and in-vehicle plumbing (Apache-2.0 / MIT / BSD, all battle-tested)

This KB had Eclipse S-CORE, Kuksa, Velocitas and Ankaios. It was **missing the transport and build
layers underneath them**, which is where most SDV integration hours actually go.

| Repo | Licence | ★ / forks | Why it is foundational |
|---|---|--:|---|
| [nanomq/nanomq](https://github.com/nanomq/nanomq) | **MIT** | **2,666★** / 325f | *"Ultra-lightweight and blazing-fast Messaging Bus/MQTT Broker for Edge & SDV."* Pushed 2026-11-19. The in-vehicle/edge broker that sits under a Kuksa or Velocitas deployment. 59 open issues. |
| [eclipse-iceoryx/iceoryx](https://github.com/eclipse-iceoryx/iceoryx) | **Apache-2.0** | **2,212★** / 491f | *"True zero-copy inter-process communication."* The IPC layer AUTOSAR Adaptive and ROS 2 automotive stacks use when latency budgets are hard. 259 open issues (large, active project). |
| [eclipse-ecal/ecal](https://github.com/eclipse-ecal/ecal) | **Apache-2.0** | 1,060★ | High-performance pub/sub + client-server middleware, cross-platform. Pushed 2026-11-19. The recording/replay companion to iceoryx in AV data pipelines. |
| [eclipse-leda/leda-distro](https://github.com/eclipse-leda/leda-distro) | **Apache-2.0** | 21★ / 12f | **Yocto-based build setup for Eclipse SDV.EDGE components.** Low stars, high leverage: this is the reproducible in-vehicle Linux image that makes Kuksa/Velocitas/Ankaios actually boot on target. Siblings: [`leda`](https://github.com/eclipse-leda/leda) (docs), [`meta-leda`](https://github.com/eclipse-leda/meta-leda) (Yocto meta-layers), [`leda-utils`](https://github.com/eclipse-leda/leda-utils), [`leda-example-applications`](https://github.com/eclipse-leda/leda-example-applications). |
| [de4sdv/DE4SDV](https://github.com/de4sdv/DE4SDV) | **Apache-2.0** | 13★ / 4f | *"Open-source systems engineering for Software-Defined Vehicle — **SysML v2**, MBSE, product-line engineering, digital continuity, continuous compliance."* Pushed 2026-11-19, 11 open issues. The only open **SysML v2** automotive systems-engineering base found. Pairs directly with the assurance layer below. |
| [xronos-inc/xronos](https://github.com/xronos-inc/xronos) | **BSD-3-Clause** | 41★ | Deterministic timing + built-in observability for robotics/vehicle software — reproducible behaviour and root-cause analysis. Relevant where non-determinism is the actual defect. |
| [eclipse-sdv-landscape/sdv-landscape](https://github.com/eclipse-sdv-landscape/sdv-landscape) | **Apache-2.0** | 1★ | The Eclipse SDV landscape map itself. A navigation artefact, not code — use it to check this KB's own coverage. |

⚠️ **`vxedge/*`** (Apache-2.0, ~10 repos, all **1★ or 0★**, all pushed 2026-11-19) is a complete
manifest-driven SDV testbed — control plane, OTA server, SysML v2 models, telemetry, an **MCP server
(`vxmcp`, targeting MCP spec 2026-07-28)** and an OCI/ORAS part registry with ARINC-665-shaped part
numbers. Recorded as a **watch item, not a recommendation**: single-contributor, no community, six
weeks old. The *architecture* is worth reading before designing an SDV testbed engagement.

### 🆕 Layer B — Bus, DBC and diagnostics tooling (the unglamorous layer that every engagement touches)

| Repo | Licence | ★ / forks | Why it is foundational |
|---|---|--:|---|
| [ebroecker/canmatrix](https://github.com/ebroecker/canmatrix) | **BSD-2-Clause** | **1,093★** / 441f | Converts CAN database formats: **`.arxml` ⇄ `.dbc` ⇄ `.dbf` ⇄ `.kcd`**. Pushed 2026-11-18. **This is the ARXML bridge** — the piece that lets an agent read an OEM's AUTOSAR communication matrix. BSD-2 is the cleanest licence in this KB. |
| [iDoka/awesome-canbus](https://github.com/iDoka/awesome-canbus) | **CC0-1.0** | **3,571★** / 426f | CAN bus tools, hardware and resources, security/reverse-engineering oriented. CC0 = public domain. The index to consult before building any bus tool. |
| [Sherin-SEF-AI/CanLab](https://github.com/Sherin-SEF-AI/CanLab) | **MIT** | 94★ / 9f | PyQt6 app for reverse-engineering CAN captures: finds counters, checksums and signal boundaries; DBC builder **verified against real frames**; exports **DBC, openpilot and Wireshark dissectors**; UDS + OBD-II. **Injection is bench-only and disarmed until armed.** |
| [autoas/as](https://github.com/autoas/as) | 🔄 🔴 **GPL-3.0 OR Commercial** (byte-read 2026-11-21, 1,299 bytes, *"Dual License: GPLv3 and Commercial"*) | 965★ | *"Simple AUTOSAR Basic Software."* Pushed 2026-11-18. The only substantial open AUTOSAR BSW found. **Resolved this pass — GitHub's `NOASSERTION` was it failing to express a dual grant.** Unusable under GPLv3 for proprietary work, **but the author offers a commercial licence**, so this is a procurement conversation, not a dead end. |
| [TrampolineRTOS/trampoline](https://github.com/TrampolineRTOS/trampoline) | 🔴 **GPL-2.0** | 759★ | Static RTOS aligned to OSEK/VDX and **AUTOSAR OS 4.2**. GPL-2.0 — reference and bench only for a client deliverable. |
| [TOSUN-Shanghai/TSMaster](https://github.com/TOSUN-Shanghai/TSMaster) | ⚠️ **LGPL-2.1** + feature gating | 442★ | Bus monitoring, simulation, testing, diagnostics and calibration across TOSUN, Vector, IXXAT, PEAK, Kvaser, Intrepid, ZLG and more. Page states *"free for research and education purpose for some features"*. **Tool, never a shipped component.** |

### 🆕 Layer C — The openpilot ecosystem as a foundation layer

Previously a single row. It is a supply chain, and the hardware bundle came apart this quarter.

| Repo | Licence | ★ / forks | Role |
|---|---|--:|---|
| [commaai/openpilot](https://github.com/commaai/openpilot) | **MIT** | **64,177★** / 11,410f | Anchor. 300+ cars. Pushed 2026-11-19, 141 open issues. |
| [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) | **MIT** | 2,178★ | 350+ makes/models — **broader vehicle coverage than upstream** |
| [zoompilot/jetlink](https://github.com/zoompilot/jetlink) | **MIT** | 57★ / **40f** | Runs openpilot's large driving model on **Jetson Orin Nano, macOS, iOS, Android, CUDA laptops** with a comma device + USB3 |
| [zoompilot/zoompilot](https://github.com/zoompilot/zoompilot) | **MIT** | 37★ / 31f | ADAS for **Mazda** and others; pushed 2026-11-19 |
| [YassineYousfi/openpilot.distill](https://github.com/YassineYousfi/openpilot.distill) | **MIT** | 38★ | Distil openpilot on your own drives |
| [StarPilotHQ/StarPilot](https://github.com/StarPilotHQ/StarPilot) | **MIT** | 163★ | Tuning-focused fork |
| [commaai/connect](https://github.com/commaai/connect) | **MIT** | 153★ | openpilot fleet/experience management |
| [commaai/opendbc](https://github.com/commaai/opendbc) | **MIT** | **3,571★** / 2,408f | *"a Python API for your car"* — the DBC corpus underneath all of the above. Pushed 2026-11-19, 378 open issues. |
| [Sherin-SEF-AI/Lyne-ADAS](https://github.com/Sherin-SEF-AI/Lyne-ADAS) | **MIT** | 22★ / 7f | **100% on-device ADAS for Android**; self-tunes from budget phones to flagships |
| [eFiniLan/openpilot-ext-radar-addon](https://github.com/eFiniLan/openpilot-ext-radar-addon) | ⚠️ `NOASSERTION` | 33★ | External radar for longitudinal control — settle licence first |

**`jetlink`'s 40 forks on 57 stars** is the signal: people are porting, not bookmarking.

### 🆕 Layer D — Assurance and standards as code

| Repo | Licence | ★ / forks | Role |
|---|---|--:|---|
| [jherrodthomas/automotive-skills-suite](https://github.com/jherrodthomas/automotive-skills-suite) | **MIT** | **2,907★** / 141f | 76 builder+reviewer skill pairs → `.xlsx` artefacts across **ISO 26262 / ISO 21434 / ISO 21448 / ASPICE / AIAG-VDA**, plus CAN-LIN-FlexRay-Ethernet, UDS/ODX/DEM, AUTOSAR Classic+Adaptive, A2L/DCM, MBSE/SysML, V&V traceability. ⚠️ **No "not certified" disclaimer on the page.** |
| [jherrodthomas/LionDriver](https://github.com/jherrodthomas/LionDriver) | **MIT** | 65★ / 3f | openpilot derivative carrying a **living safety case (36 claims, 50 evidence, 42 open defeaters, 0 accepted)** and 89 V-cycle work products; cites ISO 26262/21448/21434, **ISO/PAS 8800**, **UL 4600**, ASPICE; **explicitly claims no compliance**. Use as the **template** for an assurance repository. |
| [Lieubk/automotive-safety-security-assurance-kit](https://github.com/Lieubk/automotive-safety-security-assurance-kit) | **MIT** | 2★ | ASPICE 3.1/4.0 + ISO 26262 + ISO/SAE 21434 skills, agents and a **trace engine**. Created 2026-11-19. |

### 🆕 Layer E — Simulation, benchmarking and datasets added this pass

| Repo | Licence | ★ / forks | Role |
|---|---|--:|---|
| [Farama-Foundation/HighwayEnv](https://github.com/Farama-Foundation/HighwayEnv) | **MIT** | **3,342★** / 906f | Driving and tactical decision-making environments. Farama (the Gymnasium maintainers) — stable governance. The cheapest place to prototype a planning policy. |
| [hanruihua/ir-sim](https://github.com/hanruihua/ir-sim) | **MIT** | 1,239★ | Lightweight Python simulator for navigation, control and learning |
| [ShisatoYano/AutonomousVehicleControlBeginnersGuide](https://github.com/ShisatoYano/AutonomousVehicleControlBeginnersGuide) | **MIT** | 1,963★ | Python simulations + open textbook; swap and compare localisation/planning/control in one system. **The best onboarding asset found for a studio ramp-up.** |
| [AtsushiSakai/PythonRobotics](https://github.com/AtsushiSakai/PythonRobotics) | 🔄 ✅ **MIT** (byte-read 2026-11-21, 1,170 bytes, *"The MIT License (MIT)"*) | **30,951★** | Robotics algorithm reference implementations. **Resolved this pass — cleanly permissive, nothing to settle.** GitHub reported `NOASSERTION` only because the file inserts a contributors URL after the copyright line, which breaks its exact-match classifier. |
| [MRPT/mrpt](https://github.com/MRPT/mrpt) | **BSD-3-Clause** | 2,175★ | Mobile Robot Programming Toolkit — SLAM, localisation, point clouds |
| [aditya-ramabadran/drivingbench_harness_code](https://github.com/aditya-ramabadran/drivingbench_harness_code) | **MIT** | 63★ / 8f | **Agents drive real cars over MCP** (comma four, Toyota TSS2, Tesla M3 HW3) with a 3 m/s ceiling and a 6 m/s hard cutoff; Gaussian-splat simulator; full trace replay |
| [radar-lab/OpenCDA-MARL](https://github.com/radar-lab/OpenCDA-MARL) | **Apache-2.0** | 16★ | Cooperative-driving MARL benchmark on **CARLA + SUMO co-simulation** |
| [thi-ad/UrbanIng-V2X](https://github.com/thi-ad/UrbanIng-V2X) | **MIT** | 88★ / 14f | **NeurIPS 2025** multi-vehicle, multi-infrastructure cooperative-perception dataset across multiple intersections (TH Ingolstadt, **EMEA**) |
| [nv-tlabs/omni-dreams](https://github.com/nv-tlabs/omni-dreams) | **Apache-2.0** | 367★ | **NVIDIA OmniDreams** — real-time photorealistic AV-sim video world model |
| [visionpilot-project/VisionPilot](https://github.com/visionpilot-project/VisionPilot) | **MIT** | 43★ | Modular AD simulation on **BeamNG.tech** with Foxglove visualisation. ⚠️ **Not** `autowarefoundation/vision_pilot` — see the collision note below. |
| [autowarefoundation/AWSIM](https://github.com/autowarefoundation/AWSIM) | 🔴 **bespoke "AWSIM License"** | 765★ / 163f | Autoware digital-twin simulator. **Not Apache-2.0** — LICENSE read raw. Read the terms before any deliverable depends on it. |

### 🆕 Index repos to track instead of re-searching

[Thinklab-SJTU/Awesome-LLM4AD](https://github.com/Thinklab-SJTU/Awesome-LLM4AD) (**Apache-2.0,
1,906★**) is the best single map of LLM/VLM/VLA/world-model work for autonomous driving.
[worldbench/awesome-3d-4d-world-models](https://github.com/worldbench/awesome-3d-4d-world-models)
(Apache-2.0, 1,031★, TPAMI 2026) and
[leofan90/Awesome-World-Models](https://github.com/leofan90/Awesome-World-Models) (BSD-3-Clause,
2,059★) cover the world-model tier.
[szenergy/awesome-lidar](https://github.com/szenergy/awesome-lidar) (CC0-1.0, 1,373★) covers sensors.
🔴 [LMD0311/Awesome-World-Model](https://github.com/LMD0311/Awesome-World-Model) (2,304★) and
🔴 [Little-Podi/Collaborative_Perception](https://github.com/Little-Podi/Collaborative_Perception)
(639★) carry **no licence** — read, do not vendor.

### ⚠️ Name collision recorded as a procurement hazard

`visionpilot-project/VisionPilot` (**MIT, 43★**, BeamNG simulation) vs
`autowarefoundation/vision_pilot` (**Apache-2.0, 928★/197f**, productionizable L2 ADAS stack). Different
owners, licences and purposes; near-identical names; both appear for the query "VisionPilot". **Always
write the full `owner/name` in a statement of work or an architecture decision record.**

### 🔴 Negative results settled 2026-11-19 — do not re-search these

| Query (`gh api search/repositories`) | Result |
|---|---|
| `EV battery charging AI in:name,description pushed:>2026-08-01 stars:>15` | **0 repos** |
| `automotive manufacturing quality inspection AI in:name,description pushed:>2026-06-01 stars:>3` | **0 repos** — plant-floor vision is proprietary |
| `fleet management telematics in:name,description pushed:>2026-08-01 stars:>5` | **2 repos** only: `openremote/fleet-management` (51★, `NOASSERTION`), `santoshiimind/fleet-management-system` (**Apache-2.0**, 8★ — FastAPI + SQLAlchemy, OBD-II + GPS + CAN decode + DTC + driver behaviour + fuel analytics; the only permissive open fleet stack found, and it is a one-person project) |
| `car dealership management in:name,description,topics pushed:>2026-01-01` | 408 repos, **top star count 5**, nearly all unlicensed |
| `V2X cooperative perception in:name,description pushed:>2026-08-01 stars:>30` | **3 repos**; only `thi-ad/UrbanIng-V2X` is permissively licensed |
| Generic agent searches (`top open source AI agents automotive 2026 github MIT`, `github trending automotive AI 2026`) | **Still a dead end** — returns OpenHands, OpenCode, CrewAI, OpenClaw, browser-use with no automotive content. Sixth pass with this result. **Search the standard and the protocol, not the buzzword.** |

## 🆕 Added 2026-11-13 — the Autoware Foundation published a stack, not a model

Between **10 and 12 November 2026** the Autoware Foundation org pushed an entire vertical slice of ADAS:
a production L2 stack, two perception models, a trucking charter, a latent-space planner, a fork of
NVIDIA's Alpamayo, and zero-copy ROS 2 middleware. **Eight repositories, verified individually below.**
The practical consequence for this file is that **Layer 2 is no longer the interesting layer** — the new
material spans Layers 2, 3 and a new Layer 0, because a usable ADAS stack is now open.

**The single most important row added to this KB this pass** is `vision_pilot`: **Apache-2.0, 927★,
196 forks, 4,282 commits**, a *"productionizable and safety certifiable"* **L2 ADAS stack** with ACC, FCW,
AEB, LKAS, LDW, ISA and hands-free highway autopilot, running **mapless** on **a single monocular camera**
via ONNX Runtime on GPU **or CPU**. Until today the only large permissive automotive codebase in this file
was openpilot (MIT). There are now two, and the new one is Apache-2.0 under foundation governance with an
**ISO 26262 / ISO 8800** roadmap.

🔴 **One of the eight has no licence.** `autoware_latent_drive` (42★) has no sidebar licence field, no
licence statement in its README, and `LICENSE`, `LICENSE.md`, `LICENSE.txt` and `license.rst` **all 404 on
`main`**. It is excluded from every shelf in this KB and recorded in
[`../agents/top.md`](../agents/top.md) under exclusions. **A major foundation's org is not a grant.**

🟢 **And one was rescued from a wrong label.** `autoware-safety-island` reads as **"Other"** in GitHub's
org listing because its licence lives in `license.rst`. Fetched raw, it is verbatim **Apache License 2.0**.
Shelved in Layer 3. **Treat "Other" as an instruction to fetch the file, never as a verdict.**

## 🆕 Layer 0 — Production ADAS stacks (new layer 2026-11-13)

A new layer, because these are neither simulation nor research models nor in-vehicle middleware: they are
**shippable driver-assistance systems**. This is the layer a client means when they say "we want ADAS".

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕 [autowarefoundation/vision_pilot](https://github.com/autowarefoundation/vision_pilot) | **Apache-2.0** | **927** | *"Free and fully open-source L2 ADAS stack powered by End-to-End AI technology"*; README: *"a productionizable and safety certifiable implementation of an open-source L2 ADAS system called Vision Pilot."* **ACC, FCW, AEB, LKAS, LDW, ISA + single-lane hands-free highway Autopilot**, **mapless** (no 3D HD maps). *"Hybrid End-to-End AI Architecture"* — perception models in parallel with E2E models, *"processed in parallel by perception AI models for safety, and End-to-End AI models for performance."* Three models: **AutoSpeed** (closest in-path object), **AutoSteer** (ego path waypoints), **AutoDrive** (E2E distance + in-path presence + curvature). Input: **one front monocular camera, 52–55° HFOV, 1–2 MP**. **ONNX Runtime**, CUDA **or CPU**, Docker, optional ROS 2, CARLA 0.9.16 closed loop. v1.0 `.deb`. Roadmap: radar fusion, 8 MP/120° camera, **ISO 26262 + ISO 8800**. 196 forks, 4,282 commits. ⚠️ "Certifiable" is a roadmap item, not a status. ⚠️ README's clone URL says `autoware_vision_pilot.git`; the repo is `vision_pilot`. |
| 🆕 [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | **64.1k** | *"An operating system for robotics … upgrades the driver assistance system on 300+ supported cars."* 64.0k → 64.1k this pass. Previously recorded only in `agents/top.md`; it belongs in foundations too, since it is the largest permissive automotive codebase in existence. |
| 🆕 [sunnypilot/sunnypilot](https://github.com/sunnypilot/sunnypilot) | MIT | 2.2k | The significant openpilot fork, **same MIT grant**, advertising *"over 350 supported car makes and models"* — **more vehicle coverage than upstream's 300+**. 19,012 commits. Check here when a client's specific vehicle is unsupported upstream. |
| 🆕 [autowarefoundation/autoware.trucks](https://github.com/autowarefoundation/autoware.trucks) | Apache-2.0 | 2 | *"Everything specific to trucking autonomy."* README: open-source **highway trucking autonomy, from SAE L2+ highway piloting toward L4**. 9 commits — a charter, not yet a codebase. Watch item: North American autonomy capital is visibly moving to freight (Kodiak, see `intel/market.md`), and `Peykan` in `agents/top.md` is the only diagnostics agent covering the **J1939** truck bus. |

## 🆕 Added 2026-10-31 — the open E2E model layer doubled

Two Apache-2.0 end-to-end driving models that this file had no row for are now verified and added to
Layer 2 below: **AutoE2E** (Autoware Foundation, tagged **29 Oct 2026**) and **Qwen-Drive-1.0** (Alibaba).
On AutoE2E's own published eight-model comparison **both sit ahead of Alpamayo 1.5**, which is the stack
this KB has recommended as the reference since July — stated here because a foundations file that only
tracks one vendor's line stops being a foundations file. The comparison is **not like-for-like** (inputs
differ by model); the full table and caveats are in
[`../agents/top.md`](../agents/top.md).

A third addition sits outside every existing layer and gets its own one below: **Auto Agent Protocol**, the
open contract for reaching a dealership over MCP/A2A/PAP.

## 🆕 The biggest addition this pass: Eclipse S-CORE

The 2026-10-15 pass covered Kuksa, Ankaios and VSS but **missed the project the German OEM bloc is actually
consolidating on**. Eclipse S-CORE (*Safe Open Vehicle Core*) is the first open-source-based SDV platform
initiative designed against **ASIL-B** functional-safety requirements — a design target, **not** a
certification, and worth stating that way to a client.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕🔄 [eclipse-score/score](https://github.com/eclipse-score/score) | Apache-2.0 | 111 | *"Score project main repository."* The platform root. **Release history read from the GitHub releases page today: `v0.7.3` (07 Oct), `v0.7.2` (02 Sep), `v0.7.1` and `v0.7.0` (24 Aug), `v0.6.4` (07 Aug), `v0.6.3` (31 Jul), `v0.6.2` (14 Jul), `v0.6.1` (13 Jul), `v0.6.0` (26 Jun), `v0.5.5` (26 Apr)** — the page shows dates without a year; all ten fall inside the last 12 months, so they are 2026. Cadence is roughly monthly, and it is shipping. |
| 🆕🔄 [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) | Apache-2.0 | 7 | *"Incubation repository for the fixed execution order framework."* Deterministic execution order — the piece that makes a safety argument tractable. Rust (inferred from `Cargo.toml`, not stated on the page). |
| 🆕 [eclipse-score/baselibs](https://github.com/eclipse-score/baselibs) | ⚪ not read this pass | — | Base libraries. Press reporting says a **Baselibs Rust** module arrived with 0.6.0. URL live 2026-10-26; licence not re-read. |
| 🆕 [eclipse-score/communication](https://github.com/eclipse-score/communication) | ⚪ not read this pass | — | Communication layer. URL live 2026-10-26. |
| 🆕 [eclipse-score/itf](https://github.com/eclipse-score/itf) | ⚪ not read this pass | — | Integration test framework — relevant to any ASIL evidence pipeline. URL live 2026-10-26. |
| 🆕 [eclipse-score/process_description](https://github.com/eclipse-score/process_description) | ⚪ not read this pass | — | The project's development process as a repository. For a client building a safety argument, **this is the artefact that matters as much as the code**. URL live 2026-10-26. |
| 🆕 [eclipse-score/module_template](https://github.com/eclipse-score/module_template) | ⚪ not read this pass | — | Template for a conforming S-CORE module — the entry point for contributing a client's own component. URL live 2026-10-26. |

**Project facts worth carrying into a conversation** (secondary sources, see the conflict note below):
Eclipse project page lists **Apache License 2.0** with the standard caveat that some sources/binaries may
carry different terms; **v0.5-alpha was the first public release (Nov 2025)**; **0.6.0 introduced full
dual-language C++ **and** Rust support, including the Ferrocene safety-critical Rust toolchain**; the
Eclipse SDV ↔ **VDA** memorandum expanded to **32 companies (Jan 2026)**; **Hyundai Mobis joined the SDV
Working Group (May 2026)**; and founding member **Qorix** sells a commercial middleware distribution built
on S-CORE — meaning the open project already has a paid-support path a risk-averse OEM can point at.

🔴 **Stated conflict, not resolved:** trade press puts 0.6.0 in **February 2026** and 0.7.0 in **May 2026**;
the **GitHub releases page read today** puts 0.6.0 at **26 Jun** and 0.7.0 at **24 Aug**. The releases page
is the primary source and is preferred here. The Eclipse project page also lists a **v1.0.0 dated
2026-12-14**, which is in the future and should be treated as a plan, not a shipped release — an ETAS
presentation separately says a complete solution is on track for **2028**. Do not quote a single 1.0 date.

## Layer 1 — Simulation & scenarios

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [carla-simulator/carla](https://github.com/carla-simulator/carla) | MIT | 14.5k | *"Open-source simulator for autonomous driving research."* The de facto standard; largest ecosystem. |
| ⏸ [carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) | MIT | 683 | Traffic-scenario definition and execution engine for CARLA. |
| 🔄 [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | NVIDIA's open AV simulation platform for end-to-end policy development and testing. |
| ⏸ [eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) | EPL-2.0 | 4.2k | Microscopic, continuous traffic simulation — city/fleet scale rather than single-vehicle. |
| ⏸ [esmini/esmini](https://github.com/esmini/esmini) | MPL-2.0 | 949 | A basic OpenSCENARIO player — the lightweight way to execute ASAM OpenSCENARIO files in CI. |
| ⏸ [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular AD platform running on CARLA and real vehicles. |

## Layer 2 — Perception, datasets & models

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | Next-generation platform for general 3D object detection. |
| ⏸ [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| ⏸ [nutonomy/nuscenes-devkit](https://github.com/nutonomy/nuscenes-devkit) | Apache-2.0 | 2.8k | Devkit for the nuScenes dataset. ⚠️ GitHub's sidebar shows no licence name; `LICENSE.txt` was read directly (2026-10-15) and is **Apache-2.0, © 2021 Motional**, no non-commercial clause. The *dataset* carries separate terms. |
| 🔄 [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | Planning-oriented end-to-end AD (CVPR 2023 Best Paper). |
| 🆕🔄 [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | AAAI 2026 end-to-end VLA, **0.5B checkpoint on Hugging Face** — the small-model option. |
| 🆕 [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) | **Apache-2.0** (`LICENSE` fetched raw and read 2026-10-31) | 184 | **AutoE2E v1.0, tagged 29 Oct 2026.** Camera-first E2E driving model, **no HD maps required**: 79.9M params, six surround cameras @10 Hz → BEV grid → GRU planner → **6.4 s of acceleration and curvature**. 1 Hz World Action and Reasoning models still in development. ~76 FPS (SwinV2-Tiny, RTX 5080, batch 1 — project figure). 38 forks. **Vendor-neutral governance** (Autoware Foundation Robotaxi WG) is the reason to prefer it as a teaching/reference base over a vendor line. ⚠️ Secondary source (TIER IV exec LinkedIn) claims **OpenMDW-1.1** for the weights; the repo `LICENSE` is Apache-2.0 and the **weights licence is unresolved** — see the channel gap. |
| 🆕 [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) | Apache-2.0 | 537 | Alibaba's open AV vision-language foundation model: **Qwen3.5-4B** VLM + **BEV perception head** (3D detection, occupancy, map segmentation) + **flow-matching Planning Expert**. **4B fills the gap between OpenDriveVLA (0.5B) and Alpamayo 1.5 (10B)** — the practical size for a single-GPU client experiment. 56 forks. Weights advertised as `Qwen/Qwen-Drive-1.0-4B` on Hugging Face and ModelScope; repo states Apache-2.0 without separately naming the weights. |
| 🆕 [autowarefoundation/scene_3d](https://github.com/autowarefoundation/scene_3d) | Apache-2.0 | 2 | *"Open-source AI model for monocular depth estimation."* Per-pixel **relative** depth (nearer/farther) at high resolution from one camera. README states it is **part of the AutoSeg Foundation Model, the core of the vision pipeline for the Autoware Autonomous Highway Pilot System** — so this is a published component of a named foundation model, not a standalone experiment. Ships **Scene3DLite, distilled from DepthAnythingV2**; the distilled variant is the deployable one. 3 commits. Early, but it is the depth input Vision Pilot's perception half needs. |
| 🆕 [autowarefoundation/ego_lanes](https://github.com/autowarefoundation/ego_lanes) | Apache-2.0 | 1 | *"Semantic segmentation and classification of lane lines."* README: a *"legacy semantic end-to-end lane boundary segmentation network"* segmenting driving lanes from monocular frames **without HD maps**. 30 commits. ⚠️ **"Legacy" is the maintainers' own word** — use it as the baseline to beat in an LKAS/LDW engagement, not as the target architecture. |
| 🆕 [hustvl/Senna](https://github.com/hustvl/Senna) | Apache-2.0 | 559 | *"[IJCV 2026] Senna: Bridging Large Vision-Language Models and End-to-End Autonomous Driving."* **Peer-reviewed (IJCV 2026)** VLM↔E2E bridge from HUST's vision lab. The academic counterweight to the vendor lines, and a second opinion on attaching a language model to a planner without replacing it. 16 commits. Surfaced via the `DatariusAI/AI-in-Automotive` feed, which is the first time that unlicensed reading-feed has paid for itself. |
| 🆕 [autowarefoundation/alpamayo-autoware](https://github.com/autowarefoundation/alpamayo-autoware) | Apache-2.0 | 161 | **The Autoware Foundation's own fork of `NVlabs/alpamayo`**, updated 11 Nov 2026, default branch **`alpamayo2.0-edge`**, 42 commits, no description set. Matters as **governance, not science**: the vendor-neutral foundation now carries an edge branch rather than consuming NVIDIA releases. For a client who cares about vendor neutrality, track this fork rather than upstream. |

## Layer 3 — Software-defined vehicle (SDV) in-vehicle platform

The layer most relevant to OEM/Tier-1 engagements and the least known outside them. **Read the S-CORE
section above first** — it sits above this stack rather than beside it.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | MPL-2.0 | 451 | *"Vehicle Signal Specification - standardized way to describe automotive data."* The common vocabulary every project below maps onto. **Start here.** COVESA hosts 100+ companies around it. |
| 🆕 [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | ⚪ not read this pass | — | The tooling that turns a VSS model into generated artefacts. Needed in practice as soon as VSS is adopted; URL live 2026-10-26. |
| 🔄 [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 82 | *"A modern in-vehicle VSS server written in RUST."* gRPC, containerisable. Release 0.6.1 (Apr 2026) and a Quarkslab security audit. Low stars ≠ low importance. |
| 🆕 [eclipse-kuksa/kuksa-python-sdk](https://github.com/eclipse-kuksa/kuksa-python-sdk) | ⚪ not read this pass | — | Python client for the Databroker — the fastest way to prototype against VSS signals. URL live 2026-10-26. |
| 🔄 [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios) | Apache-2.0 | 125 | *"Workload and container orchestration for embedded devices like automotive HPCs"* — the "Kubernetes of the car", where real Kubernetes does not fit. |
| 🆕🔄 [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management) | Apache-2.0 | 27 | **The single most useful new find for engagement work.** A runnable truck-fleet reference wiring **Kuksa CSV Provider → Kuksa Databroker → FMS Forwarder → Eclipse uProtocol → FMS Consumer → InfluxDB → Grafana**, plus an **FMS Server exposing the rFMS API**. A published end-to-end topology instead of an architecture diagram. |
| ⏸ [eclipse-velocitas/cli](https://github.com/eclipse-velocitas/cli) | Apache-2.0 | 6 | CLI for the Velocitas toolchain for containerised in-vehicle apps. Very early; listed for stack completeness. |
| 🆕 [autowarefoundation/agnocast](https://github.com/autowarefoundation/agnocast) | Apache-2.0 | 212 | *"A rclcpp-compatible true zero-copy IPC middleware that supports all ROS message types."* **The most reusable piece of infrastructure added this pass.** Keeps the rclcpp API while removing message copies between ROS 2 processes — including for unsized message types, which is the case normal zero-copy approaches cannot handle. Implemented as a **kernel module (`agnocast_kmod`) plus a heaphook library**, integrates `CallbackIsolatedExecutor`, targets **ROS 2 Humble and Jazzy on Ubuntu 22.04/24.04**. 1,258 commits, and the README grounds it in the authors' published papers. Relevant far beyond ADAS: any ROS 2 perception pipeline under latency pressure. |
| 🆕 [autowarefoundation/autoware-safety-island](https://github.com/autowarefoundation/autoware-safety-island) | **Apache-2.0** (`license.rst` fetched raw and read 2026-11-13; GitHub's org listing mislabels it **"Other"**) | 8 | *"Autoware Safety Island Implementation based on ARM SoCs."* **608 commits** — by commit count the most substantial safety-relevant repo in this layer, and it was nearly lost to a bad licence label. A safety island is the independent monitoring element a functional-safety argument is built around, so this sits directly alongside **Eclipse S-CORE** above: S-CORE is the ASIL-B-targeted platform, this is a concrete ARM-SoC implementation. Pair them in any safety engagement. |
| 🆕 [autowarefoundation/autoware-index](https://github.com/autowarefoundation/autoware-index) | Apache-2.0 | 1 | *"Federated registry of community Autoware packages (`distribution.yaml` + sweep-driven validation history)."* A federated package registry **with recorded validation history** is how this ecosystem will be navigated from here — and the validation-history part is what makes it more than a list. 1★: brand new. Track it. |
| 🆕 [autowarefoundation/openadkit-rcar-x5h](https://github.com/autowarefoundation/openadkit-rcar-x5h) | Apache-2.0 | 0 | *"Board support for Open AD Kit on the Renesas R-Car X5H: AutoSD image, kernel, CR52 dual boot and demos."* **Silicon-specific board support is the step most open AV stacks never publish** — and this one includes an **AutoSD image, a kernel and CR52 dual boot**, which is what turns "runs on automotive hardware" from a claim into something a client can reproduce on a mainstream Renesas SoC. 0★ and it is still one of the most engagement-relevant repos in the org. |

## Layer 4 — Vehicle bus / diagnostics (unglamorous, highly reusable)

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [commaai/opendbc](https://github.com/commaai/opendbc) | MIT | 3.5k | *"a Python API for your car"* — CAN message definitions for production vehicles. Fastest route to real vehicle signals. |
| ⏸ [cantools/cantools](https://github.com/cantools/cantools) | MIT | 2.3k | CAN bus tools: DBC/KCD parsing, encode/decode, diagnostics. |
| ⏸ [hardbyte/python-can](https://github.com/hardbyte/python-can) | **LGPL-3.0** | 1.6k | CAN support for Python. ⚠️ LGPL — dynamic linking is fine, but flag it in any shipped client deliverable. |

## 🆕 Layer 5 — The agent-facing contract layer (new 2026-10-31)

New layer, because it belongs to none of the four above: it is neither simulation, perception, in-vehicle
platform nor vehicle bus. It is how an **external** agent is supposed to talk to an automotive *business*.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕 [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | **Apache-2.0** (specification, schemas, code) · documentation **CC BY 4.0** | 110 | *"The open automotive contract for MCP, A2A and Personal Agent Protocol: dealer discovery, inventory, evidence, pricing and consented inquiries."* README describes **v3.1** as an additive minor release that preserves the published **3.0** contract's meanings; AAP **2.x implementations must complete the 3.0 migration first**. Discovery works by the dealer domain publishing an **Agent Card**, a **Poppy document** and **`llms.txt`** that link live MCP, A2A and PAP endpoints, with the MCP tool catalogue and A2A OpenAPI served from versioned **`/v3.0/`** paths. Independent of — and built on — Google's A2A, which is Apache-2.0 under the Linux Foundation. No release tag shown on the repo page. |

**Why this earns a layer rather than a footnote.** Three passes of this KB concluded the automotive *retail*
layer is a closed oligopoly with nothing to fork, and that remains true of the **systems of record**
(CDK, Reynolds & Reynolds, Tekion, DealerSocket). But the **interface** to that layer is now specified in
the open, versioned, and separately licensed for docs. For an engagement that means a dealer-group client
can be given an agent-reachable surface **without** replacing their DMS — the integration target is a
published contract instead of a bespoke negotiation per vendor. 🔴 **Unknown, and worth saying to a client:
how many dealerships actually serve these endpoints today.** The spec's existence is verified; its
deployment is not.

## Licence flags for this industry

- **Permissive, safe to build on:** CARLA, openpilot, Autoware, Apollo, Alpamayo code / Alpamayo 2 /
  AlpaSim / AlpaGym, OpenDriveVLA, WorldEngine, OpenPCDet, mmdetection3d, opendbc, cantools,
  nuscenes-devkit, Kuksa, Ankaios, **Eclipse S-CORE**, the SDV fleet-management blueprint,
  AutoE2E, Qwen-Drive-1.0 and Auto Agent Protocol (all Apache-2.0); 🆕 **Vision Pilot**,
  🆕 **agnocast**, 🆕 **autoware-safety-island**, 🆕 **Scene3D**, 🆕 **EgoLanes**,
  🆕 **alpamayo-autoware**, 🆕 **autoware.trucks**, 🆕 **Senna** (Apache-2.0); 🆕 **sunnypilot** (MIT).
- 🆕 **A licence label is not a licence, in both directions.** `autoware-safety-island` reads as
  **"Other"** and is really **Apache-2.0** (file: `license.rst`) — a false negative that would have cost
  this KB a 608-commit safety repo. `autoware_latent_drive` sits in the **same org** with **no licence at
  all**, and `petrpatek/obd2-mcp-server` and `j2534-mcp-server` both claim MIT in a README with no file —
  false positives. **Fetch the file. Every time. The org's reputation is not a grant.**
- **Weak-copyleft / file-level — usable with care:** VSS and esmini (MPL-2.0), SUMO (EPL-2.0),
  python-can (LGPL-3.0).
- **Strong copyleft — do not put client proprietary code on top without legal sign-off:** Fleetbase and
  OpenRemote (AGPL-3.0), Odoo (LGPL-3.0 core), **OpenAutoCore (GPL-3.0)**. See `verticals/solutions.md`.
- 🆕 **Model weights are licensed separately from code.** Alpamayo 1.5: repo Apache-2.0, **weights
  OpenMDW-1.1**. Never infer the checkpoint's terms from the repository badge.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0) and most AV *datasets*.

## 🆕 Negative results settled 2026-10-31 — do not re-search these

- **`Dolibarr/dolibarr`** (7.8k★, PHP, default branch `develop`) — **GPL-3.0**, read from the sidebar.
  Surfaced as an ERP/CRM base for aftersales. Ruled out on licence; **Odoo (LGPL-3.0) and Apache OFBiz
  (Apache-2.0) already cover this slot** and OFBiz is the permissive one.
- **`navariltd/Fleet-Management-System`** (12★, 18 forks, default branch `develop`) — **GPL-3.0** per README
  and badge; the GitHub sidebar shows a License link but **does not name the licence**, so the README is the
  source. Frappe-framework fleet solution. Copyleft, so not a base for a proprietary deliverable.
- **No open-source Dealership Management System exists.** Re-searched 2026-11-13 with
  `open source platform automotive ERP CRM dealership MIT Apache`; **unchanged across five passes.** The
  search returns general-purpose ERP/CRM only, and explicitly confirms the gap: none of the candidates
  carry dealership primitives — **no inventory-by-VIN, no deal jacket, no DMS integration**. A dealer
  engagement still means building those modules on a general ERP, against the Auto Agent Protocol contract
  in Layer 5.
- **No LATAM-origin automotive repository found**, in this or any previous pass. **Five passes, zero.**
  This is now a durable finding rather than a miss: see `intel/market.md` → LATAM for what it implies.
- 🆕 **Generic "AI agent" searches remain a dead end for this industry.** `top open source AI agents
  automotive 2026 github MIT` returned only general-purpose frameworks (OpenClaw, OpenCode, OpenHands,
  CrewAI, Hermes Agent) with **no automotive content**, plus the note that **AutoGPT is archived as of
  28 Jan 2026**. The productive query shape is the **protocol**, not the category — `automotive MCP server
  vehicle diagnostics` returned eight real projects. Recorded so the next pass spends its searches better.
- 🆕 **Three "MIT" ERP/CRM claims from search summaries failed verification** — `idurar-erp-crm` is
  **AGPL-3.0**, Huly is **EPL-2.0 and frozen**, `open-mercato` is MIT with a **commercial
  `packages/enterprise` carve-out**. Details in `verticals/solutions.md`. Do not re-trust secondary
  licence claims for this layer.

## Declared channel gap

🔴 **New this pass: `huggingface.co` does not resolve from this session** (DNS failure, consistent with the
proxy's allowed-domain policy). Every model-weight repository referenced in this file — AutoE2E's
`AutowareFoundation/auto_e2e` checkpoints, `Qwen/Qwen-Drive-1.0-4B`, OpenDriveVLA's 0.5B checkpoint — is
therefore **unverified as to its licence**. This is not a cosmetic gap: this KB has already caught
**Alpamayo 1.5 shipping Apache-2.0 code with OpenMDW-1.1 weights**, and a secondary source makes the same
claim about AutoE2E. **Do not ship a fine-tuned derivative of any of these to a client until the model card
is read.** Next pass: request `huggingface.co` in the session's allowed domains.

🔴 **`eclipsesdv.org` could not be fetched on 2026-10-26** (DNS resolution failure through the available
fetch channel), so S-CORE release notes were read from the **GitHub releases page** plus trade press
instead of the project's own announcements. The GitHub dates above are primary and reliable; the module
contents attributed to 0.6.0 are press-sourced and should be confirmed against the project site when it
is reachable. **`api.github.com` returns HTTP 403 for repositories not attached to this session**, which is
why licences and stars are read from rendered repository pages rather than the API — the same constraint
the 2026-10-15 pass recorded.

---
*Verified 2026-11-13 (previous passes 2026-10-31, 2026-10-26). Figures marked 🆕/🔄 were read from the rendered repository page today;
⏸ carried from an earlier pass and labelled; ⚪ URL present in the org listing but licence/stars deliberately left blank rather than guessed.
`curl` and `api.github.com` are both 403 in this session, so the rendered page and `raw.githubusercontent.com` are the verification channels.
See `verticals/solutions.md` for full customisable platforms and `agents/top.md` for the exclusion list.*

---

## 🆕 Layer H — the permissive diagnostics & ECU-tooling stack (added 2026-11-21, fourth pass)

**Why this layer did not exist until now, and it is the same cause as Layer G:** it was never absent
from the world, only from the queries. Layer G was missed because five passes said *automotive* to a
layer that calls itself *industrial anomaly detection*. Layer H was missed because the `gh` queries were
**too long** — `search/repositories` matches name/description/topics and ANDs every term, so a
five-word phrase returns a literal zero. Eight short queries returned 27 unheld repos. **Full defect
write-up: `agents/trending.md` → 2026-11-21 fourth pass.**

This is the layer a studio actually bills against: **UDS/OBD diagnostics, ECU bench tooling and
AUTOSAR data plumbing**, and unlike the AV-stack layers it is **permissively licensed nearly throughout.**

| Repo | Licence (byte-read 2026-11-21) | ★ | Pushed | Why it is here |
|---|---|--:|---|---|
| [pylessard/python-udsoncan](https://github.com/pylessard/python-udsoncan) | **MIT** — `master/LICENSE.txt`, 1,074 b | **746** | 2026-10-26 | **The anchor of this layer.** A Python implementation of **UDS (ISO-14229)**, the diagnostic protocol every ECU on a modern vehicle speaks. Clean permissive grant, actively pushed. Any diagnostics agent that needs to *do* something rather than describe it starts here. |
| [oxibus/automotive_diag](https://github.com/oxibus/automotive_diag) | **MIT** — `main/LICENSE-MIT`, 1,139 b | 105 | 2026-11-09 | **UDS (ISO-14229-1), KWP2000 (ISO-14230), OBD-II (ISO-9141) and DoIP (ISO-13400) definitions** as a Rust crate. The constants/enums layer — pairs with `python-udsoncan` rather than competing: Rust for on-vehicle/edge, Python for the bench and the agent. Dual-licensed (`LICENSE-MIT` present; Apache variant typical of Rust crates). |
| [ecubus/EcuBus-Pro](https://github.com/ecubus/EcuBus-Pro) | ⚠️ **Apache-2.0 *declared in `package.json` v0.8.68*; NO `LICENSE` FILE IN THE TREE** | **914** | 2026-11-05 | An open **CANoe/CAPL-class ECU development bench**: **UDS, CAN-TP, DoIP, LIN, TypeScript scripting "like CAPL", HIL test**. Functionally the most valuable single tool in this layer — commercial equivalents are five-figure seats. ⚠️ **Probed `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `license`, `COPYING` on `main` and `master`: all 404.** The grant is a metadata field with no licence text in the repo. **Fine to evaluate; get a `LICENSE` file added before it sits under a client deliverable.** |
| [cogu/autosar](https://github.com/cogu/autosar) | **MIT** — `master/LICENSE`, 1,088 b | 503 | 2026-10-16 | Python modules for reading/writing **AUTOSAR XML (ARXML)**. ARXML is the interchange format for AUTOSAR ECU configuration, and this is the permissive way to generate and diff it programmatically. Direct pair for `automotive-skills-suite`'s ARXML skill. |
| [COVESA/vsomeip](https://github.com/COVESA/vsomeip) | **MPL-2.0** — `master/LICENSE`, 16,725 b | **1,471** | 2026-11-13 | An implementation of **SOME/IP** (Scalable service-Oriented MiddlewarE over IP), the service protocol of automotive Ethernet. **COVESA-governed**, i.e. an actual industry consortium rather than a lone maintainer. ⚠️ **MPL-2.0 is file-level weak copyleft:** modified MPL files must stay MPL, but linking proprietary code alongside is permitted. Usable — with the file boundary respected. |
| [COVESA/dlt-viewer](https://github.com/COVESA/dlt-viewer) | **MPL-2.0** — `master/LICENSE.txt`, 372 b (short-form pointer) | 557 | 2026-11-19 | **Diagnostic Log and Trace (DLT)** viewer — AUTOSAR's standard logging transport. The companion to `vsomeip` for anything that has to read vehicle logs at scale. Same MPL file-boundary caveat. |
| [toyota-connected/ivi-homescreen](https://github.com/toyota-connected/ivi-homescreen) | **Apache-2.0** — `main/LICENSE`, 571 b | 404 | **2026-11-21** | A **Flutter embedder for automotive/embedded displays** — Wayland, DRM/KMS, EGL, Vulkan incl. zero-copy. Maintained by **Toyota Connected North America**, pushed today. The permissive route to an IVI/cluster UI without licensing a HMI stack. ⚠️ 571 bytes is the **short-form Apache notice**, not the full text — read and confirmed to grant Apache-2.0 unambiguously (*"Licensed under the Apache License, Version 2.0"*, Copyright 2020 Toyota Connected North America). |
| [OpenSparX/MasterAgent](https://github.com/OpenSparX/MasterAgent) | **Apache-2.0** — `main/LICENSE`, 11,259 b | **966** | 2026-09-28 | *"Build AI agents that run 100% on-device. Sub-100 ms latency on Qualcomm NPU. Zero cloud dependency."* **Not automotive-labelled, which is why no pass saw it** — but Qualcomm NPUs are the dominant in-cabin compute, and "no cloud" is the in-vehicle constraint. The permissive base for a cabin agent that must work in a tunnel. |
| [Chanchaldhiman/CANviz](https://github.com/Chanchaldhiman/CANviz) | **MIT** — `main/LICENSE`, 1,076 b | 299 | 2026-08-08 | Browser-based **CAN bus analyzer** working off low-cost USB hardware. The zero-install triage tool for a workshop or a demo. |
| [kkonteh97/SwiftOBD2](https://github.com/kkonteh97/SwiftOBD2) | **MIT** (API; not byte-read this pass) | 163 | 2026-01-26 | Swift **OBD-II** library — live data, DTC clearing. The iOS half of a diagnostics product; `CarDash` is the Android half. |
| [the-can-opener/simple-elm](https://github.com/the-can-opener/simple-elm) | **MIT** (API; not byte-read this pass) | 19 | 2026-04-20 | Small **ELM327** helper for serial OBD/CAN adapters. Listed for one specific reason: it is the **permissive replacement for `Ircama/ELM327-emulator`, which is CC-BY-NC** and therefore unusable in a commercial engagement. |
| [sw-mobility/open-sdv](https://github.com/sw-mobility/open-sdv) | **Apache-2.0** — `main/LICENSE`, 11,357 b, canonical | 12 | 2026-11-16 | *"Open Software Defined Vehicle Framework."* **12★ — a seed, not a platform**, recorded as a watch item because a canonical Apache grant on an SDV framework is rare (compare `de4sdv/DE4SDV` at 13★ in Layer D). |

### Perception/AV additions found by the same sweep

| Repo | Licence (byte-read) | ★ | Pushed | Note |
|---|---|--:|---|---|
| [autonomousvision/transfuser](https://github.com/autonomousvision/transfuser) | **MIT**, 1,073 b | **1,616** | 2026-09-21 | **[PAMI'23] TransFuser** — transformer-based multi-modal sensor fusion for autonomous driving (+ [CVPR'21]). One of the standard CARLA leaderboard baselines, and **MIT**, so a client prototype can start from a published baseline rather than a blank repo. |
| [sjtuyinjie/Ultra-Fusion](https://github.com/sjtuyinjie/Ultra-Fusion) | **MIT**, 1,074 b | 930 | 2026-08-29 | Tightly-coupled **multi-sensor fusion SLAM under sensor degradation** and spatiotemporal misalignment. The failure-mode case — degraded/misaligned sensors — is the one that matters in production and is usually the one no baseline handles. |
| [YuruiAI/DistillDrive](https://github.com/YuruiAI/DistillDrive) | **MIT**, 1,063 b | 127 | 2026-08-30 | **[ICCV 2025]** end-to-end multi-mode driving **distillation**. Distillation is the deployability lever: it is how an E2E planner gets small enough for vehicle compute (same role `Scene3DLite` plays in Layer F). |
| [jiachenli94/Awesome-Interaction-Aware-Trajectory-Prediction](https://github.com/jiachenli94/Awesome-Interaction-Aware-Trajectory-Prediction) | **MIT** (API) | **1,696** | 2026-08-24 | A curated state-of-the-art index for **trajectory prediction**. A reading list, not a dependency — the fastest way to brief an engagement team on the prediction literature. |

### 🔴 What this sweep refused — read before reusing any V2X or cooperative-driving code

Three grants were refused on byte-read, and **all three arrived as `NOASSERTION` from the API**:

- **[ucla-mobility/OpenCDA](https://github.com/ucla-mobility/OpenCDA)** (1,174★) — **Academic
  Software License, not open source.** Grant runs only to *"academic or nonprofit researchers"*;
  *"you are prohibited from further transferring the Software — including any derivatives you make
  thereof"*; *"Commercial entities: please contact the UCLA Mobility Lab … for licensing
  opportunities."* **Hard exclusion** — a cooperative-driving prototype built on it is undeliverable.
- **[riebl/vanetza](https://github.com/riebl/vanetza)** (231★) — **CC-BY-NC, 43,043 b.** The open
  implementation of the **ETSI C-ITS protocol stack**: non-commercial.
- **[Ircama/ELM327-emulator](https://github.com/Ircama/ELM327-emulator)** (708★) — **CC-BY-NC,
  20,849 b**, and it is what MIT-licensed `Automotive-AI` tells you to install to test without a car.

⚠️ **The V2X/C-ITS neighbourhood has no permissive anchor.** `vanetza` CC-BY-NC, `riebl/artery`
GPL-2.0, `eclipse-mosaic/mosaic` EPL-2.0, `sommer/veins` GPL-2.0, `DriveX-devs/VaN3Twin` GPL-2.0.
Permissive options exist only on the *research dataset/model* side —
[DerrickXuNu/v2x-vit](https://github.com/DerrickXuNu/v2x-vit) MIT (348★, stale 2024-09),
[DerrickXuNu/CoBEVT](https://github.com/DerrickXuNu/CoBEVT) Apache-2.0 (263★, stale 2024-08),
[ai4ce/V2X-Sim](https://github.com/ai4ce/V2X-Sim) Apache-2.0 (147★, stale 2025-01). **So a V2X
engagement in EMEA is a copyleft-compliance conversation from day one, not a licence-shopping exercise.**
The one permissive, current, policy-side asset is
[openmobilityfoundation/mobility-data-specification](https://github.com/openmobilityfoundation/mobility-data-specification)
— **CC-BY-4.0** (14,527 b), a *data specification* for right-of-way regulation and geofencing, 754★.

---

## 🔌 New on 2026-11-24 (second pass) — the charging stack, in five layers

> Opened as a virgin plane (0 prior mentions of `OCPP`/`OCPI`/`EVerest`/`SteVe`/`charging station` in
> this KB). **Every licence below is byte-read** from `raw.githubusercontent.com`; the branch each grant
> was actually served from is named, because in this plane **three repos do not default to `main` or
> `master`**. Stars from `gh api -X GET search/repositories`, 2026-11-24, one instrument throughout.

### Layer 1 — The station-side stack (what runs on or beside the charger)

| Repo | ★ | Licence (byte-read) | Served from | Role |
|---|---|---|---|---|
| [EVerest/EVerest](https://github.com/EVerest/EVerest) | 299 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | LF Energy's **EV charging software stack**. Umbrella/meta repo. The permissive anchor of the whole plane. |
| [EVerest/everest-core](https://github.com/EVerest/everest-core) | *n/a* | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | The actual modular runtime. **★ deliberately blank: `search/repositories` returns HTTP 422 on this slug** while `ls-remote` and `raw` both serve it — a false-absence, and cross-writing a star count from another instrument is forbidden here. |
| [SmartEVSE/SmartEVSE-3](https://github.com/SmartEVSE/SmartEVSE-3) | 240 | ✅ MIT (1,065 B) | `master/LICENSE` | Open charging-station hardware + firmware, load balancing. |
| [pazzk-labs/evse](https://github.com/pazzk-labs/evse) | 22 | ⚠️ **GPL-3.0 declared, not byte-read** | *no file on 36 paths* | README states a **dual-licence model** (GPLv3 OSS + paid commercial firmware licence) and the line `License: GNU GPLv3` — but there is no LICENSE file in 12 filenames × 3 branches. A metadata-only grant: record as *declared*. |

### Layer 2 — OCPP: the charger↔back-office protocol (the mandated layer)

| Repo | ★ | Licence (byte-read) | Served from | Role |
|---|---|---|---|---|
| [evcc-io/evcc](https://github.com/evcc-io/evcc) | **7,654** | ✅ MIT (1,089 B) | `master/LICENSE` | The largest repo in this plane by an order of magnitude. Smart charging + an enormous **vendor/device abstraction** across wallboxes, inverters and meters. Its real value to a studio is that abstraction layer. |
| [mobilityhouse/ocpp](https://github.com/mobilityhouse/ocpp) | 1,052 | ✅ MIT (1,074 B) | `master/LICENSE` | Reference **Python** OCPP 1.6 / 2.0.1 implementation. |
| [matth-x/MicroOcpp](https://github.com/matth-x/MicroOcpp) | 547 | ✅ MIT (1,081 B) | `main/LICENSE` | OCPP 1.6 / 2.0.1 client **for microcontrollers** — the embedded path. |
| [ChargeTimeEU/Java-OCA-OCPP](https://github.com/ChargeTimeEU/Java-OCA-OCPP) | 380 | ✅ MIT (1,074 B) | `master/LICENSE` | Java client **and** server library. |
| [lorenzodonini/ocpp-go](https://github.com/lorenzodonini/ocpp-go) | 376 | ✅ MIT (1,056 B) | `master/LICENSE` | Go implementation. |
| [c-jimenez/open-ocpp](https://github.com/c-jimenez/open-ocpp) | 174 | ⚠️ LGPL-2.1 (26,529 B) | **`develop`**`/LICENSE` | C++ OCPP 1.6/2.0.1. **Defaults to `develop`, not `main`/`master`** — and LGPL-2.1, so dynamic linking only. |

### Layer 3 — ISO 15118 / V2G: the vehicle↔charger protocol (Plug & Charge)

| Repo | ★ | Licence (byte-read) | Served from | Role |
|---|---|---|---|---|
| [SwitchEV/RISE-V2G](https://github.com/SwitchEV/RISE-V2G) | 260 | ✅ MIT (1,096 B) | `master/LICENSE.txt` | The long-standing **V2G reference implementation** (ISO 15118-2). |
| [ecog-io/iso15118](https://github.com/ecog-io/iso15118) | 250 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | ISO 15118 **-2, -20 and -8**. The -20 coverage is what the EMEA 2027 duty turns on. |
| [ecog-io/josev](https://github.com/ecog-io/josev) | 164 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | Josev community edition — "an operating system for the V2G charging stack". |
| [ecog-io/pyslac](https://github.com/ecog-io/pyslac) | 56 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | **SLAC** (ISO 15118-3) — the PLC link-layer pairing step. |
| [EVerest/libslac](https://github.com/EVerest/libslac) | 19 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | EVerest's own SLAC implementation. |
| [tux-evse/iso15118-encoders](https://github.com/tux-evse/iso15118-encoders) | 11 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | EXI encoders/decoders for the V2G message set. |
| [Ecognize/openv2g](https://github.com/Ecognize/openv2g) | 26 | ⚠️ LGPL-3.0 (7,650 B) | **`trunk`**`/LICENSE.txt` | Dormant, but **load-bearing**: another repo's grant resolves *to this file* (see Layer 5). **Defaults to `trunk`.** |

### Layer 4 — OCPI: roaming between networks (the layer US federal law names)

| Repo | ★ | Licence (byte-read) | Served from | Role |
|---|---|---|---|---|
| [ocpi/ocpi](https://github.com/ocpi/ocpi) | 602 | 🔴 **NO LICENCE FILE** | *none on 36 paths* | **The OCPI specification itself** — and see the warning below. Defaults to **`2.3.0/release/core`**. |
| [TECHS-Technological-Solutions/ocpi](https://github.com/TECHS-Technological-Solutions/ocpi) | 64 | ✅ MIT (1,085 B) | `master/LICENSE` | Python OCPI implementation. |
| [IZIVIA/ocpi-toolkit](https://github.com/IZIVIA/ocpi-toolkit) | 39 | ✅ MIT (1,049 B) | `main/LICENSE` | Kotlin OCPI library. Self-declares *not* affiliated with the EVRoaming Foundation. |
| [ocpi/ocpi-tool](https://github.com/ocpi/ocpi-tool) | 33 | ✅ MIT (1,060 B) | `main/LICENSE` | Data export from OCPI platforms. |
| [BitzArt/OCPI.Net](https://github.com/BitzArt/OCPI.Net) | 27 | ✅ MIT (1,063 B) | `main/LICENSE` | .NET OCPI implementation. |
| [solidstudiosh/ocpi-schema](https://github.com/solidstudiosh/ocpi-schema) | 20 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | JSON-Schema generator for OCPI 2.1.1+. Useful as a **conformance gate in CI**. |
| [tandemdrive/ocpi-tariffs](https://github.com/tandemdrive/ocpi-tariffs) | 40 | 🔴 **UNRESOLVED** | *none* | OCPI tariff calculation — i.e. *the money*. No LICENSE on 36 paths, no licence line in README, root `Cargo.toml` **404**. Repo is live; the grant is not establishable from the served bytes. **Do not use pending clarification.** |
| [OpenChargingCloud/WWCP_OCPI](https://github.com/OpenChargingCloud/WWCP_OCPI) | 29 | ⚠️ AGPL-3.0 (34,519 B) | `master/LICENSE` | WWCP↔OCPI bridge. **Genuine AGPL** (34,519 B) — contrast with the GPL-3.0 repos at 35,148 B. |

> ### 🔴 The mandated specification has no open grant
> `ocpi/ocpi` carries **no LICENSE file in 12 filenames × 3 branches (36 paths)**, and its README states
> that development of the next version lives in `ocpi/ocpi-3`, *"only accessible to Contributors of the
> EV Roaming Foundation"* — i.e. **membership-gated**. Meanwhile **23 CFR 680.108 requires US charging
> networks to interoperate in accordance with OCPI 2.2.1.** A specification that federal law compels you
> to conform to, published without an open licence, with a membership-gated successor. This is a
> procurement and legal-review line item, not a footnote — and it is the strongest argument in this plane
> for buying the *conformance evidence* as a deliverable.

### Layer 5 — Test, simulation and wire analysis (where the billable evidence is produced)

| Repo | ★ | Licence (byte-read) | Served from | Role |
|---|---|---|---|---|
| [SAP/e-mobility-charging-stations-simulator](https://github.com/SAP/e-mobility-charging-stations-simulator) | 231 | ✅ Apache-2.0 (11,369 B) | `main/LICENSE` | OCPP-J charging-station simulator, **SAP-maintained**. Load-generates the fleet you do not own. |
| [monta-app/ocpp-emulator](https://github.com/monta-app/ocpp-emulator) | 182 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | Kotlin Multiplatform charge-point emulator, vendor-backed. |
| [shiv3/ocpp-cp-simulator](https://github.com/shiv3/ocpp-cp-simulator) | 48 | ✅ Apache-2.0 (11,356 B) | `main/LICENSE` | Simulator written **for AI-agent testing** + CSMS development. |
| [aws-solutions-library-samples/guidance-for-modernizing-electric-vehicle-charging-on-aws](https://github.com/aws-solutions-library-samples/guidance-for-modernizing-electric-vehicle-charging-on-aws) | 94 | ✅ **MIT-0** (945 B) | `main/LICENSE` | OCPP gateway as a proxy, reference architecture. MIT-0 = no attribution duty. |
| [Sevenstax/FreeV2G](https://github.com/Sevenstax/FreeV2G) | 71 | ✅ **MIT (1,181 B)** — *API said `NOASSERTION`* | `master/LICENSE.txt` | Host application for WHITE-BEET V2G modules. **A permissive grant the API hid** — a rescue, not a trap. |
| [uhi22/pyPLC](https://github.com/uhi22/pyPLC) | 242 | ⚠️ GPL-3.0 (35,148 B) | `master/LICENSE.md` | CCS charging investigation in Python. Excellent for lab work, copyleft for product. |
| [uhi22/ccs32clara](https://github.com/uhi22/ccs32clara) | 118 | ⚠️ GPL-3.0 (35,148 B) | `main/LICENSE` | STM32 + QCA7005 CCS charge controller. |
| [dspace-group/dsV2Gshark](https://github.com/dspace-group/dsV2Gshark) | 115 | 🔴 **MIT *and* GPL-2.0, split by directory** (19,512 B) | `main/LICENSE` | See the trap note below. |
| [ChargePoint/wireshark-v2g](https://github.com/ChargePoint/wireshark-v2g) | 65 | 🔴 **Licence by reference** (18,308 B) | `main/LICENSE` | See the trap note below. |

> ### 🔴 Two licence traps new to this KB, both in the wire-analysis layer, both `NOASSERTION` in the API
>
> **1. The directory-scoped licence map — `dsV2Gshark` (115★).** A single 19,512 B LICENSE file opens:
> *"The project is licensed under the MIT licence. Files that involve the Wireshark API are licensed
> under the GPL-2.0. This applies to all files in `Wireshark/`. Files in
> `V2G_Libraries/Third_Party/` have their own licenses, as described therein."* So the repo is MIT **and**
> GPL-2.0 **and** an unenumerated third-party set — **partitioned by directory**. The sting: the
> *deliverable* is the Wireshark dissector, which is the **GPL-2.0** part. "dsV2Gshark is MIT" is true of
> the repo and false of the thing you would ship. Stronger than the concatenated-licences trap
> (`InvoicePlane`, travel plane): here the answer depends on **which directory you copy from**.
>
> **2. Licence by reference to another project — `ChargePoint/wireshark-v2g` (65★).** Its LICENSE reads,
> in full at the top: *"This license consists of two parts / Part I: Distribution of this wireshark
> dissector / Part II: Reference the openv2g license."* The grant is **not self-contained**: resolving it
> means opening `Ecognize/openv2g` → **LGPL-3.0, 7,650 B, on the `trunk` branch**. A licence whose terms
> live in a third repository, on a non-default branch name, in a dormant project. **New rule: a LICENSE
> file that cites another project's licence is unresolved until that other file has been byte-read too.**
