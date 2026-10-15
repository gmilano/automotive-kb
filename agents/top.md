---
industry: automotive
region: Global
updated: 2026-10-15
---

# 🎯 AI agents & models — Automotive

> Open-source AI agents, policies and models for the automotive industry. Focus: MIT / Apache 2.0 / BSD.
> Every row below was verified on 2026-10-15: URL reachable (`git ls-remote`), licence and star count read
> from the repository page. No row is a placeholder.

## Headline finding for this pass

**The automotive "AI agent" category is not where the permissively-licensed value is.** Searches for
automotive-specific *agents* return overwhelmingly 0-star, unlicensed hobby projects (see
`## Verified but NOT usable` below). The real, buildable 2026 assets are **driving policies and
vision-language-action (VLA) models** — and the single biggest change since this KB's last pass is
**NVIDIA's Alpamayo family**, Apache-2.0, released January 2026 and iterated through 1.5 and 2.

## Driving policies & VLA models

| Agent / model | Repo | Licence | Stars | What it is |
|---|---|---|---|---|
| **Alpamayo 1.5** | [NVlabs/alpamayo1.5](https://github.com/NVlabs/alpamayo1.5) | Apache-2.0 | 368 | Open 10B reasoning VLA for AVs: RL-enhanced reasoning, navigation guidance, visual question answering. **Current** model line. |
| **Alpamayo 1 Nano** | [NVlabs/alpamayo](https://github.com/NVlabs/alpamayo) | Apache-2.0 | 2.0k | Original 10B reasoning VLA pairing driving trajectories with Chain-of-Causation reasoning. ⚠️ Repo states it is "no longer under active development", limited maintenance only — start from 1.5. |
| **Alpamayo Recipes** | [NVlabs/alpamayo-recipes](https://github.com/NVlabs/alpamayo-recipes) | Apache-2.0 | 205 | Developer hub: ready-to-use recipes for fine-tuning, RL post-training, quantization and deployment. This is the entry point for customising Alpamayo. |
| **WorldEngine** | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 520 | Post-training framework for AD: trains a base policy by imitation, mines failure-prone scenarios from real logs, rebuilds them with 3D Gaussian Splatting, refines with RL. Updated Sep 2026. |
| **UniAD** | [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | CVPR 2023 Best Paper: planning-oriented end-to-end autonomous driving. The reference architecture for unified perception→prediction→planning. |
| **DriveLM** | [OpenDriveLab/DriveLM](https://github.com/OpenDriveLab/DriveLM) | Apache-2.0 (code) | 1.4k | ECCV 2024 Oral: driving with graph visual question answering. ⚠️ Language **data** is CC BY-NC-SA 4.0 — non-commercial. Code is reusable; the dataset is not. |
| **openpilot** | [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 63.9k | "An operating system for robotics"; upgrades the driver-assistance system on 300+ supported cars. By far the largest permissive automotive codebase. |
| **Autoware** | [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | "The world's leading open-source software project for autonomous driving." ROS 2 based. |
| **Apollo** | [ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) | Apache-2.0 | 26.9k | Baidu's open autonomous driving platform. ⚠️ Partially open: core perception/planning released, HD maps and cloud services retained. |

## Perception toolboxes

| Toolbox | Repo | Licence | Stars | What it is |
|---|---|---|---|---|
| **mmdetection3d** | [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | OpenMMLab's next-generation platform for general 3D object detection. |
| **OpenPCDet** | [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| **Pylot** | [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular autonomous driving platform running on CARLA **and real-world vehicles** — useful as a reference modular pipeline. |

## Simulation & closed-loop evaluation for agents

| Tool | Repo | Licence | Stars | What it is |
|---|---|---|---|---|
| **AlpaSim** | [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | Open AV simulation platform for development and testing of end-to-end AV policies. Pairs with Alpamayo. |
| **AlpaGym** | [NVlabs/alpagym](https://github.com/NVlabs/alpagym) | Apache-2.0 | 157 | Reinforcement-learning framework for end-to-end AD policies; runs closed-loop on AlpaSim. |
| **PCLA** | [MasoudJTehrani/PCLA](https://github.com/MasoudJTehrani/PCLA) | Apache-2.0 | 104 | Framework for testing autonomous agents in the CARLA simulator. |

## ⚠️ Verified but NOT usable — do not queue these for a licence probe

These were the top hits for "automotive AI agent" searches. All exist; none can be built on.

| Repo | Stars | Licence state | Why it is excluded |
|---|---|---|---|
| [Hemanth-N-code/Connected-Car-AI-Support-Agent](https://github.com/Hemanth-N-code/Connected-Car-AI-Support-Agent) | 0 | **No licence** (README badge reads "Academic Evaluation") | Architecturally the most interesting hit — LangGraph state machine, intent routing over CRM + telematics + subscription data, ChromaDB RAG over service manuals, human technician sign-off gate before any vehicle action. **Worth reading as a design reference; cannot be reused.** Data sources are mock JSON. |
| [JeffreyYu-Dev/Car](https://github.com/JeffreyYu-Dev/Car) | 0 | **No licence** | LLM vehicle diagnostics, small in-car model + large cloud model split. Implementation of an IEEE paper. No grant. |
| [DatariusAI/AI-in-Automotive](https://github.com/DatariusAI/AI-in-Automotive) | 0 | **No licence** | Daily-refreshed feed of automotive AI papers/code. Usable as a *reading* feed, not as code. |

## Rows removed this pass

The previous table listed five rows, of which **three were not automotive at all** — they were keyword-scrape
artefacts: `BottleNetes` (a Kubernetes resource dashboard), `agentic-factory-hack` (a generic Microsoft
predictive-maintenance hackathon kit) and `ev-charging-optimization` / `REVOL-E-TION` (energy-system
optimisation, belongs in the energy KB). `TaxiSimulatorOnGraph` (MIT, fleet-dispatch research) is genuinely
mobility-adjacent and is retained in `repos/foundations.md` context rather than as an agent.

---
*Verified 2026-10-15. Licence and star figures read from each repository page on that date; stars are
GitHub's rounded display values.*
