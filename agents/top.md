---
industry: automotive
region: Global
updated: 2026-10-31
---

# 🎯 AI agents & models — Automotive

> Open-source AI agents, policies and models for the automotive industry. Focus: MIT / Apache 2.0 / BSD.
> **Verification method this pass (2026-10-31):** `curl -sI` against `github.com` returns **HTTP 403**
> through this session's proxy, so URL existence is proved with `git ls-remote` and licence/star figures are
> read from the rendered repository page. Where a `LICENSE` file mattered it was fetched raw from
> `raw.githubusercontent.com` and read directly — that is how the AutoE2E licence conflict below was settled.
> **`huggingface.co` does not resolve in this session**, so no model-weight licence was verified first-hand
> this pass; every weights claim is labelled as unverified.
>
> **Previous pass method:** every URL below was probed with `git ls-remote --symref` on 2026-10-26
> (all returned a live default ref), and each row marked 🔄 had its licence and star count **re-read from
> the repository page the same day**. Rows marked ⏸ are carried from the 2026-10-15 pass with the URL
> re-verified today but the licence/star figures not re-read — they are labelled rather than silently
> refreshed. No row is a placeholder.

## What changed on 2026-10-31

1. 🆕 **The open end-to-end driving-model field became a race, and NVIDIA is no longer alone at the top.**
   Two Apache-2.0 models that this KB had **no row for** are now verified and shelved:
   **`autowarefoundation/auto_e2e` (AutoE2E v1.0**, released 29 Oct 2026 — two days ago) and
   **`QwenLM/Qwen-Drive-1.0`** (Alibaba, 537★). On AutoE2E's own published KITScenes-Multimodal
   comparison of eight open-weights models, **Qwen Drive 1.0 is first and AutoE2E second — both ahead of
   Alpamayo 1.5**. The reference stack this KB has recommended since July is now mid-table on its
   competitor's benchmark.
2. 🆕 **A vehicle-diagnostics agent layer now exists, built on MCP** — the category this KB has recorded as
   empty for three passes. It is **real but pre-traction** (0–8★, see the new section below), so it is
   shelved as a *watch* category with the star counts stated plainly rather than talked up.
3. 🆕 **The dealership gap has an open contract, even though it still has no open DMS.**
   **Auto Agent Protocol** (`auto-agent-protocol/auto-agent-protocol`, Apache-2.0, 110★, v3.1) specifies
   dealer discovery, inventory, evidence, pricing and consented inquiries over MCP + A2A + PAP. See
   [`../verticals/solutions.md`](../verticals/solutions.md) — it changes the DMS conclusion from
   "integration only" to "integration against a published contract".
4. 🟢 **Licence conflict resolved by reading the file, not the listicle.** A TIER IV executive's LinkedIn
   posts describe AutoE2E as **OpenMDW-1.1**; the repository's `LICENSE` file, fetched raw on 2026-10-31,
   is **verbatim Apache-2.0**, and the README badge agrees. **Apache-2.0 is what this KB records for the
   code.** The weights are a separate question that could not be checked — see the declared gap.
