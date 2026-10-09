# Ultrasonic Range Finder & Custom Power Architecture

**Author:** Agustin Marmor  
**Context:** UCF EEL3926L Junior Design Class Project (Fall 2026)  
**Core Technologies:** MSP430, TI WEBENCH Power Designer, Electronic Test Equipment, Breadboard Prototyping, Autodesk Fusion 360  

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

### 4. Custom Boost Converter Breakout & PCB Design (Labs 4 & 5)
Designed and validated a custom 2-layer PCB breakout board to supply a stable 3.3V rail.
*   **EDA Toolchain:** Utilized Autodesk Fusion 360 to design the schematic, incorporate a ground plane, and complete the final board layout.
*   **Footprints & Manufacturing:** Imported external surface-mount component footprints via Ultra Librarian and exported standard Gerber manufacturing files.
*   **Board Specifications:** Designed a 2-layer board measuring 21.26 mm × 31.73 mm (0.837 × 1.249 inches).
*   **Regulator BOM:** Implemented a TPS613221A regulator (U1) alongside a 4.7 µH inductor (L1), 22 µF ceramic capacitors (C1, C2), a 1K resistor (R1), and an indicator LED (LED1).

### 5. Hardware Interfacing & MSP430 Pinout Architecture (Lab 6)
Mapped the complete hardware interfacing architecture for the MSP430G2553, distributing power logic, analog sensing, and I2C communication:
*   **Power & Programming:** Core digital logic is powered via DVCC (Pin 1) and grounded through DVSS (Pin 20). Programming utilizes the Spy-Bi-Wire protocol via the TEST (Pin 17) and RST (Pin 16) lines.
*   **Sensor Excitation & Capture:** The HC-SR04 ultrasonic sensor is triggered by an output pulse on P2.1 (Pin 9), and its return echo is captured on P2.0 (Pin 8) using a voltage divider to step down the 5V signal.
*   **Analog & Load Control:** A potentiometer feeds the continuous ADC10 input on A3 (Pin 5). Secondary load control is driven by a BS170 MOSFET switched via P1.5 (Pin 7), with an additional status LED tied to P1.4 (Pin 6).
*   **Display Communication:** The USCI_B0 hardware I2C peripheral drives the LCD display using the UCB0SCL (Pin 14) and UCB0SDA (Pin 15) lines.

### 6. Range Finder Project PCB (Lab 7 - Current Phase)
Currently finalizing the schematic capture and board layout for the main Junior Design project PCB in Fusion 360.
*   Integrating the physical dimensions of the LCD display, ultrasonic sensor, battery holder, and previously designed regulator breakout boards to optimize component placement.
*   Routing traces for the MSP430, BS170 MOSFET, and peripheral sensors over a dedicated ground plane.

## Upcoming Milestones
1.  **Firmware Integration (Lab 8):** Prototyping bare-metal C code on the MSP-EXP430G2ET to interface the ultrasonic sensor and I2C display.
2.  **Fabrication & Assembly (Labs 9 & 10):** Applying solder paste via stencils, utilizing a reflow oven for surface-mount components, and manually soldering through-hole headers.
