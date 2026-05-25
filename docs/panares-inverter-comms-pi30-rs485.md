# Panares Inverter Communication & PI30 Integration

## Overview

This document covers the communication interfaces, telemetry architecture, and integration strategy for the Panares all-in-one inverter / charger / MPPT system using the PI30 protocol.

The inverter exposes communication over an RJ45 port providing:
- UART TX/RX
- RS485 A/B
- Power
- Ground

The preferred long-term telemetry approach is RS485 using the PI30 protocol, bridged through the NUC into MQTT, Node-RED, InfluxDB, and Grafana.

---

# 1. Physical Communication Port

## RJ45 Pinout

| Pin | Function |
|---|---|
| 1 | TX |
| 2 | RX |
| 3 | VCC |
| 4 | VCC |
| 5 | RS485A |
| 6 | RS485B |
| 7 | GND |
| 8 | GND |

---

# 2. Important Safety Notes

## RJ45 Does NOT Mean Ethernet

Although the inverter uses an RJ45 connector, this is NOT an Ethernet port.

The connector carries:
- UART serial
- RS485
- Power rails

Do NOT connect this port directly to:
- Ethernet switches
- Routers
- NICs

---

## Avoid Connecting VCC

Pins 3 and 4 expose VCC.

These should NOT initially be connected to:
- USB UART adapters
- RS485 adapters
- ESP32 devices

Communication does not require VCC.

---

# 3. Recommended Hardware

## RJ45 Breakout Terminal

An RJ45 screw terminal breakout is recommended for safe testing and non-destructive interfacing.

Benefits:
- Easy probing
- No custom cable cutting
- Easy pin reassignment
- Safe multimeter verification

---

## USB RS485 Adapter

Recommended initial communication method:

Inverter RJ45
→ RJ45 breakout
→ USB RS485 adapter
→ NUC

This approach is preferred over direct UART access because:
- RS485 is more robust
- Intended for telemetry integration
- Better long-term architecture
- Less protocol parsing complexity

---

# 4. RS485 Connection

## Recommended Initial Wiring

| Inverter Pin | RS485 Adapter |
|---|---|
| 5 (RS485A) | A |
| 6 (RS485B) | B |
| 7 or 8 (GND) | Optional GND |

---

## A/B Reversal Warning

RS485 naming is inconsistent across manufacturers.

If communication fails:
- Swap A and B
- Retry

---

# 5. UART Connection (Optional)

UART may be useful for:
- Debugging
- Console access
- Protocol inspection

## Safe Initial UART Test

Only connect:

| Inverter Pin | USB UART Adapter |
|---|---|
| 1 (TX) | RX |
| 7 or 8 (GND) | GND |

DO NOT connect TX from the adapter initially.

---

# 6. PI30 Protocol

The inverter uses the PI30 protocol common to:
- Voltronic
- Axpert
- MPP Solar
- Rebranded all-in-one inverters

The protocol is:
- ASCII-based
- CRC protected
- Command/response oriented

## Example Command

QPIGS

Returns:
- voltages
- currents
- battery status
- load information
- temperatures
- PV production
- charging state

---

# 7. Recommended Software Architecture

Preferred architecture:

Inverter
→ RS485
→ USB RS485 Adapter
→ NUC
→ mpp-solar
→ MQTT
→ Node-RED
→ InfluxDB
→ Grafana

---

# 8. mpp-solar

The recommended software integration layer is:

mpp-solar

This software already handles:
- PI30 protocol
- CRC calculation
- command framing
- response parsing
- MQTT integration

## Installation

pip install mpp-solar

## Example Test Command

mpp-solar -p /dev/ttyUSB0 -P PI30 -c QPIGS

---

# 9. Typical Serial Settings

| Setting | Typical Value |
|---|---|
| Baud | 2400 / 9600 |
| Data Bits | 8 |
| Parity | N |
| Stop Bits | 1 |

Most common:
- 2400 8N1
- 9600 8N1

---

# 10. Future ESPHome Integration

Long-term, telemetry could also be bridged through ESP32 hardware:

Inverter
→ RS485
→ ESP32 RS485 Gateway
→ ESPHome
→ MQTT

However:
- PI30 is not native Modbus
- Requires protocol parsing
- More complex than using mpp-solar

The NUC-based bridge is strongly recommended initially.

---

# 11. Long-Term Telemetry Integration

The inverter telemetry should ultimately integrate into the broader Panares telemetry architecture:

RS485
NMEA2000
ESPHome
MQTT
Node-RED
Signal K
InfluxDB
Grafana

---

# 12. Recommended Next Steps

## Immediate

- Verify RJ45 pinout using breakout terminal
- Connect RS485 adapter
- Test communication
- Install mpp-solar
- Run QPIGS test command

## Near Future

- MQTT integration
- Node-RED ingestion
- InfluxDB logging
- Grafana dashboards

## Long-Term

- ESP32 RS485 gateway
- Signal K integration
- Full vessel telemetry integration

---

# 13. Useful References

PI30 Protocol Discussion:
https://github.com/evcc-io/evcc/discussions/10479

mpp-solar Detailed Usage:
https://github.com/jblance/mpp-solar/wiki/Detailed-Usage#list-available-commands-for-a-protocol

mpp-solar GitHub:
https://github.com/jblance/mpp-solar

ESPHome Modbus Controller:
https://esphome.io/components/modbus_controller/

ESPHome UART:
https://esphome.io/components/uart/

Node-RED:
https://nodered.org/

Signal K:
https://signalk.org/
