---
industry: automotive
region: Global
updated: 2026-10-26
---

# 🎯 AI agents & models — Automotive

> Open-source AI agents, policies and models for the automotive industry. Focus: MIT / Apache 2.0 / BSD.
> **Verification method this pass:** every URL below was probed with `git ls-remote --symref` on 2026-10-26
> (all returned a live default ref), and each row marked 🔄 had its licence and star count **re-read from
> the repository page the same day**. Rows marked ⏸ are carried from the 2026-10-15 pass with the URL
> re-verified today but the licence/star figures not re-read — they are labelled rather than silently
> refreshed. No row is a placeholder.

## What changed since 2026-10-15

1. 🆕 **`NVlabs/alpamayo2` exists as a repository** — Apache-2.0, 287★, *"Alpamayo 2 Super … an open 34B
   multi-task foundation model"* (32B VLM backbone + 2B diffusion expert). The previous pass mentioned
   Alpamayo 2 in prose but had **no verified row for it**. It now has one.
2. 🆕 **`DriveVLA/OpenDriveVLA`** — Apache-2.0, 824★, AAAI 2026. A second credible open VLA line alongside
   NVIDIA's, from an academic group rather than a vendor. Was missing entirely.
3. 🔴 **Licence correction on Alpamayo 1.5.** The repository is Apache-2.0, **but its README states the
   model weights are under `OpenMDW-1.1`**, not Apache-2.0. The previous pass recorded Apache-2.0 without
   this split. Anyone shipping derived weights must read OpenMDW-1.1 — see the licence flags below.
4. ⬆️ Star movement: openpilot 63.9k → **64.0k**, Alpamayo 1 Nano 2.0k → **2.1k**, alpamayo-recipes
   205 → **217**, AlpaGym 157 → **163**, Alpamayo 1.5 368 → **370**, WorldEngine 520 → **528**.

## Headline finding (unchanged, re-confirmed)

**The automotive "AI agent" category is still not where the permissively-licensed value is.** Repeating
this pass's searches (`top open source AI agents automotive 2026 github MIT`,
`github trending automotive AI 2026`) returned general-purpose agent frameworks with no automotive content
(OpenClaw, OpenCode, OpenHands, CrewAI, AutoGPT) plus 0-star unlicensed hobby projects. The buildable
assets are **driving policies / vision-language-action (VLA) models** and **SDV infrastructure** — and the
infrastructure side moved more than the model side this period (see `repos/foundations.md` → Eclipse S-CORE).

## Driving policies & VLA models

