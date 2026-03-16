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
adb kill-server
adb start-server
adb devices

```
## 4. Download and Install 
direct download: after Samsung device is connected and recognized, curl with -L flag was used to follow github redirects 

```bash

# Termux
curl -L -o termux.apk https://github.com/termux/termux-app/releases/download/v0.118.1/termux-app_v0.118.1+github-debug_universal.apk

adb install termux.apk
```

T-UI and Markor downloaded via browser to local ~/Downloads folder 

```bash
# Markor and T-UI .apk downloaded from github

# install Markor
adb install ~/Downloads/net.gsantner.markor-v162-2.16.0-flavorDefault-release.apk

# install T-UI (console launcher)
adb install ~/Downloads/ohi.andre.consolelauncher_fdroid_205_11.17.apk
```

## 5. Finalizing UI
* on device, Settings>Apps>Choose default apps
* select T-UI as default home
* refresh and ensure Markor and Termux are indexed

```bash
# refresh app index
refresh

# verify Markor and Termux are indexed
apps -ls
```
