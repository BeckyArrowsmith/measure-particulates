# Measure particulates

Measure Particulates in the atmosphere with a PMS5003 Particulate Sensor

## What this does

I want to grab particulate data and send it to my own API gateway so I can grab the data and do what I want with it, as well as send it to the Luftdaten project.

Seems like something lots of people would like to do, so I thought I'd make this public & write some tests :)

## Pi setup

I'm using a RPi Zero with an Enviro+ PiHAT for this. The particulate sensor is the PMSM5003. You'll need to enable I2C, SPI and serial; disable the serial console and enable the miniuart interface that the Pi uses to talk to the PMS5003 particulate sensor.

**on your RPi, not your development environment**

* Run `sudo pip install enviroplus`

**Note** this wont perform any of the required configuration changes on your Pi, you may additionally need to:

* Enable i2c: `raspi-config nonint do_i2c 0`
* Enable SPI: `raspi-config nonint do_spi 0`

And if you're using a PMS5003 sensor you will need to:

* Enable serial: `raspi-config nonint set_config_var enable_uart 1 /boot/config.txt`
* Disable serial terminal: `sudo raspi-config nonint do_serial 1`
* Add `dtoverlay=pi3-miniuart-bt` to your `/boot/config.txt`

And install additional dependencies:

```
sudo apt install python-numpy python-smbus python-pil python-setuptools
```

## Todo

- [ ] Get data from sensor
- [ ] Post it to API gateway
- [ ] Post it to Luftdaten
- [ ] Learn how to unittest RPi/mock GPIO