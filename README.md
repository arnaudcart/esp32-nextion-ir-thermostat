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

## UI Preview

Real screenshots of the working Nextion thermostat UI:

![DSC_1036](https://github.com/user-attachments/assets/be95f118-0446-4343-809b-a0b9c348c84e)
![WhatsApp Image 2026-01-17 at 20 42 05](https://github.com/user-attachments/assets/b0a77502-3227-4d96-ba90-27e7c3d74709)


