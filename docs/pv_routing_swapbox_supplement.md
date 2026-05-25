# Supplement — Dual Independent PV Arrays and Battery-Side Auxiliary MPPT Routing

## Purpose

This document supplements:

**[Portable / Hot-Swappable 24 V LiFePO₄ Battery Packs (~100 Ah)](./Portable_24v_swap_boxes.md)**

It defines the **container-side** architecture for:

- two **permanently separated** photovoltaic (PV) arrays and MPPT channels,
- a **main** energy path (main PV → all-in-one MPPT → stationary bank),
- an **auxiliary** energy path (auxiliary PV → dedicated auxiliary MPPT → **battery-side** destination selection),
- and safe extension of that auxiliary charge path to either the **stationary bank (BAB)** or a **portable swap-box**—without reconfiguring PV strings, without live PV transfer switching, and without multiple MPPT units sharing the same PV source.

Direct **battery-to-battery** charging from BAB into a swap-box remains **out of scope** as an intentional energy-transfer method; charge is delivered through **MPPT-regulated** outputs consistent with each battery’s BMS and charge limits.

---

## 1. Design philosophy

Each electrical domain follows the same high-level pattern:

```text
Dedicated PV array → Dedicated MPPT → Selected battery (per routing policy)
```

The design prefers:

- **independent PV domains** (no shared strings, no PV-side “A/B” allocation),
- **independent MPPT domains** (each tracker owns its own array wiring end to end),
- **battery-side routing** for the auxiliary charger output—where currents are regulated and where destination choice is mechanically or logically simplest,
- fewer failure modes than architectures that multiplex strings between trackers,
- straightforward diagnostics (**one array → one MPPT → one conduit of responsibility** prior to battery selection),
- a path toward **SOC-aware automation** without ever automating PV string switching.

The portable swap-box remains a **standalone** battery system (own BMS, own disconnects). When selected on the auxiliary path, it receives charge from the **auxiliary MPPT**, not from a DC jumper from BAB.

---

## 2. Core architecture

### 2.1 Main system

The primary stationary chain is unchanged in concept:

```text
Main PV Array
       │
       ▼
PV isolator (main)
       │
       ▼
All-in-One Inverter / Charger (integrated MPPT)
       │
       ▼
BAB (Big Ass Battery — stationary LiFePO₄ bank)
```

**Assignments:** permanent homeruns from the **main array** to the **main isolator**, then to the **all-in-one PV input**. There is **no** requirement for that wiring to interoperate with the auxiliary array aside from coordinated protection, labeling, and mechanical separation.

---

### 2.2 Auxiliary system

The secondary chain is also **fixed** on the PV side:

```text
Auxiliary PV Array
       │
       ▼
PV isolator (auxiliary)
       │
       ▼
Dedicated Auxiliary MPPT Controller
       │
       ▼
Battery-selection routing system  (battery side)
       ├──► BAB  (stationary bank)
       └──► Portable swap-box (or OFF)
```

**Routing lives after the auxiliary MPPT output**, not in front of it. The auxiliary MPPT **always** sees the **same** PV array terminals; changing the destination does **not** alter string voltage available to that tracker.

---

### 2.3 End-to-end system sketch

Conceptually:

```text
Main PV ──► AIO MPPT ─────────────► BAB ◄────┐
                                              │ (when selected)
Aux PV ──► Aux MPPT ──► A/OFF/B ──────────────┘
                              └──► Swap-Box
```

The branch to BAB duplicates a **regulated charge source** onto a bus that may already receive current from the AIO charger. Section 5 explains why that parallel charging model is acceptable when executed with matched charge policies and coordinated hardware.

---

## 3. Why dedicated arrays (not PV string switching)

Prior concepts considered **moving** PV strings between MPPT inputs using DC transfer switches. That approach is **not** retained.

**Problems with PV-side switching:**

- **MPPT contention:** two controllers must never drive the **same** array concurrently; break-before-make transfer gear must interrupt **PV** under challenging DC arc conditions.
- **Complexity:** per-string Voc/Isc ratings, irradiance transients during transfer, labeling, lockout granularity, and failure analysis all scale poorly.
- **Diagnostics:** intermittent MPPT instability is harder to attribute when strings are multiplexed instead of statically assigned.

**Dedicated arrays:**

