# City Patrol Police (PC) — Teardown Documentation

**Game:** City Patrol Police (v1.0.1)  
**Platform:** PC (Windows 64-bit, Steam)  
**Developer:** Unknown (indie)  
**Publisher:** Unknown  
**Year:** Unknown (v1.0.1)  
**Engine:** **Unreal Engine 4** (verified)

---

## 1. Game Engine

**Engine:** **Unreal Engine 4** (verified: UE project layout + PhysX3, no Chaos/Oodle)  
- **Middleware (verified via file evidence):**
  - **PhysX 3** (`Engine/Binaries/ThirdParty/PhysX3`, `PhysX` ×157 in shipping exe, `Chaos` ×0, `Oodle` ×0 — pre-Chaos UE4)
  - **Ogg/Vorbis** (`Engine/Binaries/ThirdParty/Ogg`, `Vorbis`)
  - **NVIDIA** (ThirdParty vendor libs)
  - **Steamworks** (`steam_api64.dll` + `SteamInstallScript.vdf`)
- **Executables:** `CityPatrol.exe` (350 KB bootstrap, zero strings) + `WorldracingGame/Binaries/Win64/CityPatrol-Win64-Shipping.exe` (49.7 MB)
- **Container:** `WorldracingGame/Content/Paks/WorldracingGame-WindowsNoEditor.pak` (UE4 IoStore/.pak)
- **Project:** `WorldracingGame` (UE project: `Binaries/`, `Content/`, `Config/controller.vdf`)
- **Crash reporting:** `Engine/Binaries/Win64/CrashReportClient.exe` + `Engine/Programs/CrashReportClient`

**Evidence from dump:**
- UE engine-tree layout (`Engine/Binaries|Config|Extras|Programs` + project `Binaries/Content`)
- UE4-version fingerprint: PhysX3 present, Chaos/Oodle/EOS absent, VS-era ThirdParty set

---

## 2. Key Technical Details

- Small-footprint UE4 indie title (police patrol driving) on stock UE4 packaging
- Bootstrap exe carries no strings — all engine linkage in the Shipping binary

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\City Patrol Police v1.0.1\`*  
*Engine: Unreal Engine 4, Unknown Developer*