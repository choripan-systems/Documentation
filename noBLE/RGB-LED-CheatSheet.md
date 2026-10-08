noBLE uses the RGB LED on the ESP32 DevKit to give the user visual hints of its running state, indicated by the color and blinking rate of the LED. 

The supported colors are:

![Static Badge](https://img.shields.io/badge/BLUE-blue)
![Static Badge](https://img.shields.io/badge/CYAN-cyan)
![Static Badge](https://img.shields.io/badge/GREEN-green)
![Static Badge](https://img.shields.io/badge/MAGENTA-magenta)
![Static Badge](https://img.shields.io/badge/ORANGE-orange)
![Static Badge](https://img.shields.io/badge/RED-red)
![Static Badge](https://img.shields.io/badge/YELLOW-yellow)
![Static Badge](https://img.shields.io/badge/WHITE-white)

The LED blinking rates are: 1 bps, 2 bps, 4 bps, in addition to showing a solid color (no blinking) or being off.

Whenever noBLE is powered up, or is reset, the RGB LED is first turned off, and then it follows a ![Static Badge](https://img.shields.io/badge/RED-red) ![Static Badge](https://img.shields.io/badge/GREEN-green) ![Static Badge](https://img.shields.io/badge/BLUE-blue) sequence, to let the user identify LED devices that have the ![Static Badge](https://img.shields.io/badge/RED-red) and ![Static Badge](https://img.shields.io/badge/GREEN-green) colors reversed, as it happens on some "clone" ESP32 DevKits.  The noBLE Companion app has a config setting that lets the firmware compensate for this color discrepancy. 

The table below summarizes the different operating states currently supported:

| Operating State | Color | Blink Rate |
| ----- | ----- | ---------- |
| Missing WiFi Credentials | ![Static Badge](https://img.shields.io/badge/MAGENTA-magenta) | 4 bps |
| Invalid WiFi Credentials | ![Static Badge](https://img.shields.io/badge/RED-red) | 4 bps |
| Connecting to WiFi | ![Static Badge](https://img.shields.io/badge/WHITE-white) | 4 bps |
| Connected to WiFi | ![Static Badge](https://img.shields.io/badge/WHITE-white) | solid |
| Scanning for BLE Devices | ![Static Badge](https://img.shields.io/badge/BLUE-blue) | 4 bps |
| Connecting to BLE Devices | ![Static Badge](https://img.shields.io/badge/BLUE-blue) | 1 bps |
| Sending mDNS Announcements | ![Static Badge](https://img.shields.io/badge/YELLOW-yellow) | 2 bps |
| Accepting DIRCON Connection | ![Static Badge](https://img.shields.io/badge/GREEN-green) | 4 bps |
| DIRCON Connection Established | ![Static Badge](https://img.shields.io/badge/GREEN-green) | 1 bps |
| OTA Firmware Update in Progress | ![Static Badge](https://img.shields.io/badge/CYAN-cyan) | 4 bps |
| OTA Firmware Update Failure | ![Static Badge](https://img.shields.io/badge/ORANGE-orange) | 4 bps |
| Fatal Firmware Error | ![Static Badge](https://img.shields.io/badge/RED-red) | solid |

