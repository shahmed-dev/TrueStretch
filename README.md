# AspectFlow

AspectFlow is a native Win32 desktop application for managing monitors and display resolutions on Windows. It provides a compact dark interface for selecting a monitor, enabling or disabling it through Device Manager, switching display modes, and registering custom resolutions.

## Features

- View connected monitor devices and their hardware IDs.
- Enable or disable a selected monitor (with an elevation prompt when required).
- Browse supported display resolutions in a compact, scrollable list.
- Apply a selected resolution and confirm whether to keep it.
- Return to the resolution active when the application started.
- Test and add a custom width and height.
- Dark native Win32 UI with no Python runtime dependency.

> Disabling the only active monitor can make the screen go black until the device is enabled again.

## Requirements

- Windows 10 version 1809 or later (Windows 11 recommended).
- A C++17 compiler: MinGW-w64 or Visual Studio 2022 with Desktop development with C++.
- CMake 3.16 or later, if building with CMake.

Administrative permission is required for monitor enable/disable operations and for adding an EDID-based custom resolution. AspectFlow asks for elevation only when that is needed.

## Build with CMake

### MinGW-w64

```bash
cmake -S . -B build -G "MinGW Makefiles"
cmake --build build
```

The executable is generated as `build/AspectFlow.exe`.

### Visual Studio

```powershell
cmake -S . -B build
cmake --build build --config Release
```

The Release executable is generated as `build\\Release\\AspectFlow.exe`.

## Build directly with MinGW-w64

From a MinGW-w64 shell in the project folder:

```bash
windres app.rc -O coff -o app_res.o
g++ -std=c++17 -mwindows -municode -O2 app.cpp util.cpp controls.cpp dialog.cpp monitors.cpp display.cpp app_res.o -o AspectFlow.exe -ldwmapi -luxtheme -lsetupapi -lcfgmgr32 -lcomctl32 -lshell32 -luser32 -lgdi32 -static -static-libgcc -static-libstdc++
```

## Credits

Created by Derwesh  
Copyright © September 2026 Derwesh. All rights reserved.
