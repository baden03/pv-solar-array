# Mounting, Ballast & Thermal Management

We started with a simple goal: secure solar panels on a shipping container using water ballast. This led to a series of expanding ideas to maximize efficiency, energy recovery, and sustainable integration. This document outlines the current implemented design, future plans, and the conceptual history of the project.

---

## 1. Implemented Design (Master Plan)

This section details the current, implemented configuration of the mounting system.

*   **Mounting System**: The chosen hardware is the **[Avoltik Solarpanel Halterung für 4 Module (10°)](https://pv-insel.de/products/avoltik-solarpanel-halterung-fur-4-module-komplettset-fur-solarmodule-bis-2000-1200-mm)**.
*   **Configuration**: The array is configured with a central North-South ridge. Two panels are tilted 10° to the east, and two panels are tilted 10° to the west.
*   **Ballast**: The system uses a modular, non-penetrating water ballast system to anchor the array and support future thermal integration. For full engineering details, see **[Solar Ballast System & Thermal Integration Concepts](./solar_balast.md)**.
*   **Airflow**: The mounting hardware provides a sufficient air gap (≥10 cm) between the panel backsheets and the container roof, promoting passive convective cooling.
*   **Maintenance**: The 10° tilt is less than ideal for self-cleaning. Panels may require more frequent manual rinsing.

## 2. Contingency Plan (Plan B)

*   **Fallback Configuration**: If the East/West orientation does not meet performance requirements, the mounting hardware can be reconfigured to create two separate south-facing banks with a 23° tilt angle to maximize peak sun capture.

---

## 3. Future Development: Thermal Integration (Future Plan)

This section outlines the concepts for integrating a thermal management system for PV panel cooling and hot water generation. This represents the next potential phase of the project.

*   **Ballast System**: For all technical details, see **[Solar Ballast System & Thermal Integration Concepts](./solar_balast.md)**.
*   **PV Panel Cooling**: Rear-side cooling is planned, with water circulated between a backplate and the rear of the PV panels to extract waste heat.
*   **System Integration**: The heated water from the panel cooling loop will be circulated back into the main water ballast tanks, pre-heating the thermal mass.
*   **Hot Water Options**: See the linked ballast document for open loop, closed loop, and thermosiphon integration concepts.

---

## 4. Design History

This document is focused on the mounting and integration overview. For the full evolution of ballast system concepts, see **[Solar Ballast System & Thermal Integration Concepts](./solar_balast.md)**.