5. ⏸ **openpilot re-read today: MIT, 64.0k★ — unchanged** from 2026-10-26. No star movement to report, which
   is itself worth recording after three passes of steady growth.

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
| 🆕 **AutoE2E v1.0** | [autowarefoundation/auto_e2e](https://github.com/autowarefoundation/auto_e2e) | Apache-2.0 (`LICENSE` file read raw 2026-10-31) | 184 | **Autoware Foundation's camera-first E2E model, first tagged release 29 Oct 2026** — two days before this pass. *"An open-source, camera-first End-to-End driving model for highways, arterial roads and city streets."* **79.9M parameters**, six surround cameras at 10 Hz lifted to a BEV grid, optional map raster, GRU planner emitting **6.4 s of acceleration and curvature**. Three cooperating models: the Reactive model drives; the 1 Hz **World Action** and **Reasoning** models are *in development*. Inference **~76 FPS** (SwinV2-Tiny, feature-concat fusion, RTX 5080, batch 1) — project's own figure. 38 forks. From the Autoware **Robotaxi working group**. |
| 🆕 **Qwen-Drive-1.0** | [QwenLM/Qwen-Drive-1.0](https://github.com/QwenLM/Qwen-Drive-1.0) | Apache-2.0 | 537 | *"An Initial Step towards a Vision-Language Foundation Model for Autonomous Driving."* Alibaba's entry: a **Qwen3.5-4B** VLM with two added modules — a **BEV perception head** (3D detection, occupancy, map segmentation) and a **flow-matching Planning Expert** emitting trajectories. **Leads AutoE2E's own eight-model benchmark** (ADE 0.565 m / FDE 1.397 m @ 3 s). At 4B it sits between OpenDriveVLA (0.5B) and Alpamayo 1.5 (10B) — the middle rung that was missing. 56 forks. Repo states *"Qwen-Drive-1.0 is released under the Apache 2.0 license"* without separately naming the weights; weights are advertised on Hugging Face and ModelScope as `Qwen/Qwen-Drive-1.0-4B`. |
| 🔄 **WorldEngine** | [OpenDriveLab/WorldEngine](https://github.com/OpenDriveLab/WorldEngine) | Apache-2.0 | 528 | Post-training framework for AD: imitation-learn a base policy, mine failure-prone scenarios from real logs, rebuild them with 3D Gaussian Splatting, refine with RL. Stable checkpoints released 2026/09/15. |
| 🔄 **UniAD** | [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | *"[CVPR 2023 Best Paper Award] Planning-oriented Autonomous Driving."* The reference architecture for unified perception→prediction→planning. |
| ⏸ **DriveLM** | [OpenDriveLab/DriveLM](https://github.com/OpenDriveLab/DriveLM) | Apache-2.0 (code) | 1.4k | ECCV 2024 Oral: driving with graph visual question answering. ⚠️ Language **data** is CC BY-NC-SA 4.0 — non-commercial. Code is reusable; the dataset is not. |
| 🔄 **openpilot** | [commaai/openpilot](https://github.com/commaai/openpilot) | MIT | 64.0k | *"An operating system for robotics … upgrades the driver assistance system on 300+ supported cars."* By far the largest permissive automotive codebase. |
| 🔄 **Autoware** | [autowarefoundation/autoware](https://github.com/autowarefoundation/autoware) | Apache-2.0 | 12.2k | *"The world's leading open-source software project for autonomous driving."* ROS 2 based, vendor-neutral foundation governance. |
| 🔄 **Apollo** | [ApolloAuto/apollo](https://github.com/ApolloAuto/apollo) | Apache-2.0 | 26.9k | Baidu's open AV platform; README's current line is **Apollo 11.0**, which *"focuses on the large-scale deployment of functional autonomous vehicles."* ⚠️ Partially open — HD maps and cloud services retained. |

## 🆕 Where the open E2E models actually stand (one published comparison, read first-hand)

From AutoE2E's README on 2026-10-31. All eight models are scored **open-loop**: each predicts the next 3 s
from logged camera frames, compared against the human driver's path. ADE = mean position error over 3 s;
FDE = error at the 3 s point. **Lower is better.**

| Model | ADE @ 3 s | FDE @ 3 s | Note |
|---|--:|--:|---|
| **Qwen Drive 1.0** | **0.565 m** | **1.397 m** | First — but on a **different evaluation setting** (first-of-6-trajectories checkpoint, 202 keyframes). |
| **AutoE2E** (fine-tuned) | 0.744 m | 1.980 m | Second of eight, with only 79.9M parameters. |
| Alpamayo 1.5, SimForge, METEOR | — | — | All three are **behind AutoE2E** on this table. |

🔴 **Do not quote this as a clean ranking.** AutoE2E's README states plainly that **inputs differ by
model** — AutoE2E itself receives an HD map and the route, and the Qwen Drive row uses a different
checkpoint and keyframe set. It is **not like-for-like**. It is still the only published multi-model open
comparison in this field, and it is the vendor-neutral one, since the Autoware Foundation is not selling a
model. Community benchmark coordination runs in **issue #210**; **PRs #220 and #229** (by `atanasko`) added
the Qwen Drive 1.0 and Alpamayo 1.5 evaluation scripts, so the comparison is reproducible rather than
asserted.

## 🆕 Vehicle-diagnostics agents — a new category, and honestly pre-traction

Three passes of this KB recorded *"no permissively-licensed automotive AI agents exist."* That is **no
longer true**, but the correction must be stated with its scale attached: this cluster is **0–8 stars**.
It is a real category with real licences and near-zero adoption. Shelved as **watch items**, not as
recommendations — and listed so the next pass measures movement instead of rediscovering them.

| Agent | Repo | Licence | ★ | Region | What it is |
|---|---|---|--:|---|---|
| 🆕 **Vehicle Diagnostic Assistant** | [castlebbs/Vehicle-Diagnostic-Assistant](https://github.com/castlebbs/Vehicle-Diagnostic-Assistant) | MIT (`LICENSE` read raw; © 2025 Ghislaine and David Robert) | 8 | EMEA | **The most complete reference design in this category.** *"AI agent that connects directly to your car and helps you diagnose issues."* Gradio chat UI → **LangGraph** agent (InMemorySaver checkpointing, UUID sessions) → **MCP server over streamable HTTP / JSON-RPC 2.0** with tools `get_system_status`, `send_elm327_command`, `get_history`. Custom tools include a sandboxed OBD-II formula evaluator, a VIN decoder against the **NHTSA vPIC API**, and repair-tutorial search. Hardware path: WinnerMicro W600-B800 MCU (FreeRTOS + lwIP) → UART 38400 baud → ELM327 → CAN. LLM backend is Nebius (Qwen3-Coder-480B, Llama-3.3-70B, DeepSeek-R1) with Claude also listed. |
| 🆕 **obd2-mcp** | [shoka-jp/obd2-mcp](https://github.com/shoka-jp/obd2-mcp) | MIT (`LICENSE` read raw; © 2026 Sho Kamakura) | 2 | APAC | *"MCP server: let AI assistants read your car via ELM327 — DTCs, live data, freeze frame, VIN."* **Ships a mock vehicle, so it runs with no hardware** — which makes it the cheapest way to put a real vehicle-signal tool in front of a client in a workshop. 0 forks. |
| 🆕 **automotive-ai-skills** | [shoka-jp/automotive-ai-skills](https://github.com/shoka-jp/automotive-ai-skills) | MIT (`LICENSE` read raw) | — | APAC | Companion skill pack to `obd2-mcp` from the same author: diagnostics, maintenance, repair and EV topics for beginners through professional mechanics. Star count not read this pass. |
| 🆕 **Auto Agent Protocol** | [auto-agent-protocol/auto-agent-protocol](https://github.com/auto-agent-protocol/auto-agent-protocol) | **Apache-2.0** (spec, schemas, code) · docs **CC BY 4.0** | 110 | Global | Not an agent — the **contract agents use to reach a dealership**. *"The open automotive contract for MCP, A2A and Personal Agent Protocol: dealer discovery, inventory, evidence, pricing and consented inquiries."* **README describes v3.1** as an additive minor release preserving the published 3.0 contract; AAP 2.x implementations must complete the 3.0 migration first. Discovery works by the dealer domain publishing an Agent Card, a Poppy document and `llms.txt` pointing at live MCP/A2A/PAP endpoints, with the MCP tool catalogue and A2A OpenAPI at versioned `/v3.0/` paths. **By far the highest-starred thing in this section (110★) and the only one with a governance story.** No release tag is shown on the repo page. |

**How to read this section in a client conversation.** The honest framing is that the **plumbing
standardised before the agents arrived**: MCP is settled as the transport (every project above uses it),
and ELM327/OBD-II and J2534 are settled as the physical layer — but **nobody has built the diagnostic
agent that wins**. For Globant that is the favourable shape of a market, not an unfavourable one: the
integration contracts exist and the differentiated product does not.

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
| 🆕 [cyrusdavirusss/j2534-mcp-server](https://github.com/cyrusdavirusss/j2534-mcp-server) | 0 | ⚠️ **README says "MIT"; there is NO `LICENSE` file** — probed `LICENSE`, `LICENSE.md`, `LICENSE.txt` on both `main` and `master`, all **404**, and the sidebar names no licence | **Technically the most interesting agent found this pass and the one that cannot be used.** J2534 PassThru MCP server: adapter control, CAN channels, UDS/OBD-II/KWP2000 requests, DTC lookup, PID decoding; tested on Toyota/Lexus. J2534 is the *professional* diagnostic interface, so this reaches far deeper into a vehicle than the ELM327 projects above. **A licence sentence in a README pointing at a file that does not exist is not a grant.** Identical defect to `mcp-canvas-lms` in the education KB — this is a recurring pattern, not a one-off. Read as a design reference; ask the maintainer to add the file. |
| 🆕 [carvectorio/carvector-mcp](https://github.com/carvectorio/carvector-mcp) | 1 | MIT (client only) | The MIT grant is real but nearly empty: the README states the client *"bundles **no data**"*, that *"every call forwards to the CarVector API, authenticated with your key"*, and that it **exits without `CARVECTOR_API_KEY`**. Free tier 500 requests/month. **This is a proprietary data service with an open client** — correct to exclude from a buildable shelf, and worth naming so the MIT badge does not mislead a future pass. |
| 🆕 [rgy2291929165-boop/vehicle-diagnosis-agent](https://github.com/rgy2291929165-boop/vehicle-diagnosis-agent) | — | not read | EV fault analysis with RAG + LangGraph + MCP **and a human-approval gate** — the same gate pattern this KB recommends, arrived at independently. Snapshot dated **2026-10-19**, but the README calls it a learning project running on **simulated data catalogues**. Not shelvable; the architecture agreement is the signal. |
| [Hemanth-N-code/Connected-Car-AI-Support-Agent](https://github.com/Hemanth-N-code/Connected-Car-AI-Support-Agent) | 0 | **No licence** (README badge: "Academic Evaluation") | Architecturally the most interesting hit — LangGraph state machine, intent routing over CRM + telematics + subscription data, ChromaDB RAG over service manuals, human technician sign-off before any vehicle action. **Read as a design reference; cannot be reused.** Data sources are mock JSON. |
| [JeffreyYu-Dev/Car](https://github.com/JeffreyYu-Dev/Car) | 0 | **No licence** | LLM vehicle diagnostics, small in-car model + large cloud model split. No grant. |
| [DatariusAI/AI-in-Automotive](https://github.com/DatariusAI/AI-in-Automotive) | 0 | **No licence** | Daily-refreshed feed of automotive AI papers/code (self-described as refreshing from arXiv and GitHub). Usable as a *reading* feed, not as code. |

## Licence flags that decide an engagement

- **Clean for a proprietary client deliverable:** openpilot (MIT), Autoware, Apollo code, AlpaSim, AlpaGym,
  Alpamayo *code*, Alpamayo 2, OpenDriveVLA, WorldEngine, UniAD, mmdetection3d, OpenPCDet (all Apache-2.0),
  🆕 **AutoE2E** and 🆕 **Qwen-Drive-1.0** (Apache-2.0), 🆕 **Auto Agent Protocol** (Apache-2.0 spec/schemas/code),
  🆕 `obd2-mcp` / `automotive-ai-skills` / `Vehicle-Diagnostic-Assistant` (MIT).
- 🆕 **Two licence traps that look like grants.** `j2534-mcp-server` claims MIT in prose with **no LICENSE
  file in the repository** (verified 404 on every conventional filename, both branches). `carvector-mcp` is
  genuinely MIT but is a **client for a keyed proprietary API** — the code is free and the data is not.
  Neither is usable as a base; both are easy to mistake for one.
- 🆕 **Model-weight licences are now a separate question from code licences.** Alpamayo 1.5's weights are
  **OpenMDW-1.1**, not Apache-2.0. Read it before distributing fine-tuned derivatives; do not assume the
  repository badge covers the checkpoint.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0), and most AV *datasets*.
  The code licence and the dataset licence are routinely different — check both, every time.
- 🆕 **Documentation can be licensed apart from the spec.** Auto Agent Protocol: Apache-2.0 for
  specification, schemas and code, **CC BY 4.0 for documentation prose**. If a client deliverable
  reproduces the protocol docs, that is the attribution-bearing licence, not Apache-2.0.

## 🔴 Declared gap this pass — model weights could not be verified

**`huggingface.co` does not resolve from this session** (DNS failure, consistent with the proxy's allowed-domain
policy), so **no model-weight licence on this page was read first-hand on 2026-10-31**. This matters more
than usual here, because the KB has already caught one code/weights split (Alpamayo 1.5: repo Apache-2.0,
**weights OpenMDW-1.1**) and because secondary sources make exactly that claim about AutoE2E:

- **AutoE2E:** repository `LICENSE` is **verbatim Apache-2.0** (fetched raw, 2026-10-31) and the README badge
  agrees; a **TIER IV executive's LinkedIn posts** describe the model as released under **OpenMDW-1.1** for
  commercial use. The repo is the primary source for the *code*; the **weights licence is unresolved.**
  Weights live at `huggingface.co/AutowareFoundation/auto_e2e` (`nuplan-epoch-5` and `kitscenes-epoch-5`
  checkpoints, per README links).
- **Qwen-Drive-1.0:** the repo says *"released under the Apache 2.0 license"* but does not separately name
  the weights. Weights are advertised at `Qwen/Qwen-Drive-1.0-4B` on Hugging Face and ModelScope.
- **Action for the next pass:** if Hugging Face remains unreachable, read these model cards through a
  reachable mirror or ask for `huggingface.co` to be added to the session's allowed domains. **Do not ship a
  fine-tuned derivative of either model to a client until the weights licence is read from the model card.**

---
*Verified 2026-10-31 (previous pass 2026-10-26). 🆕 = new this pass. 🔄 = licence and stars re-read from the repository page. ⏸ = URL re-probed
today, licence/stars carried from 2026-10-15. Stars are GitHub's rounded display values.*
