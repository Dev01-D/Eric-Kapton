A high-precision 2D plotter conversion of a Creality Ender 3 Pro. This project features a complete removal of 3D printing heaters and extruders to create a dedicated, lightweight, and silent drawing machine controlled via a Raspberry Pi Zero 2W.

🚀 Key Features

    Pure Plotter Architecture: All non-essential 3D printing wiring and the hotend have been removed.

Sensorless Homing: Utilizes TMC2209 StallGuard on the X and Y axes for a sleek build without physical limit switches.

UART Serial Connection: Direct communication between the Pi Zero 2W and SKR Pico via /dev/ttyAMA0.

Custom Status Lighting: Integrated NeoPixel support for visual feedback.

🛠️ Hardware Specifications & Pinout
Component	Configuration
Printer Model	

Creality Ender 3 Pro

Controller	

BigTreeTech SKR Pico v1

Host	

Raspberry Pi Zero 2W

Connection	

UART via GPIO Pins

X/Y Homing	

Sensorless (Virtual Endstops)

Z Endstop	

Physical Switch (GPIO 25)

📂 Plotter Configuration

The machine is optimized for high-speed vector movement with a max_velocity of 250 and max_accel of 5000.

Sensorless Homing Setup

The X and Y axes use TMC2209 drivers with the following sensitivity settings to ensure reliable homing without crashing:

    X-Axis Sensitivity (driver_SGTHRS): 80 

Y-Axis Sensitivity (driver_SGTHRS): 80

Homing Speed: 30 mm/s

Pen Control Macros

The Z-axis acts as the pen lift mechanism. You can find these in macros.cfg:

    PEN_UP: Lifts the pen to 10.0mm.

PEN_DOWN: Lowers the pen to 0.2mm for drawing.

START_PRINT: Homes the machine and moves to the center of the bed.

END_PRINT: Lifts the pen and slides the Y-axis forward to present the finished art.

🔧 Setup & Installation

    Install Klipper: Use KIAUH to install Klipper, Moonraker, and Mainsail.

    Flash Firmware: Flash the SKR Pico for communication over UART (/dev/ttyAMA0).

Deploy Configs: Copy printer.cfg and macros.cfg to your configuration folder.

Calibrate Z: Use Z_ENDSTOP_CALIBRATE to set your initial pen-to-paper height.

🎨 Aesthetics

    NeoPixel: The board LED is configured for a custom purple/blue aesthetic (RED: 0.455, BLUE: 1.0).

Monitoring: Includes temperature sensors for both the SKR Pico MCU and the Pi Zero 2W.

🤝 Credits

    Created by: Sabitech 

Firmware: Klipper

UI: Mainsail

Pen Holder: MakerWorld Design
