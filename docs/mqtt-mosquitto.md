# Mosquitto MQTT (Home Assistant Add-on)

This project uses MQTT for communication between devices (ESP32, Zigbee2MQTT, etc.).

## Installation (Home Assistant Add-on)
1. In Home Assistant, go to **Settings → Add-ons → Add-on Store**.
2. Install **Mosquitto broker**.
3. Start the add-on.
4. Enable:
   - Start on boot
   - Watchdog (optional)

## MQTT User (Required)
Zigbee2MQTT requires **explicit MQTT credentials**.

1. In Home Assistant, go to **Settings → People → Users**.
2. Create a new user (example: `mqtt`).
3. Set a password.
4. Ensure the user has **Local access** enabled.

These credentials will be used in:
- Zigbee2MQTT configuration
- ESPHome (if using MQTT instead of native API)

## Default Settings
- Port: `1883`
- Broker host: Home Assistant IP
