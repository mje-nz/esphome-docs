VL53L0X Time Of Flight Distance Sensor
======================================

.. seo::
    :description: Instructions for setting up VL53L0X distance sensors in ESPHome.
    :image: vl53l0x.jpg
    :keywords: VL53L0X

.. note::

    This page is incomplete and could some work. If you want to contribute, please read the
    :doc:`contributing guide </guides/contributing>`. This page is missing:

      - An image for the front page.
      - Images/screenshots/example configs of this device being used in action.

The ``vl53l0x`` sensor platform allows you to use VL53L0X optical time of flight
(`datasheet <https://www.st.com/resource/en/datasheet/vl53l0x.pdf>`__,
`ST <https://www.st.com/resource/en/datasheet/vl53l0x.pdf>`__) with ESPHome
to measure distances. The sensor works optically by emitting short infrared pulses
and measuring the time it takes the light to be reflected back

The sensor can measure distances up to 2 meters, though that figure depends significantly
on several conditions like surface reflectance, field of view, temperature etc. In general
you can expect surfaces up to 60cm to work, after that you need to make sure the surface is reflecting
well enough (see also section 5 of datasheet).

The :ref:`I²C Bus <i2c>` is
required to be set up in your configuration for this sensor to work.

.. code-block:: yaml

    # Example configuration entry
    sensor:
      - platform: vl53l0x
        name: "VL53L0x Distance"
        address: 0x29
        update_interval: 60s

Configuration variables:
------------------------

- **name** (**Required**, string): The name of the sensor.
- **update_interval** (*Optional*, :ref:`config-time`): The interval to check the
  sensor. Defaults to ``60s``.
- **signal_rate_limit** (*Optional*, float): Set the return signal rate limit in units of MCPS
  (mega counts per second). This is the minimum signal amplitude detected by the sensor necessary
  for it to report a valid reading. Setting a lower value may increase the range of the sensor
  but also increases the chance of getting inaccurate readings. Defaults to ``0.25``.
- All other options from :ref:`Sensor <config-sensor>`.
- **address** (*Optional*, int): Manually specify the I^2C address of the sensor. Defaults to ``0x29``.
- **id** (*Optional*, :ref:`config-id`): Manually specify the ID used for code generation.

See Also
--------

- :ref:`sensor-filters`
- :apiref:`vl53l0x/vl53l0x_sensor.h`
- `vl53l0x-arduino library <https://github.com/pololu/vl53l0x-arduino/>`__ by `Pololu <https://github.com/pololu>`__
- :ghedit:`Edit`
