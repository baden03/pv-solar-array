Solar Ballast & Thermal Integration Concepts

This repository documents modular, low-cost, and expandable design ideas for solar panel ballast systems that can double as thermal mass for hot water generation and photovoltaic (PV) panel cooling.

Overview

We started with a simple goal: secure solar panels on a shipping container using water ballast. This led to a series of expanding ideas to maximize efficiency, energy recovery, and sustainable integration.

⸻

Phase 1: Simple Water Ballast System

Purpose: Provide sufficient weight to anchor solar panel mounting frames without drilling into the container roof.

Design:
	•	2 × 200 mm diameter PVC-U UV-resistant pipes, 4 m long
	•	Connected at one end with 90° elbows and about 0.5 m length of 200 mm pvc-u pipe (forming a U-shape)
	•	Mid-point connection(s) with T-connectors and a crossflow brace pipe(s)
	•	Inlet and outlet: garden hose fittings (top fill, bottom drain)
	•	Approx. 280 L of water = ~280 kg ballast

Advantages:
	•	Inexpensive and available materials
	•	Modular and scalable
	•	Stable with distributed weight and bracing

⸻

Phase 2: Hot Water Integration Options

Option A: Open Loop Circulation
	•	Top of ballast tank feeds hot water to the top of a domestic tank
	•	Cold water from the bottom of the domestic tank returns to the bottom of the ballast
	•	Simple pump-driven loop

Pros:
	•	Direct heating
	•	Simple plumbing

Cons:
	•	Ballast water must be clean
	•	Potential contamination or stagnation

Option B: Closed Ballast + Heat Exchanger
	•	Ballast water stays sealed
	•	Heat exchanger (copper coil or external plate) extracts heat
	•	Secondary loop circulates potable water

Pros:
	•	Safer, isolated system
	•	Easier to treat or antifreeze ballast loop

Cons:
	•	Slightly more complex and expensive

Option C: Thermosiphon System
	•	Elevated thermal tank above ballast
	•	Hot water rises passively from ballast to thermal tank
	•	Cold water sinks back to ballast bottom

Pros:
	•	Passive, no pump required
	•	Simple and reliable

Cons:
	•	Height difference required
	•	Slow transfer rate

⸻

Phase 3: Cooling & Water Replacement Concepts

Goal:
	•	Keep solar panels cool
	•	Maintain ballast tanks at optimal thermal transfer
	•	Generate usable hot water

Concept A: Passive Refill via filtered Rainwater
	•	When ballast reaches ~60°C, open overflow to thermal tank
	•	Refill ballast from rainwater barrels via float valve

Concept B: Temperature-Triggered Diverter Valve
	•	Use thermostatic valve to switch from thermal tank loop to cool rainwater source

Concept C: Heat Exchanger + Coolant Drain
	•	Ballast is closed, heated water pumped out to hot tank
	•	Ballast then drained and refilled with cool filtered water

⸻

Phase 4: PV Panel Cooling Concepts

Front-side Cooling (Rejected)
	•	Water film across glass surface
	•	Problems: refraction, mineral deposits, cleaning issues

Rear-side Cooling (Adopted)
	•	Install metal or ploycarbonate backplate behind panel
	•	Water flows between backplate and panel, extracting heat
	•	Water collected and reused or stored

Pros:
	•	No impact on solar output
	•	More efficient heat extraction
	•	Easier flow control and maintenance

⸻

Next Steps
	•	Build and test initial 200mm ballast tank system
	•	Measure thermal performance
	•	Add temperature probes for data
	•	Explore thermosiphon tank or exchanger integration
	•	Iterate based on practical results

---

## Phase 5: Final Design & Mounting Strategy

Based on the initial concepts, the following design has been selected for implementation.

### 5.1 Mechanical & Structural

*   **Mounting System**: The array will be configured in a **10° East/West split**. Two panels will face east at 10°, and two will face west at 10°, with the central ridge running North-South. This setup is designed to provide a broader power generation curve throughout the day.
*   **Mounting Hardware**: The chosen mounting system is the **[Avoltik Solarpanel Halterung für 4 Module (10°)](https://pv-insel.de/products/avoltik-solarpanel-halterung-for-4-module-komplettset-for-solarmodule-bis-2000-1200-mm)**. This is a ballast-based system designed for flat roofs, which aligns with the project goal of avoiding roof penetration.
*   **Fallback Configuration**: If the East/West orientation does not meet performance requirements, the mounting hardware can be reconfigured to create two separate south-facing banks with a 23° tilt angle.
*   **Wind Loading**: The ballast for the Avoltik system must be weighted appropriately to secure the array against local wind conditions.
*   **Air Gap**: The mounting system provides a sufficient air gap between the panel backsheets and the container roof to promote convective airflow.

### 5.2 Thermal Management

*   **PV Cooling**: The rear-side cooling concept has been adopted. Cool water from the ballast system will be actively circulated in a closed loop behind the panels to extract heat.
*   **Insulation**: All plumbing for the cooling loop will be insulated to prevent unwanted heat gain from the ambient environment or reverse heat loss overnight.

### 5.3 Water & Drainage

*   **Self-Cleaning**: The **10° tilt angle is lower** than the ideal >15° for natural self-cleaning. Panels may require more frequent manual rinsing to remove soiling and maintain optimal performance.
*   **Plumbing**: All water lines will be routed beneath the mounting rails to prevent drips or leaks onto the panel surfaces, which could cause soiling or mineral deposits.