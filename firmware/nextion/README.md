# Nextion HMI

This folder contains the Nextion user interface used by the thermostat.

## Files

- `Thermostat_4.3_Final.hmi`  
  Source HMI file (editable using Nextion Editor)

- `Thermostat_4.3_Final.tft`  
  Compiled firmware for flashing via SD card

## Flashing the UI

1. Copy the `.tft` file to a microSD card.
2. Insert the SD card into the Nextion display.
3. Power the display.
4. Wait until flashing reaches 100%.
5. Power off the display.
6. Remove the SD card.
7. Power the display again.

## Compatibility

- Screen size: 4.3"
- Tested on:
  - NX4827P043-011R-Y
  - NX4827P043-011C-Y

## Notes

- The `.hmi` file allows full customization of the UI.
- Component and page IDs are referenced by the ESPHome UI controller YAML.
