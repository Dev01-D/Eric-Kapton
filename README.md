# 🖋️ Eric-Kapton: The Ender 3 2D Plotter
[![Klipper](https://img.shields.io/badge/Firmware-Klipper-blue)](https://www.klipper3d.org/)
[![Mainsail](https://img.shields.io/badge/UI-Mainsail-orange)](https://docs.mainsail.xyz/)
[![Hardware](https://img.shields.io/badge/Mainboard-BTT%20SKR%20Pico-red)](https://biqu.equipment/products/btt-skr-pico-v1-0)

A high-precision 2D plotter conversion of a Creality Ender 3 Pro. This build features a complete "gutting" of 3D printing components—**no hotend, no heated bed**—creating a dedicated, lightweight, and silent drawing machine.

---

## 🚀 Highlights
* [cite_start]**Pure Plotter Build:** All heaters and extruders have been removed to reduce weight and complexity[cite: 8].
* [cite_start]**Sensorless Homing:** Utilizing TMC2209 StallGuard on X and Y axes for a cleaner look without physical limit switches[cite: 8, 9].
* [cite_start]**UART Communication:** Direct serial connection between the Raspberry Pi Zero 2W and SKR Pico via `/dev/ttyAMA0`[cite: 8, 9].
* [cite_start]**Status Lighting:** Integrated NeoPixel support for visual feedback (currently set to a purple/blue theme)[cite: 9].

---

## 🛠️ Hardware Specifications
| Component | Specification |
| :--- | :--- |
| **Printer Model** | [cite_start]Creality Ender 3 Pro [cite: 8] |
| **Controller** | [cite_start][BigTreeTech SKR Pico V1.0](https://biqu.equipment/products/btt-skr-pico-v1-0) [cite: 8] |
| **Host** | [cite_start][Raspberry Pi Zero 2W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/) [cite: 8] |
| **Firmware** | [cite_start]Klipper / Mainsail (via KIAUH) [cite: 8] |
| **X/Y Drivers** | [cite_start]TMC2209 with Sensorless Homing [cite: 8, 9] |
| **Z Endstop** | [cite_start]Physical Switch on Pin `gpio25` [cite: 9] |
| **Pen Holder** | [Precision Linear Pen Holder](https://makerworld.com/en/models/2258664-ender-3-precision-linear-pen-holder) |

---

## 📂 Plotter Configuration & Macros
The machine logic is split between `printer.cfg` for motion and `macros.cfg` for plotter-specific workflows.

### **Motion & Homing**
* [cite_start]**X/Y Sensitivity:** Both axes are tuned with a `driver_SGTHRS` of **80** for reliable sensorless homing[cite: 9].
* [cite_start]**Speed:** Optimized for plotting with a `max_velocity` of **250** and `max_accel` of **5000**[cite: 8, 9].
* [cite_start]**Z-Axis:** Repurposed to act as the pen lift with a `position_min` of **-7** to allow for varied surface heights[cite: 9].

### **Essential Macros**
Detailed macro logic can be found in [`macros.cfg`](https://github.com/Dev01-D/Eric-Kapton/blob/main/Klipper_config/macros.cfg):
* [cite_start]**`PEN_UP`**: Lifts the pen to **10.0mm**[cite: 1].
* [cite_start]**`PEN_DOWN`**: Lowers the pen to **0.2mm** for drawing[cite: 1].
* [cite_start]**`START_PRINT`**: Homes the machine and moves the toolhead to the center of the bed, waiting **10 seconds** for pen attachment/adjustment[cite: 2, 3].
* [cite_start]**`END_PRINT`**: Gently lifts the pen and slides the bed forward to "present" the finished drawing[cite: 3, 4].

---

## 🔧 Installation
1. Install Klipper via **KIAUH**.
2. Flash the SKR Pico to communicate over **UART**.
3. Use the provided `printer.cfg` and `macros.cfg`.
4. [cite_start]Calibrate your Z-offset for your specific pen tip using `Z_ENDSTOP_CALIBRATE`[cite: 10].

---

## 🤝 Credits
* [cite_start]**Developer:** Sabitech [cite: 8]
* **Firmware:** [Klipper](https://www.klipper3d.org/)
* **Interface:** [Mainsail](https://docs.mainsail.xyz/)
* **Pen Mount:** Design via [MakerWorld](https://makerworld.com/en/models/2258664-ender-3-precision-linear-pen-holder)
