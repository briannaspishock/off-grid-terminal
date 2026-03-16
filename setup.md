# 1. enable developer options (7 tap)
* Settings>About Phone>Software Information
* tap Build Number 7 times until "Developer mode has been turned on."
* return to main Settings menu
* Developer Options will now appear

# 2. enable USB debugging
* open Developer Options
* locate USB Debugging toggle and switch to ON

 # 3. Linux udev rules configuration
 to allow a non-root user to access the Android device, define a udev rule for the hardware

```bash

# identify vendor ID for Samsung unit
lsusb

# vendor ID is 04e8
# create and fill rule text
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0666", GROUP="plugdev"' | sudo tee /etc/udev/rules.d/51-android.rules

# check file contents
cat /etc/udev/rules.d/51-android.rules

#reset ADB daemon
adb killer-server
adb start-server
adb devices

```
