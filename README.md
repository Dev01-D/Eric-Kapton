This project transforms a standard Creality Ender 3 into a high-precision 2D plotter using Klipper firmware and a custom pen-mount assembly.
Hardware Specs

    Controller: BigTreeTech SKR Pico (connected via UART)

    Host: Raspberry Pi Zero 2W

    Firmware: Klipper / Mainsail (installed via KIAUH)

    Pen Holder: Precision Linear Pen Holder

Klipper Configuration

To use this as a plotter, I have modified the printer.cfg to optimize for 2D movement.

    Z-Axis as Pen Lift: The Z-axis is configured with specific offsets to ensure "Pen Up" and "Pen Down" positions are consistent.

    Disabled Extruder: To prevent Klipper errors, the extruder is commented out or "dummy" configured.

Software Workflow

    Generate Art: (e.g., Inkscape + EggBot Plugin)

    G-Code Prep: Export as .gcode with Z-height movements instead of extrusion.

    Upload: Use the Mainsail web interface to run the plot.
