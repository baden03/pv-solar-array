# JK-B2A20S20P-HC Smart BMS Datasheet (Normalized Reference)

Source:
- JK Smart BMS Operation and Maintenance Manual
- Model Family: JK-B2AxxS-20P
- Specific Unit: JK-B2A20S20P-HC

Reference File:
JK-BMS-user-manual.pdf

---

# 1. Overview

The JK-B2A20S20P-HC is a smart lithium Battery Management System (BMS) with integrated active balancing, Bluetooth monitoring, CANBUS/RS485 communication, and programmable protection logic.

The BMS supports:
- LiFePO4
- Li-Ion (NMC/NCA)
- LTO

Primary functions:
- Cell voltage monitoring
- Active balancing
- Over-voltage protection
- Under-voltage protection
- Over-current protection
- Short-circuit protection
- Temperature protection
- SOC estimation
- Bluetooth telemetry
- CANBUS / RS485 communication

---

# 2. Core Specifications

| Parameter | Value |
|---|---|
| Model | JK-B2A20S20P-HC |
| Supported Cell Count | 7S–20S |
| Continuous Current | 200A |
| Peak Current | 350A |
| Balance Type | Active Balancing |
| Max Balance Current | 2A |
| Wiring Method | Same Port |
| Communication | Bluetooth, CANBUS, RS485 |
| Heating Support | Yes |
| Internal Resistance | 0.47mΩ |
| Operating Voltage Range | 20–100V |
| Operating Temperature | -40°C to +85°C |
| Storage Temperature | -40°C to +95°C |
| Temperature Sensor Inputs | 3x NTC |
| Short Circuit Protection | Yes |
| Coulomb Counter | Yes |
| Smartphone Support | Android / iOS |

---

# 3. Measurement Accuracy

## Cell Voltage Detection

| Parameter | Value |
|---|---|
| Detection Range | 0–5V |
| Typical Error | <5mV |
| Max Error | <10mV |

## Pack Voltage Detection

| Parameter | Value |
|---|---|
| Detection Range | 0–100V |
| Accuracy | <0.5% FSR |

## Current Detection

| Parameter | Value |
|---|---|
| Range | -150A to +300A |
| Accuracy | <0.5% FSR |

## SOC Estimation

| Parameter | Value |
|---|---|
| SOC Accuracy | <8% |
| Remaining Capacity Error | <8% |

---

# 4. Active Balancing System

## Balance Method

The JK BMS uses:
- Active energy transfer balancing

Energy is:
- removed from higher-voltage cells
- temporarily stored
- transferred into lower-voltage cells

This is NOT passive resistor balancing.

## Balance Current

| Parameter | Value |
|---|---|
| Continuous Balance Current | 2A |

## Recommended Balance Trigger Settings

JK recommends:

| Battery Size | Trigger Delta |
|---|---|
| >50Ah | 0.005V |
| <50Ah | 0.010V |

For large CATL 320Ah cells:
- Recommended practical range:
  - 0.003V–0.008V

---

# 5. Supported Chemistries

## LiFePO4
Supported.

## Li-Ion
Supported.

## LTO
Supported.

The app includes chemistry presets.

---

# 6. Temperature Monitoring

## Inputs

| Sensor Count | 3 |
|---|---|

## Temperature Detection Range

| Parameter | Value |
|---|---|
| Detection Range | -40°C to +125°C |

## Protection Types

- Charge Over Temperature Protection
- Charge Under Temperature Protection
- MOS Over Temperature Protection
- Discharge Temperature Protection

---

# 7. Communication Interfaces

## Bluetooth

Integrated Bluetooth:
- Android support
- iOS support

Functions:
- Real-time telemetry
- Parameter configuration
- Protection status
- Balance monitoring
- SOC monitoring

Default Bluetooth password:
- 1234

---

## RS485

Supported.

Can be used for:
- External monitoring
- ESPHome integration
- Home Assistant
- Custom telemetry systems

---

## CANBUS

Integrated CANBUS controller.

Important:
- Protocol compatibility varies
- Not automatically Victron-native

Integration may require:
- protocol translation
- ESP32 bridge
- dbus-serialbattery
- Venus OS customization

---

# 8. Connector Definitions

## P1/P2 — Cell Sense & Balance Leads

Functions:
- Cell voltage acquisition
- Active balancing

Connections:
- B-
- B1
- B2
- B3
- etc.
- B20
- B+

---

## P3 — Temperature Sensors

| Pin | Function |
|---|---|
| T1A/T1B | Temp Sensor 1 |
| T2A/T2B | Temp Sensor 2 |

---

