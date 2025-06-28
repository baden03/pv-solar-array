# Solar Panel Array

This document outlines the research, selection, and configuration of the photovoltaic (PV) panels for the solar array mounted on a 20 ft shipping container in Lübeck, Germany.

## 1. Panel Selection

*   **Quantity & Rating**: 4 × 400 W, bifacial PV modules
*   **Mounting Note**: The rear side will not be explicitly used for bifacial gain, but the mounting frames are designed to ensure good air circulation, which is beneficial for all panel types.

## 2. Array Layout & Wiring

*   **Electrical Strings**:
    *   The panels are wired in two parallel strings.
    *   Each string consists of two modules wired in series (2S).
    *   This "2S2P" (two in series, two in parallel) configuration balances voltage and current for the MPPT controller and provides redundancy.
*   **MPPT Input**:
    *   The nominal voltage of each string (~2 × Vmp) sits comfortably within the inverter's 55–450 VDC MPPT range.
    *   The total expected charging current is well under the 110 A MPPT limit.

## 3. Tilt & Orientation

*   **Final Tilt Chosen**: 10° East/West Split
*   **Configuration**: The array is mounted with a central North-South ridge. Two panels are tilted 10° to the east, and two panels are tilted 10° to the west.
*   **Rationale**:
    *   This orientation provides a more consistent power output throughout the day, capturing morning sun on the east-facing panels and afternoon sun on the west-facing panels. This creates a broader, flatter production curve compared to the sharp, narrow peak of a south-facing array.
    *   The chosen mounting hardware, the [Avoltik Solarpanel Halterung](https://pv-insel.de/products/avoltik-solarpanel-halterung-fur-4-module-komplettset-for-solarmodule-bis-2000-1200-mm), is specifically designed for this type of ballast-based, low-angle installation.
    *   **Trade-off**: The 10° tilt is less effective for self-cleaning via rainwater compared to a steeper angle. More frequent manual cleaning may be necessary.
*   **Fallback Configuration**: While the initial setup is East/West, the system is designed with flexibility. If the daily energy yield is insufficient, the hardware can be reconfigured into two separate south-facing banks, and later increasing the angle to 23° tilt, to maximize peak sun capture.

## 4. Expected Performance

The East/West split was chosen to broaden the daily generation window, which is preferable to a sharp midday peak for this system's usage pattern.

| Time of Day | 10° East/West Split (Chosen) | 23° South-Facing (Backup) |
| ----------- | ---------------------------- | --------------------------- |
| Morning     | Moderate peak (east bank)    | Lower output                |
| Midday      | High plateau                 | Sharper, higher peak        |
| Afternoon   | Moderate peak (west bank)    | Tapers off smoothly         |

> **Conclusion:** A 10° East/West split configuration provides a superior daily energy yield profile for the intended use case. While it sacrifices the maximum midday peak and some self-cleaning ability, the extended generation in the morning and afternoon is a worthwhile trade-off.