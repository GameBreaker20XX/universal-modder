# APB Reloaded (PC) — Teardown Documentation

**Game:** APB Reloaded  
**Platform:** PC (Windows, Steam AppID 113400)  
**Developer:** Reloaded Productions (GamersFirst; original: Realtime Worlds)  
**Publisher:** GamersFirst / Little Orbit  
**Year:** 2011 (F2P relaunch; original APB 2010)  
**Engine:** Unreal Engine 3 (verified: APBGame/Binaries/Engine layout + Scaleform symbols)

---

## 1. Game Engine

**Engine:** Unreal Engine 3 (verified via layout + `System@Scaleform@@` C++ symbols; exe carries almost no engine-name strings)  
- **Middleware (verified via binary/DLL evidence):**
  - **Scaleform GFx** (C++ symbols + `GFx/` dir — UI)
  - **Bink Video** (`BinkOpen` import + `binkw32.dll`/`binkw64.dll`)
  - **Vivox Voice** (`vivoxsdk.dll` import in exe strings — voice chat)
  - **Steamworks** (`steam_api64.dll` import + AppID 113400)
  - **DirectX 9** (`d3d9.dll`, `d3dx9_43.dll`, `DINPUT8`, `XINPUT`)
  - **Crash reporting** (`dbghelp.dll`, `AutoReporter`, `BugReport.exe`, `DebuggerAddIn`)
  - **GPU vendor libs** (`atiags`, `cudart` — AMD/NVIDIA perf)
- **Executable:** `Binaries\APB.exe` (29,484,232 bytes, unpacked)
- **Container:** `APBGame\` (Baked/Config/Content/Localization/Movies/ScriptUserBuild/Splash/WebFonts/WebStyle/__Trashcan)
- **Scripting:** UnrealScript (UE3 packages)
- **Physics:** Unconfirmed (no PhysX/Havok strings despite UE3 base — possibly stripped)

**Falsified:** `Nx` ×282 / `Ogg` ×2 / `CRI` ×1 = opcode noise. `UE3` ×1 = binary soup. No Havok/PhysX/FMOD/Miles/Lua/Wwise/PunkBuster/SecuROM/Oodle. `BattlEye/` dir present but zero `BattlEye`/`BEClient` strings in exe (service files without exe linkage).

---

## 2. Key Technical Details

- F2P cops-vs-criminals MMO shooter on stock UE3 packaging with unusually quiet engine strings (customized/stripped build)
- Steam + Vivox + Bink + Scaleform = complete live-service FPS stack; anti-cheat presence on disk but unlinked in code

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\APB Reloaded\Binaries\APB.exe`*  
*Engine: Unreal Engine 3, Reloaded Productions 2011 (AppID 113400)*