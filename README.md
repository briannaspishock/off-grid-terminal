
![license](https://img.shields.io/badge/license-MIT-blue.svg)
![aesthetic](https://img.shields.io/badge/aesthetic-extraterrestrial--author-pink)
![status](https://img.shields.io/badge/status-off--grid-green)

## off-grid-terminal
minimalist, off-grid Writerdeck prototype

this project is an experiment in distraction-free writing via repurposing a deactivated Samsung node into a dedicated single-use terminal for deep writing.

---
## hypothesis:

can a piece of redundant mobile hardware be lobotomized and re-engineered into an industrial word processor? by stripping away the cellular noise and injecting a Linux-based software stack, we can transform a consumer distraction into a professional-grade creative terminal.

---
## hardware:
* Dell Inspiron (petri-dish) running Ubuntu 24.04
* Deactivated Samsung mobile
* Attack Shark X66 (60% mechanical keyboard) modified with Typehaven PBT industrial gray keycaps
* Samsung OEM OTG (USB-C to USB-A) adapter for direct physical input
* Mumba Steam Deck hard-shell case modified for station use

---
## software:
* T-UI terminal based laucher for pure text user interface that eliminates icons in favor of a command-line prompt
* Termux for a full Linux environment on Android for running local scripts and terminal-based tools (cmatrix, neofetch)
* Markor for a distraction-free Markdown word processor
* Kiwix for hosting a local, offline copy of Wiktionary and specialized medical wikis for instant, off-grid reference
* VLC for a local media archive for research-related video and audio

---
## installation:
```bash
# verify node is online
adb devices

# inject software
adb install Termux.apk
adb install Markor.apk
adb install TUI.apk
adb install VLC.apk

# force permanent landscape orientation (desktop mode)
adb shell settings put system user_rotation 1

# finalizing aesthetic in phone via TUI prompt
# theme -color #00FFFF   (sets a cyan lab glow)
# fullscreen -on         (removes the phone status bar)
