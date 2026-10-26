---
industry: automotive
region: Global
updated: 2026-10-26
---

# 🏗️ Foundational repos — Automotive

> The bases to build on. Open licence, active community. Grouped by layer, because "automotive open source"
> is four unrelated stacks that are routinely confused.
> **Verification:** every URL probed with `git ls-remote` on 2026-10-26 — all live. 🔄 = licence and stars
> re-read from the repository page today. ⏸ = URL re-probed today, figures carried from 2026-10-15.

## 🆕 The biggest addition this pass: Eclipse S-CORE

The 2026-10-15 pass covered Kuksa, Ankaios and VSS but **missed the project the German OEM bloc is actually
consolidating on**. Eclipse S-CORE (*Safe Open Vehicle Core*) is the first open-source-based SDV platform
initiative designed against **ASIL-B** functional-safety requirements — a design target, **not** a
certification, and worth stating that way to a client.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🆕🔄 [eclipse-score/score](https://github.com/eclipse-score/score) | Apache-2.0 | 111 | *"Score project main repository."* The platform root. **Release history read from the GitHub releases page today: `v0.7.3` (07 Oct), `v0.7.2` (02 Sep), `v0.7.1` and `v0.7.0` (24 Aug), `v0.6.4` (07 Aug), `v0.6.3` (31 Jul), `v0.6.2` (14 Jul), `v0.6.1` (13 Jul), `v0.6.0` (26 Jun), `v0.5.5` (26 Apr)** — the page shows dates without a year; all ten fall inside the last 12 months, so they are 2026. Cadence is roughly monthly, and it is shipping. |
| 🆕🔄 [eclipse-score/inc_feo](https://github.com/eclipse-score/inc_feo) | Apache-2.0 | 7 | *"Incubation repository for the fixed execution order framework."* Deterministic execution order — the piece that makes a safety argument tractable. Rust (inferred from `Cargo.toml`, not stated on the page). |
| 🆕 [eclipse-score/baselibs](https://github.com/eclipse-score/baselibs) | ⚪ not read this pass | — | Base libraries. Press reporting says a **Baselibs Rust** module arrived with 0.6.0. URL live 2026-10-26; licence not re-read. |
| 🆕 [eclipse-score/communication](https://github.com/eclipse-score/communication) | ⚪ not read this pass | — | Communication layer. URL live 2026-10-26. |
| 🆕 [eclipse-score/itf](https://github.com/eclipse-score/itf) | ⚪ not read this pass | — | Integration test framework — relevant to any ASIL evidence pipeline. URL live 2026-10-26. |
| 🆕 [eclipse-score/process_description](https://github.com/eclipse-score/process_description) | ⚪ not read this pass | — | The project's development process as a repository. For a client building a safety argument, **this is the artefact that matters as much as the code**. URL live 2026-10-26. |
| 🆕 [eclipse-score/module_template](https://github.com/eclipse-score/module_template) | ⚪ not read this pass | — | Template for a conforming S-CORE module — the entry point for contributing a client's own component. URL live 2026-10-26. |

**Project facts worth carrying into a conversation** (secondary sources, see the conflict note below):
Eclipse project page lists **Apache License 2.0** with the standard caveat that some sources/binaries may
carry different terms; **v0.5-alpha was the first public release (Nov 2025)**; **0.6.0 introduced full
dual-language C++ **and** Rust support, including the Ferrocene safety-critical Rust toolchain**; the
Eclipse SDV ↔ **VDA** memorandum expanded to **32 companies (Jan 2026)**; **Hyundai Mobis joined the SDV
Working Group (May 2026)**; and founding member **Qorix** sells a commercial middleware distribution built
on S-CORE — meaning the open project already has a paid-support path a risk-averse OEM can point at.

🔴 **Stated conflict, not resolved:** trade press puts 0.6.0 in **February 2026** and 0.7.0 in **May 2026**;
the **GitHub releases page read today** puts 0.6.0 at **26 Jun** and 0.7.0 at **24 Aug**. The releases page
is the primary source and is preferred here. The Eclipse project page also lists a **v1.0.0 dated
2026-12-14**, which is in the future and should be treated as a plan, not a shipped release — an ETAS
presentation separately says a complete solution is on track for **2028**. Do not quote a single 1.0 date.

## Layer 1 — Simulation & scenarios

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [carla-simulator/carla](https://github.com/carla-simulator/carla) | MIT | 14.5k | *"Open-source simulator for autonomous driving research."* The de facto standard; largest ecosystem. |
| ⏸ [carla-simulator/scenario_runner](https://github.com/carla-simulator/scenario_runner) | MIT | 683 | Traffic-scenario definition and execution engine for CARLA. |
| 🔄 [NVlabs/alpasim](https://github.com/NVlabs/alpasim) | Apache-2.0 | 1.3k | NVIDIA's open AV simulation platform for end-to-end policy development and testing. |
| ⏸ [eclipse-sumo/sumo](https://github.com/eclipse-sumo/sumo) | EPL-2.0 | 4.2k | Microscopic, continuous traffic simulation — city/fleet scale rather than single-vehicle. |
| ⏸ [esmini/esmini](https://github.com/esmini/esmini) | MPL-2.0 | 949 | A basic OpenSCENARIO player — the lightweight way to execute ASAM OpenSCENARIO files in CI. |
| ⏸ [erdos-project/pylot](https://github.com/erdos-project/pylot) | Apache-2.0 | 535 | Modular AD platform running on CARLA and real vehicles. |

## Layer 2 — Perception, datasets & models

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [open-mmlab/mmdetection3d](https://github.com/open-mmlab/mmdetection3d) | Apache-2.0 | 6.6k | Next-generation platform for general 3D object detection. |
| ⏸ [open-mmlab/OpenPCDet](https://github.com/open-mmlab/OpenPCDet) | Apache-2.0 | 5.7k | Toolbox for LiDAR-based 3D object detection. |
| ⏸ [nutonomy/nuscenes-devkit](https://github.com/nutonomy/nuscenes-devkit) | Apache-2.0 | 2.8k | Devkit for the nuScenes dataset. ⚠️ GitHub's sidebar shows no licence name; `LICENSE.txt` was read directly (2026-10-15) and is **Apache-2.0, © 2021 Motional**, no non-commercial clause. The *dataset* carries separate terms. |
| 🔄 [OpenDriveLab/UniAD](https://github.com/OpenDriveLab/UniAD) | Apache-2.0 | 4.8k | Planning-oriented end-to-end AD (CVPR 2023 Best Paper). |
| 🆕🔄 [DriveVLA/OpenDriveVLA](https://github.com/DriveVLA/OpenDriveVLA) | Apache-2.0 | 824 | AAAI 2026 end-to-end VLA, **0.5B checkpoint on Hugging Face** — the small-model option. |

## Layer 3 — Software-defined vehicle (SDV) in-vehicle platform

The layer most relevant to OEM/Tier-1 engagements and the least known outside them. **Read the S-CORE
section above first** — it sits above this stack rather than beside it.

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [COVESA/vehicle_signal_specification](https://github.com/COVESA/vehicle_signal_specification) | MPL-2.0 | 451 | *"Vehicle Signal Specification - standardized way to describe automotive data."* The common vocabulary every project below maps onto. **Start here.** COVESA hosts 100+ companies around it. |
| 🆕 [COVESA/vss-tools](https://github.com/COVESA/vss-tools) | ⚪ not read this pass | — | The tooling that turns a VSS model into generated artefacts. Needed in practice as soon as VSS is adopted; URL live 2026-10-26. |
| 🔄 [eclipse-kuksa/kuksa-databroker](https://github.com/eclipse-kuksa/kuksa-databroker) | Apache-2.0 | 82 | *"A modern in-vehicle VSS server written in RUST."* gRPC, containerisable. Release 0.6.1 (Apr 2026) and a Quarkslab security audit. Low stars ≠ low importance. |
| 🆕 [eclipse-kuksa/kuksa-python-sdk](https://github.com/eclipse-kuksa/kuksa-python-sdk) | ⚪ not read this pass | — | Python client for the Databroker — the fastest way to prototype against VSS signals. URL live 2026-10-26. |
| 🔄 [eclipse-ankaios/ankaios](https://github.com/eclipse-ankaios/ankaios) | Apache-2.0 | 125 | *"Workload and container orchestration for embedded devices like automotive HPCs"* — the "Kubernetes of the car", where real Kubernetes does not fit. |
| 🆕🔄 [eclipse-sdv-blueprints/fleet-management](https://github.com/eclipse-sdv-blueprints/fleet-management) | Apache-2.0 | 27 | **The single most useful new find for engagement work.** A runnable truck-fleet reference wiring **Kuksa CSV Provider → Kuksa Databroker → FMS Forwarder → Eclipse uProtocol → FMS Consumer → InfluxDB → Grafana**, plus an **FMS Server exposing the rFMS API**. A published end-to-end topology instead of an architecture diagram. |
| ⏸ [eclipse-velocitas/cli](https://github.com/eclipse-velocitas/cli) | Apache-2.0 | 6 | CLI for the Velocitas toolchain for containerised in-vehicle apps. Very early; listed for stack completeness. |

## Layer 4 — Vehicle bus / diagnostics (unglamorous, highly reusable)

| Repo | Licence | Stars | Description |
|---|---|---|---|
| 🔄 [commaai/opendbc](https://github.com/commaai/opendbc) | MIT | 3.5k | *"a Python API for your car"* — CAN message definitions for production vehicles. Fastest route to real vehicle signals. |
| ⏸ [cantools/cantools](https://github.com/cantools/cantools) | MIT | 2.3k | CAN bus tools: DBC/KCD parsing, encode/decode, diagnostics. |
| ⏸ [hardbyte/python-can](https://github.com/hardbyte/python-can) | **LGPL-3.0** | 1.6k | CAN support for Python. ⚠️ LGPL — dynamic linking is fine, but flag it in any shipped client deliverable. |

## Licence flags for this industry

- **Permissive, safe to build on:** CARLA, openpilot, Autoware, Apollo, Alpamayo code / Alpamayo 2 /
  AlpaSim / AlpaGym, OpenDriveVLA, WorldEngine, OpenPCDet, mmdetection3d, opendbc, cantools,
  nuscenes-devkit, Kuksa, Ankaios, **Eclipse S-CORE**, the SDV fleet-management blueprint.
- **Weak-copyleft / file-level — usable with care:** VSS and esmini (MPL-2.0), SUMO (EPL-2.0),
  python-can (LGPL-3.0).
- **Strong copyleft — do not put client proprietary code on top without legal sign-off:** Fleetbase and
  OpenRemote (AGPL-3.0), Odoo (LGPL-3.0 core), **OpenAutoCore (GPL-3.0)**. See `verticals/solutions.md`.
- 🆕 **Model weights are licensed separately from code.** Alpamayo 1.5: repo Apache-2.0, **weights
  OpenMDW-1.1**. Never infer the checkpoint's terms from the repository badge.
- **Non-commercial data traps:** DriveLM's language data (CC BY-NC-SA 4.0) and most AV *datasets*.

## Declared channel gap

🔴 **`eclipsesdv.org` could not be fetched this pass** (DNS resolution failure through the available
fetch channel), so S-CORE release notes were read from the **GitHub releases page** plus trade press
instead of the project's own announcements. The GitHub dates above are primary and reliable; the module
contents attributed to 0.6.0 are press-sourced and should be confirmed against the project site when it
is reachable. **`api.github.com` returns HTTP 403 for repositories not attached to this session**, which is
why licences and stars are read from rendered repository pages rather than the API — the same constraint
the 2026-10-15 pass recorded.

---
*Verified 2026-10-26. Every URL in this file probed live via `git ls-remote`. 🔄 figures read today; ⏸ carried from
2026-10-15; ⚪ URL confirmed live but licence/stars deliberately left blank rather than guessed.
See `verticals/solutions.md` for full customisable platforms.*
