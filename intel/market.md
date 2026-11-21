---
industry: automotive
region: Global
updated: 2026-11-21
---

# 🗺️ Market map — Automotive

> Key players, market map and opportunities **by region**. Updated 2026-11-13.
> Every regulatory date below names its instrument. Where sources conflict, the conflict is shown rather
> than resolved — and where a date comes from a vendor page rather than a primary register, it says so.

## 🆕 What changed on 2026-11-21

**Eight region-scoped and global searches run; all five regional subsections updated under
`## Opportunities by region`.** Shelf evidence is first-hand this pass: 174 repository URLs probed with
`git ls-remote`, 152 LICENSE files byte-read from `raw.githubusercontent.com`.

**The four things that would change a conversation this week:**

1. **NA — the federal AV framework became a rulemaking.** NHTSA granted **Zoox the first commercial
   robotaxi exemption** (up to 2,500 vehicles/yr for 2 years), proposed **removing the manual
   brake-pedal requirement** for driverless-only designs, and signed a **3-year $5M agreement with SAE
   ("A2SCEND") to author measurable driving competencies**. State authorisations and **federal
   preemption remain unsettled.**
2. **APAC — China now grades cockpit AI.** **GB/Z 177.7—2026** (released 30 Apr 2026, CATARC-drafted)
   classifies cockpit AI **C1–C5**, reported as the first such scale anywhere. Two **mandatory**
   standards (cybersecurity, software updates) apply to newly approved models from **1 Jul 2026**;
   **GB 47955—2026** on combined driving assistance from **1 Jan 2027**.
3. **EMEA — the AI Act reaches vehicles through type approval.** Best reading this pass: the **Annex I
   type-approval route** under **Regulation (EU) 2026/1744** puts the operative automotive deadline at
   **2 Aug 2028**, not the Act's general 2 Aug 2026 date. The date conflict is **not resolved** — so
   **quote the mechanism, not the date.** Also safe to state: no separate AI Act conformity assessment,
   and type approval alone does not confer compliance.
4. **LATAM — the gap is now specific rather than general.** **Brazil's Bill 2,338/2023** sits in the
   Chamber of Deputies awaiting a rapporteur's opinion; **Mexico has no AI-specific law** and, per
   Chambers, **no regulations governing AI in autonomous vehicles**. The demand-side entry point is
   **Rota 2030 (Decree 9.557/2018)**, a funded industrial-policy programme with R&D obligations.

**Five claims refused this pass for lack of corroboration** — recorded so no later pass quotes them: a
€45M fine on a German supplier; first CEN-CENELEC harmonised standards; "no OEM is fully AI Act
compliant in 2026"; "Europe 28% vs North America 42%" of agentic AI in automotive (single vendor, no
methodology); and MLIT-driven cockpit collision-mitigation adoption in Japan. **Also: the 2026 market
size has a 1.6× spread across vendors ($5.8B–$9.1B) — cite the range, never one number.**

---

## 🆕 What changed on 2026-11-19

1. **The first global AV regulation is now a fact, with a date and a vote.** UNECE **WP.29 approved the
   Automated Driving System Global Technical Regulation by vote of all contracting parties, 22–26 June
   2026, Geneva**, co-developed by **China, the EU, the UK, the US, Canada and Japan**, with **China
   co-leading drafting**. Previous passes recorded "a global regulation now sits above the regional
   patchwork" (**T1**); this pass it has an adopting body, a date range and an authorship list.
   ⚠️ **Approval ≠ authorisation:** jurisdictions still decide where driverless vehicles may operate.
2. **The EU AI Act automotive timeline is still contested six days later, and no primary source has
   been read.** Three incompatible readings are in circulation (2 Aug 2026 / Annex III to 2 Dec 2027
   via **Regulation (EU) 2026/1744** published 24 Jul 2026 / Omnibus adopted June 2026). 🔴 **Recorded
   as unresolved.** A client needing certainty needs Official Journal legal work, not a vendor page.
3. **Dealer AI adoption figures are irreconcilable — 43%, 52%, 82% — but one number is defensible and
   more useful than all of them:** Cox Automotive's **69% expect revenue growth vs 22% who have seen
   it**. Quote the gap, not the level.
4. **On-device in-car AI became a North America production programme.** Mercedes-Benz × **Liquid AI**,
   announced **23 Apr 2026**, multi-year, Liquid Foundation Models running **on-device** on **MB.OS**
   for 3rd/4th-generation MBUX in North America, **no cloud dependence**, targeting *"initial production
   deployment as early as H2 2026"*.
5. **Robotaxi is a multi-city operating business** (Waymo ~10–15 US markets and 20+ more planned
   including London and Tokyo; Zoox paid service in Las Vegas only; Tesla across six-plus metros, partly
   supervised). The counts conflict by source — **the operations, remote-assistance and
   evidence-retention software around them is the engagement, and it does not require owning a stack.**
6. **Assurance-as-code is the cross-region commercial opening of this pass.** Three independent MIT
   projects in six weeks now generate ISO 26262 / 21434 / 21448 / ASPICE / AIAG-VDA artefacts as agent
   output — 2,907★ / 141 forks on the largest. One artefact factory, four regional buyers.
7. **Market-size estimates for AI in automotive now differ by more than 4× for 2026** (USD 5.80B /
   6.52B / 9.13B / and 27.33B from an earlier pass). 🔴 **Do not quote a single number** — this file's
   standing **T9** position is reinforced, not softened.
8. **LATAM's open-source supply gap is confirmed a fifth time**, with the eleven queries that produced
   it named, and the demand side sharpened: LATAM commercial-vehicle telematics **USD 197.4M (2023) →
   USD 374.9M (2028)**, Brazil and Mexico leading; **USMCA review July 2026** the dominant Mexican
   variable; **Brazil PL 2338 still pending in the Chamber as of May 2026**; **Mexico has no horizontal
   AI law**.

> **Source discipline for this section and the regional subsections below:** nearly all 2026 regulatory
> and adoption claims available to this pass come from **law-firm briefings, compliance-vendor pages and
> market-research publishers**. Where a claim is secondary it says so; where two sources conflict, both
> are printed; where a figure could not be corroborated it is marked ⚠️ unverified. **No primary
> register (Official Journal, Federal Register, DOF, UNECE document server) was fetched this pass** —
> `github.com` and `api.github.com` are blocked by the egress policy and no primary-register fetch was
> attempted, so treat every date below as *needing one confirmation step* before it reaches a client
> deck.

## What changed on 2026-11-13

**The supply side moved more than the demand side this pass, and it moved in APAC.**

1. 🆕 **The open AV/ADAS stack is now being *produced* in APAC, not merely adopted there.** The entire
   release wave this pass — an Apache-2.0 production **L2 ADAS stack** (`vision_pilot`, 927★), zero-copy
   ROS 2 middleware, two perception models, an ARM-SoC safety island and a trucking charter — came from
   the **Autoware Foundation**, whose anchor contributor is **TIER IV (Japan)**. Every previous pass placed
   APAC as the largest *market*; this pass places it as the *source of the open supply*. For a Globant
   engagement in any region, the upstream now sits in an APAC-led foundation, which changes who you
   partner with, not just who you sell to.
2. 🆕 **An open stack with a certification story changes the EMEA pitch.** `vision_pilot`'s roadmap names
   **ISO 26262 and ISO 8800**, and `autoware-safety-island` (Apache-2.0, 608 commits) is a concrete ARM-SoC
   safety element. EMEA's whole consulting market in this KB is compliance-led; until now the honest answer
   to *"can we certify open source?"* was silence. It is now *"there is a stack aiming at exactly that,
   and here is its safety element."* ⚠️ Aiming, **not certified** — say it that way.
3. 🆕 **North America's freight signal got a second data point.** `autoware.trucks` (*"Everything specific
   to trucking autonomy … starting with SAE Level 2+ highway piloting and working toward Level 4"*) lands
   alongside **Kodiak AI's autonomous trucking demonstrations in Indiana and Ohio** reported this year.
   Freight is where North American autonomy capital is visibly moving, and the open stack has followed.
4. 🟡 **UNECE WP.29 adopted the first regulation specifically addressing fully driverless ADS on
   24 June 2026** — reported this pass. A **global** instrument sitting above the regional patchwork. ⚠️
   Reported via secondary sources; **not** confirmed against UNECE's own documents from this session.
5. 🔴 **An EU AI Act amendment is being reported that this KB cannot confirm.** Multiple sources describe
   **Regulation (EU) 2026/1744**, a *"Digital Omnibus on AI"* dated **8 July 2026**, in force **27 July
   2026**, amending Regulation (EU) 2024/1689. **This could not be verified against EUR-Lex from this
   session.** It is recorded as **reported-unverified** because it would change compliance scoping if true.
   **Do not cite it to a client until EUR-Lex is read.** See the declared gaps.
6. 🟡 **LATAM: five passes, zero LATAM-origin automotive repositories, and now a measured reason.** The
   regional search returned **no named LATAM automotive AI vendor or OEM programme** — only regulatory
   movement (Brazil's PL 2338 and Mexico's February 2026 Senate bill) and one **unverifiable** OEM claim.
   This is now a durable structural finding rather than a search miss. See LATAM below.

---

## What changed on 2026-10-31

**Two items the previous pass flagged as unverified are now resolved with named instruments, and one
regulatory date moved by nine months.**

1. 🟢 **RESOLVED — China's mandatory AV standards have numbers.** The 2026-10-26 pass recorded *"one source
   puts a mandatory L3/L4 standard referencing the UN GTR in effect 1 July 2027 — ⚠️ unverified."* It is
   **GB 44721-2026**, issued by **MIIT** for **Class M and Class N** vehicles, **effective 1 July 2027**
   with a reported one-year transition. A **second** mandatory standard, **GB 47955-2026**, covers
   **combined driver-assistance systems** and is **effective 1 January 2027** — earlier than anything this
   KB had, and the one that bites first.
2. 🔴 **CHANGED — the EU AI Act's automotive deadline appears to have moved to 2 August 2028.** The
   **Digital Omnibus**, reported adopted **June 2026**, is described as deferring the high-risk obligations
   that reach automotive through the **Annex I type-approval route** to **2 August 2028**. The previous pass
   recorded August 2027 (with a conflicting 2 December 2027 note). ⚠️ **Still not verified against the
   Official Journal** and the sources are law-firm and vendor commentary — but the direction is consistent
   across two independent ones. **Do not re-plan a client roadmap on this until it is confirmed.**
   Meanwhile **Article 50 transparency obligations are reported as already applying since 2 August 2026.**
3. 🆕 **North America: NHTSA proposes removing the manual brake pedal requirement** for vehicles designed to
   operate exclusively without a human driver — the rule that currently blocks pedal-less designs such as
   Tesla's Cybercab. The national standard work now has a name: **A2SCEND**, the three-year, $5M SAE
   consortium, with Administrator **Jonathan Morrison** stating the aim of replacing the state patchwork
   with a single national AV competency standard and one source putting the comprehensive rulebook at a
   **2028** target.
4. 🆕 **North America: enforcement is now individualised.** NHTSA issued a **Special Order on 10 September
   2026 requiring Tesla to answer questions under oath**, due **30 October 2026** — i.e. yesterday relative
   to this pass. A probe into **Avride** opened May 2026. And the **31 July 2026 deadline for AV
   first-responder remediation plans has passed with no operator submission made public and no NHTSA
   outcome announced** — which answers the previous pass's open "if the introduced legislation lands"
   question with: the administrative route moved first.
