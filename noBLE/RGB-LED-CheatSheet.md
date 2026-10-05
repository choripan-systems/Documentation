noBLE uses the RGB LED on the ESP32 DevKit to give the user visual hints of its running state, indicated by the color and blinking rate of the LED. 

The supported colors are:

![Static Badge](https://img.shields.io/badge/BLUE-blue)
![Static Badge](https://img.shields.io/badge/CYAN-cyan)
![Static Badge](https://img.shields.io/badge/GREEN-green)
![Static Badge](https://img.shields.io/badge/MAGENTA-magenta)
![Static Badge](https://img.shields.io/badge/ORANGE-orange)
![Static Badge](https://img.shields.io/badge/RED-red)
![Static Badge](https://img.shields.io/badge/YELLOW-yellow)

And the LED blinking rates are: 1 bps, 2 bps, 4 bps, in addition to showing a solid color (no blinking) or being off.

The table below summarizes the different states currently supported:

| State | Color | Blink Rate |
| ----- | ----- | ---------- |
| Missing WiFi Credentials | ![Static Badge](https://img.shields.io/badge/MAGENTA-magenta) | 4 bps |
| Invalid WiFi Credentials | ![Static Badge](https://img.shields.io/badge/RED-red) | 4 bps |
| Connecting to WiFi | ![Static Badge](https://img.shields.io/badge/BLUE-blue) | 4 bps |
| Connected to WiFi | ![Static Badge](https://img.shields.io/badge/BLUE-blue) | solid |
| Scanning for BLE Devices | ![Static Badge](https://img.shields.io/badge/YELLOW-yellow) | 4 bps |
| BLE Scan Finished | ![Static Badge](https://img.shields.io/badge/YELLOW-yellow) | solid |
| Accepting DIRCON Connection | ![Static Badge](https://img.shields.io/badge/GREEN-green) | 4 bps |
| DIRCON Connection Established | ![Static Badge](https://img.shields.io/badge/GREEN-green) | 1 bps |
| OTA Firmware Update in Progress | ![Static Badge](https://img.shields.io/badge/CYAN-cyan) | 4 bps |
| Fatal Firmware Error | ![Static Badge](https://img.shields.io/badge/RED-red) | solid |

