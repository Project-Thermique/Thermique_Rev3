| :warning: WARNING                        |
|:-----------------------------------------|
| This codebase is valid for Rev3 only     |

# Thermique revision 3 (final)

Project Thermique is aimed to be an all-in-one solution to detect COVID-19 infected individuals entering an office or institution.
It makes use of state-of-the-art thermal imaging and a fullstack application to automatically extract a person's temperatature from the
region of interest, before logging them and alerting admins in case of a possible COVID infection. Being a contactless kiosk placed at an
entryway, it also serves as an attendance tracker.

The overall system is structured as follows:

<img width="720" alt="rev3diagram" src="https://github.com/user-attachments/assets/c3f8037b-ba9b-45c4-bce1-3959910a2caf" />

## Differences from Revision 2

1. The Raspberry Pi was no longer needed, after replacing the breakout board of the Lepton thermal imaging sensor with a USB interfacing board (PureThermal 2). The same sensor was used, just with a different interface (SPI breakout for Rev2, USB for Rev3).

2. The Jetson board takes care of the entire logic, from facial detection and temperature reading, error correction, to database logging.

3. An error correction module was added to correct the temperature bias by detecting the ambient temperature from an independent sensor within the camera's viewport. The sensor readings are transmitted to the Jetson board via MQTT messages.

> More reading: [FDA article on Thermal Imaging accuracy - Archived](https://github.com/Group-B-Foxtrot/Thermique_Rev3/blob/main/Thermal%20Imaging%20Systems%20(Infrared%20Thermographic%20Systems%20_%20Thermal%20Imaging%20Cameras)%20_%20FDA.pdf)

## Usage

This codebase is simpler.

1. Make sure the proper libraries are installed and everything is connected (PiCam via CSI connector, Lepton FLIR via USB, and a display)
2. Navigate to the `Jetson` folder, and run the proper script mentioned in that folder's README. This will launch all the listeners and necessary 
3. Navigate to the `Website_src_snapshot` folder, and extract the archive. Then install the `composer` dependencies and run the Laravel server
4. Ensure the temperature sensor unit for bias correction is set up to broadcast MQTT messages, and an MQTT broker is being run locally. This is optional, but helps with accuracy




