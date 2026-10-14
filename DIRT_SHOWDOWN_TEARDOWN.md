# DiRT Showdown (PC) — Teardown Documentation

**Game:** DiRT Showdown  
**Platform:** PC (Windows, Steam)  
**Developer:** Codemasters  
**Publisher:** Codemasters  
**Year:** 2012  
**Engine:** EGO Engine (Neon lineage, verified)

---

## 1. Game Engine

**Engine:** EGO Engine (verified: `Ego` ×19, `Neon` threading/memory-heap strings, `Codemasters` ×13, zero `Ego`-less alternatives)  
- **Middleware (verified via binary/DLL evidence):**
  - **Bink Video** (`Bink` ×20 API imports + `binkw32.dll` 226 KB)
  - **Ogg Vorbis** (`ogg.dll`, `vorbis.dll`, `vorbisfile.dll`; CMStream banked audio)
  - **Steamworks** (`Steam` ×32 + `steam_api.dll`; `SteamLobbyHostName` multiplayer)
  - **DirectX 9/11** (`D3DX` ×7, `d3dcompiler` imports; `showdown_avx.exe` AVX build)
  - **Games for Windows Live** (`game_gdf.dll` — GDF legacy)
  - **Codemasters online** (`dbxLive32.dll`)
- **Executables:** `showdown.exe` (15.3 MB) + `showdown_avx.exe` (15.4 MB) + example benchmark XML
- **Container:** `win_000.nfs` patch container + `raceload.jpk`
- **Configs:** `car_monitor_setup.xml`, `surface_materials.xml` (63 KB), `wet_materials_remap.xml`, `game_version.xml`, `install.vdf`, `steam_api.ini`
- **Physics:** In-house (no Havok/PhysX strings)
- **Scripting:** None found (C++ only; no Lua)

**Falsified:** `CRI` ×13 = binary noise. `Ogg` ×2 = noise. `XACT` ×1 = noise (`/root.ego` UI path nearby). `fmod` ×2 = CRT math. `Miles` ×0. No FMOD/Wwise/Havok/PhysX/Lua/Unreal.

**Evidence from dump:**
- 23 asset dirs (`cars/`, `tracks/`, `audio/`, `gymkhana/`, `replay/`, `shaderpack/`, `video/`, `network/`, `gameconfig/`, `language/`...)
- `ni.mmo` (25 MB region data)

---

## 2. Key Technical Details

- **EGO + Neon threading** in one binary — the Neon→EGO lineage visible at strings level (`Neon NeMemoryHeap`, no standalone `Ego` engine name strings because EGO *is* the Neon evolution)
- Hoonigan/gymkhana-era DiRT spinoff on the full Codemasters online stack (Steam + dbxLive + GFWL remnants)

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\DiRT Showdown\showdown.exe`*  
*Engine: EGO Engine (Neon lineage), Codemasters 2012*