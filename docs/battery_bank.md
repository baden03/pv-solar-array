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
- **Assembly Steps**:
  - Place the battery cells in the enclosure.
  - Connect the cells in series.
  - Connect the parallel cell in series with the series group.
  - Connect the main positive and negative terminals to the BMS.
  - Connect the BMS to the battery monitor.
  - Connect the main system load to the battery bank.
  - Install the 250A ANL fuse.
  - Connect the wiring to the busbars.
  - Seal the enclosure.

## 5. Maintenance
- **Regular Checks**:
  - Check the battery bank for any signs of damage or leakage.
  - Check the battery bank for any signs of overheating.
  - Check the battery bank for any signs of corrosion.
- **Charging**:
  - Charge the battery bank using a solar charger or a grid-tied inverter.
- **Discharging**:
  - Discharge the battery bank using a grid-tied inverter or a grid-connected load.

## 6. Safety
- **Handling**:
  - Handle the battery bank with care to avoid damage.
  - Handle the battery bank with gloves to avoid skin contact with the battery terminals.
- **Storage**:
  - Store the battery bank in a cool, dry place.
  - Store the battery bank in an upright position.
- **Disposal**:
  - Dispose of the battery bank properly according to local regulations.

## 7. Conclusion
The 24V LiFePO4 battery bank has been designed, assembled, and maintained according to the specifications and guidelines provided in this document. It is now ready for use in the off-grid power system. 