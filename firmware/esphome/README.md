# ESPHome Firmware

This project uses **two ESP32 devices**:

## 1) UI Controller (Nextion)
- File: `ui-controller.yaml`
- Connected to Nextion screen via UART
- Publishes user actions to MQTT (power, mode, fan, set temperature)
- Subscribes to MQTT state updates to refresh the screen

## 2) IR Blaster (AC control)
- File: `ir-blaster.yaml`
- Connected to IR LED/transmitter
- Receives commands via MQTT and sends IR to the AC (tested with Midea)
- Publishes current state back to MQTT

## Secrets
Copy `secrets.example.yaml` to `secrets.yaml` locally and fill in your Wi-Fi/MQTT details.