| Agent / model | Repo | Licence | Stars | What it is |
|---|---|---|---|---|
| 🆕🔄 **Alpamayo 2 Super** | [NVlabs/alpamayo2](https://github.com/NVlabs/alpamayo2) | Apache-2.0 | 287 | Open **34B** multi-task AV foundation model: 32B VLM backbone + 2B diffusion expert. The largest open AV model in this KB and the current top of NVIDIA's line. New row this pass. |
| 🔄 **Alpamayo 1.5** | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 (code) · ⚠️ **OpenMDW-1.1 (weights)** | 370 | Open 10B reasoning VLA: RL-enhanced reasoning, navigation guidance, visual question answering. The practical starting point — smaller than Alpamayo 2 and the one the published recipes target. |
| 🔄 **Alpamayo 1 Nano** | [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.1k | Original 10B reasoning VLA pairing driving trajectories with Chain-of-Causation reasoning. ⚠️ Banner under "Important": *"This repository is no longer under active development and will receive only limited maintenance updates."* **Do not start here.** |
| 🔄 **Alpamayo Recipes** | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 217 | The developer hub, and where the work actually happens. Verified recipe set: Alpamayo 1 SFT and 1.5 SFT (HF Trainer + DeepSpeed), 1.x RL post-training (Cosmos-RL + GRPO), and **1.5 quantization (FP8 and NVFP4+FP8 mixed precision)** via the Model Optimizer Toolkit. Plus dataset download/curation and checkpoint-conversion utilities. |
| 🆕🔄 **OpenDriveVLA** | [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | **[AAAI 2026]** End-to-end autonomous driving with a large vision-language-action model. Paper accepted 2025/11/08; a **0.5B checkpoint is published on Hugging Face** (2025/11/14) — by far the smallest open AV VLA here, which makes it the realistic candidate for on-target experiments where Alpamayo needs ≥24 GB VRAM. |
| 🔄 **WorldEngine** | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | Post-training framework for AD: imitation-learn a base policy, mine failure-prone scenarios from real logs, rebuild them with 3D Gaussian Splatting, refine with RL. Stable checkpoints released 2026/09/15. |
| 🔄 **UniAD** | [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | *"[CVPR 2023 Best Paper Award] Planning-oriented Autonomous Driving."* The reference architecture for unified perception→prediction→planning. |
| ⏸ **DriveLM** | [OpenDriveLab/DriveLM](https://github.com/OpenDriveLab/DriveLM) | Apache-2.0 (code) | 1.4k | ECCV 2024 Oral: driving with graph visual question answering. ⚠️ Language **data** is CC BY-NC-SA 4.0 — non-commercial. Code is reusable; the dataset is not. |
| 🔄 **openpilot** | [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.0k | *"An operating system for robotics … upgrades the driver assistance system on 300+ supported cars."* By far the largest permissive automotive codebase. |
| 🔄 **Autoware** | [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | *"The world's leading open-source software project for autonomous driving."* ROS 2 based, vendor-neutral foundation governance. |
| 🔄 **Apollo** | [ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) | Apache-2.0 | 26.9k | Baidu's open AV platform; README's current line is **Apollo 11.0**, which *"focuses on the large-scale deployment of functional autonomous vehicles."* ⚠️ Partially open — HD maps and cloud services retained. |

## Perception toolboxes

| Toolbox | Repo | Licence | Stars | What it is |
|---|---|---|---|---|
| 🔄 **mmdetection3d** | [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | OpenMMLab's next-generation platform for general 3D object detection. |
| ⏸ **OpenPCDet** | [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| ⏸ **Pylot** | [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular AD platform running on CARLA **and real vehicles** — a useful reference modular pipeline. |

## Simulation & closed-loop evaluation for agents

| Tool | Repo | Licence | Stars | What it is |
|---|---|---|---|---|
| 🔄 **AlpaSim** | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | *"Open-source autonomous vehicle simulation platform designed for development and testing of end-to-end AV policies."* Pairs with Alpamayo. |
| 🔄 **AlpaGym** | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 163 | *"Reinforcement-learning framework for end-to-end autonomous-driving policies"*; runs closed-loop on AlpaSim. |
| ⏸ **PCLA** | [MasoudJTehrani/PCLA](https://github.com/MasoudJTehrani/PCLA) | Apache-2.0 | 104 | Framework for testing autonomous agents in the CARLA simulator. |

## ⚠️ Verified but NOT usable — do not queue these for a licence probe

Top hits for "automotive AI agent" searches. All exist; none can be built on. Re-confirmed live 2026-10-26.

| Repo | Stars | Licence state | Why it is excluded |
|---|---|---|---|
| [Hemanth-N-code/Connected-Car-AI-Support-Agent](https://github.com/Hemanth-N-code/Connected-Car-AI-Support-Agent) | 0 | **No licence** (README badge: "Academic Evaluation") | Architecturally the most interesting hit — LangGraph state machine, intent routing over CRM + telematics + subscription data, ChromaDB RAG over service manuals, human technician sign-off before any vehicle action. **Read as a design reference; cannot be reused.** Data sources are mock JSON. |
| [JeffreyYu-Dev/Car](https://github.com/JeffreyYu-Dev/Car) | 0 | **No licence** | LLM vehicle diagnostics, small in-car model + large cloud model split. No grant. |
| [DatariusAI/AI-in-Automotive](https://github.com/DatariusAI/AI-in-Automotive) | 0 | **No licence** | Daily-refreshed feed of automotive AI papers/code (self-described as refreshing from arXiv and GitHub). Usable as a *reading* feed, not as code. |

## Licence flags that decide an engagement

- **Clean for a proprietary client deliverable:** openpilot (MIT), Autoware, Apollo code, AlpaSim, AlpaGym,
  Alpamayo *code*, Alpamayo 2, OpenDriveVLA, WorldEngine, UniAD, mmdetection3d, OpenPCDet (all Apache-2.0).
- 🆕 **Model-weight licences are now a separate question from code licences.** Alpamayo 1.5's weights are
  **OpenMDW-1.1**, not Apache-2.0. Read it before distributing fine-tuned derivatives; do not assume the
  repository badge covers the checkpoint.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0), and most AV *datasets*.
  The code licence and the dataset licence are routinely different — check both, every time.

---
*Verified 2026-10-26. 🔄 = licence and stars re-read from the repository page today. ⏸ = URL re-probed
today, licence/stars carried from 2026-10-15. Stars are GitHub's rounded display values.*
