# Dependencies and first launch

## What users download

Download **Silah.exe** from the [latest release](https://github.com/oshoubber/Silah/releases/latest). It is a self-contained Windows x64 application. No ZIP extraction, .NET installation, FFmpeg installation, or L-Connect installation is required.

The executable automatically extracts its bundled runtime/native files into Windows' per-user temporary storage. Do not delete those files while Silah is running. Settings and imported-profile references remain in `%LOCALAPPDATA%\Silah`; images/videos referenced by a profile must still exist on your PC.

## Bundled inside the executable

- **.NET 8 / Windows Desktop runtime**: runs the native WPF interface; no separate runtime download.
- **FFmpeg n8.1.3-17-gc389840894 (2026-10-11, BtbN Windows x64 static GPL build)**: GIF/video decoding, composition, live text and H.264 encoding. It runs as a separate process. No external FFmpeg DLLs or L-Connect files are needed. Hardware encoding is preferred when supported; a software encoder is included as a fallback.
- **PawnIO 2.2.0 official installer**: provided locally so sensor setup does not need another download. The installer is not run without your consent.
- **LibreHardwareMonitorLib 0.9.6**: CPU/GPU/motherboard sensor access.
- **LibUsbDotNet 3.0.224 and libusb 1.0.30**: supported direct USB communication.
- **HidSharp 2.6.4**: HID device access.
- Sensor-library internals are also bundled: **BlackSharp.Core 1.0.7**, **DiskInfoToolkit 1.1.2**, **RAMSPDToolkit-NDD 1.4.2**, **Mono.Posix.NETStandard 1.0.0**, and Microsoft System.* support libraries. None requires a separate user download.

## Installed separately, with permission

**PawnIO is a signed, system-wide kernel driver**, required for CPU temperature and supported motherboard fan sensors/control. If missing, an interactive launch offers installation using the bundled official installer. You can decline and continue with USB/OLED features. Windows may require a restart to finish driver installation; Silah does not automatically restart Windows or disable security features.

Silah itself requests administrator access at launch for hardware access. Windows/UAC approval is still required. Already-installed PawnIO is reused; minimized startup does not display an unsolicited driver-install prompt. PawnIO is shared with other monitoring tools, so deleting Silah does not uninstall that driver.

Silah's application executable is currently **unsigned**, unlike the signed PawnIO driver installer. Windows SmartScreen may display an unknown-publisher warning. Download only from the official repository and compare the executable's SHA-256 with the release's `Silah-SHA256.txt`; do not disable Windows security features to run it.

## Supplied by Windows or the hardware vendor

- **Windows 10/11 x64** and normal graphics drivers. GPU-specific encoder availability depends on those drivers; CPU encoding remains available.
- **Microsoft WinUSB** for the supported HydroShift USB interfaces. The tested display and pump advertise `USB\MS_COMP_WINUSB` and use Windows' built-in `winusb.inf`; no vendor driver package was required for those interfaces on the tested system. Other firmware/device combinations have not all been tested.
- Installed system fonts are used for text. A profile using a font absent on another PC may render differently.

**L-Connect is not a dependency.** If installed, stop it or disable its startup before using Silah to control the same exclusive USB devices.

## Licenses and source archives

See [third-party notices](THIRD_PARTY_NOTICES.md). The release's optional FFmpeg source/build archives and dependency-source parts are for licensing and rebuilding the bundled encoder, **not prerequisites for running Silah**. They contain third-party sources, not Silah's private source code. Download only `Silah.exe` to use the app.

## Verification scope

The release packaging is tested by launching the single executable from a folder containing no sidecar dependencies, verifying the bundled FFmpeg/PawnIO hashes, and encoding H.264 with text using an empty PATH. Automated tests cover driver-install consent policy. This is not a full clean-Windows virtual-machine test or a guarantee of every motherboard's sensor/control support.
