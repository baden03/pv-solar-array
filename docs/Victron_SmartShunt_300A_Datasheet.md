# Victron SmartShunt 300A Datasheet 

Source:
- Victron Energy SmartShunt Datasheet
- Model: SmartShunt 300A

Reference File:
Datasheet-SmartShunt-EN.pdf

---

# 1. Overview

The Victron SmartShunt 300A is a high-precision battery monitor with integrated Bluetooth and VE.Direct communication.

Unlike the BMV series:
- it has no built-in display
- no programmable relay
- no audible alarm

The SmartShunt is intended to:
- monitor battery SOC
- track energy flow
- record historical trends
- integrate into Victron GX systems
- provide accurate current measurement

Monitoring is performed through:
- VictronConnect (Bluetooth)
- VE.Direct
- GX devices

---

# 2. Core Specifications

| Parameter | Value |
|---|---|
| Model | SmartShunt 300A |
| Max Continuous Current | 300A |
| Supply Voltage Range | 6.5–70V DC |
| Current Draw | <1mA |
| Battery Capacity Setting | 1–9999Ah |
| Operating Temperature | -40°C to +50°C |
| Protection Rating | IP21 |
| VE.Direct Port | Yes |
| Bluetooth | Integrated |

---

# 3. Measurement Capabilities

The SmartShunt can monitor:

- Battery voltage
- Current
- Power
- Amp-hours consumed
- State of charge
- Time-to-go
- Historical trends
- Midpoint voltage
- Starter battery voltage
- Temperature (optional sensor)

---

# 4. Resolution & Accuracy

## Current Measurement

| Parameter | Value |
|---|---|
| Resolution | ±0.01A |
| Accuracy | ±0.4% |
| Offset | <10mA |

---

## Voltage Measurement

| Parameter | Value |
|---|---|
| Resolution | ±0.01V |
| Accuracy | ±0.3% |

---

## Amp-Hour Measurement

| Parameter | Value |
|---|---|
| Resolution | ±0.1Ah |

---

## SOC Measurement

| Parameter | Value |
|---|---|
| Resolution | ±0.1% |

---

## Time-to-Go

| Parameter | Value |
|---|---|
| Resolution | ±1 minute |

---

## Temperature Measurement

(Optional external sensor)

| Parameter | Value |
|---|---|
| Range | -20°C to +50°C |
| Accuracy | ±1°C |

---

# 5. Communication Interfaces

## Bluetooth

Integrated Bluetooth allows:
- smartphone monitoring
- configuration
- firmware updates
- historical trend viewing

Compatible with:
- Android
- iOS

Uses:
- VictronConnect app

---

## VE.Direct

Integrated VE.Direct communication port.

Can interface with:
- GX devices
- Cerbo GX
- Venus OS
- ESP32 serial readers
- Home Assistant integrations

---

# 6. Auxiliary Input Functions

The SmartShunt auxiliary input can be configured for:

## Second Battery Monitoring

Typically:
- starter battery voltage

---

## Midpoint Monitoring

Useful for:
- series battery banks
- imbalance detection

Particularly valuable:
- 24V and 48V systems

---

## Temperature Sensor

Optional accessory:
- ASS000100000

Provides:
- battery temperature monitoring

---

# 7. Stored Trend Data

The SmartShunt internally stores:
- voltage history
- current history
- SOC history
- auxiliary input history

Retention period:
- 46 days

---

# 8. Installation Details

## Dimensions

| Parameter | Value |
|---|---|
| Height | 44mm |
| Width | 120mm |
| Depth | 44mm |

---

## Connection Bolts

| Parameter | Value |
|---|---|
| Bolt Size | M8 |

---

# 9. Wiring Architecture

## Correct Placement

The SmartShunt MUST be installed:
- in the primary negative path
- between battery negative and system negative bus

Correct order:

Battery (-)
→ SmartShunt BATTERY SIDE
→ SmartShunt SYSTEM SIDE
→ all loads and chargers

---

# 10. Important System Integration Notes

## EVERYTHING Must Pass Through the Shunt

For accurate SOC:
ALL current must pass through the shunt.

This includes:
- inverter loads
- chargers
- solar chargers
- DC loads
- DC/DC converters

Exceptions:
- direct emergency bypasses
- chassis bonding

