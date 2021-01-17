This is an [esphome](https://esphome.io) component for the PMSA003I (pmsa003i) sensor.

[<img src="https://cdn-shop.adafruit.com/970x728/4632-10.jpg" width="400px">](https://www.adafruit.com/products/3686)

## Installation
Copy the `pmsa003i` directory into your ESPHome `custom_components` directory (creating it if it does not exist).

## Dependencies
The [I2C Bus](https://esphome.io/components/i2c.html#i2c) must be set up in order for this component to work.

## Minimal configuration
The following configuration shows the minimal set up to read temperature and humidity from the sensor.
```yaml
i2c:

sensor:
  - platform: pmsa003i
    pm_2_5:
      name: "PM2.5"
```

## Available Sensors

- pm_1_0:  mass of particles with a diameter of 1 micrometres or less (μg/m^3)
- pm_2_5: mass of particles with a diameter of 2.5 micrometres or less (μg/m^3)
- pm_10_0: mass of particles with a diameter of 10 micrometres or less (μg/m^3)
- pmc_0_3: count of particles with diameter > 0.3 um in 0.1 L of air (#/0.1L)
- pmc_0_5: count of particles with diameter > 0.5 um in 0.1 L of air (#/0.1L)
- pmc_1_0: count of particles with diameter > 1 um in 0.1 L of air (#/0.1L)
- pmc_2_5: count of particles with diameter > 2.5 um in 0.1 L of air (#/0.1L)
- pmc_5_0: count of particles with diameter > 5 um in 0.1 L of air (#/0.1L)
- pmc_10_0: count of particles with diameter > 10 um in 0.1 L of air (#/0.1L)

## Parameters

address: The I2C address of the device. Default is `0x12`
update_interval: How frequently to poll the device. Default is `60s`
standard_units: Whether to use standard units (`True`) or environmental units (`False`)

## Complete configuration

```
  - platform: pmsa003i
    pm_1_0:
      name: "Aether PM1.0"
    pm_2_5:
      name: "Aether PM2.5"
    pm_10_0:
      name: "Aether PM10.0"
    pmc_0_3:
      name: "Aether PMC <0.3µm"
    pmc_0_5:
      name: "Aether PMC <0.5µm"
    pmc_1_0:
      name: "Aether PMC <1µm"
    pmc_2_5:
      name: "Aether PMC <2.5µm"
    pmc_5_0:
      name: "Aether PMC <5µm"
    pmc_10_0:
      name: "Aether PMC <10µm"
    address: 0x12
    update_interval: 60s
    standard_units: True
```

## Standard vs Environmental Units

From https://publiclab.org/questions/samr/04-07-2019/how-to-interpret-pms5003-sensor-values#c23772

> "Standard" refers to the concentration "corrected" to the "standard atmosphere" which in the US is DEFINED as "having a temperature of 288.15 K at the sea level 0 km geo-potential height and 1013.25 hPa" details here
>
> On the other hand, the "ambient conditions" are just as the air is "now" (whatever temperature and pressure there is) Now what does that mean ...
>
> Air being a gas, it is compressible which means that it changes its volume when the pressure changes so when you report concentrations as mass per volume of air it is relevant at what pressure that volume is calculated. For example, if you have a bunch of particles rising in the air in a bubble (no loss of particles, no addition, they're just riding a bubble up in the air) then, as they rise, the pressure drops so what was 1cc at the ground it is now 2cc so the concentration is now half without anything actually changing other than the ambient pressure. So, it is common to report concentrations (of anything) as "x mg per standard m3" and because we scientist don't like to write much (current example excluded) you'll usually see the "standard" being dropped because it is "implicit".

## Datasheet

English datasheet https://cdn-shop.adafruit.com/product-files/4632/4505_PMSA003I_series_data_manual_English_V2.6.pdf

## Hardware

The hardware is available from Adafruit https://www.adafruit.com/product/4632