5. 🆕 **LATAM: Brazil has an AV-specific bill, which this KB had missed.** **PL 1317/2023** would add
   licensing, reporting and **AI governance duties to the Código de Trânsito**. It is distinct from
   **PL 2338/2023** (the general AI framework) that this file already tracks, and it is the instrument a
   CONTRAN-level rule would most likely follow. Still before Congress; **there is still no regulation
   governing the testing or circulation of autonomous vehicles on any Brazilian road.**
6. 🆕 **LATAM: a US instrument is the region's nearest-term automotive AI risk.** The **Connected Vehicle
   Security Act of 2026** was **unanimously approved and advanced by a Senate committee in July 2026**, and
   analysis expects US connected-vehicle rules to reach EV imports **assembled in Brazil**, Turkey, the EU
   and Thailand. For a Brazilian or Mexican plant, the binding AI-and-data rule arrives from Washington
   before it arrives from Brasília or Mexico City.
7. 🆕 **APAC: Japan's agent-relevant guidance is explicit.** Japan's **AI Business Guidelines v1.2** cover
   governance for **AI agents and physical AI** specifically, under a **Phase II AI Basic Plan** adopted as
   a **non-binding** national strategy. Japan's Level 4 deployments remain tightly bounded by **operating
   design domain**.
8. 🆕 **The open model layer stopped being single-vendor** — Apache-2.0 models from the **Autoware
   Foundation** (AutoE2E, tagged 29 Oct 2026) and **Alibaba** (Qwen-Drive-1.0) now both sit ahead of
   Alpamayo 1.5 on AutoE2E's published comparison. This changes the "do not compete on models" posture
   below from a one-vendor observation into a structural one. Detail in
   [`../agents/top.md`](../agents/top.md).
9. 🆕 **An open dealership contract exists** — **Auto Agent Protocol** (Apache-2.0, 110★, v3.1), covering
   dealer discovery, inventory, evidence, pricing and consented inquiries over MCP/A2A/PAP. See the new
   **Global** subsection and [`../verticals/solutions.md`](../verticals/solutions.md).

## What changed since 2026-10-15

1. 🆕 **A global AV regulation now exists.** **UNECE adopted the first global technical regulation for
   automated driving systems on 24 June 2026**, reported as **UN GTR No. 26** paired with **UN Regulation
   No. 185**, endorsed by Canada, China, the EU, Japan, the UK and the US; NHTSA voted in favour on behalf
   of the US in June 2026. This is the single most consequential change for a multi-region vehicle
   programme since this KB began, and the previous pass did not have it. ⚠️ The GTR/regulation numbers come
   from secondary and vendor sources — **confirm against UNECE's own publications before client use.**
2. 🆕 **North America issued its first commercial robotaxi exemption** (NHTSA/DOT, late July 2026): **Zoox
   may commercially deploy up to 2,500 robotaxis annually for two years.** A national AV performance
   standard is in development under a **three-year, $5M partnership with SAE Industry Technologies
   Consortia**, aimed at replacing the state-by-state patchwork.
3. 🆕 **South Korea's AI Basic Act is in force — 22 January 2026**, not merely "due in 2026" as the previous
   pass had it. Three tracks: transparency for generative/high-impact AI, safety duties for frontier
   models, governance duties for high-impact systems in sensitive sectors.
4. 🆕 **China moved from voluntary to mandatory.** Newly issued **mandatory standards for combined driving
   assistance and automated driving** (reported July 2026); one source puts a mandatory **L3/L4 standard
   referencing the UN GTR in effect 1 July 2027 for new models** (date unverified). **L2 penetration has
   passed 70% of new passenger vehicles** (MIIT).
5. 🆕 **LATAM gap partially closed with a hard negative.** **Brazil's PL 2338/2023 AI framework is still
   not law**, and **Mexico has no general AI law** — details and sources under LATAM. This is now a
   *verified* absence rather than an unsearched one, and it changes the sales posture there.
6. 🆕 **Mexico cut the auto-parts import duty to 0% for five years, effective 14 October 2026**, limited to
   terminal automakers under authorised fiscal-warehouse status.
7. 🆕 **CES 2026 pivot:** S&P Global reports automakers emphasised **AI rather than electrification** as EV
   demand softened, positioning cars as software-defined rather than fixed hardware.

## Market size — read the conflict, do not quote a single number

Published 2026 estimates for "AI in automotive" differ by more than **4×** because they use different
market definitions. Anyone quoting one figure to a client is quoting an arbitrary choice:

| Source | Figure |
|---|---|
| The Business Research Company | $17.51B (2025) → **$26.98B (2026)** |
| MarketsandMarkets | **$38.45B by 2030** |
| Acumen Research | **$54.16B by 2035** |
| Impel | $4.29B (2024) → **$14.92B by 2030** |
| Precedence Research 🆕 | **~$5.80B (2026)** → ~$58.99B by 2035 |
| Fortune Business Insights 🆕 | **China alone ~$4.9B (2026)** |
| MarkNtel 🆕 | **India ~$0.96B (2026)** |

🔴 Note the incoherence directly: a $5.80B global figure cannot coexist with a $4.9B China figure and a
$26.98B global figure. **These are marketing pages for paid reports, not reconciled estimates.** Use the
adoption figures instead — they are more consistent and more useful in a sales conversation:

- **PwC** (Global Automotive Outlook): AI and other advanced technologies across the value chain rising
  from **47% today to 72% by 2030**.
- **Perforce** (survey of automotive software professionals): **71% are implementing AI in their
  vehicles**; **57% are currently working on SDV architectures**; **70%** use AI for SDV optimisation.
  Vendor survey — directional.
- **Dealer survey**: **43% of dealers** already deploying AI in operations.
- **Analytics Insight** (manufacturing survey, 2026): automotive **leads all sectors** on AI adoption at
  **~26%**, ahead of APAC-wide manufacturing at 22% and Europe at 18%.

## Global players

| Company | Type | Strength | Weakness |
|---|---|---|---|
| **NVIDIA** | Silicon + open models | DRIVE platform plus the **Alpamayo** open family — now including **Alpamayo 2 Super, 34B, Apache-2.0** — and AlpaSim/AlpaGym. Sets the open reference stack. Ships in Mercedes-Benz CLA from Q1 2026 | Positions Alpamayo as a *teacher* model, not in-car software; integration stays with the OEM/partner. ⚠️ Weights carry **OpenMDW-1.1**, not Apache-2.0 |
| **Mobileye** (Intel) | ADAS/AV systems | Deep OEM design-win base; EyeQ volume; publicly calls **2026–2027 the defining years for ADAS in India** | Closed stack; less open-ecosystem pull than NVIDIA |
| **Qualcomm** | Silicon (cockpit + ADAS) | Snapdragon Digital Chassis; strong in cockpit. 🆕 **Jan 2026 Hyundai Mobis MoU** on ADAS/SDV co-development, with **India named as a target market** | Weaker in full-autonomy perception than NVIDIA/Mobileye |
| **Bosch · Continental · ZF · Denso · Valeo** | Tier-1 | Own physical integration and the functional-safety process; indispensable for type approval | Slow software cycles; the SDV transition is their structural risk |
| **Waymo · Zoox** | Robotaxi | 🆕 Zoox holds the **first US commercial robotaxi exemption** (2,500/yr, 2 years). Deepest real-world validation data | Geographically narrow; capital-intensive |
| **Tesla** | OEM + AV | Vertical integration; fleet data scale | Fully closed; no partner surface |
| **BYD · XPeng · Huawei** 🆕 | OEM / AV (China) | At the 2026 World Intelligent Connected Vehicles Conference: **BYD announced a 4nm intelligent-driving chip in mass production, claimed to support L3/L4**; **XPeng's CEO said the company would "skip L3"**; Huawei ADS presented | China-centric; export exposure to the new mandatory standards |
| **Baidu (Apollo)** | AV platform | 26.9k★ Apache-2.0 platform, **Apollo 11.0** targeting large-scale deployment; most-cited in research | **Partially** open — HD maps and cloud services withheld; China-centric |
| **Autoware Foundation** | AV platform | Genuinely fully open (Apache-2.0), ROS 2, vendor-neutral governance | Smaller commercial deployment base than Apollo |
| **comma.ai** | Consumer ADAS | openpilot, MIT, **64.0k★**, 300+ supported cars — largest permissive automotive codebase | Consumer L2; not an enterprise/OEM vendor |
| **Eclipse SDV · COVESA · Qorix** 🆕 | Standards/foundations + commercial | **S-CORE** (Apache-2.0, ASIL-B target, `v0.7.3` 07 Oct 2026, dual C++/Rust with Ferrocene); VDA MoU now **32 companies**; **Hyundai Mobis joined May 2026**; **Qorix sells a commercial distribution on top** | Low public visibility; star counts (7–451) badly understate real OEM adoption |
| **Sonatus** 🆕 | SDV software | Showed AI-powered SDV work at CES 2026 with **Nissan Technical Centre Europe, Bosch, Michelin, NXP, Renesas**; Schaeffler motion-control work reported July 2026 | Proprietary; a competitor for the same OEM software budget |

## Opportunities by region

### North America

**🆕 Added 2026-11-21 — the federal AV framework stopped being a consultation and became a rulemaking.**
- **NHTSA granted Zoox the first-ever commercial exemption for a purpose-built robotaxi** (reported
  30 Jul 2026), permitting up to **2,500 vehicles annually for two years**. The federal hurdle is
  cleared; **state-level authorisations are still required before service launches**, so the
  patchwork problem moved down a layer rather than disappearing.
- **The brake-pedal NPRM is the structural change.** NHTSA proposed amending the Federal Motor Vehicle
  Safety Standards to **remove the manual brake-pedal requirement** for vehicles designed to operate
  exclusively without a human driver. If finalised, purpose-built cabins (no steering wheel, no pedals)
  become type-approvable rather than exemption-dependent. **This is the single item to watch for a NA
  robotaxi engagement.**
- **A federal performance standard is being authored, not just discussed.** NHTSA signed a **three-year,
  $5M cooperative agreement with SAE International ("A2SCEND")** to develop **measurable driving
  competencies** for automated driving systems. ⚠️ **Opportunity signal:** "measurable competencies"
  means a published, testable rubric — the same shape as the assurance-as-code layer in
  `repos/foundations.md` Layer D. Whoever has the harness wired when the rubric lands has a head start.
