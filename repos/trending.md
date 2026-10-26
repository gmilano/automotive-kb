---
industry: automotive
region: Global
updated: 2026-10-26
---

# 📈 Trending repos — Automotive

> **APPEND-ONLY.** Newest dated section on top; history preserved below. Never rewrite earlier sections.

## 2026-10-26

**Method note stands, and is the reason this file reads the way it does:** `github.com/trending` has **no
automotive topic filter**, and the relevant topic pages (`automotive-ai`, `automotive`,
`autonomous-vehicles`, `automotive-data`) surface mostly 0–5 star projects. There is no reliable trending
feed for this industry. What follows is movement in *verified* repos plus vendor/foundation releases — the
only signal available. 🔴 Additional constraint this pass: `api.github.com` returns **HTTP 403** for
repositories not attached to this session, so all figures were read from rendered repository pages.

### The find of this pass: Eclipse S-CORE was invisible to the previous one

| Repo | Licence | Stars | Movement |
|---|---|---|---|
| 🆕 [eclipse-score/score](https://github.com/eclipse-score/score) | Apache-2.0 | 111 | **First appearance in this KB.** The ASIL-B-targeted open SDV platform core. Releases read from the GitHub releases page today: `v0.7.3` (07 Oct), `v0.7.2` (02 Sep), `v0.7.1`/`v0.7.0` (24 Aug), `v0.6.4` (07 Aug), `v0.6.3` (31 Jul), `v0.6.2` (14 Jul), `v0.6.1` (13 Jul), `v0.6.0` (26 Jun), `v0.5.5` (26 Apr) — **ten releases, ~monthly, all 2026.** VDA memorandum now 32 companies; Hyundai Mobis joined May 2026; Qorix ships a commercial distribution on top. |
| 🆕 [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) | Apache-2.0 | 7 | Incubation repo for the fixed execution order framework — deterministic execution, the piece a safety argument needs. 7 stars: design input, not a shippable dependency. |
| 🆕 [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management) | Apache-2.0 | 27 | **Most immediately useful new repo for engagement work.** Runnable topology: Kuksa CSV Provider → Databroker → FMS Forwarder → **Eclipse uProtocol** → FMS Consumer → InfluxDB → Grafana, plus an **rFMS API** server. Replaces ~2 weeks of architecture debate at project start. |

### Movement in tracked repos

| Repo | Licence | Stars | Movement |
|---|---|---|---|
| 🆕 [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | First appearance. AAAI 2026 end-to-end VLA with a **0.5B** Hugging Face checkpoint — the small-model option this KB lacked. |
| 🆕 [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | Apache-2.0 | 287 | First verified row. 34B (32B VLM + 2B diffusion expert). |
| [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.0k | ↑ 63.9k → **64.0k**, crossed 64k. |
| [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.1k | ↑ 2.0k → 2.1k **while deprecated**. |
| [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 217 | ↑ from 205. The hub where Alpamayo work actually happens. |
| [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 163 | ↑ from 157. |
| [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | ↑ from 520. |
| [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 (code) · ⚠️ OpenMDW-1.1 (weights) | 370 | ↑ from 368. **Weight licence recorded for the first time.** |
| [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 82 | ↑ from 80. Release 0.6.1 + Quarkslab audit. Maturity signal despite low stars. |
| [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | MPL-2.0 | 451 | ↑ from 449. COVESA hosts 100+ companies around it. |
| [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios) | Apache-2.0 | 125 | Flat. Workload orchestration for automotive HPCs. |
| [ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) | Apache-2.0 | 26.9k | Flat. README line is now **Apollo 11.0**, *"focuses on the large-scale deployment of functional autonomous vehicles."* |
| [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | Flat. Remains the leading vendor-neutral AV stack. |
| [traccar/traccar](https://github.com/traccar/traccar) | Apache-2.0 | 7.9k | Flat. 200+ device protocols; steady, not spiking. |
| [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Flat (rounded). |

### Stable anchors (re-verified, no significant movement)

[carla-simulator/carla](https://github.com/carla-simulator/carla) MIT 14.5k★ ·
[open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) Apache-2.0 6.6k★ ·
[OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) Apache-2.0 4.8k★ ·
[commaai/opendbc](https://github.com/commaai/opendbc) MIT 3.5k★

### New repos recorded but NOT recommended

Found while re-searching the dealership-management gap. All live on 2026-10-26; none is a usable base.

| Repo | Licence | Stars | Why it is here |
|---|---|---|---|
| [winterautollc/OpenAutoCore](https://github.com/winterautollc/OpenAutoCore) | ⚠️ **GPL-3.0** | 9 | Live independent-repair-shop manager (Python/PyQt6/MySQL). Recorded so the DMS gap is precise: shop managers exist, a DMS does not. GPL blocks proprietary deliverables. |
| [ChanMeng666/Automotive-Repair-Management-System](https://github.com/ChanMeng666/Automotive-Repair-Management-System) | not read | — | The most feature-complete hit — **archived by its owner 2026-07-08**. Recorded as a dead end so it is not rediscovered as a candidate. |
| [dimitar-grigorov/GarageBuddy](https://github.com/dimitar-grigorov/GarageBuddy) | not read | — | ASP.NET Core garage management; README marks features "work in progress". |

---

## 2026-10-15

**Method note first, because it changes how this file should be read:** `github.com/trending` has **no
automotive topic filter**, and the relevant topic pages (`automotive-ai`, `automotive`,
`autonomous-vehicles`, `automotive-data`) surface mostly 0–5 star projects. There is no reliable trending
feed for this industry. The entries below are therefore movements in *verified foundational repos* and
vendor releases, which is the only signal available — not a scraped trending list.

### Movement this period

| Repo | Licence | Stars | Movement |
|---|---|---|---|
| [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | New in 2026; open AV simulation platform for end-to-end policies. Now rivals CARLA in mindshare for policy evaluation. |
| [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.0k | Reached 2.0k★ then was **deprecated** in favour of Alpamayo Recipes / 1.5. |
| [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 520 | Stable checkpoints published Sep 2026. |
| [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 80 | Release 0.6.1 (Apr 2026) + completed Quarkslab security audit — meaningful maturity signal despite low stars. |
| [traccar/traccar](https://github.com/traccar/traccar) | Apache-2.0 | 7.9k | Actively maintained (updated Oct 2026); 200+ device protocols. Steady, not spiking. |
| [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | Stable; remains the leading vendor-neutral AV stack. |

### Stable anchors (no significant movement, listed for reference)

[commaai/openpilot](https://github.com/commaai/openpilot) MIT 63.9k★ ·
[ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) Apache-2.0 26.9k★ ·
[carla-simulator/carla](https://github.com/carla-simulator/carla) MIT 14.5k★ ·
[open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) Apache-2.0 6.6k★ ·
[open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) Apache-2.0 5.7k★ ·
[OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) Apache-2.0 4.8k★ ·
[eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) EPL-2.0 4.2k★ ·
[commaai/opendbc](https://github.com/commaai/opendbc) MIT 3.5k★

---

## History — snapshots before 2026-10-15

> ⚠️ **Accuracy note added 2026-10-15:** the snapshot below was byte-identical to `agents/trending.md` —
> the same scrape written to both files, so it recorded no distinct repo trend. Several entries are not
> automotive software and several have `?` / `NOASSERTION` licences (no verified grant). Preserved verbatim
> for continuity, **not** as recommendations.


> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [MotionBastard](https://github.com/luca1234413/MotionBastard) | MIT | Build AI motion design for After Effects and frontend animations from chat with  | 0 |
| [InterFuser-UI](https://github.com/zubairm8580/InterFuser-UI) | Apache-2.0 | Monitor InterFuser in real time with a Pygame UI for CARLA driving, showing came | 1 |
| [autoware_universe](https://github.com/autowarefoundation/autoware_universe) | Apache-2.0 |  | 1.7k |
| [git-lanes](https://github.com/ferdifi/git-lanes) | MIT | Enable parallel AI coding agents to work on a Git repository with isolated branc | 1 |
| [PCLA](https://github.com/MasoudJTehrani/PCLA) | Apache-2.0 | PCLA: A framework for testing autonomous agents in the CARLA simulator | 77 |
| [robotaxi-tpm-work-samples-](https://github.com/ramika2/robotaxi-tpm-work-samples-) | ? | 🚖 Explore robotaxi pain points through practical work samples focused on produc | 0 |
| [AirForce-API-Auto-Register-System](https://github.com/Nahsen1271/AirForce-API-Auto-Register-System) | Apache-2.0 | 🚀 Automate API registration with the AirForce system, simplifying the process a | 4 |
| [video2robot](https://github.com/ShiroNekoe/video2robot) | NOASSERTION | 🤖 Generate robot motions from video or prompts using an efficient end-to-end pi | 1 |
| [cockpit-agent](https://github.com/SuperdeMan/cockpit-agent) | ? | 面向智能座舱的云边协同 Multi-Agent 系统，支持端侧快意图、云端 LLM 规划、跨域 Agent 编排、车控 VAL 安全执行、HMI 流式交互、语义 | 1 |
| [Deconstructing-BYD-s-Technology-Architecture](https://github.com/vaisakhvenugopal/Deconstructing-BYD-s-Technology-Architecture) | ? | 🚗 Deconstructing BYD's Software-Defined Vehicle (SDV) & AI-DV Strategy. A deepl | 0 |

---
*Pipeline automático — se actualiza cada hora.*

