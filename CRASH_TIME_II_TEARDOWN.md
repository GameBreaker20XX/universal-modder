# Crash Time II (Burning Wheels) — Teardown Documentation

**Game:** Crash Time II (German: Burning Wheels)  
**Platform:** PC (Windows)  
**Developer:** Synetic GmbH  
**Publisher:** RTL Games / dtp entertainment  
**Year:** 2008  
**Engine:** **Synetic Engine** (verified: `Synetic` string, `.mox`/`.mtl`/`.ptx` formats, ODE physics)

---

## 1. Game Engine

**Engine:** **Synetic Engine** (Crash Time series lineage)  
- **Middleware (verified via `BurningWheelsHi.exe` strings):**
  - **ODE** (Open Dynamics Engine) — 82× `ODE` strings (physics)
  - **FMOD Ex** — 2× `fmod` (audio)
  - **Lua 5.1** — 24× `Lua`/`lua` (scripting)
  - **Synetic Formats** — 55× `mox` (models), 5× `mtl` (materials), 1× `PTX` (textures)
  - **Nx** — 13× (opcode noise, not PhysX)
  - **Bullet** — 0 (1× in CT3 only)
- **Executable:** `BurningWheelsHi.exe` (2.58 MB, `Synetic` ×3 in binary)
- **Container:** Loose files in `Autos/`, `Missions/`, `Scenarios/`, `Music/`, `Sounds/`, `Videos/`, `Traffic/`, `Trains/`, `stdstuff/`, `FrontEnd2/`, `DirectX/`, `Haenger/`, `Motoren2/`, `Coach/`, `Ben*/`, `Buggy/`, `Coupe*/`, `Drone/`, `Executive/`, `FormelC11/`, `Geldtransporter/`, `Gianluca/`, `Gokart/`, `GrandSport/`, `Alligator*/`
- **Config:** `CtrlDefaults.ini`, `SetUp_Loka.ini`, `SampleVolumes.ini`, `11390_install.vdf` (Steam AppID 11390)
- **Video:** `Videos/` (Bink likely, not confirmed in exe)
- **Setup:** `BW_Setup.exe` (110 KB), `WMCodec/` (Windows Media codecs)

**Falsified:** `Nx` = noise. No Havok/PhysX/Bink/Marmalade/Firebrand/Octane/Newton. `Bink` = 0 in exe (but Videos/ folder suggests Bink video).

---

## 2. Key Technical Details

- Synetic Engine v2 (Crash Time II / Burning Wheels) — same core as CT1/CT3/Undercover
- ODE physics confirmed (82× strings) — retracts earlier Havok claims for CT1
- Lua scripting for missions/scenarios
- `.mox`/`.mtl`/`.ptx` pipeline validated by Synetic General tools (WR PTXTool, AFC11 managers)
- Steam AppID 11390 (install.vdf)

---

*Generated from `Crash Time II/BurningWheelsHi.exe` (2.58 MB)*  
*Engine: Synetic Engine, Synetic GmbH 2008*