- **An interim final rule now allows vehicles to be built *before* an exemption is granted** (comment
  period extended to late Sep 2026 at the Alliance for Automotive Innovation's request).
- **Enforcement is live, not theoretical.** NHTSA escalated its Tesla robotaxi probe with a **Special
  Order** (Sep 2026; sworn response reported due 30 Oct 2026), and opened a probe into **Avride**
  (May 2026). A **31 Jul 2026 deadline for first-responder remediation plans** from robotaxi operators
  passed with **no submissions made public** per one tracker — ⚠️ unconfirmed, flagged not quoted.
- **Dealer-side adoption is the under-served half of this region.** Kerrigan Advisors is reported at
  **43% of dealers already deploying AI and 47% planning to**. This base now holds its first
  MIT-licensed dealer-operations agent layer ([`arielcoro/dealer-ai-skills`](https://github.com/arielcoro/dealer-ai-skills)),
  which is **North-America-shaped by vocabulary** (BDC, F&I, equity mining, fixed ops).
  **The robotaxi story attracts the attention; the 18,000-dealer service-and-retail estate is where
  near-term engagement volume is.**
- 🔴 **Unresolved and material:** **federal preemption of state AV rules** is still not settled, so a
  NA deployment plan must still be written per-state.

**🆕 Added 2026-11-19.**
- **Robotaxi is now a multi-city operating business, and the city counts conflict across trackers —
  quote the conflict, not a number.** Waymo is reported at **"about 10 to 15 U.S. markets"** depending
  on source; one outlet says **Las Vegas was its 15th US market** and that **15 US metros have
  driverless rides as of 9 Nov 2026**; Waymo's own stated plan is **20+ additional cities in 2026,
  including London and Tokyo**. **Zoox** has paid ride-hailing in **Las Vegas only**, free service for
  select riders in San Francisco, and supervised testing slated for Houston and San Diego. **Tesla** is
  reported live in **Dallas, Houston, San Antonio, Orlando, Tampa, Miami**, some rides monitored and
  some unsupervised; as of 14 Sep 2026 it still had **no commercial Las Vegas service despite holding a
  permit**. One tracker reports the **Nevada Transportation Authority approved commercial robotaxi
  permits on 20 Aug 2026 for Tesla (up to 5,000 vehicles across Clark County), Waymo and Uber**.
  *All of the above are secondary trackers; counts differ on whether launched or announced markets are
  counted. Treat as directional.*
- **Why that matters commercially:** a multi-city robotaxi footprint creates **fleet operations,
  remote-assistance, incident-review and evidence-retention** workloads that are software engagements,
  not autonomy engagements. That is Globant-shaped work and does not require owning a driving stack.
- **NHTSA enforcement and rulemaking, 2026 (law-firm and trade sources — verify against the primary
  register before quoting):** engineering analysis **EA26002 opened 18 Mar 2026 covering ~3.2 million
  Tesla vehicles**, on whether FSD detects a degraded state and warns the driver in glare and airborne
  obscurants; **Zoox received the first-ever FMVSS exemption for a commercial robotaxi**, alongside an
  interim final rule allowing a **Section 555** exemption for a vehicle manufactured before the
  exemption's effective date; **15 of the NHTSA/FMCSA rulemakings on the 2026 agenda are AV-focused**;
  the **AV STEP** proposal from Jan 2025 has been **withdrawn**; the **SELF DRIVE Act of 2026
  (H.R. 7390)** would expand NHTSA's authority over ADS-equipped vehicles and is reported to require a
  **safety case for SAE L3–L5** — its status beyond introduction is **not established** by the sources
  found. California is reported to require an operator response to a notice of AV noncompliance
  **within 72 hours since 1 Jul 2026**.
- **The engagement this creates:** *safety-case production and field-monitoring evidence*. A safety-case
  requirement in federal law turns ISO 26262 / ISO 21448 / UL 4600 artefact production into a budgeted
  deliverable. **This is exactly what `jherrodthomas/automotive-skills-suite` (MIT, 2,907★) and
  `jherrodthomas/LionDriver` (MIT) now provide open templates for** — and LionDriver's field-monitoring
  process already carries a live case tied to **NHTSA PE26007**. See `compose/patterns.md` → **P14**.
- **Dealer AI adoption: the numbers are irreconcilable and that is the finding.** Kerrigan Advisors
  (via Impel): **43% of dealers already deploying AI, 47% more planning to**. Impel's own post:
  **82%**. Cox Automotive's *AI in Auto Retail Tracker*: **82% in Q2 2026**. A Ringlead summary:
  **~52%**. Cox also found **69% of dealers expected AI to drive revenue growth while only 22% of AI
  users had seen it**. Spyne's survey of **~1,200 dealership executives** put **AI voice agents top of
  the investment list at 74%**, focused on lead response, inbound calls and service scheduling.
  **Use the 69%-vs-22% expectation gap as the opening of a dealer conversation** — it is the most
  defensible number here, and it describes a delivery problem, which is what a studio sells.
- **On-device in-car AI is a North America production programme, not a concept.** Mercedes-Benz and
  **Liquid AI** announced a **multi-year partnership on 23 Apr 2026** to run **Liquid Foundation Models
  on-device** for the MBUX Virtual Assistant on **MB.OS**, covering 3rd- and 4th-generation MBUX in
  **North America**, with speech recognition, language understanding and reasoning processed locally
  **without cloud dependence**. Mercedes' own release targets *"initial production deployment as early
  as the second half of 2026"* — **"as early as" makes this a target, not a date**. Reported eligible
  models: 2025+ C-Class and GLC (ICE), 2026+ GT and SL, 2026 electric CLA and its 2027 ICE counterpart,
  2027 electric C-Class.
- **The opportunity in that:** **on-device means small models, tight latency budgets and no cloud
  fallback** — the engineering profile matches `cockpit-agent-sim`'s fast/slow dual layer (MIT, 98★)
  and `Sherin-SEF-AI/Lyne-ADAS`'s on-device Android ADAS (MIT). An OEM that has committed to on-device
  needs evaluation harnesses, fallback design and HMI confirmation flows — all deliverable without
  model weights.

**🆕 Added 2026-11-13.**
- **Federal safety rule as the AI demand driver:** NHTSA's final rule on automatic emergency braking,
  **FMVSS No. 127**, is projected to *"save at least 360 lives per year and prevent at least 24,000
  injuries annually once fully in effect."* AEB is an ADAS function, so a federal AEB mandate is a federal
  **perception-software** mandate — and `vision_pilot` (Apache-2.0) ships AEB, FCW and ACC today. That is
  the single cleanest mandate-to-open-stack mapping in this KB.
- **State layer moved again in 2026:** **California DMV adopted new AV regulations on 28 April 2026**,
  covering **light- and heavy-duty** vehicles (the heavy-duty inclusion is the newsworthy part — it is the
  freight opening). **Tennessee HB2302**, enacted **April 2026**, makes **AV builders answerable for
  traffic violations** — a liability-allocation precedent worth tracking because it prices the compliance
  work. **Kentucky HB 223 died in committee.** Driverless operation remains legal in **California, Arizona
  and Texas**, generally under permit.
- **NHTSA's exemption process is still the route for vehicles without human controls**, used by **Waymo,
  Zoox and Cruise** for purpose-built fleets.
- **Freight is the live segment.** **Kodiak AI** ran autonomous trucking demonstrations in **Indiana and
  Ohio** in 2026. Pair with `autoware.trucks` and with **Peykan** — the only diagnostics agent in this KB
  covering **SAE J1939**, the commercial-vehicle bus.
- **Dealer-side adoption, with a real Canada gap:** dealership chatbot adoption is reported at **~52% in
  the US vs ~35% in Canada**, attributed to a smaller vendor market, **Quebec bilingual requirements**,
  **CASL** compliance complexity, and fewer OEM programmes. **No major OEM has issued a formal AI mandate
  yet**, with tool-use-tied incentive programmes predicted for late 2026 / early 2027. ⚠️ Single vendor
  blog — directional only. **The Canada delta is the opportunity:** a bilingual, CASL-compliant dealer
  agent is a differentiated, under-served build.
- **Share:** North America at **36.8–40%** of global automotive AI revenue depending on source.
- 🔴 **Gap:** almost nothing found on **Canadian federal** AV/AI rules, and no detail on **OEM AI
  strategies** beyond dealer-focused vendor blogs.

- **Position:** largest or near-largest regional market in most reports (34–37% of revenue depending on
  source); leader on testing volume, investment and regulatory flexibility.
- **Regulatory shape — moving fast, and federally this time.** NHTSA owns vehicle safety, states control
  testing and operation, but 2026 shifted weight to the centre:
  - 🆕 **First commercial robotaxi exemption** (Zoox, up to 2,500/yr for 2 years), late July 2026.
  - 🆕 **National AV performance standard in development** — 3-year, **$5M** partnership with **SAE
    Industry Technologies Consortia**, explicitly to replace the state patchwork.
  - 🆕 **DOT AV National Strategy (FY 2026–2030)**, published Sept 2026: federal leadership coexisting
    with State authority over rules of the road.
  - 🆕 **NHTSA is investigating AI applications within ADS** and assessing **AI training and validation
    strategies** — i.e. the regulator is now asking the validation question directly.
  - 🆕 **Legislation introduced** after NHTSA's warning on driverless vehicles interfering with emergency
    operations: mandatory coordination protocols, emergency hotlines, **geofencing requirements**,
    enforceable performance standards for AV operators.
  - 🆕 ⏳ **The surface transportation law funding these programmes expires 30 September 2026** — a hard
    deadline sitting in the middle of this quarter. Check its status before quoting programme continuity.
  - 🆕 **Brake-pedal NPRM:** NHTSA has **proposed removing the manual brake pedal requirement** for
    vehicles designed to operate exclusively without a human driver — the rule that blocks pedal-less
    designs (Tesla's Cybercab has no steering wheel or pedals). If finalised, purpose-built robotaxis stop
    being exemption-dependent, which is what turns Zoox's one-off into a category.
  - 🆕 **The national standard has a name: A2SCEND** — the three-year, **$5M** cooperative agreement with
    **SAE International**, whose data is intended to inform the **first federal performance standard for
    automated driving systems**. Administrator **Jonathan Morrison** frames the goal as replacing the
    patchwork of inconsistent state and local requirements with a **single national AV competency
    standard**; one source puts the comprehensive rulebook at a **2028** target.
  - 🆕 **Enforcement has gone individual, not just rule-making.** A **Special Order of 10 September 2026
    requires Tesla to answer NHTSA's questions under oath**, due **30 October 2026**. NHTSA **opened a probe
    into Avride in May 2026**. And the **31 July 2026 deadline for AV first-responder remediation plans has
    passed with no public submission and no announced outcome** — so the emergency-services issue advanced
    administratively rather than through the introduced legislation above.
  - 🆕 **Players:** Waymo, Tesla, **Zoox** (Amazon-owned) and 🆕 **Avride**, which launched a robotaxi
    service with **Uber** in December 2025. States permitting commercial L4 under geofenced,
    reporting-based frameworks: **California, Arizona, Texas, Florida**.
  - 🆕 ⚠️ **Transparency is moving the wrong way for anyone selling validation.** One analysis notes that
    2025's changes to reporting requirements imply **decreasing public visibility of AV failure modes as
    fleets grow**. That shrinks the public corpus a scenario-mining offering can draw on — and raises the
    value of a client's own logs, which is where P1 points anyway.
  - **FMVSS No. 127** (automatic emergency braking) remains a live compliance driver. California permitted
    AVs logged **over 9 million test miles** Dec 2024 – Nov 2025.
- **Opportunity — AV validation and scenario engineering.** Heavy testing volume + per-state reporting +
  **a regulator now explicitly assessing AI training and validation strategies** makes closed-loop
  scenario mining a repeatable offering. WorldEngine or AlpaSim + CARLA/scenario_runner turn fleet logs
  into regression suites. See `compose/patterns.md` P1.
- **Opportunity — geofencing-and-incident compliance tooling.** 🆕 If the introduced emergency-services
  legislation lands, every AV operator needs auditable geofence enforcement and an incident-coordination
  trail. That is the P3 evidence pipeline pointed at a US instrument instead of an EU one.
- **Opportunity — dealership and aftersales agents.** 43% dealer adoption plus a closed DMS oligopoly
  (CDK, Reynolds & Reynolds, Tekion, DealerSocket) means integration against proprietary APIs —
  defensible, recurring, not commoditised by open source. Warranty-claim validation against repair orders
  is the highest-volume entry point. See P2. 🆕 **Now with a published contract on the outward-facing side:**
  implement **Auto Agent Protocol v3.x** for dealer discovery, inventory, evidence and consented inquiries
  instead of inventing a schema — the DMS integration stays bespoke, the agent interface does not.
- 🆕 **Opportunity — pedal-less-vehicle homologation support.** If the brake-pedal NPRM finalises, every
  purpose-built robotaxi programme needs an FMVSS-delta argument for a vehicle with no manual controls.
  That is the P3 evidence pipeline aimed at an FMVSS exemption/compliance file, and the deadline pressure
  is the client's product launch rather than a regulator's calendar.

### EMEA

**🆕 Added 2026-11-21 — the type-approval route is now the clearest reading of how the AI Act reaches vehicles.**
- **The mechanism matters more than the date.** The most coherent account found this pass: vehicle AI
  reaches the AI Act **through the Annex I type-approval route**, which pushes the operative automotive
  deadline to **2 Aug 2028** under **Regulation (EU) 2026/1744**, rather than the Act's general
  application date of **2 Aug 2026**. One source records the **Digital Omnibus published in the OJ on
  24 Jul 2026, in force 27 Jul 2026**. Older material still says 2027.
  ⚠️ **The three-way conflict recorded on 2026-11-19 is not resolved — it is now better explained.**
  Quote the *mechanism* (type approval, Annex I) and let the client's counsel pick the date.
- **Two compliance facts that are safe to state, because they are structural rather than date-dependent:**
  1. **Manufacturers do not run a separate AI Act conformity assessment** — it folds into existing type
     approval. 2. **A type-approved vehicle is not automatically AI Act compliant.** Both can be said
     without taking a position on the deadline.
- **UNECE regulations are the evidence layer, and this is the actionable detail.** Specific UNECE rules
  map onto AI Act articles — e.g. **R157 transition-demand design is evidence for the human-oversight
  requirement**. ⚠️ **Opportunity:** that mapping is a deliverable. An EMEA engagement that produces a
  traceable UNECE-article → AI-Act-article matrix, backed by the assurance-as-code layer in
  `repos/foundations.md` Layer D, is selling demonstrable oversight rather than asserted compliance.
- **Who is the "provider" is settled enough to design around:** the **OEM** is generally the provider,
  and **Tier-1 suppliers furnishing AI subsystems are providers of those subsystems**. That makes the
  Tier-1 a compliance counterparty in its own right — a distinct, addressable buyer.
- **L3 is shipping in-region:** BMW Highway Assistant and Mercedes-Benz Drive Pilot under **UNECE R157**.
- 🔴 **Claims refused this pass for lack of corroboration** (recorded so no later pass quotes them):
  a **€45M fine on a German supplier**; **first CEN-CENELEC harmonised standards**; **"no OEM is fully
  AI Act compliant in 2026"**; and **Europe at 28% vs North America at 42% of agentic AI in automotive**
  (single vendor source, no stated methodology). None independently verified.
- ✅ **EMEA is where the open SDV commons actually lives**, and that is a durable regional advantage:
  the Eclipse stack (**S-CORE, Kuksa, Leda, Ankaios, iceoryx, eCAL, Velocitas**) and **COVESA VSS**
  (**MPL-2.0**, byte-confirmed) are European-governed and permissively licensed. For a sovereignty-
  sensitive EMEA client this is assembled from parts they can audit — see `compose/patterns.md`.

**🆕 Added 2026-11-19.**
- **The AI Act timeline conflict is still unresolved, and it is now the single most valuable thing to
  know in an EMEA automotive conversation.** Sources split three ways: (a) the main automotive
  obligations apply from **2 Aug 2026**; (b) **Regulation (EU) 2026/1744** (Digital Omnibus) was
  **published in the Official Journal on 24 Jul 2026, in force 27 Jul 2026**, pushing **Annex III
  high-risk obligations to 2 Dec 2027** and **embedded Annex I products to 2 Aug 2028**; (c) a third
  source dates the Omnibus adoption to **June 2026**. 🔴 **All are secondary (compliance-vendor and
  law-firm pages). Verify against the Official Journal before quoting any of them to a client.**
  This KB's 2026-11-13 entry recorded the same conflict; **six days later it has not resolved**, which
  itself is information: nobody in the vendor layer knows, so a client who needs certainty needs
  primary-source legal work, not a vendor deck.
- **How vehicles are actually covered:** through **existing UNECE type-approval**. One source states
  the UN-ECE type-approval procedure **absorbs** the AI Act requirements; another states plainly that
  **a type-approved vehicle is not automatically AI Act compliant**. The practical bridge reported:
  OEMs with existing **UNECE R151** documentation can build on it but must **add AI-specific items —
  bias testing and AI Act risk-management language**. That delta is the billable work.
- 🆕 **UNECE WP.29 adopted the first regulation specifically addressing fully driverless ADS in
  June 2026** (see Global). Note the limit: **individual countries and jurisdictions still decide where
  and how such vehicles may operate** — this is not EU-wide authorisation. One legal overview describes
  the EU AV framework as **"relatively patchwork across Member States"**, drawing on UNECE, the Vienna
  Convention and EU instruments rather than a harmonised EU AV law.
- **Players, as reported (vendor compliance page — unverified):** **BMW** Level 3 Highway Assistant
  under **UNECE R157**; **Mercedes** Drive Pilot Level 3; **Tesla FSD approved in the EU at Level 2
  only**; and the claim that **no OEM is yet fully AI Act compliant**. Enforcement split: the
  Commission's **AI Office** oversees general-purpose AI models, **national authorities** enforce most
  other parts.
- 🆕 **EMEA supplies the systems-engineering and middleware tier of the open stack**, which is a better
  fit for sovereignty-constrained engagements than the APAC model tier: `de4sdv/DE4SDV` (Apache-2.0,
  **SysML v2**, pushed 2026-11-19), `eclipse-leda/*` (Apache-2.0, Yocto SDV images),
  `eclipse-iceoryx/iceoryx` (Apache-2.0, 2,212★), `eclipse-ecal/ecal` (Apache-2.0, 1,060★),
  `ebroecker/canmatrix` (BSD-2, 1,093★ — the **ARXML ⇄ DBC** bridge), `thi-ad/UrbanIng-V2X`
  (**MIT, 88★, NeurIPS 2025**, TH Ingolstadt), `BUAksakal/reqlens` (MIT, Türkiye — LangGraph + LlamaIndex
  requirements review). **An EMEA engagement can be built end-to-end on EMEA-origin, permissively
  licensed code**, which answers the sovereignty objection recorded as **T5** without importing a
  Chinese or US model.
- **Germany, measured:** a 2026 study of **204 workshops and dealerships** reported **35% already using
  AI tools and 84% seeing concrete future potential**. That 35/84 split is the clearest aftersales
  adoption datapoint in this file for any region — a large stated-intent gap, which is a pipeline.

**🆕 Added 2026-11-13.**
- 🔴 **Reported-unverified, and material:** **Regulation (EU) 2026/1744**, the *"Digital Omnibus on AI"*,
  dated **8 July 2026** and in force **27 July 2026**, amending **Regulation (EU) 2024/1689** (the AI Act).
  Multiple secondary sources carry it; **EUR-Lex could not be read from this session**. If real it changes
  AI Act scoping. **Verify before citing.**
- **Germany implemented nationally:** a German **AI implementation law took effect 29 July 2026**, naming
  national supervisory authorities and creating a **coordination hub at the Bundesnetzagentur**, with
  market-surveillance and innovation-support provisions. Reporting indicates **high-risk vehicle AI such as
  ADAS will face audits and documentation duties** — i.e. the evidence pipeline is the deliverable. ⚠️
  Secondary sources.
- **Automated driving approvals loosened:** the **European Commission removed the small-series limitation
  for Automated Valet Parking** in 2026 — AVP is the most deployable L4 feature in Europe, and the
  volume cap was the blocker. Robotaxi approval still depends on vehicle type, use case and national rules.
- **Binding cybersecurity baseline unchanged:** **UN R155** (CSMS) and **UN R156** (SUMS).
- **Players:** **Wayve** is the leading European homegrown AV contender, developing its **AI Driver** with
  **Uber** and **Stellantis**. Robotaxi names also reported for European cities: **Bolt, Waymo, WeRide**.
  Robotaxis expected in several European cities in 2026 — **London, Luxembourg, Madrid, Munich**.
  ⚠️ **BMW, Mercedes-Benz and VW Group reportedly allocate >€15B annually to SDV architectures** — this
  figure traces to no primary document and should not be quoted to a client.
- **Industrial-AI beachhead:** **BMW + University of Zagreb** have run the **INSIGHT** project since 2024
  applying AI across **battery-cell production** — a reminder that EMEA automotive AI money is not all in
  the vehicle; manufacturing-side AI is a parallel market with looser safety constraints.
- **Standing read:** Europe trails the US and China on commercial robotaxi operation, attributed to
  fragmented regulation. **Fragmentation is the consulting market** — see P4.

- **Position:** regulation-led adoption. ADAS uptake is driven by mandate rather than consumer pull, which
  makes compliance the budget line. This remains the strongest consulting market in this KB.
- **Regulatory shape — the densest calendar of any region:**
  - **EU AI Act**: **2 August 2026** is the general-application date. For AI that is a **safety component
    of a regulated product** (most ADAS/AD), obligations start later — **August 2027**. ⚠️ One source cites
    **2 December 2027** for standalone Annex III high-risk systems via the Digital Omnibus; this conflicts
    with the above and **could not be verified against the Official Journal — confirm before using it in a
    client deliverable.** The Act **does not replace** ISO 26262, ISO 21448/SOTIF, ISO/SAE 21434, UN R155
    or UN R156; it adds a governance layer, and runs through the type-approval regime rather than as a
    parallel filing (the latter per a compliance vendor — verify).
  - 🆕 **UN GTR No. 26 / UN Regulation No. 185** (ADS), adopted **24 June 2026**, EU among the endorsers.
  - **UNECE R155 (CSMS) and R156 (SUMS)** remain a legal prerequisite for type approval; GB in force
    Nov 2025, first mandatory deadline for **new types from 1 June 2026**.
  - **EU General Safety Regulation**: Event Data Recorder mandatory **7 Jan 2026**; Advanced Driver
    Distraction Warning mandatory **7 Jul 2026** — driving in-cabin monitoring demand now.
  - 🆕 **UK**: the **Automated Vehicles (Permits for Automated Passenger Services) Regulations 2026** have
    been in force since **15 May 2026** — a live permitting regime, not a consultation.
  - 🔴 🆕 **The automotive date may now be 2 August 2028.** The **Digital Omnibus** (reported adopted
    **June 2026**) is described as deferring the high-risk obligations that reach automotive via the
    **Annex I type-approval route** to **2 August 2028**; a second source independently says automotive
    reaches the Act "mainly through the Annex I type-approval route at 2 August 2028". This **supersedes
    the August 2027 / 2 December 2027 readings above if confirmed.** ⚠️ **Not verified against the Official
    Journal; sources are law-firm and vendor commentary.** Treat as likely-but-unconfirmed and **do not
    re-baseline a client roadmap on it yet.**
  - 🆕 **Article 50 transparency obligations are reported as already in application since 2 August 2026** —
    the part of the Act that is live today for in-cabin generative/assistant features.
  - 🆕 **Framing that wins the compliance conversation:** *a type-approved vehicle is not automatically AI
    Act compliant*, and **UNECE compliance is supporting evidence, not a discharge.** Practically,
    existing **UN R151** documentation can be extended to satisfy **AI Act Article 11** technical-file
    duties — which makes the offering "extend what you already filed", not "start a new filing".
  - 🆕 **Extraterritorial reach, and a live UK exposure:** UK automotive businesses placing AI systems **or
    their outputs** on the EU market may still be in scope post-Brexit. A UK Tier-1 selling into the EU is
    a qualified lead for the same conformity offering.
  - ⚠️ 🆕 **One widely-repeated claim to avoid:** a low-authority German site asserts that **no OEM is fully
    AI Act compliant in 2026** (naming Tesla, BMW, VW, Mercedes). It cites nothing. **Do not use it in a
    deliverable** — it is the kind of line that is easy for a client to challenge.
  - **ISO/PAS 8800** (AI safety for road vehicles) complements ISO 26262 and ISO 21448/SOTIF.
- **Opportunity — AI Act + ISO/PAS 8800 conformity tooling.** Each high-risk AI system needs a technical
  file, a post-market monitoring plan and a serious-incident pipeline: a documentation and evidence
  pipeline, generatable and auditable, repeatable across OEMs. **Highest-margin offering in this KB.**
- **Opportunity — sovereign/on-prem SDV data layer, now with S-CORE in it.** 🆕 VSS + Kuksa + Ankaios +
  **Eclipse S-CORE** self-hosted satisfies data-residency expectations and R156 update traceability. The
  VDA-backed, 32-company governance and the **Qorix** commercial distribution answer the "unsupported open
  source" objection in procurement. See P3 and the new P7.
- **Players to partner with or around:** BMW, VW, Mercedes-Benz, Audi, Volvo Cars; Tier-1s Bosch,
  Continental, ZF, Mobileye; Harman in cockpit; 🆕 Sonatus and Qorix as both partners and competitors.
- 🆕 **Calendar anchor:** the **European AI and Software-Defined Vehicle Summit** is the OEM/Tier-1 venue
  for this agenda (reported 19–20 May 2026, Stuttgart) — useful for engagement timing.

### APAC

**🆕 Added 2026-11-21 — China now *grades* cockpit AI, which turns a feature argument into a compliance target.**
- 🚨 **The headline: cockpit AI has a national grading scale.** **GB/Z 177.7—2026**, a guidance document
  released **30 Apr 2026** and drafted with **CATARC**, classifies intelligent-cockpit AI into **five
  levels, C1 through C5**. This is reported as the **first evaluation system for grading cockpit AI
  capability** anywhere. ⚠️ **Why it is the most actionable APAC item in this file:** a graded scale
  converts "our cockpit is smart" into "our cockpit is C3 and here is the evidence." That is a
  measurable engineering target, and it is exactly the shape
  [`neura-edit/omni-intent`](https://github.com/neura-edit/omni-intent) (MIT, deterministic on-device
  intent routing — see `agents/top.md` §6) is built for.
- **Two mandatory national standards — vehicle cybersecurity and software updates — apply to newly
  approved models from 1 Jul 2026.** A third, **GB 47955—2026** on combined driving assistance, is set
  to take effect **1 Jan 2027**. Mandatory OTA and cybersecurity standards are a **services** opportunity
  (update pipelines, evidence packages), not only a product one.
- **Adoption is mass-market, not pilot-stage:** **L2 driver-assistance penetration reported at 70.5%**
  in China. **IDC** puts China's AI-cockpit market at **¥710M in H1 2026**, with **Volcano Engine at 45%
  share**. ⚠️ Market-size figures across APAC reports conflict and are directional only.
- **The silicon layer is the concentration risk worth naming:** **Qualcomm still holds ~71.4% of China's
  cockpit domain-controller chip market in H1 2026**, with Huawei and SiEngine well behind. A
  cockpit-software engagement should assume Qualcomm NPU targets while designing for portability.
- **Partnership structure is the entry mode:** Xpeng MONA L03 with **XOS 6** (Jul 2026); **Neusoft Smart
  Go + Tencent Cloud** on AI cockpit (Apr 2026); **Toyota Boshoku + Huaqin** smart-cockpit JV (Jul 2026).
  **Japan and Korea contribute cluster/HUD expertise; China sets the mass-production pace.**
- ✅ **APAC is where the open driving-policy and world-model work is**, consistent with earlier passes —
  `QwenLM/Qwen-Drive-1.0`, `hustvl/Senna`, `xiaomi-research/recogdrive`, the Autoware ecosystem
  (TIER IV, Japan). **The models are APAC; the SDV middleware is EMEA; the robotaxi operators are NA.**
- 🔴 **Japan's regulatory picture remains thin.** One market report attributes accelerating
  cockpit-integrated collision-mitigation adoption to **MLIT** rules; the source is low-detail and
  **this is not corroborated**. Recorded as unverified, not quoted.

**🆕 Added 2026-11-19.**
- 🆕 **China co-led the first global AV regulation, and that is a standard-setting shift, not a
  compliance detail.** The **UN World Forum for Harmonization of Vehicle Regulations (WP.29) approved
  the Automated Driving System Global Technical Regulation by vote of all contracting parties on
  22–26 June 2026 in Geneva**, co-developed by **China, the EU, the UK, the US, Canada and Japan**, with
  **China co-leading the drafting**. Consequence for engagements: a client's ADS documentation now has a
  **single global target** with Chinese authorship in it — and Chinese domestic rules are *stricter*
  than the GTR, so a China-compliant artefact pack is close to a superset.
- **China's domestic rules, as reported:** the 2025 regulation **bans public beta testing**, restricts
  certain marketing terminology and **heavily regulates over-the-air updates**. OTA regulation is the
  under-priced item — it makes release engineering and evidence retention a regulated function.
- **Japan:** permits certain AVs on public roads against its own safety standards and **requires remote
  monitoring for all Level 4 vehicles**. Remote monitoring is an operations software engagement.
- **South Korea:** a comprehensive legal framework supporting AV testing and commercialisation, plus
  **issued ethical guidelines for accident decision-making**. The ethics guidelines are the distinctive
  item — they create a documentation deliverable no other region requires in the same form.
- **Adoption and players:** one report puts **combined driver-assistance penetration in new cars above
  60% as of mid-2026** — ⚠️ **could not be independently verified; do not quote it as fact.**
  **Pony.ai partnered with Toyota in January 2026** to develop and deploy mass-produced robotaxis;
  **Volkswagen's CARIZON and Horizon Robotics expanded their China partnership in July 2026** for L3,
  with **L3-equipped models planned for the Chinese market from H2 2027**. Named players: **Baidu,
  Pony.ai, BYD, Geely**; Toyota and Hyundai active regionally.
  ⚠️ One source claims China required **30% of new vehicles to have L3+ capability by 2025** — this
  **could not be corroborated and should not be relied on**.
- 🆕 **APAC still supplies the model tier, and this window it was Xiaomi's turn.**
  `xiaomi-research/recogdrive` (**Apache-2.0, 631★/78f, ICLR 2026**, pushed 2026-11-19) — a reinforced
  cognitive framework for end-to-end AD — sits alongside `LMD0311/HERMES` (Apache-2.0, 265★, ICCV 2025),
  `H-EmbodVis/HERMESV2` (Apache-2.0, IEEE TPAMI), `TabGuigui/WorldDrive` and `chenshi3/DriveWAM` (both
  Apache-2.0, **NeurIPS 2026**), `curryqka/AgentThink` (Apache-2.0, 154★, EMNLP 2025) and
  `Thinklab-SJTU/Awesome-LLM4AD` (Apache-2.0, **1,906★** — the best index of the field).
  `yancent-dao/cockpit-agent-sim` (MIT, 98★) adds the **cockpit HMI agent** layer from the same region.
- **The licence fact that makes this usable:** **11 of the 14 new model/world-model rows admitted this
  pass are Apache-2.0.** The APAC research tier has become licence-safe by convention. Two passes ago
  the no-licence rate was the main blocker in this tier; it is now the exception
  (`FrankRun/WCog-VLA`, `xiongqi123123/MarginAD`).
- **The standing caution still stands:** an APAC-origin model in a North America or EMEA delivery
  imports a provenance conversation. Apache-2.0 answers the *licence* question; it does not answer the
  *training-data* question, and `huggingface.co` is unreachable from this session so **no weight licence
  has been verified first-hand**.

**🆕 Added 2026-11-13 — and this is the pass where APAC's role changed.**
- 🆕 **APAC is now the *source* of the open stack, not just the largest market.** The Autoware
  Foundation — anchored by **TIER IV (Japan)** — published the entire release wave this pass:
  `vision_pilot` (Apache-2.0 L2 ADAS, 927★), `agnocast` (zero-copy ROS 2 IPC, 212★),
  `autoware-safety-island` (ARM SoC, 608 commits), `scene_3d`, `ego_lanes`, `autoware.trucks`,
  `alpamayo-autoware`. Add **Alibaba's Qwen-Drive-1.0** and **HUST's Senna (IJCV 2026)** from China.
  **The open automotive AI supply chain is APAC-led.** Engagement consequence: partnership and upstream
  contribution strategy belongs in APAC regardless of where the client sits.
- **China — the most assertive regime in the region.** Mandatory **registration and labelling**, fines up
  to **¥50 million**, **CAC filing required for generative AI**, with **550+ generative AI services filed
  by mid-2026**. Combined with **GB 44721-2026** (MIIT, Class M/N, effective **1 July 2027**) already in
  this file, China is the one market where the compliance calendar is both binding and dated.
- **Japan — light touch, and that is the point.** The **AI Promotion Act**, in force since **June 2025**,
  is a framework law **with no penalties**; commentary expects possible movement toward mandatory rules.
  **A permissive domestic regime is part of why the open stack is being built here** — Japan's automotive
  strength is safety-critical engineering and Tier-1 integration, and `autoware-safety-island` plus the
  ISO 26262/8800 roadmap is exactly that posture expressed as open source.
- **India — no standalone AI law.** A **July 2026** report says the government signalled possible
  **dedicated, risk-based AI legislation**, which some industry voices warn could slow adoption; sectoral
  rules (e.g. central bank) apply meanwhile. Automotive AI growth is **from a small base**, concentrated in
  **fleet management and ADAS**.
- **Players:** **Horizon Robotics** and **Huawei** (China); **Mobileye**, **Qualcomm** and Tier-1
  suppliers more broadly.
- 🔴 **Figures do not reconcile and should not be averaged:** one report gives APAC automotive AI a
  **37.8% CAGR (2026–2034)**, another **25.8% (2026–2035)**. Directional only.
- 🔴 **Gap:** no direct sources found this pass for **automotive-specific** APAC rules such as **L2+/L3
  driving-assistance approvals** outside China's GB standard. Needs a dedicated follow-up search.

- **Position:** the **largest** region in several reports (one puts it at 56.7% share in 2025 — note this
  does not reconcile with the North America figures above, because the definitions differ). Growth led by
  China, Japan, South Korea and India.
- **Regulatory shape — fragmented by jurisdiction, which is itself the opportunity:**
  - 🆕 **China:** moved from voluntary to **mandatory standards for combined driving assistance and
    automated driving** (reported July 2026). One source puts a mandatory **L3/L4 standard referencing the
    UN GTR in effect 1 July 2027 for new models** — ⚠️ unverified, check before quoting. Separately, a
    April 2026 analysis found **no nationwide mandatory AV safety rule** and noted **some municipalities,
    including Beijing, had pulled back** from unfettered autonomous operation: the direction of travel is
    centralisation, and it is mid-flight. **L2 penetration >70% of new passenger vehicles (MIIT).**
  - 🟢 🆕 **China — the standards now have numbers, resolving this file's previous "unverified" note.**
    **GB 44721-2026** covers safety for **Level 3 and Level 4** automated driving systems, issued by
    **MIIT** for **Class M and Class N** vehicles, **effective 1 July 2027** with a reported one-year
    transition period. **GB 47955-2026** covers **combined driver-assistance systems** and is **effective
    1 January 2027** — the earlier and therefore more urgent of the two. China's domestic L3/L4 rules are
    reported as **stricter than the UN GTR baseline**, which reads as Beijing trying to set the
    international benchmark rather than follow it.
  - 🆕 **China adoption, refined:** MIIT reports **L2 assisted-driving penetration above 70%** of new
    passenger vehicles and **urban navigation-assisted driving above 20%** — the second figure is new here
    and is the one that indicates real L2+ city capability rather than highway-only.
  - **Japan:** among the first to legally permit **Level 3** on public roads (Honda Legend); 🆕 **remote
    monitoring is required for all Level 4** vehicles. 🆕 **Level 4 deployments remain tightly bounded by
    operating design domain** — Japan's posture is narrow-and-permitted rather than broad-and-restricted.
  - 🆕 **Japan's AI rules are deliberately non-binding, and they name agents.** The **Phase II AI Basic
    Plan** was adopted as a **non-binding** national AI strategy, and the **AI Business Guidelines v1.2**
    cover governance for **AI agents and physical AI** specifically. For an automotive-agent engagement in
    Japan this is the most directly relevant instrument in the region — and because it is guidance rather
    than law, **conformance is an argument you construct**, which is billable in exactly the way EMEA's is.
  - 🆕 **Rest of APAC, sized honestly:** market analysis positions **Japan** as the automotive-grade safety
    and Tier-1 integration market, **Australia** as import-led (software and features, not platform), and
    **India and South Korea** as higher-percentage growth from smaller bases.
  - 🆕 **South Korea:** the **AI Basic Act took effect 22 January 2026** — transparency duties for
    generative/high-impact AI, safety requirements for frontier models, governance duties for high-impact
    systems in sensitive sectors. Presidential decree and ministry guidelines clarify scope but are
    **interpretive, not legally binding**. Government 2026 automotive budget **~KRW 464.5B (~US$316M)** for
    R&D and infrastructure.
  - 🆕 **India:** **Bharat NCAP (BNCAP)** incentivises camera-based ADAS, and per Mobileye's commentary
    **BNCAP 2.0 will require multiple ADAS features for a high crash-test rating** (~9-month-old source —
    check the current BNCAP text). One market report says **MoRTH is mandating AI-enabled ADAS for
    commercial vehicles from 2026** — ⚠️ not confirmed against an official notification. **AIS 140**
    vehicle-tracking mandates remain the funded, concrete telematics driver. Mobileye calls **2026–2027
    the defining years for ADAS in India**. Domestic SDV platforms exist: **Tata Motors acti.ev and
    Arcade.ev** (OTA + connected), and **Matter's AI-defined platform for electric two-wheelers**
    (Jan 2026).
  - **Vietnam:** **Digital Technology Industry Law**, risk-based, from **2026**.
- **Opportunity — multi-jurisdiction policy layer.** One vehicle programme selling into CN/JP/KR/IN now
  faces four different AI *and* AV regimes, and 🆕 **two of them (Korea's AI Basic Act, China's mandatory
  standards) became binding in 2026 while the UN GTR arrived above all of them.** A policy-as-configuration
  layer — per-market rules evaluated at runtime with an evidence trail — is a genuine product. See P4.
- **Opportunity — AIS 140-compliant telematics** in India built on Traccar (Apache-2.0, 200+ protocols)
  rather than licensing a proprietary stack.
- 🆕 **Opportunity — Korean high-impact-AI governance.** The AI Basic Act's governance track for
  high-impact systems in sensitive sectors covers in-vehicle AI, and the guidelines are interpretive —
  which means the conformity *interpretation* is billable work, exactly as it is in EMEA.
- **Barriers to price in:** uneven frameworks, infrastructure limits in developing markets, and
  data-security/localisation constraints.

### LATAM

**🆕 Added 2026-11-21 — sixth confirmation of the supply gap, and the regulatory answer is now specific.**
- 🔴 **Supply gap, confirmed again and stated as a gap, not as silence.** A region-scoped search
  (`AI automotive LATAM Brazil Mexico 2026 adoption regulation automotive industry`) plus the full
  174-URL shelf audit produced **no LATAM-origin automotive AI repository**. Observed origins across
  this base remain **US, China, Germany, Türkiye, Korea, India**. **This is an informed gap: it was
  searched for and it is absent.** Do not read the absence as "not yet surveyed."
- 🔴 **No AI-specific automotive regulation exists in either major market, and that is now sourced
  rather than assumed:**
  - **Brazil** — **Bill 2,338/2023** passed the Federal Senate and sits in the **Chamber of Deputies**,
    **awaiting the rapporteur's opinion in a special committee as of Jul 2026**. A separate government
    bill, **6,237/2025**, proposes a National System for AI Development, Regulation and Governance.
    ⚠️ One source describes **Oct 2026 Senate amendments adding strict civil liability for high-risk
    automated decision systems**; not corroborated elsewhere — **flagged, not quoted.**
  - **Mexico** — **no AI-specific federal law.** Sources conflict on whether **2026 amendments** count as
    the first binding AI obligations; both readings can hold, since those amendments are not a
    comprehensive law. A Chambers guide states plainly that **there are no specific regulations in
    Mexico governing AI in autonomous vehicles.**
  - **Consequence for an engagement:** LATAM automotive AI runs under **general data-protection,
    consumer and sector rules** — not an AV-specific regime. **That is a lower compliance barrier than
    EMEA and a less certain one than NA.** Say both halves.
- ✅ **The demand side is industrial policy, and it has a name.** Brazil's **Rota 2030 — Mobilidade e
  Logística** (**Decree 9.557/2018**) still anchors industrial and technology requirements around
  **energy efficiency, safety and innovation**, with R&D spend obligations attached. ⚠️ **This is the
  LATAM entry point:** a programme that *requires* qualifying R&D is a budget line that an AI
  engineering engagement can be written against. Regional vehicle regulation is also shaped by
  **Mercosur** trade disciplines (local content, tariffs, model approvals).
- ✅ **The concrete adoption example found this pass is aftermarket retail, not manufacturing:**
  **AI-driven appraisal engines in used-car retail**, offering transparent pricing — reported to raise
  consumer trust and shorten transaction times. **That is reachable with permissively licensed parts
  today** (see `compose/patterns.md`) and does not wait on any legislature.
- **Read the gap as the position.** No local open-source supply, no AV-specific rule, and a funded
  industrial-policy programme is the profile of a region where **a studio that brings the stack is the
  differentiator** — the parts are EMEA/APAC/NA-origin and permissively licensed, so they can be
  assembled and localised rather than invented.

**🆕 Added 2026-11-19 — the supply gap is confirmed a fifth time, and the demand side got more concrete.**
- 🔴 **Supply, restated with the queries:** **eleven** GitHub REST API queries were run this pass
  (automotive agents, AD agents, VLA/E2E, ADAS, SDV, vehicle MCP, dealership, fleet, AUTOSAR/ISO,
  world models, V2X). Observed repository origins: **US, China, Germany, Türkiye, Korea, India.**
  **No LATAM-origin automotive AI repository appeared in any of them.** Fifth consecutive snapshot.
  This is an *informed* gap: the searching was done and the region is absent from the open supply side.
- **What that means for a studio, concretely:** in LATAM, Globant is **not** competing against a local
  open-source ecosystem for automotive AI. There isn't one. The competition is **global vendors selling
  into the region** and **in-house teams at nearshore plants**. First-mover room is real, and the
  cheapest credible first move is to **publish** something — a LATAM-origin permissively licensed
  automotive repository would be the first in this KB's five-pass record.
- 🆕 **Demand, with numbers (market-research sources; figures conflict — quote the range):** LATAM
  **commercial-vehicle telematics** at **USD 197.4M (2023) → USD 374.9M (2028), ~13.7% CAGR**, with
  **Brazil and Mexico the leading markets**, driven by regulatory mandates and cost pressure. A second
  publisher gives **Brazil a 62.3% regional share**, and gives Mexico **USD 1.18B** in one report and
  **USD 1.72B** in another — ⚠️ **the same publisher disagrees with itself; treat all of these as
  directional only.**
- 🆕 **Two regulatory hooks worth checking before a telematics engagement** (both reported, neither
  verified against an official register — do that first):
  1. **Brazil — CONTRAN Resolution 962**, reported to require **emergency-call and stolen-vehicle
     tracking on new models from 2025**. If accurate, this is a *mandated* telematics install base, the
     strongest demand driver in the region.
  2. **Brazil — ANATEL certification** for connected devices with cellular or Bluetooth interfaces.
     A hardware-adjacent compliance step that catches software teams by surprise.
  Also reported: **~500,000 vehicle thefts a year in Brazil** driving telematics-based security and
  recovery demand — ⚠️ unverified.
- **Mexico — the 2026 variable is trade, not technology.** The **USMCA review in July 2026** is named as
  the most consequential policy event of the year, with outcomes ranging from modest modernisation
  (digital-trade provisions, rules-of-origin documentation) to **tighter Chinese-content restrictions
  and revisited automotive value-content thresholds**. The **Bajío** (Guanajuato, Querétaro,
  Aguascalientes, San Luis Potosí) remains the automotive heartland, with **BMW, GM, Honda, Mazda,
  Toyota and Volkswagen** plants. **BYD** has reaffirmed long-term interest but is **reassessing the
  timing of new Mexican plant investment** amid tariff uncertainty, naming **Mexico and Brazil as core
  strategic markets**; one report expected a formal announcement **before January 2026** — status
  unknown. Mexico FDI is reported around **USD 41B**.
  **This is the strongest LATAM engagement thesis in this file: rules-of-origin and regional-content
  traceability as an AI-assisted data problem.** See `compose/patterns.md` → **P8**.
- **AI regulation:** **Brazil's AI Bill 2338** passed the Senate in December 2024 and was **still
  pending in the Chamber of Deputies as of May 2026**. **Mexico has no comprehensive horizontal AI
  law**; its 2026 reforms are **sector-specific** (performer likeness, deepfakes, enforcement), and it
  is described as moving toward a more structured environment. **Neither country has automotive-specific
  AI regulation.** Consequence: in LATAM the binding constraints are **data protection (LGPD) and
  trade**, not AI law — which is why **P5** (LGPD-compliant telematics) and **P8** (USMCA traceability)
  are the two LATAM patterns and why an AI Act-shaped compliance pitch lands flat here.
- 🔴 **Declared gap, unchanged:** no reliable figures exist on how many Brazilian or Mexican automakers
  or suppliers are deploying AI in vehicles or plants. Searched; not found. Any client conversation
  needs primary discovery, not a benchmark.

**🆕 Added 2026-11-13 — the negative finding is now the finding.**
- 🔴 **No named LATAM automotive AI vendor, OEM programme or Tier-1 initiative was found**, running
  `AI automotive LATAM Brazil Mexico 2026 adoption regulation players`. Combined with **five consecutive
  passes finding zero LATAM-origin automotive repositories**, this is no longer plausibly a search
  artefact. **Read it as structural:** LATAM participates in automotive AI as a *manufacturing and
  nearshoring* region, not as a *producer of automotive AI software or IP*. That is precisely the gap a
  Globant LATAM studio is positioned to fill, and it should be pitched as a first-mover position rather
  than as catch-up.
- **Brazil — regulation is moving, by two routes at once:**
  - **PL 2338/2023** passed the **Senate in December 2024**, reached the **Chamber of Deputies on
    17 March 2025**, and appeared in the official database as **"Awaiting Report" on 22 October 2026**.
    Nearly two years in the lower house: **do not scope a client engagement around its passage.**
  - **The faster route is the regulator.** The **ANPD** is the proposed AI overseer *and* has placed
    **artificial intelligence among the 16 items of its 2025–2026 Regulatory Agenda, in Phase 1** — so
    binding obligations may well arrive **via ANPD instruments before the bill passes**. For connected-
    vehicle telemetry this matters more than PL 2338, because **LGPD already applies today**.
- **Mexico — no comprehensive federal AI law; sources conflict on direction.** One describes movement
  *"towards a more structured regulatory environment … even in the absence of a comprehensive horizontal
  AI law"* citing 2026 amendments; another says no comprehensive federal law is enacted with several bills
  pending. The concrete datum: a **national AI bill was introduced in the Senate on 11 February 2026**,
  creating a regulator that **classifies AI systems by risk**. Mexico's automotive weight is assembly and
  export, so **USMCA rules-of-origin traceability (P8) remains the stronger near-term offer than AI
  regulation compliance.**
- 🔴 **One OEM claim, explicitly unverified:** a market report states **Stellantis and Toyota have
  announced that all new Brazilian-assembled passenger cars will ship with at least automatic emergency
  braking by 2027.** Not confirmable against any primary company source from this session. **If true it is
  the largest single ADAS-demand event in the region** — AEB on all new Brazilian-assembled cars — and
  `vision_pilot` ships AEB under Apache-2.0. **Verify before building a pitch on it.** The same report's
  regional shares (e.g. **Brazil at 62.5%**) read as estimates, not audited data.
- 🔴 **Gap:** no **Latin NCAP** requirement detail and no ADAS rule specifics found this pass. Latin NCAP
  is the mechanism most likely to create regional ADAS demand; it deserves a dedicated search next pass.

- 🟡 **The gap is now narrower and better evidenced than in the previous pass — and the most valuable
  finding is a negative one.** Searches run this pass included
  `AI automotive LATAM Brazil Mexico 2026 adoption regulation nearshoring manufacturing`,
  `Brasil regulação inteligência artificial PL 2338 2026 lei aprovada veículos autônomos CONTRAN` and
  `México regulación inteligencia artificial 2026 ley vehículos autónomos NOM automotriz AMIA`
  — i.e. in Portuguese and Spanish, which the previous pass flagged as the missing channel.
- 🆕 **Brazil has no AI law in force.** **PL 2338/2023** passed the **Senate on 10 December 2024** and
  remains in the Câmara dos Deputados, status *"Aguardando Parecer"* in the Special Committee on AI, with
  the latest movement dated **2 September 2026** and rapporteur **Dep. Aguinaldo Ribeiro**. Votes have been
  postponed repeatedly — the cited blockers are the **copyright impasse**, the 2026 electoral calendar, and
  unresolved facial-recognition and environmental-impact questions. A market projection suggests sanction
  in **2027** and entry into force **2028–2029** (an estimate, not a schedule). The text is risk-based,
  EU-AI-Act-inspired, with fines up to **2% of revenue capped at R$50M** per infraction.
- 🆕 **Mexico has no general AI law either.** Sectoral reforms exist (Ley Federal del Trabajo, Ley Federal
  del Derecho de Autor) but no cross-cutting framework; multiple bills sit in committee in the Cámara de
  Diputados plus a multi-party Senate version, one of which would amend **Article 73** of the Constitution
  to give Congress the power to legislate on AI at all. A September 2026 piece says Congress is moving
  toward a general law **late 2026**; an Universidad Anáhuac analysis counts **85 initiatives since April
  2023, 67 still pending**.
- 🟢 🆕 **Brazil has an AV-specific bill this KB had missed: PL 1317/2023.** It would add **licensing,
  reporting and AI governance duties to the Código de Trânsito** (Traffic Code). It is a *different*
  instrument from **PL 2338/2023** (the general AI framework tracked above), it is still before Congress,
  and it is the most likely vehicle for the CONTRAN-level rule this file has been looking for. Meanwhile the
  operative position is unchanged and worth stating to a client in exactly these words: **there is currently
  no specific regulation in Brazil governing the testing or circulation of autonomous vehicles on any type
  of road.** Data duties come from **LGPD** plus **ANPD** normative acts.
- 🆕 **Mexico, with more precision than the previous pass:** there is no specific AI law, and the
  **LFPDPPP does not define AI** at all. Autonomous vehicles fall under **general traffic and consumer
  law**, and **Mexico City's mobility regulations covering car-service platforms make no reference to AI or
  automation.** Regionally, a law-firm review puts **Brazil and Chile furthest along** with regulation still
  at the institutional-study stage.
- 🔴 🆕 **The nearest-term binding rule for a LATAM plant comes from the United States.** The **Connected
  Vehicle Security Act of 2026** was **unanimously approved and advanced by a Senate committee in July
  2026**, and analysis expects US connected-vehicle restrictions to apply to EV imports **assembled in
  Brazil**, Turkey, the EU and Thailand. Mexico's exposure runs through the **USMCA review**, which is
  expected to focus heavily on **China's expanding market presence in Mexico**. **Sell connected-vehicle
  supply-chain and data-provenance compliance in LATAM before AI compliance** — the former has a dated US
  instrument behind it; the latter still has no local legal hook.
- ⚠️ 🆕 **São Paulo has run Level 3 autonomous taxi trials**, with fully self-driving vehicles not yet
  permitted — **source dated 2024**, so treat as historical and re-check before use.
- 🔴 **Still not found, stated explicitly:** no **CONTRAN** resolution on autonomous vehicles in Brazil; no
  **NOM** for autonomous vehicles in Mexico; no AMIA position; **no AI-adoption data for Mexican or
  Brazilian auto plants**. A blog claim of an INAI AI registry from June 2026 could not be verified and
  **should not be used**. Closing this needs Diario Oficial de la Federación, CONTRAN resolutions and
  ANFAVEA/AMIA primary sources — not available through this pass's search channel.
- **What the operative rules actually are, today:** **LGPD** in Brazil (engaged the moment video, audio,
  driver identity, vehicle or location data can identify a person) and **Anatel** certification before
  selling AI-enabled vehicle devices such as dashcams. In Mexico, data protection plus sectoral rules. **An
  AI-specific compliance pitch has no legal hook in LATAM yet; a data-protection one does.**
- 🆕 **The industrial signal is strong and dated.** Mexico removed the **10% auto-parts import tariff for
  five years effective 14 October 2026** (limited to terminal automakers under authorised fiscal-warehouse
  status). FDI was **~$41B in the first three quarters of 2025, +15% YoY**, closing 2025 at a record
  **$40.87B**. ⚠️ **The 2026 USMCA review is the live risk:** analysts expect **higher regional
  value-content thresholds for autos**, and nearshoring that still depends on Chinese sub-components may
  lose duty-free access. The next nearshoring wave is expected to turn on **technology adoption, trade
  compliance and regional integration** rather than labour cost. Brazil is positioning as the region's
  digital-infrastructure destination, with clean-energy/hydrogen manufacturing pulling advanced
  manufacturing demand.
- **Opportunity — manufacturing-side AI in Mexico and Brazil, not retail AV.** The industrial base is real
  and newly tariff-advantaged; AV regulatory demand is absent. The engagement is converting pilots into
  production on the plant floor.
- 🆕 **Opportunity — USMCA rules-of-origin traceability.** Higher RVC thresholds mean component-level
  provenance evidence per vehicle. That is the P3 evidence pipeline aimed at **trade compliance** instead
  of AI compliance, and it is the one LATAM offering with a dated deadline behind it.
- **Opportunity — LGPD-compliant fleet telematics.** Anatel + LGPD give a concrete compliance hook that
  proprietary vendors handle poorly; Traccar self-hosted answers both. See P5.

### Global

**🆕 Added 2026-11-21.**
- **The regional division of labour is now stable enough to plan against, and it is the most useful
  single sentence in this file:** **driving models and cockpit AI are APAC, SDV middleware and the
  compliance apparatus are EMEA, robotaxi operations and dealer retail are North America, and LATAM is
  demand without local supply.** Every pass since 2026-10-15 has reproduced this shape.
- **2026 automotive-AI market size: quote the conflict.** Estimates for 2026 range from **~$5.8B**
  (Precedence Research) to **~$6.5B** (Market Research Future) to **~$9.1B** (Coherent Market Insights)
  — a **1.6× spread between vendors for the same year**. Growth forecasts diverge further. ⚠️ **Never
  cite one of these as *the* number**; cite the range and name the houses.
- **Software-defined vehicle + AI is the consensus frame.** Perforce's 2026 survey reports **70% of
  respondents using AI for SDV optimisation** (predictive maintenance, in-vehicle personalisation).
  ⚠️ Perforce sells automotive software tooling — vendor-surveyed figure, treat as directional.
- **Physical AI moved to domain-specific models.** At **CES 2026** NVIDIA unveiled **Alpamayo**, a
  **10-billion-parameter** model for complex driving scenarios; S&P Global describes an industry shift
  toward **domain-specific models trained on navigation data, vehicle controls and safety rules**
  rather than general-purpose ones. ✅ **Verified first-hand:** the `NVlabs/alpamayo*` family and
  `autowarefoundation/alpamayo-autoware` are in this base, **Apache-2.0, byte-read** — this is the rare
  case where a CES announcement has permissively licensed code behind it.
- **OTA is becoming table stakes with regulation attached** — continuous OTA plus cybersecurity and
  functional-safety requirements (China mandates both from 1 Jul 2026; see APAC).
- **The open-source commons has a clear split that should drive build-vs-adopt:** **perception research
  code is largely frozen** (7 of 9 canonical perception repos dormant >1yr, 1 archived — see
  `repos/foundations.md` Layer F) while **stacks and middleware are actively pushed** (CARLA
  2026-11-21, Autoware 2026-11-20, PythonRobotics 2026-11-16). **Take algorithms from the frozen layer;
  take infrastructure from the live one.**

**🆕 Added 2026-11-19.**
- 🆕 **The first global AV regulation exists.** **UNECE WP.29 approved the Automated Driving System
  Global Technical Regulation by vote of all contracting parties, 22–26 June 2026, Geneva**,
  co-developed by **China, the EU, the UK, the US, Canada and Japan**. Two consequences that matter more
  than the headline: (1) a client's ADS artefact pack now has **one global target** instead of three
  regional ones, so assurance work becomes reusable across regions; (2) **approval is not
  authorisation** — individual countries and jurisdictions still decide where and how driverless
  vehicles may operate, so the **operational-permit layer stays regional** and stays billable.
- **Market size — the spread got worse, not better, and that is the finding.** For *AI in automotive*,
  2026 estimates found this pass: **Market Research Future USD 6.52B**, **Coherent Market Insights
  USD 9.13Bn**, **Precedence Research USD 5.80B**; Grand View projects **USD 14.92B by 2030**. Earlier
  passes recorded USD 27.33B (2026) → USD 78.09B (2030) from another publisher. **These differ by more
  than 4× for the same year.** 🔴 **Never quote a single automotive-AI market number.** Quote adoption
  percentages instead — they come from surveys with stated samples and they describe behaviour a client
  recognises.
- **The adoption numbers that are worth quoting** (sample sizes stated, sources named):
  - **Perforce survey: 70% of industry professionals use AI for SDV optimisation** — predictive
    maintenance, in-vehicle personalisation, adaptive UI.
  - **>57% of surveyed automotive development teams are deploying SDV architectures.**
  - **Cox Automotive: 69% of dealers expect AI to drive revenue growth; 22% of AI users have seen it.**
  - **Spyne (~1,200 dealership executives): AI voice agents top the investment list at 74%.**
  - **Germany, 204 workshops/dealerships: 35% already using AI, 84% see future potential.**
  The shape is consistent across all five: **high intent, low realised value.** That gap is the service
  line — it is a delivery problem, and delivery is what a studio sells.
- 🆕 **CES 2026 set the vocabulary for the year:** NVIDIA unveiled **Alpamayo**, a **10-billion-parameter**
  model for reasoning about complex, unpredictable driving scenarios, and analyses noted OEMs turning to
  **domain-specific automotive language models trained on navigation data, vehicle controls and safety
  rules** rather than general LLMs. Both point the same way: **small, domain-trained, on-device**, which
  is the Mercedes/Liquid AI programme in North America and the design premise of `cockpit-agent-sim` and
  `Lyne-ADAS`.
- 🆕 **"Agents that actuate" is now demonstrable, with a published safety envelope.**
  `aditya-ramabadran/drivingbench_harness_code` (MIT, 63★) runs chat models, API models and trained VLA
  policies against the same MCP interface on a **comma four, a Toyota TSS2 and a Tesla Model 3 HW3**,
  with a **3 m/s default ceiling, a hard 6 m/s cutoff, command expiry, cancellation on any driver
  input**, the agent's `reason` string **logged but never sent to the controller**, and **image age**
  returned on every observation. ⚠️ **No scores are published** — this is evidence that the
  architecture is feasible, **not** evidence that any model drives well.
- 🆕 **Assurance-as-code is the cross-region commercial opening.** Three independent MIT projects in six
  weeks (`automotive-skills-suite` 2,907★/141f, `LionDriver` 65★, `automotive-safety-security-assurance-kit`
  created 2026-11-19) produce ISO 26262 / ISO 21434 / ISO 21448 / ASPICE / AIAG-VDA artefacts as agent
  output. The same deliverable sells into **North America** (safety case for federal AV rulemaking),
  **EMEA** (AI Act + UNECE R151 delta), **APAC** (GTR + China OTA rules) and **LATAM** (nothing
  mandates it, so it sells as export-readiness for suppliers shipping into the other three).
  **One artefact factory, four regional buyers.** See `compose/patterns.md` → **P14**.

Cross-region facts that belong to no single market, and are the reason this file now has a Global
subsection at all.

- 🆕 **An open contract for the dealership layer exists: Auto Agent Protocol** (Apache-2.0 for
  specification, schemas and code; documentation **CC BY 4.0**; **110★**; **v3.1** per README). It covers
  dealer discovery, inventory search, vehicle-fact verification and **consented** customer inquiries over
  **MCP**, **A2A** and **Personal Agent Protocol**, discovered through an **Agent Card**, a **Poppy
  document** and **`llms.txt`** on the dealer domain. Built on — and independent of — Google's A2A
  (Apache-2.0, Linux Foundation). 🔴 **Deployment is unverified:** nothing found this pass establishes how
  many dealerships serve these endpoints. The opportunity is implementing both sides of a published
  contract, not riding an established standard.
- **The UN GTR sits above every regional regime.** Adopted **24 June 2026**, endorsed by **Canada, China,
  the EU, Japan, the UK and the US**. Multi-region work is therefore "map one global baseline onto national
  implementations", and **the national deltas are the billable surface** — with China's GB standards now
  the clearest, and reportedly stricter, delta.
- 🆕 **The open end-to-end model layer is no longer single-vendor.** Apache-2.0 models from the **Autoware
  Foundation** (**AutoE2E v1.0**, tagged 29 Oct 2026, 79.9M params, 184★) and **Alibaba**
  (**Qwen-Drive-1.0**, 4B, 537★) both sit **ahead of Alpamayo 1.5** on AutoE2E's published eight-model
  comparison — which is **not like-for-like** (inputs differ by model). Two consequences: the "teacher
  model" commodity layer now has **three independent suppliers**, so betting a client's architecture on one
  vendor's line is an avoidable risk; and the **vendor-neutral** option (Autoware Foundation, which sells no
  model) is the better reference base for teaching and for a client who must not look captured.
- 🆕 **A vehicle-diagnostics agent category appeared, at 0–8 stars.** Every project is an **MCP server**;
  the physical layer has settled on **ELM327/OBD-II** for consumer work and **J2534** for professional.
  **The plumbing standardised before anyone built the winning agent** — which is the favourable shape of a
  market for a services firm. Detail and licence traps in [`../agents/top.md`](../agents/top.md).
- **Adoption figures, which travel better than market-size figures:** **PwC** 47% → **72% by 2030** for
  advanced technologies across the value chain; **Perforce** 71% implementing AI in vehicles, 57% working
  on SDV architectures, 70% using AI for SDV optimisation (vendor survey); **43% of dealers** already
  deploying AI with a further **47% planning to**.

## Globant positioning

- **Lead with compliance in EMEA, validation in North America, jurisdictional complexity in APAC, and
  trade-plus-manufacturing in LATAM.** The same underlying open-source stack serves all four; the wrapper
  and the buyer differ by region. 🆕 In LATAM, lead with **USMCA traceability and LGPD**, *not* AI
  regulation — because there is none to comply with yet, and claiming otherwise is checkable.
- 🆕 **Own the SDV core, not just the data layer.** Eclipse S-CORE is Apache-2.0, ASIL-B-targeted, shipping
  monthly, VDA-backed with 32 companies, has a commercial distribution behind it — and 111 stars. Near-zero
  consultant mindshare on the thing German OEMs are standardising on is the clearest arbitrage in this KB.
- **Do not compete on models — and 🆕 do not marry one either.** NVIDIA gives Alpamayo away Apache-2.0 and
  calls it a teacher model; as of this pass the **Autoware Foundation** and **Alibaba** also give away
  Apache-2.0 models that **beat Alpamayo 1.5 on the one published open comparison**. Three independent
  suppliers of a free commodity is a stronger argument for Globant's position than one was: the margin is
  in fine-tuning, closed-loop validation, the compliance evidence trail and the human gate — and in being
  **model-agnostic by design**, which is now demonstrable rather than rhetorical.
- **Be the firm that reads licences.** Three of the most attractive vertical bases here are AGPL or LGPL,
  the only live open shop-management tool is GPL-3.0, the leading automotive VQA dataset is non-commercial,
  and 🆕 **Alpamayo's weights are OpenMDW-1.1 while its code is Apache-2.0.** Getting this wrong late is
  expensive; getting it right early is a differentiator a client can verify. 🆕 This pass added three more
  specimens: a J2534 diagnostics server claiming **MIT in prose with no LICENSE file in the repository**, an
  **MIT client for a keyed proprietary data API**, and a protocol whose **documentation is CC BY 4.0 while
  its code is Apache-2.0**. The pattern is consistent enough to be a service line, not an anecdote.

## 🔴 Declared gaps 2026-11-13 — what this pass could not verify

Stated explicitly, because an informed gap is information and silence looks exactly like coverage.

1. **EUR-Lex was not reachable**, so **Regulation (EU) 2026/1744** (the reported *"Digital Omnibus on AI"*,
   dated 8 July 2026, in force 27 July 2026, amending Reg. (EU) 2024/1689) is **reported-unverified**. It
   is the single most consequential unconfirmed item in this file: if real, it changes AI Act scoping for
   every EMEA engagement. **Do not cite it to a client.**
2. **UNECE's own documents were not read**, so the **first WP.29 regulation specifically addressing fully
   driverless ADS, reported adopted 24 June 2026**, is secondary-sourced. A global instrument above the
   regional patchwork deserves a primary read.
3. **The Stellantis/Toyota Brazilian AEB-by-2027 claim is unverified** and comes from a market-research
   page. It would be the largest ADAS-demand event in LATAM if true.
4. **Canadian federal AV/AI regulation: effectively nothing found.** The North America picture in this file
   is a US picture with a Canadian dealer-adoption statistic attached. Named as a gap rather than left to
   look like coverage.
5. **APAC automotive-specific approval rules outside China's GB 44721-2026 were not found** — no L2+/L3
   driving-assistance approval detail for Japan, Korea or India.
6. **Latin NCAP requirements were not found**, despite being the most likely mechanism for regional ADAS
   demand in LATAM.
7. **Market-size figures remain irreconcilable and are getting worse, not better.** This pass saw
   automotive AI 2026 quoted at **US$6.52B** and **US$9.13B** by different firms, both projecting ~22%/yr;
   APAC CAGR at **37.8%** and **25.8%**; North America share at **36.8–40%**; and an APAC share of 56.7%
   that does not reconcile with the North America figures at all because the definitions differ.
   **Use ranges and name the source, or do not use a number.** The adoption and regulation figures in this
   file are far more trustworthy than any market size in it.

---
*Updated 2026-11-13 (previous passes 2026-10-31, 2026-10-26). Figures attributed to their source; conflicts shown rather than resolved.
Market-size numbers come from commercial research marketing pages and are estimates. Regulatory dates should be
confirmed against primary sources (Official Journal, EUR-Lex, UNECE, Federal Register, Diário Oficial, DOF) before
client use — the ⚠️ and 🔴 markers above flag the ones this pass could not verify.*
