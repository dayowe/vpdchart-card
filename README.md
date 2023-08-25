# VPD Chart card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

A VPD chart custom card for Home Assistant Lovelace. The card loads the chart form vpdchart.com and sends the sensor data for air humidity, air temperature and canopy temperature to automatically calculate VPD when the values change.

![VPD Chart Card](/vpdchart-card.png)

## Installation

1. Install via [HACS](https://hacs.xyz/).
2. Add to resources:
   ```yaml
   url: /hacsfiles/vpdchart-card/vpdchart-card.js
   type: module
   ```

<details>
   <summary>Manual install</summary>
1. Download the vpdchart-card.js file and store it in your configuration/www/ HASS folder

2. Add to resources:

```yaml
url: /local/vpdchart-card.js
type: module
```

</details>

## Configuration
Add a card with the following configuration to any of your Lovelace views.
```yaml
# Crop IDs
# "0": Cannabis - all growth stages
# "2": Cannabis - Early Vegetative Growth / Propagation
# "3": Cannabis - Late Vegetative / Early Flower
# "4": Cannabis - Cannabis - Mid / Late Flower
# "2": Cannabis - Early Vegetative Growth / Propagation
# "1": Tomatoes
# "5": Leafy Greens
# "6": Cucumber (Cucumis sativus)

type: custom:vpdchart-card
title: VPD Chart
crop_id: "0"
temp_unit: "C" # "C" or "F"
air_rh: sensor.relative_humidity
air_temp: sensor.ambient_temperature
leaf_temp: sensor.leaf_temperature
leaf_temp_offset: "0"
```

### Available configuration options:
| Name             | Type    | Default      | Description                                  |
| ---------------- | ------- | ------------ | -------------------------------------------- |
| type             | string  | **Required** | `custom:vpdchart-card`                       |
| title            | string  | **Optional** | Card title                                   |
| crop             | string  | **Required** | `0\|1\|2\|3\|4\|5\|6`                        |
| temp_unit        | string  | **Required** | `C\|F`                                       |
| air_rh           | string  | **Required** | A humidity sensor entity id                  |
| air_temp         | string  | **Required** | A temperature sensor entity id               |
| leaf_temp        | string  | **Required** | A temperature sensor entity id               |
| leaf_temp_offset | number  | **Optional** | An offset applied to the leaf_temp defined sensor. This is degrees C or F. Temperature unit is taken from HASS settings (Settings > General > Unit System) |
