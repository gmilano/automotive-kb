---
industry: automotive
region: Global
updated: 2026-10-26
---

# 🏭 Vertical platforms — Automotive

> Real, running open-source systems that can be customised with an AI layer on top.
> Model: start from something that already works, add the agentic layer above it.
> Verified 2026-10-26 (URLs re-probed live; 🔄 = licence/stars re-read today).

## The DMS gap — now narrowed from "nothing exists" to a precise statement

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
| ⏸ **OpenRemote** | [openremote/openremote](https://github.com/openremote/openremote) | ⚠️ **AGPL-3.0** | 1.9k | Java | 100% open IoT platform — device integration, rules, custom apps; fits connected-vehicle/charging telemetry. Sidebar shows no licence name; `LICENSE.txt` read directly (2026-10-15) = **AGPL v3, © 2016 OpenRemote Inc.** |

## ERP / CRM bases for aftersales, parts and dealer operations

| Platform | Repo | Licence | Stars | Stack | Use case |
|---|---|---|---|---|---|
| ⏸ **Odoo** | [odoo/odoo](https://github.com/odoo/odoo) | ⚠️ **LGPL-3.0** | 55.0k | Python | Ships a **Fleet** module out of the box plus inventory, purchasing, maintenance and CRM — shortest path to a working parts/service/fleet back office. `LICENSE` read directly (2026-10-15) = **LGPL v3**. Community edition only; Enterprise is proprietary. |
| ⏸ **Apache OFBiz** | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1.1k | Java | ERP + CRM + e-commerce + supply-chain and manufacturing resource planning in one Apache-2.0 framework. **The most permissive full ERP base**; strongest fit for parts distribution and manufacturing-side work. Heavier to learn than Odoo. |
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
3. **Wrap existing workflows with agents** rather than replacing them: eligibility checks, claim validation
   against repair orders, parts substitution, service scheduling.
4. **Put a human gate on anything that actuates a vehicle or commits money.** Still the one consistent
   design feature across every credible automotive agent reviewed in this KB — and it is what makes the
   EU AI Act's human-oversight duty demonstrable rather than asserted.
5. **Conversational UI / API last.** The value is in the domain model and the gate, not the chat box.

---
*Verified 2026-10-26. 🆕 = new this pass. 🔄 = licence/stars read today. ⏸ = URL re-probed today, figures
carried from 2026-10-15. Where a licence is listed as "not read", the URL is confirmed live and the licence
was deliberately left blank rather than guessed.*
