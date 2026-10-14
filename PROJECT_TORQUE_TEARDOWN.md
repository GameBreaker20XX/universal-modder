# Project Torque (PC) — Teardown Documentation

**Game:** Project Torque (free-to-play MMO racer)  
**Platform:** PC (Windows)  
**Developer:** Invictus Games Ltd. (`Invictus-Games Ltd. 2005-2020` in exe)  
**Publisher:** Aeria Games (F2P operator)  
**Year:** 2008  
**Engine:** Invictus Engine (`DFEngine.dll`)

---

## 1. Game Engine

**Engine:** Invictus Engine (verified: `DFEngine.dll` 725 KB + Invictus copyright in exe)  
- **Middleware (verified via binary/DLL evidence):**
  - **Bink Video** (engine-level: `Bink` ×23 in DFEngine.dll)
  - **FMOD Ex** (`fmodex.dll` + `fmod_event.dll` shipped; engine loads dynamically — zero FMOD strings in exe)
  - **SpeedTree** (`SpeedTreeRT.dll` + `SpeedTree_setRenderMode` in exe — vegetation)
  - **Steamworks** (`SteamManager_Initialize/Shutdown/RunCallbacks` + `steam_api.dll`)
  - **zlib** (compression)
  - **DirectX 9** (VC71 CRT era, `xinput` ×2)
- **Executable:** `ProjectTorque.exe` (10.6 MB)
- **Container:** `Packages.lpack` (3.8 KB index) + `packages/` + `music/` + `tutorials/`
- **Config:** `sil.dat` (260 KB)
- **Splash:** `splash.bmp`

**Falsified:** `Nx` ×227 = opcode noise (no PhysX). `Lua` ×3 / `Ogg` ×1 = noise. `Torque` ×4 = vehicle-physics terms (`setTorqueFactors` — gameplay, not Torque engine). `Ogre` ×0. No Havok/Miles/Unreal.

---

## 2. Key Technical Details

- Invictus Engine lineage (same house as CRC 2005's Invictus Engine in the xlsx) with SpeedTree vegetation + Bink + FMOD + Steam — lean licensed stack for a 2008 F2P MMO racer
- No Havok/PhysX: vehicle physics in-house (`setTorqueFactors` family)

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\Project Torque\ProjectTorque.exe`*  
*Engine: Invictus Engine, Invictus Games 2008*