---
industry: automotive
region: Global
updated: 2026-10-15
---

# 📡 Trends — Automotive

> Current trends, verified 2026-10-15. The previous version of this file was a list of five "most active
> repos this week" of which three were not automotive software; it has been replaced with sourced trends.

## T1 — The open reference AV stack is now vendor-published, and it is Apache-2.0

The defining change of 2026. **NVIDIA released the Alpamayo family open-source in January 2026** at CES:
a 10B-parameter reasoning vision-language-action model that takes multi-camera video and emits both
driving trajectories **and reasoning traces** ("Chain-of-Causation"). It shipped alongside **AlpaSim**
(open AV simulator) and Physical AI open datasets with 1,700+ hours of driving data. The line has already
iterated: **Alpamayo 1.5** (Mar 2026), and **Alpamayo 2 Super** at 32–34B on the Cosmos 3 backbone.
Named partners include JLR, Lucid, Uber and Berkeley DeepDrive; the model ships in the Mercedes-Benz CLA
from Q1 2026.

**Why it matters commercially:** NVIDIA explicitly positions Alpamayo as a **teacher model, not in-car
software**. The weights are free; the integration, distillation, validation and homologation are not.
That is the billable surface, and it did not exist 12 months ago.

## T2 — Post-training, not pre-training, is where AV capability is now won

**OpenDriveLab's WorldEngine** (Apache-2.0, updated Sep 2026) frames this directly: imitation-learn a base
policy, run open-loop rollouts over real logs to **automatically surface failure-prone scenarios**, rebuild
those scenes with **3D Gaussian Splatting**, then refine with RL under a shaped safety/efficiency/comfort
reward. Their claim: post-training from a 50k-scene base gives gains equivalent to **~14× more pre-training
data**, with simulated collision rate down up to 45.5% and zero disengagements over a 200 km on-road test
(project's own figures, not independently verified).

Paired with **AlpaGym** (RL on AlpaSim), the closed-loop post-training pipeline is now fully open-source.
The scarce input is no longer compute or model architecture — it is **failure-case data and the pipeline
to mine it**.

## T3 — Software-defined vehicle moves from roadmap to data layer

AI in automotive is moving from feature experimentation to production-grade deployment, driven by ADAS
regulation, SDV roadmaps and scale partnerships. **70% of automotive professionals report using AI for
SDV optimisation** (predictive maintenance, personalisation). The open plumbing has matured accordingly:
**Eclipse Kuksa Databroker** reached 0.6.1 (Apr 2026) and has had a **Quarkslab security audit**; Eclipse
SDV Blueprints now publish reference topologies wiring Kuksa signals over **Zenoh** with the Databroker as
an **Ankaios** workload. **COVESA VSS** is the common vocabulary underneath all of it.

**The signal to read:** these repos have 80–449 stars. Star count is a terrible proxy for importance in
this industry — this is the layer OEM SDV programmes are actually built on.

## T4 — Compliance became the 2026 budget line in EMEA

Four dated obligations land inside 12 months: **EDR mandatory 7 Jan 2026**, **EU AI Act general
application 2 Aug 2026**, **ADDW mandatory 7 Jul 2026**, and **UNECE R155/R156 for new vehicle types from
1 Jun 2026** in GB's type-approval system. **ISO/PAS 8800** (AI safety for road vehicles) complements
ISO 26262 and ISO 21448/SOTIF without replacing them, and the AI Act adds a governance layer on top:
risk management, data quality, transparency, human oversight, robustness, cybersecurity and post-market
monitoring, with a technical file and serious-incident pipeline per high-risk system.

⚠️ **The timeline is genuinely contested.** Safety-component AI (most ADAS/AD) appears to start
**Aug 2027**, and one source cites **2 Dec 2027** for standalone Annex III systems via the Digital
Omnibus. We could not verify that against the Official Journal. Do not put a single date in a client
deliverable without checking primary sources.

## T5 — Adoption is broad, but the market-size numbers are not trustworthy

**71% of automotive professionals are implementing AI in their vehicles**; PwC projects advanced-tech use
across the value chain rising **47% → 72% by 2030**; automotive **leads all sectors** in one 2026
manufacturing survey at ~26% adoption. Meanwhile published 2026 market sizes range from **$14.92B** to
**$38.45B** to **$26.98B** depending on definition — a >4× spread. Use adoption percentages in client
conversations and cite market size only with its source attached. Detail in `intel/market.md`.

## T6 — Aftersales and warranty is the commercial beachhead, and it is agentic

**43% of dealers** already deploy AI. The concrete use cases are unglamorous and high-volume: warranty
eligibility checks, claim submission and validation against repair orders and OEM rules, parts
substitution, fraud/anomaly detection on claim patterns, and service scheduling. Vendors (Salesforce
Agentforce, specialist builders) integrate into **CDK, Reynolds & Reynolds, Tekion and DealerSocket** at
VIN level. There is **no open-source DMS** to disrupt this — see `verticals/solutions.md`. So the
automotive retail AI market is an **integration** market, and will stay one.

## T7 — Every credible automotive agent design has a human gate

Observed consistently across the agent implementations reviewed this pass: the architecturally serious ones
put a **human sign-off between the model and the vehicle**. The clearest example calls it
"Technician-in-the-Loop" — low-confidence or safety-critical cases route to a technician before any
over-the-air action. Treat the gate as a required architectural element in automotive agent work, not a
nice-to-have; it is also what makes the AI Act's "human oversight" requirement demonstrable.

## T8 — Declared gaps this pass

Recording these because an unstated gap is indistinguishable from coverage:

1. 🔴 **No LATAM-specific automotive AI analysis exists** in the searched sources for 2026. See
   `intel/market.md` → LATAM for what was found and what would close it.
2. 🔴 **No open-source Dealership Management System** exists in any searched source.
3. 🟡 **No mature, permissively-licensed automotive-specific *agent* framework.** The top search hits are
   0-star and unlicensed. The buildable layer is policies/VLAs and SDV infrastructure, not agents.
4. 🟡 **GitHub trending could not be filtered for automotive.** `github.com/trending` has no automotive
   topic filter; the topic pages (`automotive-ai`, `autonomous-vehicles`) surface mostly tiny projects.
   Trend detection for this industry has to come from foundations and vendor releases, not trending feeds.

---
*Verified 2026-10-15. Vendor and project self-reported performance figures are labelled as such.*
