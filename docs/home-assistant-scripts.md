# Home Assistant Scripts – Thermostat Control

The Nextion UI triggers Home Assistant scripts, which directly control
the IR climate entity created by ESPHome.

This example shows **one thermostat**.  
For multiple AC units, duplicate the scripts and change the climate entity.

---

## scripts.yaml (example)

```yaml
#Thermostat 1

'tempup1':
   alias: 'Temperature up by 0.2C 1'
   sequence:
     action: climate.set_temperature
     data_template:
          entity_id: climate.ac_ir_11
          temperature: '{{states.climate.ac_ir_11.attributes.temperature| float(default=0) + 0.2}}'

'tempdown1':
   alias: 'Temperature down by 0.2C 1'
   sequence:
     action: climate.set_temperature
     data_template:
          entity_id: climate.ac_ir_11
          temperature: '{{states.climate.ac_ir_11.attributes.temperature| float(default=0) - 0.2}}'

'acoff1':
   alias: 'AC OFF 1'
   sequence:
     action: climate.set_hvac_mode
     data_template:
          entity_id: climate.ac_ir_11
          hvac_mode: 'off'

'acon1':
   alias: 'AC ON 1'
   sequence:
     action: climate.set_hvac_mode
     data_template:
          entity_id: climate.ac_ir_11
          hvac_mode: 'cool'

'dry1':
   alias: 'Dry 1'
   sequence:
     action: climate.set_hvac_mode
     data_template:
          entity_id: climate.ac_ir_11
          hvac_mode: 'dry'

'fanonly1':
   alias: 'Fan only 1'
   sequence:
     action: climate.set_hvac_mode
     data_template:
          entity_id: climate.ac_ir_11
          hvac_mode: 'fan_only'

'fanauto1':
   alias: 'Fan auto 1'
   sequence:
     action: climate.set_fan_mode
     data_template:
          entity_id: climate.ac_ir_11
          fan_mode: 'auto'

'fanlow1':
   alias: 'Fan low 1'
   sequence:
     action: climate.set_fan_mode
     data_template:
          entity_id: climate.ac_ir_11
          fan_mode: 'low'

'fanmed1':
   alias: 'Fan med 1'
   sequence:
     action: climate.set_fan_mode
     data_template:
          entity_id: climate.ac_ir_11
          fan_mode: 'medium'

'fanhigh1':
   alias: 'Fan high 1'
   sequence:
     action: climate.set_fan_mode
     data_template:
          entity_id: climate.ac_ir_11
          fan_mode: 'high'
```
