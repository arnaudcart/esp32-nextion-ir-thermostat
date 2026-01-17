
# Home Assistant – Minimum Configuration

This project assumes Home Assistant is already installed.
Only the minimum required configuration for the Nextion thermostat UI is shown below.

⚠️ Do NOT copy this file as-is.  
Merge the relevant sections into your existing `configuration.yaml`.

---

## configuration.yaml (single thermostat example)

```yaml
sensor:
  - platform: time_date
    display_options:
      - time
      - date

template:
  - sensor:
      - name: "Demo external temperature"
        unit_of_measurement: "°C"
        state: "{{ state_attr('weather.forecast_home', 'temperature') }}"

      - name: "Target Temperature"
        unique_id: target_temp_1
        device_class: temperature
        unit_of_measurement: "°C"
        state_class: measurement
        state: "{{ state_attr('climate.ac_ir_11', 'temperature') }}"

      - name: "Weather Condition (Number)"
        state: >
          {% set weather_mapping = {
            'clear-night': 1,
            'cloudy': 2,
            'fog': 17,
            'hail': 16,
            'lightning': 7,
            'lightning-rainy': 7,
            'partlycloudy': 3,
            'pouring': 4,
            'rainy': 5,
            'sunny': 6,
            'windy': 8,
            'windy-variant': 8,
            'exceptional': 6
          } %}
          {{ weather_mapping.get(states('weather.forecast_home')) }}

      - name: "Thermo cool off number"
        state: >
          {% set hvac_mode_mapping = {
            'cool': 12,
            'off': 13,
            'dry': 15,
            'fan_only': 14
          } %}
          {{ hvac_mode_mapping.get(states('climate.ac_ir_11')) }}

      - name: "Thermo cool off"
        state: "{{ states('climate.ac_ir_11') }}"

      - name: "Fan mode"
        state: >
          {% if state_attr('climate.ac_ir_11', 'fan_mode') %}
            {{ state_attr('climate.ac_ir_11', 'fan_mode') }}
          {% else %}
            Unknown
          {% endif %}

      - name: "Main room Target Temp"
        state: "{{ state_attr('climate.ac_ir_11', 'temperature') }}"

      - name: "Main room Thermo State"
        state: "{{ states('climate.ac_ir_11') }}"
```

---

## Notes
- This example shows **one AC**
- For multiple ACs, duplicate the template sensor blocks and change the climate entity ID
- Scripts are defined separately in `scripts.yaml`
