# 1. Introduction

The noBLE Companion app is used to configure and control a noBLE device. Below is a list of some of the things you can do with it:

* Set the WiFi credentials
* Enable optional features, such as BLE sensor bridging and virtual shifting
* Perform virtual gear shifting
* Control the Power Boost threshold and level

The app is written in Python, so it can run on any platform that has a Python 3 runtime environment available. If your Windows PC already has a Python 3 runtime environment installed, you can skip the following section and jump to section #3.

<br>

# 2. Install Python

Windows does not come with Python preinstalled, so unless you have already installed it for other purposes, you will need to install it now.  The good news is that Python is free and easy to install.

On Windows you can install Python in two different ways:

* Directly from the [MS Store](https://apps.microsoft.com/detail/9nq7512cxl7t?ocid=webpdpshare)
* Downloading the installer for the latest stable release from the official Python web site [python.org](https://www.python.org/downloads/windows)

In this tutorial we will install Python using the Microsoft Store app.

Open the Microsoft Store app and search for “python install”.  You should get this:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-01.png)

<br>

Press the blue Get button and wait until the software is downloaded and installed.  When the process is complete, the Get button should change to Open:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-02.png)

<br>

When you click the Open button a Command Prompt window will automatically open up, to ask you a few questions about some post-install options.  See the screenshots below:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-03.png)

<br>

![noBLE](./assets/App-Install-On-Windows/SS-04.png)

<br>

![noBLE](./assets/App-Install-On-Windows/SS-05.png)

<br>

To check that the installation was successful, open a PowerShell terminal and run the command:

```
python --version
```

which simply prints the version number and exits. In this example the version installed was 3.14.3:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-06.png)

<br>

> [!TIP]
> While the following step is not strictly necessary, at this point you may want to update Python's installer "pip" to the latest version, so that it stops printing the message "A new release of pip is available ..." each time you run it:

```
python -m pip install --upgrade pip
```

The noBLE Companion app uses a few optional Python packages that can be installed as follows:

```
python -m pip install bleak pyserial qrcode pillow
```

<br>

# 3. Install the noBLE Companion app

The nobleComp app is distributed as a ZIP file with the name "nobleComp-YY-MM-DD.zip", where YY-MM-DD indicates the version number. Once you unzip the file, use the PowerShell terminal to go to the folder "nobleComp-YY-MM-DD" where the files were extracted, and run the following shell command to ensure the app was properly installed: 

```
python .\nobleComp.py --version
```

<br>

![noBLE](./assets/App-Install-On-Windows/SS-10.png)

<br>

> [!TIP]
> The supplied file "nobleComp.vbs" is a Visual Basic Script that can be used to create a desktop shortcut, so that the app can be launched by simply double-clicking the shortcut. To create the shortcut right-click anywhere on the desktop and select New > Shortuct from the pop-up menu.  Then set the Target field to the full path to the nobleComp.vbs file:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-10.6.png)

<br>

# 4. Using the noBLE Companion app

Launching the nobleComp app with the option --auto-scan will cause the app to start scanning for noBLE devices within reach.  By default the BLE scan lasts for 3 seconds, but it can be extended if needed.  Each device discovered is shown in the list box, with the first (and usually only) noBLE device discovered pre-selected:

```
python .\nobleComp.py --auto-scan
```

<br>

![noBLE](./assets/App-Install-On-Windows/SS-11.png)

<br>

Pressing the green Connect button will cause nobleComp to connect to the selected noBLE device, and to read its current configuration and state, which is shown on the Device Configuration window.  When connecting to a brand new device all the settings will be at their factory defaults:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-12.png)

<br>

The Device Information frame at the top of the window shows, among other things, the serial number of the device, the version of the firmware that it is running, its WiFi IP address, etc.

To set the credentials required to allow noBLE to connect to the WiFi network, simply press the WiFi Config button in the lower-left corner of the window, enter the SSID (31 characters max) and the password (63 characters max) in the respective fields, and press the Set button.  

> [!IMPORTANT]
> The ESP32 only supports WiFi networks that operate in the 2.4 GHz band, and that support at least WAP2 authentication.

The RBG LED will briefly blink $${\color{cyan}cyan}$$ at a rate of 4 times a second while the device connects to the WiFi network.  Once it successfully connects to the network, the LED will turn solid $${\color{cyan}cyan}$$, and the WiFi credentials will get stored in non-volatile memory (NVRAM) to be used to auto-connect to the network whenever the device restarts. If either the SSID or the password entered are incorrect, the connection attempt will fail and the LED will blink $${\color{magenta}magenta}$$ to warn the user.

noBLE can bridge up to three BLE sensor devices, such as:

* Heart rate monitor
* Pedal or crank power meter
* Crank arm cadence sensor

If you intend to use noBLE to bridge any of these sensor devices, simply press the corresponding button in the Sensor Bridging frame to enable the feature.  Notice that the label on each button indicates the action to be performed when the button is pressed; i.e. when a given sensor bridging feature is disabled the label on its button reads Enable, while if the feature is enabled it reads Disable.  

> [!TIP]
> The BLE devices that noBLE discovered and paired with are shown in the right-most column of the Device Information frame. In the example below noBLE had all the sensor bridging features enabled, so it was able to pair with a MAGENE cadence sensor, an iFIT heart rate monitor, and an ASSIOMA power meter, in addition to the actual KICKR trainer.  Notice that in this case, noBLE also paired with a CYCPLUS BC2 gear shifting controller:

<br>

![noBLE](./assets/App-Install-On-Windows/SS-13.png)

<br>

