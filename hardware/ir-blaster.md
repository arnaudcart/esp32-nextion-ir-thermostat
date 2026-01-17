<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/6f8b3edb-b4f0-4746-b817-57615d135898" />
<img width="245" height="206" alt="image" src="https://github.com/user-attachments/assets/e27ea1fc-3932-4ded-86e8-3be739611aa1" />
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/32d49afc-11c9-4369-9ffa-5039f781d54d" />

# IR Blaster – Hardware & Installation

This document describes the IR blaster hardware used to control the AC unit.
The IR blaster is installed near the AC and communicates with Home Assistant
via ESPHome, exposing a `climate` entity.

---

## Hardware used

### Microcontroller (IR node)
- Wemos D1 Mini (ESP8266)

### Transistor
- 2N2222 NPN transistor (TO-92 package)
- Used to drive the IR LED with sufficient current

Example:
https://www.aliexpress.com/item/1005009230873249.html

### IR LED
- Standard 940 nm IR LED

### Enclosure
- Waterproof plastic DIY enclosure (55 × 35 × 15 mm)

Example:
https://www.aliexpress.com/item/1005002656686923.html

### Power cable
- Micro-USB cable (used to power the D1 Mini)

Example:
https://www.aliexpress.com/item/1005008661132841.html

### Power source
- Same **35W multi-port USB charger (PD)** used for the thermostat
- Installed near the AC unit

---

## Transistor pinout (2N2222)

Facing the **flat side** of the transistor:


---

## Electrical wiring

### Connections

| Component | Connection |
|---------|------------|
| Transistor **Emitter (1)** | GND |
| Transistor **Base (2)** | D2 (ESP8266) |
| Transistor **Collector (3)** | IR LED negative (short leg) |
| IR LED positive (long leg) | 3.3 V |

Notes:
- The **long leg of the IR LED is the positive (+)**
- The transistor switches the IR LED on the low side
- Common ground is mandatory

---

## Assembly

1. Solder the transistor, IR LED, and wiring together.
2. Connect:
   - GND to emitter
   - D2 to base
   - Collector to IR LED negative
3. Connect IR LED positive to 3.3 V.
4. Place all components inside the waterproof enclosure.
5. Route the IR LED so it points toward the AC receiver.
6. Close the enclosure.

---

## Power

- The IR blaster is powered via **micro-USB**
- Power comes from the same **35W USB charger** used for the thermostat
- No additional power supply is required

---

## Flashing ESPHome

1. Flash the D1 Mini using the ESPHome YAML provided in this repository.
2. After flashing, the device appears in Home Assistant.
3. Add it to the **ESPHome integration**.

Once added, the device exposes:
- A **`climate` entity** (Midea IR)
- This entity is controlled by:
  - Home Assistant UI
  - Nextion thermostat UI (via scripts)

---

## System role

- ESP8266 IR blaster = **AC control**
- Home Assistant = **logic**
- Nextion thermostat = **user interface**
- Zigbee temperature sensor = **room temperature input**

---

## Notes

- IR LED placement matters: point it directly at the AC
- Distance is usually not an issue indoors
- This setup has been tested with **Midea IR protocol**