- Each MPPT retains a **single, stable** VI source topology.
- Isolation for service is handled with **PV isolators** at each array—not with “moving” strings between chargers.
- **Energy allocation between BAB and portable systems** shifts to controlled **charger outputs** rather than rewiring photovoltaic sources under load.

This trades some panel count flexibility for **predictable behavior**, **cleaner commissioning**, and **simpler future automation**.

---

## 4. Why battery-side switching is preferred here

Battery-side routing (after the auxiliary MPPT) concentrates switching in a **regulated, battery-referenced** environment:

- Auxiliary MPPT output current is bounded by charger behavior and programmed limits.
- Voltage at the switching point is anchored by the **destination battery**, which provides a comparatively **stiff** bus during normal charging (within BMS permissive ranges).
- **Automation** translates to supervised contactors or motorized switches on modest DC bus conductors—equipment classes that are commonplace in marine and off-grid installs—rather than high-voltage string commutators switching near Voc.

Operational clarity improves: operators state **where auxiliary charge is routed**, not **which PV string belongs to whom today**.

---

## 5. Two MPPT controllers charging one battery — technical basis

When the auxiliary output is switched to **BAB**, **both** the all-in-one MPPT and the **auxiliary MPPT** may simultaneously source charge current into the **same physical bank**.

**This is acceptable and conventional** when:

1. Both controllers are programmed for **compatible LiFePO₄ charge voltage targets** for the stationary bank’s architecture (bulk/absorption ceilings, allowable float behavior, temperature compensation policy).
2. **Each path is individually protected** (fusing/breakering appropriate to conductors and charger output capability).
3. **BMS and bank-level rules** tolerate combined charge currents and do not command conditions that contradict either charger’s safe envelope.
4. Paralleling at the battery behaves as **shared CV/CC regulation** mediated by internal cell physics and impedance—the battery absorbs the summed contribution while terminal voltage settles to a coherent operating point absent gross disagreements between controllers.

Large battery banks routinely integrate **alternator chargers**, **solar MPPT**, and **shore chargers** concurrently; **two MPPT units** feeding the same bank differs only by source physics, not fundamentally by instability requirement—provided programmed setpoints converge and conductors are engineered with **summed current** awareness.

### 5.1 Practical coordination notes

- Align **maximum absorption voltage**, **temperature derates**, and **float/disable** preferences between chargers to reduce **push-pull** currents that waste energy at end-of-absorption transitions.
- Document **combined maximum charge acceptance** versus **recommended continuous** conductor ampacity after derating.

When the auxiliary output is routed to the **swap-box**, only that pack’s **BMS and MPPT absorption profile for 24 V-class LiFePO₄** apply; BAB is electrically **not** in the auxiliary output path unless the selector bridges there.

---

## 6. Battery-side routing topology

### 6.1 Manual implementation (conceptual)

A practical structure:

```text
Auxiliary MPPT battery (+) / (−)
        │
        ▼
Manual A/OFF/B battery-rated transfer switch (or equivalently fused selector)
        │
        ├── A → BAB DC charge bus junction (regulated node; coordinated with AIO feeder)
        ├── B → Portable swap-box DC input (connectorized Anderson or approved busbar)
        └── OFF → Auxiliary MPPT unloaded or internal MPPT suppressed per manual
```

**Requirements:**

| Topic | Recommendation |
|--------|----------------|
| Voltage rating | Exceed worst-case bank maximum including temperature and charge spikes |
| Current rating | Exceed auxiliary MPPT maximum sustained output with margin |
| DC breaking | Prefer devices **intended for DC load switching** in that voltage/current class—not AC gear |
| Configuration | Typical **four-pole** mental model when both **+** and **−** are switched for full isolation (**2-pole** minimum if intentionally commoning negatives per permitted topology—validate against fault paths) |

Exact pole count depends on grounding architecture and inverter manual; engineer **explicit return paths**, **fault currents**, and **BMS interruption** compatibly.

### 6.2 Future automation

Relay or contactor banks may replace or augment manual switching while preserving:

- mutually exclusive energized paths (no condition that parallels BAB pack and swap-box through the auxiliary output unless explicitly designed for it—normally **disallowed** without study),
- interlocks that respect **sequences** discussed in §8,
- SOC-driven decisions (§11).

Automation remains **on the battery side** of the auxiliary MPPT—not on the PV feeders.

---

## 7. Operational modes