---

## Placement Relative to BMS

For your JK BMS system:

Recommended arrangement:

Battery (-)
→ JK BMS P-
→ SmartShunt Battery Side
→ Main Negative Bus

This ensures:
- SmartShunt measures true system current
- BMS self-consumption included
- all loads visible to shunt

---

# 11. Relationship Between SmartShunt and JK BMS

## SmartShunt Strengths

Excellent for:
- SOC tracking
- long-term energy history
- charge/discharge statistics
- system-wide energy accounting

---

## JK BMS Strengths

Excellent for:
- cell-level monitoring
- balancing
- protection
- cell telemetry
- MOS protection

---

## Combined System

The combination is ideal because:

| Device | Primary Role |
|---|---|
| JK BMS | Cell protection and balancing |
| SmartShunt | Accurate SOC and energy accounting |

---

# 12. Bluetooth Range Notes

Victron notes:
- metal enclosures
- boat hulls
- seawater
- heavy cabling

can reduce Bluetooth range.

Typical usable range:
- 10–15 meters

Solutions:
- VE.Direct Bluetooth Dongle
- GX device integration
- ESPHome bridge

---

# 13. GX Device Integration

The SmartShunt integrates cleanly with:
- Cerbo GX
- Color Control GX
- Venus OS

Through:
- VE.Direct cable

This enables:
- centralized system monitoring
- remote VRM logging
- advanced dashboards

---

# 14. Operational Characteristics

## Very Low Power Consumption

| Mode | Consumption |
|---|---|
| Normal Operation | <1mA |

This makes the SmartShunt suitable for:
- long-term storage
- off-grid systems
- marine systems

---

## SOC Accuracy Depends on Synchronization

Like all coulomb counters:
- SOC drifts over time if not synchronized

Proper synchronization requires:
- full charge detection
- correct tail current settings
- accurate battery capacity configuration

---

# 15. Recommended Settings for Your CATL 320Ah Bank

## Battery Capacity

| Parameter | Suggested |
|---|---|
| Battery Capacity | 320Ah |

---

## Charged Voltage

Recommended:
- approximately 28.4–28.8V for 8S LiFePO4

Depends on:
- your chosen longevity strategy

---

## Tail Current

Recommended:
- 2–4%

For 320Ah:
- roughly 6–12A

---

## Peukert Exponent

LiFePO4:
- approximately 1.05

---

## Charge Efficiency

LiFePO4:
- 99%

---

# 16. Midpoint Monitoring Considerations

For your 8S CATL bank:
- midpoint monitoring is optional

Since:
- the JK BMS already monitors every cell individually

However:
- midpoint monitoring can still provide:
  - fast visual imbalance indication
  - independent redundancy

---

# 17. Integration with ESPHome / MQTT

Possible through:
- VE.Direct serial parsing

Common integrations:
- ESP32
- MQTT
- Home Assistant
- InfluxDB
- Grafana

Very popular in DIY ESS systems.

---

# 18. Marine / Off-Grid Suitability

The SmartShunt is particularly well suited for:
- sailboats
- off-grid cabins
- container systems
- RV systems
- solar ESS systems

Advantages:
- low power use
- high accuracy
- compact size
- reliable Bluetooth
- simple wiring

---

# 19. Important Real-World Observations

## SmartShunt SOC Is Usually More Reliable Than Many BMS SOC Estimates

Especially:
- over long timeframes
- variable load conditions

This is because:
- Victron’s coulomb counting and synchronization logic is very mature.

---

## Incorrect Wiring Is Extremely Common

Common mistake:
- connecting loads directly to battery negative

This bypasses the shunt and:
- destroys SOC accuracy

---

## Temperature Compensation

LiFePO4 voltage curves:
- are very flat

Meaning:
- voltage alone is a poor SOC indicator

The SmartShunt’s coulomb counting is therefore extremely valuable in LiFePO4 systems.

---

# 20. System Role in Your ESS

In your system:

| Component | Role |
|---|---|
| CATL Cells | Energy storage |
| JK BMS | Cell protection + balancing |
| SmartShunt | Accurate SOC + history |
| Inverter/Charger | AC conversion + charging |
| PV System | Energy generation |

The SmartShunt acts as:
- the primary fuel gauge of the system.

---