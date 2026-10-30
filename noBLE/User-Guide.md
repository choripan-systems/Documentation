# 1. Introduction

noBLE is a device that can give "new life" to your indoor bike trainer, by adding new features to it, and helping you solve real-world problems with your indoor cycling set up.

These are some of noBLE's features:

* It adds Direct Connect (DIRCON) support over WiFi, which is supported by most cycling apps as a preferred option over Bluetooth.
* It can bridge over DIRCON up to 3 external Bluetooth sensors, such as a heart rate monitor, cadence, power meter.
* It adds Virtual Shifting support, using a configurable drivetrain, to trainers that don't have native support for it.
* It is configured by a simple companion app that runs on Windows, macOS, and Linux.
* It runs on low-cost off the shelf hardware.
* It is a standalone device that runs off USB power.

The following sections decribe each feature in more detail.

# 2. Direct Connect

Most virtual cycling apps connect to the smart indoor bike trainer via Bluetooth Low Energy (BLE) and use the BLE standard Fitness Machine Service (FTMS) and the Cycling Power Service (CPS) to interact with the trainer.

BLE is ubiquitous, supported by all hardware devices where those virtual cycling apps run.

However, being a low-power wireless technology operating in the crowded 2.4 GHz range, BLE communications are subject to occasional connection drops due to either a weak signal or to interference with other nearby devices operating in the same 2.4 Ghz range. This is not good when you are in the middle of a virtual cycling activity!

To address these issues, Wahoo Fitness ® developed the Direct Connect (DIRCON) protocol, that essentially allows the trainer control and the sensor data to be exchanged over WiFi or wired Ethernet, instead of BLE. In a nutshell, DIRCON is simply "BLE-over-TCP".

For an in-depth review of DIRCON, you can read [this](https://www.dcrainmaker.com/2021/01/wahoo-starts-shipping-kickr-2020-direct-connect-cable-hands-on-details.html) blog post by DC Rainmaker, or watch [this](https://youtu.be/XtIM5675dLo?si=B5nM_biNNlvfmuu2) Youtube video from Shane Miller.

As of the time of this writing, DIRCON is supported by the following virtual cycling apps:

- FulGaz
- MyWhoosh
- Real Velo
- Wahoo SYSTM
- Zwift

and is available in the following indoor bike trainers:

| Brand | Model | Enet | WiFi |
|-------|-------|----|----|
|Elite|Justo| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Failed](https://img.shields.io/badge/-%E2%9C%98-red) |
|Elite|Justo 2| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Elite|Avanti| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|JetBlack|Victory| ![Failed](https://img.shields.io/badge/-%E2%9C%98-red) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Tacx|Neo 3M| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Wahoo|KICKR V5| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Failed](https://img.shields.io/badge/-%E2%9C%98-red) |
|Wahoo|KICKR V6| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Wahoo|KICKR BIKE V2| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Wahoo|KICKR MOVE| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Wahoo|KICKR BIKE SHIFT| ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |
|Wahoo|KICKR CORE V2| ![Failed](https://img.shields.io/badge/-%E2%9C%98-red) | ![Success](https://img.shields.io/badge/-%E2%9C%94-brightgreen) |

The trend in the smart trainer market is moving toward built-in Wi-Fi connectivity because it offers a more stable and faster connection than traditional Bluetooth or ANT+ for competitive virtual racing.  So it is likely that DIRCON will soon become a common feature in most next-gen indoor trainers. 