Operational modes describe **routing intent** behind the auxiliary MPPT—not PV string choreography.

### Mode A — Auxiliary charge to swap-box

```text
Main PV ──► AIO MPPT ──► BAB
Aux PV ──► Aux MPPT ──► Swap-Box
```

**Use:** maintain stationary ESS normally while concentrating auxiliary solar on portable preparation, expedition turnaround, or load-serving packs.

---

### Mode B — Auxiliary charge blended into BAB

```text
Main PV ──► AIO MPPT ──┐
                        ├──► BAB
Aux PV ──► Aux MPPT ───┘
```

**Use:** maximize BAB acceptance when portable charging is deferred; leverages **dual MPPT into one battery** per §5.

Monitor **combined current** acceptance and thermal rise.

---

### Mode C — Auxiliary controller idle / swap-box parked

```text
Main PV ──► AIO MPPT ──► BAB
Aux PV ─► (isolator open) OR MPPT inhibited/output disconnected
```

**Use:** commissioning, swapping portable packs absent a connected target, deliberate curtailment, or sparing auxiliary PV during maintenance windows.

Prefer **opening the auxiliary PV isolator** when auxiliary electrics remain connected but PV input must be inactive—coordinate with auxiliary MPPT documentation for correct startup after re-energization.

---

### Mode D — Isolation / servicing

Either array may be serviced independently:

```text
(Main isolator OPEN) → Main PV dark; AIO input safe for work per LOTO procedures
(Auxiliary isolator OPEN) → Auxiliary PV dark
```

Maintain **dual labeling** (**MAIN** vs **AUX**) on isolators and MPPT enclosures.

---

## 8. Switching sequence and safety considerations

### 8.1 Commissioning precedence

Industry practice and many charge-controller manuals converge on conservative ordering:

1. **Verify** conductors, fuses/breakers, polarity, grounding/bonding assumptions, transfer switch positioning, **OFF** verification.
2. **Connect battery** terminals at each MPPT that requires battery sensing for operation (consult manuals—some auxiliary units permit PV-first with explicit limits; defer to manufacturer guidance).
3. **Energize PV** beginning with isolation devices **CLOSED**, MPPT observing correct Voc within limits.

Deviation may void warranty or cause **input overvoltage** transients absent battery clamping behaviors.

---

### 8.2 Changing battery destination mid-operation

Changing the auxiliary **A/OFF/B** routing while photovoltaic energy is converting:

- **Assume that interrupting auxiliary MPPT output** may coincide with nonzero MPPT inductor/filter states and battery loop inductance—inrush or voltage excursions can arise if energy cannot freewheel per internal MPPT protections.
- **Preferred:** taper auxiliary PV input (**open auxiliary isolator**), allow MPPT ramp-down/de-energizing per manual, reposition selector to new destination (**OFF** intermediary if break-before-make), then restore PV—in order dictated by instrumentation and audible checks for arcing/abnormal buzzing.

Treat **routing changes** akin to breaker operations on an active charging bus: deliberate, paced, observable.

Never parallel BAB and swap-box inadvertently through sloppy selector wiring; verify **exclusive** auxiliary output continuity per position.

---

## 9. Auxiliary MPPT requirements

Independent PV demands a unit sized for **its** array—not for split-string duty.

| Feature | Requirement |
|---------|--------------|
| LiFePO₄ charge profiles | Required for whichever destination dominates planned use (**or** BAB profile when BAB targeting is dominant) |
| 24 V battery support | Required when swapping output targets include ~24 V-class LiFePO₄ portable packs |
| Input voltage envelope | Shall exceed **cold Voc** auxiliary array aggregate with NEC/local margin policy |
| Current handling | Shall exceed auxiliary **Imp × string factor × safety multiplier** conductor-limited upstream |
| Environment | IP class suitable for enclosure location; marine derating consideration if aboard |
| Remote shutdown / inhibition | Prefer capability if automation overlays later |

Programming **dual personality** (charging BAB vs charging portable) may entail **dual parameter sets**, **password-protected profile banks**, or **operator checklist** swaps—prevent silent mis-absorption transitions.

---

## 10. Main vs auxiliary PV hardware discipline

Both arrays independently require:

| Element | Recommendation |
|---------|----------------|
| PV isolator | Lockable, conspicuously labeled, DC-rated Voc/Isc class |
| Conductor routing | Maintain separation discipline; accidental cross-tie defeats architectural simplification assumptions |
| Surge protection / bonding | Harmonize with grounding plan and NEC/locale |

