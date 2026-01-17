# Zigbee2MQTT with SONOFF ZBDongle-E (Zigbee 3.0 USB Dongle Plus E)

This project uses **Zigbee2MQTT** with the **SONOFF ZBDongle-E (EFR32MG21)** as the Zigbee coordinator.

This document assumes Zigbee2MQTT is installed as a **Home Assistant Add-on**.

---

## Required Add-ons & Repositories

### 1) Zigbee2MQTT
Repository:
https://github.com/zigbee2mqtt/hassio-zigbee2mqtt

Steps:
1. Install the Zigbee2MQTT add-on using the repository above.
2. Start it once (to generate default config).
3. Stop the add-on before editing configuration.

---

### 2) Additional Required Add-ons
Install:
- **Mosquitto broker**

---

## Zigbee2MQTT Configuration (IMPORTANT)

### Configuration path
When using the Home Assistant add-on, Zigbee2MQTT must use:

```yaml
data_path: /config/zigbee2mqtt

### MQTT configuration

Zigbee2MQTT requires explicit MQTT credentials.

```yaml
mqtt:
  server: mqtt://core-mosquitto:1883
  user: YOUR_MQTT_USERNAME
  password: YOUR_MQTT_PASSWORD
  base_topic: zigbee2mqtt
```
## Serial configuration (ZBDongle-E)

Always use the by-id serial path.

```yaml
serial:
  port: >-
    /dev/serial/by-id/usb-Itead_Sonoff_Zigbee_3.0_USB_Dongle_Plus_V2_XXXXXXXXXXXX-if00-port0
  adapter: ezsp
```

Notes:
- Use `adapter`,
- Migration rules apply
