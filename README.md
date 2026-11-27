# Mazda CMU150 UI Simulator

Browser-based recreation of the Mazda Connect (CMU150) infotainment system UI at native 800x480 resolution. Uses original firmware image assets, fonts, and pixel-accurate layout for visual tweak development and testing.

![Settings Screen](https://github.com/user-attachments/assets/placeholder)

## Quick Start

```bash
git clone https://github.com/ilshyma/cmu-simulator.git
cd cmu-simulator
python3 -m http.server 8092
```

Open http://localhost:8092 in your browser.

## What's Inside

The simulator reproduces the core CMU150 GUI framework elements:

- **Home screen** with the 5-icon carousel (Entertainment, Communication, Navigation, Applications, Settings)
- **Settings** with tabbed interface (AD-Disp, Display, Safety, Sound, Clock, Devices, System)
- **Status bar** with domain-specific icons, app title (40px Tipperary Semibold), and clock
- **List controls** — style01 (simple), style03 (radio), style06 (label), style10/11 (toggle buttons), style12 (slider with tick marks)
- **Slider tick marks** with center markers and −/0/+ labels matching firmware behavior
- **LeftBtn** (back button) with proper chrome arc offsets
- **Tuner**, **Now Playing**, and **Dialpad** special screens

## Original Firmware Assets

All image assets and fonts in this repo come from the Mazda CMU150 firmware (JCI / Johnson Controls). Here's where they live on the actual CMU:

| Repo path | Firmware path on CMU |
|-----------|---------------------|
| `gui/common/images/background.png` | `/jci/gui/common/images/background.png` |
| `gui/common/controls/StatusBar/images/` | `/jci/gui/common/controls/StatusBar/images/` |
| `gui/common/controls/List2/images/` | `/jci/gui/common/controls/List2/images/` |
| `gui/common/controls/LeftBtn/images/` | `/jci/gui/common/controls/LeftBtn/images/` |
| `gui/common/controls/Tabs/images/` | `/jci/gui/common/controls/Tabs/images/` |
| `gui/common/images/icons/` | `/jci/gui/common/images/icons/` |
| `gui/apps/system/controls/MainMenu/images/` | `/jci/gui/apps/system/controls/MainMenu/images/` |
| `Tipperary*.ttf` | `/jci/gui/common/css/fonts/` |

The CMU runs a modified Opera browser engine rendering HTML/JS/CSS apps from `/jci/gui/`. The GuiFramework provides controls like `List2Ctrl`, `TabsCtrl` (Style4), `StatusBarCtrl`, and `SliderCtrl` that this simulator recreates in plain HTML/CSS.

## Technical Details

- **Resolution**: 800x480 (native CMU screen)
- **Font**: Tipperary family (Regular, Semibold, Bold) — custom JCI typeface
- **Tab bar**: Style4 tabs, 143px wide, 70px height, with 86px arrow buttons
- **List items**: 732px wide, 64px height, positioned after LeftBtn chrome (102px offset)
- **Sliders**: 346px track width, 13px track height, 22px knob with tick marks from firmware PNGs

## Purpose

This simulator serves as a visual reference for developing UI tweaks and modifications for the Mazda CMU150 infotainment system. It lets you preview how changes to colors, fonts, icons, and layout will look without needing the actual hardware.
