---
industry: automotive
region: Global
updated: 2026-10-26
---

# 📈 Trending AI agents & models — Automotive

> **APPEND-ONLY.** Newest dated section on top; history preserved below. Never rewrite earlier sections.

## 2026-10-26

**What moved:** two additions that were missing rather than new — **Alpamayo 2 Super now has a verified
repository row**, and **a second open VLA line (OpenDriveVLA) exists** and had never been recorded here.
Plus one licence correction that matters more than either.

| Agent / model | Repo | Licence | Stars | Why it is trending |
|---|---|---|---|---|
| 🆕 Alpamayo 2 Super | [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | Apache-2.0 | 287 | Open **34B** multi-task AV foundation model — 32B VLM backbone + 2B diffusion expert. The previous pass named it in prose; this is its first verified row. Largest open AV model in this KB. |
| 🆕 OpenDriveVLA | [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | **[AAAI 2026]** end-to-end VLA from an academic group, with a **0.5B checkpoint on Hugging Face** (2025/11/14). First credible open VLA line in this KB that is *not* NVIDIA's, and by far the smallest — which makes on-target work possible. |
| Alpamayo 1.5 | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 (code) · ⚠️ **OpenMDW-1.1 (weights)** | 370 | ↑ from 368. Still the practical entry point and the one the recipes target. **Licence split recorded for the first time — see below.** |
| Alpamayo Recipes | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 217 | ↑ from 205. Recipe set verified: 1 SFT, 1.5 SFT (HF Trainer + DeepSpeed), 1.x RL (Cosmos-RL + GRPO), 1.5 quantization (FP8, NVFP4+FP8). |
| AlpaGym | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 163 | ↑ from 157. Closed-loop RL on AlpaSim. |
| AlpaSim | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Flat at 1.3k (rounded). Open AV simulator released with Alpamayo. |
| WorldEngine | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | ↑ from 520. Stable checkpoints 2026/09/15; post-training via 3DGS reconstruction + RL. |
| openpilot | [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.0k | ↑ from 63.9k — **crossed 64k**. Largest permissive automotive codebase. |
| Alpamayo 1 Nano | [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.1k | ↑ from 2.0k **while deprecated** — stars still accruing to the repository people should no longer start from. Banner: *"no longer under active development … limited maintenance updates."* |

🔴 **Licence correction, carried into `agents/top.md` and `compose/patterns.md` P6:** the Alpamayo 1.5
repository is Apache-2.0, **but its README states the model weights are under `OpenMDW-1.1`.** Every
earlier section of this file recorded Alpamayo 1.5 as plain Apache-2.0. Code licence ≠ weight licence;
read OpenMDW-1.1 before distributing fine-tuned derivatives.

**Negative result, recorded deliberately (sixth consecutive pass):** no automotive-specific *agent
framework* trended. `top open source AI agents automotive 2026 github MIT` and
`github trending automotive AI 2026` returned general-purpose frameworks with no automotive content
(OpenClaw, OpenCode, OpenHands, CrewAI, AutoGPT) plus 0-star unlicensed hobby projects.
`github.com/trending` still offers no automotive filter. See `agents/top.md` → "Verified but NOT usable".

**Method note:** `api.github.com` returns **HTTP 403** for repositories not attached to this session, so
every licence and star figure above was read from the rendered repository page on 2026-10-26, and every
URL was probed with `git ls-remote --symref` the same day.

---

## 2026-10-15

**What moved:** the Alpamayo line. Nothing else in automotive AI changed comparably this period.

| Agent / model | Repo | Licence | Stars | Why it is trending |
|---|---|---|---|---|
| Alpamayo 1.5 | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 | 368 | Current head of NVIDIA's open reasoning-VLA line (Mar 2026). RL-enhanced reasoning + navigation guidance + VQA. |
| AlpaSim | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Open AV simulator released with Alpamayo; fastest-growing of the new NVIDIA automotive repos. |
| Alpamayo Recipes | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 205 | New developer hub; absorbed the SFT/RL scripts from the deprecated `NVlabs/alpamayo`. The place work actually happens now. |
| AlpaGym | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 157 | Closed-loop RL framework on AlpaSim — completes the open post-training loop. |
| WorldEngine | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 520 | Updated Sep 2026 with stable checkpoints. Post-training via 3DGS scene reconstruction + RL. |

**Status change to note:** [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) (Apache-2.0, 2.0k★) now
carries a banner — *"no longer under active development ... limited maintenance updates"* — and redirects
to Alpamayo Recipes. Anyone who started from Alpamayo 1 Nano should migrate.

**Negative result, recorded deliberately:** no automotive-specific *agent framework* trended this period.
Searches (`top open source AI agents automotive 2026 github MIT`, `github trending automotive AI 2026`)
returned general-purpose frameworks (CrewAI, LangGraph, OpenHands, browser-use) with no automotive content,
plus 0-star unlicensed hobby projects. `github.com/trending` offers no automotive filter. See
`agents/top.md` → "Verified but NOT usable".

---

## History — snapshots before 2026-10-15

> ⚠️ **Accuracy note added 2026-10-15:** the snapshot below was produced by an unfiltered keyword scrape.
> Several entries are **not automotive software** — `MotionBastard` (After Effects motion design),
> `git-lanes` (generic git tooling for coding agents), `AirForce-API-Auto-Register-System` (unrelated API
> registration), `video2robot` (general robotics). Several carry `?` or `NOASSERTION` licences, meaning no
> verified grant. Preserved verbatim for trend continuity, **not** as recommendations.


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

