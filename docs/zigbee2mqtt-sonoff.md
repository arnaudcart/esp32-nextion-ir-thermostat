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

---

## Room Temperature Sensor (SONOFF SNZB-02P)

This project uses a Zigbee temperature sensor to measure the room temperature:

- SONOFF SNZB-02P Zigbee Temperature & Humidity Sensor  
  https://www.aliexpress.com/item/1005002271970887.html

### Pairing with Zigbee2MQTT
1. Open the Zigbee2MQTT Web UI.
2. Enable **Permit join**.
3. Put the SNZB-02P into pairing mode (hold the button until it blinks).
4. Wait for it to appear in Zigbee2MQTT.

### Important: entity_id must match ESPHome IR config
The IR blaster ESPHome device reads the room temperature from Home Assistant using:

```yaml
sensor:
  - platform: homeassistant
    entity_id: sensor.ac3_temperature
```

So your temperature sensor must appear in Home Assistant with an entity like:
- `sensor.<your_sensor>_temperature`

If your entity_id is different, update the IR blaster YAML to match.

### Zigbee network reliability note
Zigbee networks improve as you add **router-capable devices** (mains-powered devices such as smart plugs, repeaters, etc.).
If the temperature sensor has a weak connection, temperature updates may be delayed or missing.

Adding Zigbee routers/extenders is a simple way to improve reliability.
