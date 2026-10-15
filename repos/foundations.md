---
industry: automotive
region: Global
updated: 2026-10-15
---

# 🏗️ Foundational repos — Automotive

> The bases to build on. Open licence, active community, verified 2026-10-15.
> Grouped by layer, because "automotive open source" is four unrelated stacks that are often confused.

## Layer 1 — Simulation & scenarios

| Repo | Licence | Stars | Description |
|---|---|---|---|
| [carla-simulator/carla](https://github.com/carla-simulator/carla) | MIT | 14.5k | Open-source simulator for autonomous driving research. The de facto standard; largest ecosystem. |
| [carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) | MIT | 683 | Traffic scenario definition and execution engine for CARLA. |
| [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | NVIDIA's open AV simulation platform for end-to-end policy development and testing (new in 2026). |
| [eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) | EPL-2.0 | 4.2k | Microscopic, continuous traffic simulation — city/fleet scale rather than single-vehicle. Includes intermodal simulation and scenario-creation tools. |
| [esmini/esmini](https://github.com/esmini/esmini) | MPL-2.0 | 949 | A basic OpenSCENARIO player — the lightweight way to execute ASAM OpenSCENARIO files. |
| [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular AD platform running on CARLA and real-world vehicles. |

## Layer 2 — Perception, datasets & models

| Repo | Licence | Stars | Description |
|---|---|---|---|
| [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | Next-generation platform for general 3D object detection. |
| [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| [nutonomy/nuscenes-devkit](https://github.com/nutonomy/nuscenes-devkit) | Apache-2.0 | 2.8k | Devkit for the nuScenes dataset. ⚠️ GitHub's sidebar shows no licence name; `LICENSE.txt` was read directly and is **Apache License 2.0, © 2021 Motional**, with no non-commercial clause. The *dataset* carries its own separate terms — check those. |
| [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | Planning-oriented end-to-end AD (CVPR 2023 Best Paper). |

## Layer 3 — Software-defined vehicle (SDV) in-vehicle platform

This is the layer most relevant to OEM/Tier-1 engagements and the least known outside them.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | MPL-2.0 | 449 | **Vehicle Signal Specification (VSS)** — the standardised way to describe automotive data. The common vocabulary every SDV project below maps onto. Start here. |
| [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 80 | Modern in-vehicle VSS server written in Rust; gRPC, containerisable, maps low-level signals onto VSS data points. Latest release 0.6.1 (Apr 2026); has had a Quarkslab security audit. Low star count ≠ low importance — it is an Eclipse SDV project split out of `kuksa.val`. |
| [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios) | Apache-2.0 | 125 | Workload and container orchestration **for embedded devices like automotive HPCs** — i.e. the "Kubernetes of the car", where real Kubernetes does not fit. |
| [eclipse-velocitas/cli](https://github.com/eclipse-velocitas/cli) | Apache-2.0 | 6 | CLI for the Eclipse Velocitas toolchain for containerised in-vehicle apps. Very early; listed for completeness of the Eclipse SDV stack. |

## Layer 4 — Vehicle bus / diagnostics (the unglamorous, highly reusable layer)

| Repo | Licence | Stars | Description |
|---|---|---|---|
| [commaai/opendbc](https://github.com/commaai/opendbc) | MIT | 3.5k | "A Python API for your car" — CAN message definitions for production vehicles. The fastest route to reading real vehicle signals. |
| [cantools/cantools](https://github.com/cantools/cantools) | MIT | 2.3k | CAN bus tools: DBC/KCD parsing, encode/decode, diagnostics. |
| [hardbyte/python-can](https://github.com/hardbyte/python-can) | **LGPL-3.0** | 1.6k | Controller-area-network support for Python. ⚠️ LGPL — dynamic linking is fine, but flag it in any shipped client deliverable. |

## Licence flags for this industry

- **Permissive and safe to build on:** CARLA, openpilot, Autoware, Apollo, Alpamayo/AlpaSim/AlpaGym, OpenPCDet, mmdetection3d, opendbc, cantools, nuscenes-devkit, Kuksa, Ankaios.
- **Weak-copyleft / file-level — usable with care:** VSS and esmini (MPL-2.0), SUMO (EPL-2.0), python-can (LGPL-3.0).
- **Strong copyleft / network copyleft — do not put client proprietary code on top without legal sign-off:** Fleetbase and OpenRemote (AGPL-3.0), Odoo (LGPL-3.0 core). See `verticals/solutions.md`.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0) and most AV *datasets*. The code licence and the dataset licence are routinely different — check both.

---
*All 20 URLs above verified reachable on 2026-10-15 via `git ls-remote`; licences and stars read from the
repository pages the same day. See `verticals/solutions.md` for full customisable platforms.*
