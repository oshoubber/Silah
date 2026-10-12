# Third-party notices

Silah dynamically links the following unmodified open-source libraries:

- **LibUsbDotNet 3.0.224** — LGPL-3.0; source: <https://github.com/LibUsbDotNet/LibUsbDotNet>
- **libusb 1.0.30 (VS2022 x64 runtime)** — LGPL-2.1-or-later; source and matching release archive: <https://github.com/libusb/libusb/releases/tag/v1.0.30>
- **LibreHardwareMonitorLib 0.9.6** — MPL-2.0; source: <https://github.com/LibreHardwareMonitor/LibreHardwareMonitor>
- **HidSharp 2.6.4** — Apache-2.0; project: <https://software.seekye.com/hidsharp>
- **.NET / Windows Desktop runtime 8.0.31** — MIT and included third-party terms; runtime license/notices are bundled in `licenses/`; source: <https://github.com/dotnet/runtime> and <https://github.com/dotnet/wpf>.
- Sensor-library dependencies **BlackSharp.Core 1.0.7**, **DiskInfoToolkit 1.1.2**, **RAMSPDToolkit-NDD 1.4.2** — MPL-2.0, unmodified; sources: <https://github.com/Blacktempel/BlackSharp>, <https://github.com/Blacktempel/DiskInfoToolkit>, <https://github.com/Blacktempel/RAMSPDToolkit>.
- **Mono.Posix.NETStandard 1.0.0** — MIT; source: <https://github.com/mono/mono>. Microsoft System.* support libraries retain their .NET/MIT notices.

The exact LibreHardwareMonitorLib source revision is <https://github.com/LibreHardwareMonitor/LibreHardwareMonitor/tree/3d331e3370efb858411f19511373eff65a218701>. The exact LibUsbDotNet source revision is <https://github.com/LibUsbDotNet/LibUsbDotNet/tree/a89bc81569327840e98a2c30207e5b74bbc97b3a>; that archive and libusb 1.0.30 sources are also available in the v0.2.5 release assets. LGPL-3.0 and MPL-2.0 texts are included in `licenses/`. Unmodified LGPL libraries are runtime-extracted dynamic dependencies, not merged into Silah's source. Their extracted assemblies/native DLL may be replaced with compatible modified builds for debugging those modifications; no application restriction is imposed on that activity.

Protocol references used for the UNI FAN SL-Infinity implementation (not bundled):

- **liquidctl** Lian Li UNI driver — GPL-3.0-or-later; source: <https://github.com/liquidctl/liquidctl/blob/main/liquidctl/driver/lianli_uni.py>
- **FanControl.LianLi** — LGPL-2.1; source: <https://github.com/EightB1ts/FanControl.LianLi>

The libusb license text is included at `third_party/libusb/COPYING` and bundled into the single-file release under `licenses/` when extracted at runtime.

Silah does not include L-Connect binaries, firmware, themes, or source code.

## Bundled media encoder

Silah bundles an unmodified, standalone **FFmpeg n8.1.3-17-gc389840894-20261011 Windows x64 static GPL build** from BtbN. FFmpeg is a separate executable invoked through process arguments/pipes; it is not linked into Silah. This build enables GPL and version 3, and does not enable nonfree components.

- Upstream binary release: <https://github.com/BtbN/FFmpeg-Builds/releases/tag/autobuild-2026-10-11-13-04>
- Build scripts snapshot: `63ac3265b0789ea16c7b1f8351cd2ad195a28722` at <https://github.com/BtbN/FFmpeg-Builds>
- FFmpeg source snapshot: `c389840894` at <https://github.com/FFmpeg/FFmpeg/commit/c389840894>
- Binary archive SHA-256: `2006B31D66EE416C5D159337AED1ADB832A91129F26A5CCB35BCD29D036BCC3F`
- Extracted `ffmpeg.exe` SHA-256: `59007E8C6BD78034DCD7F8D75459E241F75B3D6240CBE26004CFDBA9C8C5B262`
- License: GPL-3.0-or-later. The upstream GPL text is bundled in `licenses/FFmpeg-GPL-3.0.txt`.

The [Silah v0.2.5 release](https://github.com/oshoubber/Silah/releases/tag/v0.2.5) provides the matching FFmpeg source snapshot, upstream build scripts/patches/configuration, and dependency source cache from the same upstream build run (38138609481, artifact 11702272949). Follow the source kit's README to reassemble the split dependency cache. Those archives are optional for app users and contain only third-party source material, not Silah source. Included libraries retain their upstream copyrights/licenses; the matching source cache preserves their license files and pinned source revisions.

## Bundled sensor-driver installer

Silah embeds the unmodified **official PawnIO 2.2.0 installer**, which installs the standard signed kernel driver only after user consent. It does not install the unrestricted developer edition or alter Windows security settings.

- Publisher: namazso
- Official release: <https://github.com/namazso/PawnIO.Setup/releases/tag/2.2.0>
- SHA-256: `1F519A22E47187F70A1379A48CA604981C4FCF694F4E65B734AAA74A9FBA3032`
- Official binary edition: proprietary/freeware; installer redistribution is permitted by the author's [licensing guidance](https://github.com/namazso/PawnIO.Modules/wiki/Using-PawnIO-Modules#licensing-considerations).

The open-source driver edition has separate GPL terms. Silah distributes the official installer binary, not a modified or source-built driver. PawnIO is installed system-wide and may be shared by other monitoring applications; removing Silah does not remove that shared driver.
