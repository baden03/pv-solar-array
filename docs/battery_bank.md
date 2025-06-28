# LiFePO4 Battery Bank

This document details the design, components, and assembly of the LiFePO4 battery bank, based on official cell specifications.

## 1. Objective
The objective of the battery bank is to act as the core energy reservoir for the entire off-grid system. Its primary functions are to:
*   **Store Surplus Energy**: Capture and store all excess solar energy generated during the day that is not immediately consumed by loads.
*   **Provide On-Demand Power**: Deliver stable, reliable power to the inverter during periods of low or no solar generation (e.g., overnight, on cloudy days).
*   **Enable Energy Independence**: Decouple energy generation from consumption, providing a resilient and continuous power source for all connected appliances.

## 2. Cell Specifications

*   **Cell Model**: LEP71H3L7-01
*   **Nominal Voltage**: 3.2V per cell
*   **Typical Capacity**: 320 Ah (@25±2 °C, 1C)

### 2.1 Electrical Characteristics
*   **Operating Voltage Range**: 2.5V – 3.65V per cell
*   **Internal Impedance**: 0.18 ± 0.05 mΩ (at 1 kHz, 40% SOC)
*   **Self-Discharge Rate**: ≤ 3.5% per month
*   **Cycle Life**: ≥ 4000 cycles (to 70% of initial capacity)

### 2.2 Thermal Characteristics
*   **Operating Temperature (Charge)**: 0°C to 65°C
*   **Operating Temperature (Discharge)**: -35°C to 65°C
*   **Storage Temperature**: -20°C to 45°C

### 2.3 Charge & Discharge Protocols
*   **Standard Charge**: 0.5C constant current to 3.65V, then constant voltage until current is ≤ 0.05C.
*   **Standard Discharge**: 0.5C constant current down to 2.5V.
*   **Max Continuous Discharge**: 1C (320A)
*   **BMS Safety Cutoffs**:
    *   Stop charge at > 3.65V or > 65°C.
    *   Stop discharge at < 2.5V or < -30°C.

## 2.4 Datasheet / Manual
- [Link to datasheet](docs/CATL-320Ah-3.2V-LiFePO4-Prismatic-Battery-Cell-Specification-Datasheet.pdf)

## 3. Bank Configuration & Components
*   **Configuration**: 8S1P (8 cells in series)
*   **Nominal System Voltage**: 24V class (25.6V calculated from 8 x 3.2V/cell)
*   **Total Capacity**: ~7.7 kWh (as specified for the bank)
*   **BMS (Battery Management System)**: JK BMS B2A20S20P.
    *   **Key Features**: 2A active balancing, integrated heating relay for low-temperature charging (essential given the 0°C charge limit).
*   **Battery Monitor**: Victron Smart Shunt 300A. It is connected directly to the main negative terminal of the battery bank, with the load/BMS side connected to the shunt's "system minus" terminal.
*   **Overcurrent Protection**: A 250A ANL fuse is installed on the main positive output of the battery bank, between the battery terminal and the main system load.
*   **Wiring**: 2 Gauge (2 AWG) Red and Black Pure Copper Flexible Cable with Tinned Copper Cable Lug Terminal Connectors.
*   **Busbars**:
*   **Enclosure**:

## 4. Assembly
detailed notes on asembly to come.

## 5. Maintenance
have to think about this

## 6. Safety
safty 6th it seems

## 7. Conclusion
The 24V LiFePO4 battery bank has been designed, assembled, and maintained according to the specifications and guidelines provided in this document. It is now ready for use in the off-grid power system. 