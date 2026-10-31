---
industry: automotive
region: Global
updated: 2026-10-31
---

# 🏭 Vertical platforms — Automotive

> Real, running open-source systems that can be customised with an AI layer on top.
> Model: start from something that already works, add the agentic layer above it.
> Verified 2026-10-31 (URLs proved with `git ls-remote` — `curl -sI` on `github.com` returns **HTTP 403**
> through this session's proxy; 🆕 = new this pass, 🔄 = licence/stars re-read, ⏸ = carried forward).

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
   product, Traccar (Apache-2.0) / OFBiz (Apache-2.0) / Krayin (MIT) / the SDV blueprint (Apache-2.0) are
   the only clean bases here. Odoo, Fleetbase, OpenRemote and OpenAutoCore all carry copyleft obligations.
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
*Verified 2026-10-31 (previous pass 2026-10-26). 🆕 = new this pass. 🔄 = licence/stars read today. ⏸ = URL re-probed today, figures
carried from 2026-10-15. Where a licence is listed as "not read", the URL is confirmed live and the licence
was deliberately left blank rather than guessed.*
