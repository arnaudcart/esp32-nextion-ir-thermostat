# Zigbee2MQTT with SONOFF ZBDongle-E (Zigbee 3.0 USB Dongle Plus E)

This project uses **Zigbee2MQTT** with the **SONOFF ZBDongle-E (EFR32MG21)** as the Zigbee coordinator.

This document assumes Zigbee2MQTT is installed as a **Home Assistant Add-on**.

---

## Required Add-ons & Repositories

### 1) HACS
Repository:
https://github.com/hacs/addons

Steps:
1. Install the HACS add-on.
2. Add HACS as a Home Assistant integration.

HACS is required later for custom frontend cards.

---

### 2) Zigbee2MQTT
Repository:
https://github.com/zigbee2mqtt/hassio-zigbee2mqtt

Steps:
1. Install the Zigbee2MQTT add-on.
2. Start it once (to generate default config).
3. Stop the add-on before editing configuration.

---

### 3) Additional Required Add-ons
Install:
- **Mosquitto broker**
- **ESPHome**

Optional but recommended:
- **Samba share**
- **Studio Code Server**

---

## Zigbee2MQTT Configuration (IMPORTANT)

### Configuration path
When using the Home Assistant add-on, Zigbee2MQTT must use:

```yaml
data_path: /config/zigbee2mqtt
