<div align="center">

<img width="60" height="60" alt="truestretch" src="https://github.com/user-attachments/assets/e45109d8-edc3-4f67-be60-0f8ff19b3c80" />

# TrueStretch

**Device Manager & Display Settings — for Windows**

[![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D4?style=flat-square&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
[![Language](https://img.shields.io/badge/Language-C%2B%2B17-00599C?style=flat-square&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![License](https://img.shields.io/badge/License-Proprietary-red?style=flat-square)](#credits)
[![Build](https://img.shields.io/badge/Build-MinGW--w64%20%7C%20MSVC-brightgreen?style=flat-square)](#build)

> A lightweight, native Win32 tool for managing monitors and display resolutions — no Python, no runtime, no bloat.

</div>

---

## 🖥️ What Is TrueStretch?

TrueStretch is a compact dark-themed desktop utility that gives you direct control over your Windows display setup. Whether you're a gamer switching to a stretch resolution, a multi-monitor user managing active devices, or just someone who wants finer control over their display than Windows Settings allows — TrueStretch has you covered.

It talks directly to Windows Device Manager and the display driver stack, the same way Windows itself does, with no third-party libraries and no internet connection required.

---

## ✨ Features

### 🖱️ Monitor Controls Tab

| Feature | Description |
|---|---|
| 📋 **Monitor List** | Lists all monitors Windows knows about — active, disabled, and disconnected — with their hardware IDs |
| 🟢 **Enable Device** | Re-enables a disabled monitor through Windows Device Manager in one click |
| 🔴 **Disable Device** | Disables a monitor device with a safety confirmation prompt |
| 🔄 **Scan Monitors** | Refreshes the monitor list on demand without restarting the app |
| 🎯 **Device Status Badge** | Live status indicator — Enabled/Disabled/Not Active shown with colour-coded pill badge |
| 📐 **Supported Resolutions** | Scrollable list of all resolutions your GPU and monitor support |
| ✅ **Apply Resolution** | Switch to any listed resolution with a 10-second confirm/revert prompt |
| ↩️ **Revert Resolution** | Instantly revert to the resolution that was active when the app opened |
| 🔧 **Custom Resolution** | Enter any width × height and register it with your GPU driver using three injection methods |
| 💾 **Persistent Settings** | Your last-used resolution and scaling preference are saved and restored on next launch |

### ⚙️ System Information Tab

| Feature | Description |
|---|---|
| 💻 **Computer Name** | Your machine's Windows hostname |
| 🪟 **Windows Version** | Full build number and release version (correctly identifies Windows 10 vs 11) |
| 🧠 **Processor** | CPU brand string from the system firmware |
| 🧩 **Memory** | RAM size, type (DDR4/DDR5/etc.), slot usage, and speed from SMBIOS |
| 🎮 **GPU Adapters** | All display adapter names from Device Manager |
| 🖥️ **Active Displays** | Connected monitor names from the Windows display path |
| ⚡ **Display Scaling** | Apply driver-level scaling — stretch, centered, aspect ratio, or driver default |
| 🔄 **Refresh Hardware Scan** | Re-scans all hardware in the background with a smooth spinner animation |

---

## 🎮 Safe for Gamers

TrueStretch is designed with gamers in mind. Here is what you need to know:

### Stretch Resolutions
Many competitive players use a **non-native stretch resolution** (like 1440×1080 or 1280×1024) for a wider field of view or personal preference. TrueStretch makes this effortless — browse supported modes, pick one, and apply. Your choice is saved to the Windows registry so it survives reboots.

### Custom Resolutions
If your resolution is not in the list, use **Test & Add**. TrueStretch registers the resolution using three methods simultaneously:
- Windows CCD (display configuration database) — works on Intel, AMD, and NVIDIA
- Monitor EDID override — the same technique used by Custom Resolution Utility (CRU)
- GPU adapter registry — fallback for older integrated graphics

All three run at once so the mode is as widely registered as possible.

### Is Disabling a Monitor in Device Manager Safe?

**Yes — it is completely safe** and fully reversible. Here is what actually happens:

- Windows simply marks the device node as disabled in Device Manager
- The physical monitor hardware is not damaged or modified in any way
- The display driver is instructed to stop using that output path
- **Re-enabling takes one click** — TrueStretch shows an Enable Device button whenever a disabled monitor is selected
- If you accidentally disable your only active monitor and the screen goes black, you can re-enable it through Windows Safe Mode, or connect another display and open TrueStretch

This is the same operation Device Manager performs when you right-click a device and choose **Disable device**. TrueStretch simply makes it faster and more accessible.

### Resolution Persistence
When you apply a resolution and choose to keep it, TrueStretch writes it with `CDS_UPDATEREGISTRY` — the Windows-standard flag that persists display settings across reboots. You will not revert to a stretch resolution after restarting your system.

---

## 🛡️ Safety & Permissions

- **UAC elevation** is requested only when needed (monitor enable/disable, EDID registry write)
- **No background services** — TrueStretch is a single executable with no auto-start or background processes
- **No network access** — everything runs locally using Windows APIs only
- **Fully reversible** — every action can be undone within the app itself
- **Resolution restore** — if a resolution change causes display issues, a 10-second confirmation window lets you revert automatically

---

## 📋 Requirements

- **Windows 10 1809** or later (Windows 11 recommended)
- **Administrator rights** — required for Device Manager operations and EDID custom resolution injection

No installation required. The single `.exe` is statically linked and runs standalone.

---

## 🔨 Build

### MinGW-w64

```bash
cmake -S . -B build -G "MinGW Makefiles"
cmake --build build
```

Output: `build/TrueStretch.exe`

### Visual Studio 2022

```powershell
cmake -S . -B build
cmake --build build --config Release
```
---

## 📜 Credits

<div align="center">

**Created by Derwesh**

© September 2026 Derwesh. All rights reserved.

*Built with native Win32 / C++17 — no frameworks, no dependencies, no compromise.*

</div>
