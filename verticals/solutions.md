---
industry: automotive
region: Global
updated: 2026-10-15
---

# 🏭 Vertical platforms — Automotive

> Real, running open-source systems that can be customised with an AI layer on top.
> Model: start from something that already works, add the agentic layer above it.
> Verified 2026-10-15. **The previous version of this file contained a single placeholder row whose every
> cell was an em-dash or the words "Por completar"; it has been replaced with verified platforms.**

## The honest gap: there is no open-source DMS

Searched this pass: `open source platform automotive ERP CRM MIT Apache`, plus targeted searches for
open-source dealership management systems and auto-repair-shop software.

**Result: no open-source Dealership Management System exists.** The automotive retail layer is a closed
oligopoly — CDK, Reynolds & Reynolds, Tekion, DealerSocket — and dealership AI vendors integrate *into*
those systems rather than replacing them. There is no "Odoo for dealerships" to fork.

This is a stated gap, not an absence of research. Two consequences:
1. Dealership/aftersales engagements are **integration** work against proprietary DMS APIs, not
   customisation of an open base. Price and scope them accordingly.
2. A generic ERP/CRM base (below) plus a VIN/parts/service-order domain model is the only open starting
   point — and that modelling work is the differentiator, not commodity.

## Fleet, telematics & connected-vehicle platforms

| Platform | Repo | Licence | Stars | Stack | Use case |
|---|---|---|---|---|---|
| **Traccar** | [traccar/traccar](https://github.com/traccar/traccar) | Apache-2.0 | 7.9k | Java | Open-source GPS tracking platform, **200+ device protocols**, self-hosted or managed; multi-tenant user/permission management for running several client accounts on one server. **The best permissive starting point in this KB for fleet work.** |
| **Fleetbase** | [fleetbase/fleetbase](https://github.com/fleetbase/fleetbase) | ⚠️ **AGPL-3.0** | 4.3k | PHP/Laravel + Ember | Modular logistics and supply-chain operating system (LSOS); fleet and transport management, extension-based. Far richer than Traccar — but AGPL, so a hosted client deliverable built on it triggers source obligations. Legal sign-off required. |
| **OpenRemote** | [openremote/openremote](https://github.com/openremote/openremote) | ⚠️ **AGPL-3.0** | 1.9k | Java | 100% open-source IoT platform — device integration, rules, custom apps; appears under fleet-management topics and fits connected-vehicle/charging telemetry. ⚠️ GitHub's sidebar shows no licence name; `LICENSE.txt` was read directly and is **GNU AGPL v3, © 2016 OpenRemote Inc.** |

## ERP / CRM bases for aftersales, parts and dealer operations

| Platform | Repo | Licence | Stars | Stack | Use case |
|---|---|---|---|---|---|
| **Odoo** | [odoo/odoo](https://github.com/odoo/odoo) | ⚠️ **LGPL-3.0** | 55.0k | Python | Ships a **Fleet** module out of the box plus inventory, purchasing, maintenance and CRM — the shortest path to a working parts/service/fleet back office. ⚠️ Sidebar shows no licence name; `LICENSE` read directly = **GNU LGPL v3**. Community edition only; Enterprise is proprietary. |
| **Apache OFBiz** | [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1.1k | Java | ERP + CRM + e-commerce + **Supply Chain Management and Manufacturing Resource Planning** in one Apache-2.0 framework. The most permissive full ERP base; strongest fit for parts distribution and manufacturing-side work. Heavier to learn than Odoo. |
| **Krayin CRM** | [krayin/laravel-crm](https://github.com/krayin/laravel-crm) | MIT | 24.0k | PHP/Laravel | Free and open-source CRM for customer, lead and sales management. MIT — the cleanest licence of any CRM here. Good base for a dealer-lead / test-drive-booking front end. ⚠️ Some advanced features (e.g. multi-tenancy) are paywalled. |

## In-vehicle platform (not a "solution", but the base for SDV engagements)

For OEM/Tier-1 work the customisable base is the Eclipse SDV stack, not an ERP:
**COVESA VSS** (signal vocabulary) → **Eclipse Kuksa Databroker** (in-vehicle data layer) →
**Eclipse Ankaios** (workload orchestration on automotive HPCs). All Apache-2.0 or MPL-2.0.
See `repos/foundations.md` Layer 3 and the Eclipse SDV Blueprints
([eclipse-sdv-blueprints](https://github.com/eclipse-sdv-blueprints)), which wire Kuksa signals over
Zenoh with the Databroker running as an Ankaios workload — a ready-made reference topology.

## How to add the AI layer

1. **Pick the base by licence constraint first**, not by features. If the client needs a proprietary hosted
   product, Traccar (Apache-2.0) / OFBiz (Apache-2.0) / Krayin (MIT) are the only clean bases here.
2. **Expose the domain over MCP or a tool API** — vehicle, VIN, repair order, parts, telemetry signal.
   Use VSS names for anything vehicle-signal-shaped so the model's vocabulary matches the industry's.
3. **Wrap existing workflows with agents** rather than replacing them: eligibility checks, claim
   validation against repair orders, parts substitution, service scheduling.
4. **Put a human gate on anything that actuates a vehicle or commits money.** This is the single
   consistent design feature across every credible automotive agent we reviewed.
5. **Conversational UI / API last.** The value is in the domain model and the gate, not the chat box.

---
*Verified 2026-10-15. All six platform URLs reachable; licences read from repository pages or, where the
sidebar was silent, from the `LICENSE` file in-tree.*
