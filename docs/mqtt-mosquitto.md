# Mosquitto MQTT (Home Assistant)

MQTT is used to connect:
- Zigbee2MQTT → Home Assistant (and optionally other devices)
- ESPHome devices can also publish/subscribe to MQTT if you choose that architecture.

## Option 1 (recommended): Home Assistant Add-on (Mosquitto broker)
This is the easiest method on Home Assistant OS / Supervised installs.

1. In Home Assistant, go to **Settings → Add-ons** (or **Add-on Store** depending on HA version).
2. Find and install **Mosquitto broker**.
3. Start the add-on.
4. Enable:
   - Start on boot
   - Watchdog (optional)

Home Assistant’s MQTT integration can automatically set up the Mosquitto add-on and create credentials, so you usually don’t need to manually create users/passwords unless you want extra logins.
Default MQTT port is **1883**.
