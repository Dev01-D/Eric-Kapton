# 🖋️ Eric-Kapton: The Ender 3 2D Plotter
[![Klipper](https://img.shields.io/badge/Firmware-Klipper-blue)](https://www.klipper3d.org/)
[![Mainsail](https://img.shields.io/badge/UI-Mainsail-orange)](https://docs.mainsail.xyz/)
[![Hardware](https://img.shields.io/badge/Mainboard-BTT%20SKR%20Pico-red)](https://biqu.equipment/products/btt-skr-pico-v1-0)

A high-precision 2D plotter conversion of a Creality Ender 3 Pro. This project features a complete "gutting" of 3D printing components—**no hotend, no heated bed**—creating a dedicated, lightweight, and silent drawing machine.

---

## 🚀 Highlights
* **Pure Plotter Build:** All heaters and extruders have been removed to reduce weight and complexity.
* **Sensorless Homing:** Utilizing TMC2209 StallGuard on X and Y axes for a sleek build without physical limit switches.
* **UART Communication:** Direct serial connection between the Raspberry Pi Zero 2W and SKR Pico via `/dev/ttyAMA0`.
* **Status Lighting:** Integrated NeoPixel support for visual feedback (currently set to a purple/blue theme).

---

## 🛠️ Hardware Specifications
| Component | Specification |
| :--- | :--- |
| **Printer Model** | Creality Ender 3 Pro |
| **Controller** | [BigTreeTech SKR Pico V1.0](https://biqu.equipment/products/btt-skr-pico-v1-0) |
| **Host** | [Raspberry Pi Zero 2W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/) |
| **Firmware** | Klipper / Mainsail (via KIAUH) |
| **X/Y Drivers** | TMC2209 with Sensorless Homing |
| **Z Endstop** | Physical Switch on Pin `gpio25` |
| **Pen Holder** | [Precision Linear Pen Holder](https://makerworld.com/en/models/2258664-ender-3-precision-linear-pen-holder) |

---

## 📂 Plotter Configuration & Macros
The machine logic is split between `printer.cfg` for motion and `macros.cfg` for plotter-specific workflows.

### **Motion & Homing**
* **X/Y Sensitivity:** Both axes are tuned with a `driver_SGTHRS` of **80** for reliable sensorless homing.
* **Speed:** Optimized for plotting with a `max_velocity` of **250** and `max_accel` of **5000**.
* **Z-Axis:** Repurposed to act as the pen lift with a `position_min` of **-7** to allow for varied surface heights.

### **Essential Macros**
* **`PEN_UP`**: Lifts the pen to **10.0mm**.
* **`PEN_DOWN`**: Lowers the pen to **0.2mm** for drawing.
* **`START_PRINT`**: Homes the machine and moves the toolhead to the center of the bed, waiting **10 seconds** for pen attachment/adjustment.
* **`END_PRINT`**: Gently lifts the pen and slides the bed forward to "present" the finished drawing.

---

## 🔌 UART Wiring Reference
The Raspberry Pi Zero 2W is connected directly to the SKR Pico via the dedicated serial header.



* **Serial Interface:** `/dev/ttyAMA0`
* **Baud Rate:** 250000 (default)

---

## 🔧 Installation
1. Install Klipper via **KIAUH**.
2. Flash the SKR Pico to communicate over **UART**.
3. Deploy the provided `printer.cfg` and `macros.cfg` to your config folder.
4. Calibrate your Z-offset for your specific pen tip using `Z_ENDSTOP_CALIBRATE`.

---

## 🤝 Credits
* **Developer:** Sabitech
* **Firmware:** [Klipper](https://www.klipper3d.org/)
* **Interface:** [Mainsail](https://docs.mainsail.xyz/)
* **Pen Mount:** Design via [MakerWorld](https://makerworld.com/en/models/2258664-ender-3-precision-linear-pen-holder)
