# ESPHome Nextion IR Thermostat

A wall-mounted thermostat built using:
- Nextion touchscreen (4.3")
- ESPHome
- ESP32-S3 (UI controller)
- ESP8266 IR blaster
- Home Assistant
- Zigbee temperature sensor

Designed for AC control (cooling only).
Tested with Midea IR protocol.

---

## System Overview

```
Nextion Touch
   ↓
ESP32-S3 (ESPHome API)
   ↓
Home Assistant Scripts
   ↓
ESPHome IR Climate Entity
   ↓
IR Blaster → AC Unit
```

---

## Repository Structure

```
firmware/
  esphome/
    ui-controller.yaml
    ir-blaster.yaml

hardware/
  nextion-thermostat.md
  ir-blaster.md

docs/
  home-assistant-minimum.md
  home-assistant-scripts.md
  zigbee2mqtt-sonoff.md
```

---

## License

MIT
