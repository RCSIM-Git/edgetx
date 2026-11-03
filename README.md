# EdgeTX — Open-Source R/C Radio Firmware (RCSIM Full-Duplex CRSF USB-VCP Fork)

[![GitHub release](https://img.shields.io/github/v/release/Edgetx/edgetx)](https://github.com/EdgeTX/edgetx/releases/latest)
[![License: GPL v2](https://img.shields.io/badge/License-GPL_v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)
[![Discord](https://img.shields.io/discord/839849772864503828.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://discord.gg/wF9wUKnZ6H)

> 🌐 **Language / Język:** **English** | [Polski](README_PL.md)

Welcome to **EdgeTX**, the cutting-edge open-source firmware for R/C radio transmitters!

This repository is the **RCSIM development fork** of EdgeTX. It merges upstream EdgeTX with PR **#7630** (*CRSF Trainer over USB-VCP*) and our custom **Full-Duplex Telemetry Mirroring Engine (	elemetrySetMirrorCb)**, allowing radio transmitters (such as the RadioMaster MT12, Pocket, Boxer, TX16S, TX12, and Zorro) to function as low-latency bidirectional CRSF transceivers over a single USB-C cable.

---

## 🚀 RCSIM Special Features: Full-Duplex CRSF USB-VCP

Our modifications (active on branch pr/full-duplex-telemetry-mirror) unlock:
* 🏎️ **Control Input (PC $\rightarrow$ Radio):** Transmit 16 RC channels (100–250 Hz) from your PC Ground Control Station (RCSIM-GCS, sim-racing wheel, pedals, flight yoke) straight into the EdgeTX mixer.
* 🛰️ **Telemetry Output (Radio $\rightarrow$ PC):** Mirror real-time model telemetry (Battery voltage, Link Statistics / RSSI / LQ / SNR, GPS coordinates, IMU attitude) through the USB Virtual COM Port back to the PC for Force Feedback (FFB) and telemetry instrumentation.
* 🔌 **Zero Hardware Adapters:** Standard USB-C cable connection; no external FTDI dongles or trainer cords required.

### Supported Targets & Flash Optimization
- **RadioMaster MT12:** Surface radio target (optimized for cars/boats).
- **RadioMaster Pocket:** 512KB STM32 flash-optimized target (stripped legacy PXX/Heli protocols).
- **RadioMaster Boxer, TX16S/MKII, TX12/MKII, Zorro:** Experimental builds tested and verified.

---

## 🛠️ Building the RCSIM CRSF USB-VCP Firmware

### Prerequisites
* CMake 3.20+
* rm-none-eabi-gcc 10.3+ toolchain
* Python 3.8+ with jinja2 and pillow

### Build Example (RadioMaster MT12):
`ash
git checkout pr/full-duplex-telemetry-mirror
mkdir -p build && cd build
cmake -DPCB=MT12 -DPCBREV=REV00 -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)
`

The resulting binary (mt12-*.bin) can be flashed via the **EdgeTX Bootloader** (holding horizontal trims inward while powering on).

---

## 📖 About Upstream EdgeTX

EdgeTX is the cutting edge of OpenTX, driven by an enthusiastic open-source community:
* **Community:** [EdgeTX Discord](https://discord.gg/wF9wUKnZ6H) | [EdgeTX Discussions](https://github.com/EdgeTX/edgetx/discussions)
* **Official Manual:** [EdgeTX User Guide](https://manual.edgetx.org/)
* **Lua Docs:** [Lua Documentation Site](https://luadoc.edgetx.org/)

---

## 📜 License

Distributed under the [GNU General Public License v2.0 (GPL-2.0)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html).
