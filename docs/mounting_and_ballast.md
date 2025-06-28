# Mounting, Ballast & Thermal Management

This document outlines the current design, future plans, and conceptual history for the solar array's physical and thermal systems.

---

## 1. Implemented Design (Master Plan)

This section details the current, implemented configuration of the mounting system.

*   **Mounting System**: The chosen hardware is the **[Avoltik Solarpanel Halterung für 4 Module (10°)](https://pv-insel.de/products/avoltik-solarpanel-halterung-for-4-module-komplettset-for-solarmodule-bis-2000-1200-mm)**.
*   **Configuration**: The array is configured with a central North-South ridge. Two panels are tilted 10° to the east, and two panels are tilted 10° to the west.
*   **Ballast**: This is a non-penetrating, ballast-based system. The final ballast weight must be calculated and applied to meet local wind load requirements.
*   **Airflow**: The mounting hardware provides a sufficient air gap (≥10 cm) between the panel backsheets and the container roof, promoting passive convective cooling.
*   **Maintenance**: The 10° tilt is less than ideal for self-cleaning. Panels may require more frequent manual rinsing.

## 2. Contingency Plan (Plan B)

*   **Fallback Configuration**: If the East/West orientation does not meet performance requirements, the mounting hardware can be reconfigured to create two separate south-facing banks with a 23° tilt angle to maximize peak sun capture.

---

## 3. Future Development: Thermal Integration (Future Plan)

This section outlines the concepts for integrating a thermal management system for PV panel cooling and hot water generation. This represents the next potential phase of the project.

### 3.1. PV Panel Cooling

*   **Adopted Concept**: Rear-side cooling. Water will be actively circulated between a backplate and the rear of the PV panels to extract waste heat.
*   **System Integration**: The heated water from the panel cooling loop will be circulated back into the main water ballast tanks, pre-heating the thermal mass.
*   **Rejected Concept**: Front-side water film cooling was rejected due to issues with refraction and mineral deposits.

### 3.2. Hot Water Integration Options

Once the panel cooling loop is established, the heated ballast water can be used to generate domestic hot water. Three primary options are being considered:

*   **Option A: Open Loop Circulation**
    *   Top of ballast tank feeds hot water to the top of a domestic tank. Cold water from the bottom of the domestic tank returns to the bottom of the ballast.
    *   **Pros**: Direct heating, simple plumbing.
    *   **Cons**: Ballast water must be clean, potential for contamination or stagnation.

*   **Option B: Closed Ballast + Heat Exchanger**
    *   Ballast water stays sealed. A heat exchanger (copper coil or external plate) extracts heat for a secondary potable water loop.
    *   **Pros**: Safer, isolated system. Easier to treat ballast loop with antifreeze.
    *   **Cons**: Slightly more complex and expensive.

*   **Option C: Thermosiphon System**
    *   An elevated thermal tank is placed above the ballast. Hot water rises passively from the ballast to the tank, and cold water sinks back down.
    *   **Pros**: Passive (no pump), simple, reliable.
    *   **Cons**: Requires significant height difference, slow transfer rate.

### 3.3. Advanced Concepts: Automated Cooling & Water Replacement

*   **Concept A: Passive Refill**: Use filtered rainwater from barrels to refill the ballast via a float valve when the water is used or dumped.
*   **Concept B: Temperature-Triggered Diverter**: Use a thermostatic valve to switch from the hot water storage loop to a cool rainwater source to actively cool the panels/ballast when they get too hot.
*   **Concept C: Heat Exchanger + Drain**: Use a heat exchanger to heat domestic water, and if the ballast still gets too hot, drain and refill it with cool water.

---

## 4. Initial Ballast Design Concept

This section archives the original baseline design for the water ballast itself, which serves as the foundation for the thermal integration plans.

*   **Purpose**: Provide ~280 kg of weight to anchor solar panel frames without drilling.
*   **Initial Design**: 2 × 200 mm diameter PVC-U UV-resistant pipes, 4 m long, connected in a U-shape.