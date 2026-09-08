<div align="center">

<img width="80" height="80" alt="TrueStretch icon — Windows display resolution and device manager tool" src="https://github.com/user-attachments/assets/e45109d8-edc3-4f67-be60-0f8ff19b3c80" />

# TrueStretch — True Stretch Resolution Tool for Windows

**Device Manager & Display Settings Utility for Windows 10 / 11**

[![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-0078D4?style=flat-square&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
[![Language](https://img.shields.io/badge/Language-C%2B%2B17-00599C?style=flat-square&logo=cplusplus&logoColor=white)](https://isocpp.org/)
[![License](https://img.shields.io/badge/License-Proprietary-red?style=flat-square)](#credits)
[![Build](https://img.shields.io/badge/Build-MinGW--w64%20%7C%20MSVC-brightgreen?style=flat-square)](#build)

**TrueStretch** (also searched as **True Stretch**, **TrueStretch Resolution**, or **True Stretch Resolution**) is a free, lightweight, native Win32 tool for changing your **Windows display resolution**, applying **stretched / non-native resolutions**, and enabling or disabling **monitor devices in Device Manager** — with no Python runtime, no bloat, and no third-party dependencies.

[Features](#-features) • [Is TrueStretch Safe?](#-is-truestretch-safe) • [Requirements](#-requirements) • [Build](#-build) • [FAQ](#-frequently-asked-questions)

</div>

---

## 🖥️ What Is TrueStretch?

**TrueStretch** is a compact, dark-themed desktop utility that gives Windows users direct control over their display setup. If you searched for **"true stretch resolution,"** **"how to stretch resolution on Windows,"** or **"disable monitor in device manager,"** this tool does exactly that — in one click.

TrueStretch is built for:
- 🎮 **Gamers** who want a **stretched resolution** (e.g. 1440×1080, 1280×1024) for a competitive field-of-view advantage
- 🖥️ **Multi-monitor users** who need to quickly enable or disable a display device
- 🛠️ **Power users** who want more control over resolution and scaling than Windows Settings provides

TrueStretch talks directly to the Windows Device Manager and display driver stack — the same way Windows itself does — with no internet connection required and no data ever leaving your PC.

---

## ✨ Features

### 🖱️ Monitor Controls Tab

| Feature | Description |
|---|---|
| 📋 **Monitor List** | Lists all monitors Windows knows about — active, disabled, and disconnected — with their hardware IDs |
| 🟢 **Enable Device** | Re-enables a disabled monitor through Windows Device Manager in one click |
| 🔴 **Disable Device** | Disables a monitor device with a safety confirmation prompt |
| 🔄 **Scan Monitors** | Refreshes the monitor list on demand without restarting the app |
| 🎯 **Device Status Badge** | Live status indicator — Enabled / Disabled / Not Active — shown as a colour-coded pill badge |
| 📐 **Supported Resolutions** | Scrollable list of every resolution your GPU and monitor support |
| ✅ **Apply Resolution** | Switch to any listed resolution with a 10-second confirm/revert prompt |
| ↩️ **Revert Resolution** | Instantly revert to the resolution that was active when the app opened |
| 🔧 **Custom / Stretch Resolution** | Enter any width × height — including true stretch resolutions — and register it with your GPU driver using three injection methods |
| 💾 **Persistent Settings** | Your last-used resolution and scaling preference are saved and restored on next launch |

### ⚙️ System Information Tab

| Feature | Description |
|---|---|
| 💻 **Computer Name** | Your machine's Windows hostname |
| 🪟 **Windows Version** | Full build number and release version (correctly identifies Windows 10 vs 11) |
| 🧠 **Processor** | CPU brand string from system firmware |
| 🧩 **Memory** | RAM size, type (DDR4/DDR5/etc.), slot usage, and speed from SMBIOS |
| 🎮 **GPU Adapters** | All display adapter names from Device Manager |
| 🖥️ **Active Displays** | Connected monitor names from the Windows display path |
| ⚡ **Display Scaling** | Apply driver-level scaling — stretch, centered, aspect ratio, or driver default |
| 🔄 **Refresh Hardware Scan** | Re-scans all hardware in the background with a smooth spinner animation |

---

## 🎮 True Stretch Resolutions for Gamers

**TrueStretch** is built with gamers in mind — this is the core reason the tool exists.

### Stretch Resolutions
Many competitive players use a **non-native stretch resolution** (like 1440×1080 or 1280×1024) for a wider field of view or personal preference. TrueStretch makes this effortless — browse supported modes, pick one, and apply. Your choice is saved to the Windows registry so it survives reboots.

### Custom Resolutions
If your desired resolution isn't in the list, use **Test & Add**. TrueStretch registers the resolution using three methods simultaneously:
- **Windows CCD** (display configuration database) — works on Intel, AMD, and NVIDIA
- **Monitor EDID override** — the same technique used by Custom Resolution Utility (CRU)
- **GPU adapter registry** — fallback for older integrated graphics

All three run at once so the mode is registered as widely as possible.

---

## 🛡️ Is TrueStretch Safe?

**Yes — every action in TrueStretch is safe and fully reversible.**

### Disabling a Monitor in Device Manager
- Windows simply marks the device node as disabled — the physical monitor hardware is never damaged or modified
- The display driver is instructed to stop using that output path
- **Re-enabling takes one click** — TrueStretch shows an Enable Device button whenever a disabled monitor is selected
- If you accidentally disable your only active monitor, you can re-enable it through Windows Safe Mode, or connect another display and open TrueStretch again

This is the exact same operation Device Manager performs when you right-click a device and choose **Disable device** — TrueStretch just makes it faster.

### Resolution Persistence
When you apply a resolution and choose to keep it, TrueStretch writes it with `CDS_UPDATEREGISTRY` — the Windows-standard flag that persists display settings across reboots.

### Additional Safeguards
- **UAC elevation** requested only when needed (monitor enable/disable, EDID registry write)
- **No background services** — a single executable, no auto-start, no hidden processes
- **No network access** — everything runs locally using Windows APIs only
- **Fully reversible** — every action can be undone within the app
- **Auto-revert** — a 10-second confirmation window reverts automatically if a resolution change causes display issues

---

## 📋 Requirements

- **Windows 10 (1809+)** or **Windows 11**
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

## ❓ Frequently Asked Questions

**What is TrueStretch?**
TrueStretch is a free native Windows tool for changing display resolution (including stretched/non-native resolutions) and enabling or disabling monitors through Device Manager.

**Is "True Stretch Resolution" the same as TrueStretch?**
Yes — TrueStretch is the app that lets you apply a true stretch resolution on Windows, commonly searched as "true stretch resolution" or "how to get stretched resolution."

**Is it safe to disable a monitor in Device Manager with TrueStretch?**
Yes. Disabling a device only tells Windows to stop using that display output — it doesn't touch the hardware, and it can be re-enabled in one click.

**Does TrueStretch require Python or .NET?**
No. TrueStretch is written in native C++17 / Win32 and ships as a single standalone `.exe` with no runtime dependencies.

**Does a resolution set with TrueStretch survive a reboot?**
Yes, if you choose to keep it — it's written to the registry with the standard Windows persistence flag.

---

## 📜 Credits

<div align="center">

**Created by Derwesh**

© September 2026 Derwesh. All rights reserved.

*Built with native Win32 / C++17 — no frameworks, no dependencies, no compromise.*

</div>