## P4 — Communication

| Pin | Function |
|---|---|
| D_P | CAN_L / RS485+ |
| D_N | CAN_H / RS485- |
| GND | Signal Ground |

---

## P5 — GPS / UART

| Pin | Function |
|---|---|
| VGPS | Power |
| TX | UART TX |
| RX | UART RX |
| GND | Ground |

---

## P6 — Display Interface

RS485 display interface.

---

## P7 — Heating Interface

Integrated heating control support.

Functions:
- Heating output
- Charge indication

---

# 9. Wiring Architecture

## Same-Port Design

The JK-B2A20S20P-HC uses:
- common negative MOS architecture

Meaning:
- charge and discharge share same MOSFET path

Advantages:
- simpler wiring
- lower cost

Considerations:
- protections affect both directions
- shutdown logic affects full pack

---

# 10. Power Consumption

| Mode | Consumption |
|---|---|
| Operating (No Comms) | <5mA |
| Operating (CAN/RS485) | <15mA |
| Standby | <2mA |

Manual reference:
- 7–8mA at 100V depending on balance state

---

# 11. Protection Functions

## Over Voltage Protection

| Parameter | Adjustable Range |
|---|---|
| Cell OVP | 1.2–4.35V |
| Cell OVPR | 1.2–4.35V |

---

## Under Voltage Protection

| Parameter | Adjustable Range |
|---|---|
| Cell UVP | 1.2–4.35V |
| Cell UVPR | 1.2–4.35V |

---

## Over Current Protection

Separate:
- charge OCP
- discharge OCP

Adjustable:
- threshold
- delay
- recovery time

---

## Short Circuit Protection

Supported.

Adjustable recovery timer:
- SCPR Time

---

## Temperature Protections

Supported:
- charge high temp
- charge low temp
- discharge temp
- MOS temp

---

# 12. App Functions

The mobile app supports:

- Live cell voltages
- Delta voltage
- Pack current
- Pack power
- SOC
- Remaining Ah
- Balance current
- MOS temperature
- Cell temperatures
- Charge/discharge MOS state
- Parameter editing
- Calibration functions

---

# 13. Calibration Functions

## Voltage Calibration

Allows correction of:
- total pack voltage readings

## Current Calibration

Allows correction of:
- current shunt readings

---

# 14. Important Operational Notes

## Activation Behavior

The BMS:
- does NOT have a physical power switch

Activation occurs when:
- charger voltage exceeds battery voltage by ~5V

---

## Balance Conditions

Balancing only occurs when:
- balance enabled
- cell voltage above balance start voltage
- pack delta exceeds trigger threshold

---

## MOS Thermal Considerations

At sustained high current:
- MOS heating becomes significant

Particularly important:
- enclosed battery boxes
- hot climates
- inverter surge operation

---

# 15. Recommended Settings for CATL 320Ah LiFePO4

## Recommended Operational Targets

| Parameter | Suggested Value |
|---|---|
| Cell OVP | 3.55–3.60V |
| Cell OVPR | 3.45–3.50V |
| Cell UVP | 2.80–2.90V |
| Cell UVPR | 3.00V |
| Balance Trigger Delta | 0.005V |
| Balance Start Voltage | 3.40–3.45V |
| Max Charge Current | 150–160A |
| Max Discharge Current | 200A |
| Charge Low Temp Cutoff | 0°C |
| MOS OTP | Conservative setting recommended |

---

# 16. Integration Notes

## Victron SmartShunt

Recommended:
- use SmartShunt as primary SOC source

Reason:
- JK SOC estimation less accurate over time

---

## ESPHome / MQTT

RS485 integration is well suited for:
- ESP32 telemetry
- MQTT publishing
- Home Assistant
- Grafana dashboards

---

## Victron CAN Integration

Possible but:
- protocol compatibility must be verified
- often requires translation layer

---

# 17. Mechanical Dimensions

| Parameter | Value |
|---|---|
| Size | 162mm × 102mm × 20.4mm |
| Weight | ~430g |

---

# 18. Safety Notes

Critical:
- Incorrect balance lead wiring can destroy the BMS instantly.
- Verify every cell voltage before plugging in balance connectors.
- Never reverse polarity.
- Ensure secure thermal mounting.
- Use proper busbars and fuse protection.
- Avoid sustained operation at thermal limits.

---

# 19. System Classification

This BMS is suitable for:
- serious DIY ESS systems
- large LiFePO4 banks
- solar storage systems
- off-grid inverters
- mobile power systems
- marine systems

It is significantly more advanced than:
- passive-balancing drop-in lithium systems
- basic RV BMS units

---