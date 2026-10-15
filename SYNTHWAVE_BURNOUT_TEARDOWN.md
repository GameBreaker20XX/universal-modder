# Synthwave Burnout (v2021.11.24) — Teardown Documentation

**Game:** Synthwave Burnout (a.k.a. Synthwave Burnout v2021.11.24)  
**Platform:** PC (Windows 64-bit)  
**Developer:** Unknown (Unity/Unreal indie — see below)  
**Publisher:** Unknown (SteamUnlocked repack)  
**Year:** 2021 (build date)  
**Engine:** **Unreal Engine 4** (verified: `UE4` ×174, `Unreal` ×4, `UCAS` ×2 in shipping executable)

---

## 1. Game Engine

**Engine:** **Unreal Engine 4** (IoStore / `.pak` + `.ucas`/`.utoc`)  
- **Middleware (verified via `SynthwaveGame-Win64-Shipping.exe` strings):**
  - **Unreal Engine 4** — 174× `UE4`, 4× `Unreal`, 4× `Epic`
  - **PhysX / APEX** — 113× `PhysX`, 165× `physx`, 3× `APEX` (NVIDIA PhysX + APEX Clothing/Destructible)
  - **NVIDIA Aftermath** — `GFSDK_Aftermath_Lib.x64.dll` (crash diagnostics)
  - **Steamworks** — 59× `Steam`, 1× `steam`
  - **FMOD** — 4× `fmod` (minimal / legacy reference)
  - **Ogg/Vorbis** — `libogg_64.dll` (49 KB)
  - **OpenVR / Oculus** — `openvr_api.dll` (597 KB), `OVRPlugin.dll` (4.1 MB) — VR support
- **Executable:** `SynthwaveGame-Win64-Shipping.exe` (74.6 MB, `Synthwave` ×2)
- **Container:** `SynthwaveGame/Content/Paks/SynthwaveGame-WindowsNoEditor.pak` (4.46 GB) — IoStore package
- **Redist:** `_Redist/` — vcredist 2015-2019, DirectX, OpenAL, .NET 4.0
- **ThirdParty:** `PhysX3/`, `NVaftermath/`, `Oculus/`, `OpenVR/`, `Ogg/`, `Vorbis/`, `Windows/`

**Falsified:** No Unity/Godot/Cocos/Wwise/Bink/Marmalade/CRI. `UE5` = 0 (confirmed UE4).

---

## 2. Key Technical Details

- UE4 game with IoStore packaging (`.pak` 4.46 GB + `.ucas`/`.utoc` implied)
- Full PhysX/APEX stack (ApexFramework, APEX_Clothing, APEX_Destructible, APEX_Legacy, NvCloth)
- VR-ready (OpenVR + Oculus SDKs shipped)
- Steamworks integrated (59× strings)
- Repack source: `STEAMUNLOCKED` URL in folder — cracked/redistributed build
- Build date: 2021-11-24 (folder name)

---

*Generated from `Synthwave.Burnout.v2021.11.24/SynthwaveGame/Binaries/Win64/SynthwaveGame-Win64-Shipping.exe` (74.6 MB) + `.pak` (4.46 GB)*  
*Engine: Unreal Engine 4, Unknown Developer 2021*