# Solar Panel Array

This document outlines the research, selection, and electrical configuration of the photovoltaic (PV) panels. For all physical mounting, orientation, and performance details, please see the **[Mounting, Ballast & Thermal Management](./mounting_and_ballast.md)** document.

## 1. Panel Specifications

*   **Manufacturer / Model**: AKCOME SK8610HDGDC
*   **Power Rating**: 400W (+/- 3%)
*   **Quantity**: 4

### 1.1 Electrical Parameters (@ STC)
*   **Maximum Power (Pₘₐₓ)**: 400 W
*   **Voltage at Pₘₐₓ (Vₘₚ)**: 38.43 V
*   **Current at Pₘₐₓ (Iₘₚ)**: 10.41 A
*   **Open-Circuit Voltage (Vₒ꜀)**: 45.45 V
*   **Short-Circuit Current (Iₛ꜀)**: 11.13 A
*   **Module Efficiency**: 21.96 %

### 1.2 Mechanical & Operating Parameters
*   **Dimensions**: 1755 × 1038 × 30 mm
*   **Weight**: 22.8 kg
*   **Cell Type**: HJT, 9-BB half-cut
*   **Max System Voltage**: 1500 V DC
*   **NOCT**: 45 ± 2 °C
*   **Temperature Coefficient of Pₘₐₓ**: –0.24 % / °C

### 1.3 Datasheet / Manual
- [Link to datasheet](docs/AKCOME 400W SK8610HDGDC-(166)-(9BB)-(1755-1038-30)-(380-400)-12_D.pdf)

*   **Mounting Note**: While these are bifacial panels, the rear side will not be explicitly used for bifacial gain. However, the frame design ensures good air circulation for cooling, which is beneficial for all panel types.

## 2. Array Layout & Wiring

*   **Electrical Strings**:
    *   The panels are wired in two parallel strings.
    *   Each string consists of two modules wired in series (2S).
    *   This **2S2P** (two in series, two in parallel) configuration provides a balance of voltage and current for the MPPT controller and adds redundancy.
*   **MPPT Input Calculations**:
    *   **Voltage per string (2S)**: The open-circuit voltage (Vₒ꜀) is `2 x 45.45V = 90.9V`. The operating voltage (Vₘₚ) is `2 x 38.43V = 76.86V`. This range is comfortably within the inverter's 55–450 VDC MPPT window.
    *   **Current for array (2P)**: The total operating current (Iₘₚ) is `2 x 10.41A = 20.82A`. This is well under the 110A maximum for the MPPT controller.
*   **Cabling**:
    *   **Type**: 6mm² tinned copper photovoltaic solar cable (Red/Black).