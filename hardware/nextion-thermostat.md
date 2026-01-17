
## Recommended Parts & Purchase Links

Below are example listings for the hardware used in this project.
You can source similar parts from AliExpress, eBay, Amazon, or other vendors.

- **Nextion 4.3" Display (NX4827P043)**  
  https://www.aliexpress.com/item/1005007260252619.html

- **ESP32-S3 Dev Board**  
  https://www.aliexpress.com/item/1005007390162850.html

- **SONOFF Zigbee USB Dongle Plus (ZBDongle-E)**  
  https://www.aliexpress.com/item/1005007089589385.html

- **SONOFF SNZB-02P Zigbee Temperature Sensor**  
  https://www.aliexpress.com/item/1005002271970887.html

- **USB-C to Bare Wires Pigtail (for power)**  
  https://www.aliexpress.com/item/1005006968463545.html

- **USB-C 35W Charger (for wall power)**  
  https://www.aliexpress.com/item/1005007549145111.html


# Nextion Thermostat – Hardware & Installation

This document describes the hardware, wiring, and installation process
used for the Nextion-based wall thermostat.

The design uses:
- A **Nextion 4.3\" HMI**
- An **ESP32-S3** mounted inside the Nextion enclosure
- Zigbee temperature sensing
- Power delivered over USB-C from the AC unit area

---

## Hardware used

### Display
- Nextion 4.3"
- Models:
  - NX4827P043-011R-Y
  - NX4827P043-011C-Y

### Microcontroller (UI controller)
- ESP32-S3 development board

### Zigbee coordinator
- SONOFF Zigbee USB Dongle Plus (ZBDongle-E, Zigbee 3.0)

### Temperature sensor
- SONOFF SNZB-02P Zigbee temperature sensor  
  (Used as the room temperature source via Zigbee2MQTT)

### Power & cabling
- USB-C 90° OTG connector (mounted inside the Nextion enclosure)
- USB-C to bare-wire pigtail cable (22 AWG)
- 35W multi-port USB-C charger (installed near AC unit)
- CAT cable used as low-voltage power run (4 conductors: 2× +5V, 2× GND)

---

## Mechanical modifications (Nextion enclosure)

1. Open the back cover of the Nextion display.
2. Disconnect and remove the **speaker** (not needed).
   - Unplug the connector
   - Pull gently but firmly to remove the speaker
3. In the speaker area:
   - Create a **small oval opening**
   - This allows the **USB-C 90° adapter** to exit cleanly
4. Ensure the USB-C connector sits flat and does not stress the cable.
5. Close the Nextion back cover once wiring is complete.

---

## Electrical wiring (Nextion ↔ ESP32-S3)

The Nextion display includes a 4-wire connector.

### Wiring map

| Nextion wire | ESP32-S3 pin |
|--------------|--------------|
| Red          | 5V           |
| Black        | GND          |
| Yellow       | TX           |
| Blue         | RX           |

Notes:
- UART is direct (no level shifting required)
- Common ground is mandatory
- Ensure TX/RX are crossed correctly

---

## Power delivery

- Power originates from a **35W USB-C charger** near the AC unit
- 4 conductors are used:
  - 2 wires for +5V
  - 2 wires for GND
- This minimizes voltage drop over the wall run
- Always verify voltage at the thermostat using a **voltmeter**
  before final connection

Target voltage at ESP32 / Nextion:


---

## Flashing the Nextion HMI

1. Download the **HMI file** from the GitHub repository.
2. Copy it to a microSD card (16 GB is more than enough).
3. Insert the SD card into the Nextion display.
4. Power the display.
5. Wait until flashing reaches **100%**.
6. Power off the display.
7. Remove the SD card.

---

## Flashing ESPHome (UI controller)

1. Connect the ESP32-S3 via USB-C.
2. Use the provided ESPHome YAML from the repository.
3. Flash the firmware using ESPHome.
4. Once discovered in Home Assistant:
   - Add the device
   - Add it to the **ESPHome integration**

### IMPORTANT Home Assistant setting

After adding the ESPHome device:


This permission is **required** for Nextion button presses
to call Home Assistant scripts.

---

## System overview

- Nextion display = UI only
- ESP32-S3 = Nextion interface + HA API calls
- Zigbee temperature sensor = room temperature
- Home Assistant = logic & climate control
- IR blaster (documented separately) = AC control

---

## Notes

- No automations are used
- No MQTT is used for control
- Nextion and Home Assistant UI stay synchronized
- Multiple thermostats can be implemented by duplicating logic