**Do not**:

- splice auxiliary homeruns into main array combiners intending “temporary experimentation” without redoing labeling and protections,
- jumper MPPT PV inputs together,
- retrofit mid-string taps for third loads without restructuring design.

---

## 11. Future automation roadmap (battery-centric)

Recommended evolution:

| Phase | Capability |
|-------|-------------|
| **Manual** | A/OFF/B selector supervised; SOC noted from shunts/BMS |
| **Semi-automatic** | Contactor sequencing with PLC/ESP/Home Assistant interlocks enforcing delay between opens/closes |
| **Automated SOC policy** | If BAB SOC < threshold AND no portable connected → auxiliary → BAB bias; elif portable low SOC flagged → auxiliary → portable; hysteresis prevents chatter |

Inputs:

| Sensor / signal | Automation use |
|-----------------|----------------|
| BAB SOC/voltage proxy | Charging priority splits |
| Portable BMS SOC or pack voltage telemetry | Permission to terminate aux charge or redirect |
| PV availability heuristic | Idle reduction / curtail advisory |
| Temperature | Charger derate / disallow |
| Fault flags | Force OFF / isolate auxiliary output |

Automation **explicitly excludes** motorized PV-string switching matrices in this roadmap.

---

## 12. Example automation logic sketch (conceptual—not executable spec)

```text
IF auxiliary_pv_active AND auxiliary_mppt_idle_or_safe_transition:
    IF portable_pack_present AND portable_soc_below_threshold:
        route_aux_output SWAP_BOX
    ELSE IF bab_soc_below_high_absorb_ceiling_margin:
        route_aux_output BAB
    ELSE IF portable_absent AND bab_above_ceiling_minus_hysteresis:
        inhibit_aux_bulk OR curtail_via_mppt_specific_feature
ELSE:
    defer routing change until safe transition window verified
```

Hysteresis, delay timers, mechanical wear counts for contactors, and human override **hard switches** preserve manual authority.

---

## 13. Safety philosophy

Mandatory practices:

| Principle | Application |
|-----------|-------------|
| Clear identification | Labels: **MAIN ARRAY**, **AUX ARRAY**, **AUX OUTPUT → BAB / SWAP**, **OFF** meanings |
| LOTO suitability | Isolate both arrays distinctly for intrusive MPPT servicing |
| Coordinated sequencing | §8 commissioning and reroute discipline |
| Coherent protection sizing | Fuse/breakers sized for summed contributions when BAB receives dual chargers |
| Fire / thermal vigilance | Dual charging increases sustained charge duty—monitor bank temperature clustering |

Maintain **datasheet binders**: Voc/Isc computations for both arrays, MPPT manuals, inverter integration notes, BAB BMS allowances, portable BMS datasheet constraints.

---

## 14. Recommended development path

| Stage | Deliverable |
|-------|----------------|
| **1 — Static architecture** | Two arrays installed, labeled isolators, auxiliary MPPT manually routed, documented parameter sets |
| **2 — Safety validation** | Load-test dual MPPT into BAB currents, conductor thermal checkpoints, harmonic-free inspection of interaction at absorb boundaries |
| **3 — Telemetry** | Shunt/logging alignment for SOC automation inputs |
| **4 — Controlled automation** | Battery-side relays with proven interlocking from §§8–12 |

Defer digital complexity until empirical confidence exists in absorption alignment and sequencing.

---

## 15. Summary

The deployed architecture adopts:

```text
Main PV ──► AIO MPPT ──► BAB
Aux PV ───► Aux MPPT ─► Battery routing ──► BAB or Swap-Box
```

It **eliminates**:

- PV string transfer switching,
- shared-source MPPT multiplexing,
- dynamic string reconfiguration (e.g., 4S ⇄ 6S reassignments tied to swapping destinations),
- centralized PV routing matrices.

It **advantages**:

- simplicity and reproducibility during commissioning,
- transparent diagnostic boundaries,
- scalability toward SOC-driven **battery-output** coordination,
- maintenance of **regulated** coupling to portable packs without bridging batteries directly,

while recognizing that **two MPPT chargers feeding one bank** remains a **straightforward cooperative regime** provided engineering alignment of charge policies and protection.
