# Ultrasonic Range Finder & Custom Power Architecture

**Author:** Agustin Marmor  
**Context:** UCF EEL3926L Junior Design Class Project (Fall 2026)  
**Core Technologies:** MSP430, TI WEBENCH Power Designer, Electronic Test Equipment, Breadboard Prototyping

## Project Overview
This repository contains the documentation, component sourcing data, and power delivery simulations for a custom Ultrasonic Range Finder system developed as part of coursework at the University of Central Florida. The project focuses on designing an isolated, dual-voltage power delivery network driven by synchronous boost regulators to power an HC-SR04 sensor and an I2C HD44780U LCD display controlled via an MSP430G2553 microcontroller.

## Current Progress & Coursework Milestones

### 1. Component Specification & BOM Sourcing (Lab 1)
Established a complete Bill of Materials (BOM) meeting course requirements and footprint constraints for surface-mount manufacturing.
*   **Total Component Count:** 22 items ($143 total budget)
*   **Target Packages:** 0805 and 1206 surface-mount components
*   **Microcontroller:** MSP430G2553 (20-pin TSSOP)

### 2. Power Network Simulation & Calculations (Lab 2)
Validated the power delivery network using Texas Instruments WEBENCH Power Designer and performed hand calculations for power dissipation and thermal limits:
*   **3.3V Logic Rail (TPS613221A):** Simulated 90.1% steady-state efficiency. Calculated and verified a safe junction temperature ($T_j$) of 38.3°C under a 150mA continuous load (well below the 125°C maximum).
*   **5.0V Peripheral Rail (TPS613222A):** Simulated 91.2% efficiency operating at a 983 kHz switching frequency.

### 3. Regulator Prototyping & Bench Testing (Lab 3)
Physically built and tested the 3.3V and 5.0V boost regulator circuits on a breadboard:
*   Verified output voltage regulation under load using laboratory DC power supplies and digital multimeters.
*   Measured peak-to-peak output ripple voltage utilizing an oscilloscope in AC coupling mode.

## Repository Contents
*   `/Documentation`
    *   `EEL3926L_Lab_Manual.pdf` – Official course lab manual detailing specifications and safety rules.
    *   `annotated-Bill_of_Materials.pdf` – Itemized component list and vendor sourcing data.
*   `/Reports`
    *   `WeBench_and_Prototyping_Report.pdf` – Combined lab report containing design calculations, WEBENCH schematics, efficiency plots, and oscilloscope screenshots for both regulators.

## Upcoming Milestones
1.  **PCB Layout (Fusion 360):** Importing Ultra Librarian component footprints and routing copper traces.
2.  **Fabrication & Assembly:** Generating Gerber files, ordering through JLCPCB, applying solder paste via stencils, and reflow soldering.
3.  **Firmware Integration:** Programming the MSP430 in bare-metal C to interface the ultrasonic sensor and LCD display.
