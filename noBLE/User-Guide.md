# 1. Introduction

noBLE is a device that can give "new life" to your indoor bike trainer, by adding new features to it, and helping you solve real-world problems with your indoor cycling setup.

These are some of noBLE's features:

* It adds Direct Connect (DIRCON) support over WiFi, which is supported by most cycling apps as a preferred option over Bluetooth.
* It can bridge over DIRCON up to 3 external Bluetooth sensors, such as a heart rate monitor, cadence, power meter.
* It adds FTMS support to older trainers that don't have native support for it.
* It adds Virtual Shifting support, using a configurable drivetrain, to trainers that don't have native support for it.
* It is configured by a simple companion app that runs on Windows, macOS, and Linux.
* It runs on low-cost off the shelf hardware.
* It is a standalone device that runs off USB power.

The following sections describe each feature in more detail.

<br>

# 2. Direct Connect

Most virtual cycling apps connect to the smart indoor bike trainer via Bluetooth Low Energy (BLE) and use the BLE standard Fitness Machine Service (FTMS) and the Cycling Power Service (CPS) to interact with the trainer.

BLE is ubiquitous, supported by all hardware devices where those virtual cycling apps run.

However, being a low-power wireless technology operating in the crowded 2.4 GHz band, BLE communications are subject to occasional connection drops due to either a weak signal or to interference with other nearby devices operating in the same 2.4 GHz band. This is not good when you are in the middle of a virtual cycling activity!

To address these issues, Wahoo Fitness ® developed the Direct Connect (DIRCON) protocol that essentially allows the trainer control and the sensor data to be exchanged over WiFi or wired Ethernet, instead of BLE.

For an in-depth review of DIRCON, you can read [this](https://www.dcrainmaker.com/2021/01/wahoo-starts-shipping-kickr-2020-direct-connect-cable-hands-on-details.html) blog post by DC Rainmaker, or watch [this](https://youtu.be/XtIM5675dLo?si=B5nM_biNNlvfmuu2) Youtube video from Shane Miller.

As of the time of this writing, DIRCON is supported by the following virtual cycling apps:

- FulGaz
- MyWhoosh
- RealVelo
- Rouvy
- Wahoo SYSTM
- Zwift

and is available in the following indoor bike trainers:

| Brand | Model | Wired | WiFi |
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

Notice that some very popular indoor trainers (such as the Wahoo KICKR CORE V1, or the Elite Direto XR) are missing from that table.  noBLE adds DIRCON support over WiFi to all those trainers!

DIRCON uses Multicast DNS (mDNS), also known as Bonjour or ZeroConf, to advertise itself on the local network using the "_wahoo-fitness-tnp._tcp.local" service.  The screenshot below shows the mDiscover app (a free mDNS Browser app for Windows) having discovered two DIRCON devices on the local network: a Wahoo KICKR V5 and a noBLE device.  Notice how the noBLE device advertises the Heart Rate Service (UUID 0x180d) in addition to the Fitness Machine Service and the Cycling Power Service (UUID's 0x1826 and 0x1818, respectively.)

<br>

![mDiscover](./assets/User-Guide/SS-01.png)

<br>

# 3. Bluetooth Sensor Bridging

Some modern indoor trainers can bridge Bluetooth sensors. This is a useful feature because it reduces the number of simultaneous Bluetooth connections the virtual cycling app needs to handle.  This issue is particularly important when the virtual cycling app runs on an AppleTV 4K device, which supports only 2 simultaneous Bluetooth connections, one used to connect to the trainer and the other one typically used to connect to a heart rate monitor.

noBLE can bridge up to 3 external Bluetooth sensors, **in addition** to the indoor trainer.  This allows you to fully utilize your gear, by pairing noBLE with a heart rate monitor, a crank cadence sensor, and a pedal power meter, all at once.  

While all trainers report power, not all of them report cadence, such as on the older KICKR SNAP and KICKR V1 trainers.  And even when the trainer reports cadence, its value may not be accurate under some riding conditions, such as with the KICKR V5, which reports inaccurate cadence values when the gear ratio is below 1:1.  Being able to bridge an accurate crank arm cadence sensor solves those problems.

When cadence sensor bridging is enabled, noBLE will scan for and connect to a device that advertises the Bluetooth "Cycling Speed and Cadence Service" (CSCS).  It will use the data in the CSCS notifications either to insert or to replace the cadence data sent in the FTMS "Indoor Bike Data" or the CPS "Cycling Power Measurement notifications".

When power sensor bridging is enabled, noBLE will scan for and connect to a device that advertises the Bluetooth "Cycling Power Service" (CPS). Once the scan is complete, noBLE queries the CPS devices it found (including the one in the trainer itlsef) and selects the "best" one to use to report the power data.  In most cases the best one is the external pedal or crank power meter device, as they tend to be more accurate and to support power balance.

When heart rate sensor bridging is enabled, noBLE will scan for and connect to a device that advertises the Bluetooth "Heart Rate Service" (HRS).

In all cases, the Bluetooth services from the bridged devices are made available over DIRCON, thus reducing the number of simultaneous Bluetooth connections the virtual cycling app needs to handle.

The screenshot below shows the Device Configuration window of the noBLE Companion app, where you can see the 4 Bluetooth devices noBLE is paired with: Wahoo KICKR used for trainer resistance, Favero Assioma power meter pedals used for power and cadence, Garmin HRM Dual used for heart rate, and CYCPLUS BC2 controller used for gear shifting:

<br>

![mDiscover](./assets/User-Guide/SS-02.png)

<br>

# 4. Fitness Machine Service

Early smart indoor trainers were managed using the ANT+ "Fitness Equipment Controller" (FE-C) protocol.  The problem with ANT+ is that it isn't supported by the typical hardware devices (PC, Mac, AppleTV, etc) used to run the virtual cycling apps, so it forced the user to have to purchase an [ANT+ USB adapter](https://www.wahoofitness.com/devices/indoor-cycling/parts-components/usb-ant-kit-buy) and to have to install its driver, in order to use it.

Before the Bluetooth SIG released the "Fitness Machine Service" (FTMS) specification, some trainers (such as Tacx) allowed the use of FE-C over Bluetooth instead of ANT+, and supported CPS to report power and cadence.  And some early Wahoo trainers (such as the KICKR SNAP) used a private extension to the CPS to control the trainer, by adding a new control point characteristic with the private 128-bit UUID a026e005-0a7d-4ab3-97fa-f1500f9feb8b.

noBLE can add support for FTMS to any old trainer that has no native support for it, but does have support for either FE-C over Bluetooth or the Wahoo extension to the CPS. This feature is useful, as it allows the user to use one of these old trainers with virtual cycling apps (such as MyWhoosh) which require FTMS.






