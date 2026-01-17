# ESPHome Nextion IR Thermostat

A wall-mounted, touchscreen-based thermostat built with ESPHome and Home Assistant.

### Key components
- Nextion touchscreen (4.3")
- ESP32-S3 (UI controller)
- ESP8266 IR blaster
- Home Assistant
- Zigbee temperature sensor

The system is designed for **AC control (cooling only)** and has been  
**tested with the Midea IR protocol**.

---

## System Overview

The thermostat is split into independent components to keep the system  
modular, reliable, and easy to extend.

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

- The Nextion screen acts purely as the user interface
- Home Assistant handles logic and state
- The IR blaster sends commands directly to the AC unit

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

---

## UI Preview

Real screenshots of the working Nextion thermostat UI:

![Thermostat main screen](https://github.com/user-attachments/assets/0890588f-4f79-4d18-b8fa-fbde8dcd0186)

![Thermostat operation screen](https://github.com/user-attachments/assets/b0a77502-3227-4d96-ba90-27e7c3d74709)
