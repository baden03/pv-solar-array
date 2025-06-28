# Mounting, Ballast & Thermal Management

This document outlines the final design and conceptual history for the solar array's mounting system. The primary goals are to provide secure, non-penetrating anchoring on a shipping container roof and to integrate a thermal management system for PV panel cooling and potential hot water generation.

---

## 1. Final Mounting Configuration

The system is designed for a 10° East/West orientation to provide a broad, consistent power generation curve throughout the day, which is optimal for the system's usage patterns.

### 1.1. Mechanical & Structural Design

*   **Mounting System**: The chosen hardware is the **[Avoltik Solarpanel Halterung für 4 Module (10°)](https://pv-insel.de/products/avoltik-solarpanel-halterung-for-4-module-komplettset-for-solarmodule-bis-2000-1200-mm)**.
*   **Configuration**: The array is configured with a central North-South ridge. Two panels are tilted 10° to the east, and two panels are tilted 10° to the west.
*   **Ballast**: This is a non-penetrating, ballast-based system. The final ballast weight must be calculated and applied to meet local wind load requirements.
*   **Airflow**: The mounting hardware provides a sufficient air gap (≥10 cm) between the panel backsheets and the container roof, promoting passive convective cooling.
*   **Fallback Plan**: If the East/West orientation does not meet performance requirements, the mounting hardware can be reconfigured to create two separate south-facing banks with a 23° tilt angle to maximize peak sun capture.

### 1.2. Expected Performance Profile

The East/West split was chosen to broaden the daily generation window, which is preferable to a sharp midday peak.

| Time of Day | 10° East/West Split (Chosen) | 23° South-Facing (Backup) |
| ----------- | ---------------------------- | --------------------------- |
| Morning     | Moderate peak (east bank)    | Lower output                |
| Midday      | High plateau                 | Sharper, higher peak        |
| Afternoon   | Moderate peak (west bank)    | Tapers off smoothly         |

### 1.3. System Maintenance
*   **Self-Cleaning**: The 10° tilt angle is less than the ideal >15° for natural self-cleaning via rain. Panels may require more frequent manual rinsing to remove soiling.
*   **Plumbing**: All water lines for the thermal system will be routed beneath the mounting rails to prevent drips or leaks onto the panel surfaces.

---

## 2. Thermal Management System

The secondary function of the ballast system is to act as a heat sink for an active PV panel cooling loop.

*   **Cooling Concept**: The **Rear-side Cooling** concept was adopted. Water will be actively circulated between a backplate and the rear of the PV panels to extract waste heat.
*   **System Integration**: The heated water from the panel cooling loop will be circulated back into the main water ballast tanks, pre-heating the thermal mass.
*   **Insulation**: All plumbing for the cooling loop will be insulated to prevent unwanted heat gain from the ambient environment or reverse heat loss overnight.

---

## 3. Design History & Alternative Concepts

This section archives the initial brainstorming and phased design concepts that led to the final configuration.

### Phase 1: Simple Water Ballast System
*   **Purpose**: Provide sufficient weight to anchor solar panel mounting frames without drilling.
*   **Initial Design**: 2 × 200 mm diameter PVC-U UV-resistant pipes, ~280 L of water.

### Phase 2: Hot Water Integration Options
*   **Option A: Open Loop**: Direct circulation between ballast and domestic tank. (Rejected due to contamination risk).
*   **Option B: Closed Loop + Heat Exchanger**: Safer, isolated system. (Considered viable).
*   **Option C: Thermosiphon**: Passive, no-pump system. (Considered viable but slow).

### Phase 3: Cooling & Water Replacement Concepts
*   Concepts for using rainwater and thermostatic valves to manage ballast water temperature.

### Phase 4: PV Panel Cooling Concepts
*   **Front-side Cooling**: Rejected due to refraction and mineral deposit issues.
*   **Rear-side Cooling**: Adopted for its efficiency and minimal impact on solar output.