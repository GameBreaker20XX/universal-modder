# Crash Time III (Highway Nights) — Teardown Documentation

**Game:** Crash Time III (German: Highway Nights)  
**Platform:** PC (Windows)  
**Developer:** Synetic GmbH  
**Publisher:** RTL Games / dtp entertainment  
**Year:** 2009  
**Engine:** **Synetic Engine** (verified: `Synetic` string, `.mox`/`.mtl`/`.ptx` formats, ODE physics)

---

## 1. Game Engine

**Engine:** **Synetic Engine** (Crash Time series lineage, v3)  
- **Middleware (verified via `HighwayNightsHi.exe` strings):**
  - **ODE** (Open Dynamics Engine) — 2× `ODE` strings (physics, reduced vs CT2's 82×)
  - **FMOD Ex** — 2× `fmod` (audio)
  - **Lua 5.1** — 22× `Lua`/`lua` (scripting)
  - **Synetic Formats** — 47× `mox` (models), 5× `mtl` (materials), 1× `PTX` (textures)
  - **Nx** — 57× (opcode noise, not PhysX)
  - **Bullet** — 1× (noise)
- **Executable:** `HighwayNightsHi.exe` (2.56 MB, `Synetic` ×3 in binary)
- **Container:** Loose files in `Autos/`, `Missions/`, `Scenarios/`, `Music/`, `Sounds/`, `Videos/`, `Traffic/`, `Trains/`, `stdstuff/`, `FrontEnd2/`, `DirectX/`, `Haenger/`, `Motoren2/`, `Alligator*/`, `Ben*/`, `BenKombi/`, `Buggy/`, `British*/`, `Coach/`, `Coupe_Cabrio/`, `Dreirad*/`, `Drone/`, `Executive/`, `Feuerwehr/`, `BigOffroad/`
- **Config:** `CtrlDefaults.ini`, `SetUp_Loka.ini`, `SampleVolumes.ini`, `33620_install.vdf` (Steam AppID 33620)
- **Video:** `Videos/` (Bink likely)
- **Setup:** `HN_Setup.exe` (162 KB), `HighwayNights.exe` (76 KB launcher), `HighwayNightsLow.exe` (2.5 MB low-spec build)

**Falsified:** `Nx` = noise. `Bullet` = 1× noise. No Havok/PhysX/Bink/Marmalade/Firebrand/Octane/Newton. ODE presence minimal (2×) vs CT2 — physics may be more in-house.

---

## 2. Key Technical Details

- Synetic Engine v3 (Crash Time III / Highway Nights) — iterative update of CT2 engine
- ODE physics strings greatly reduced (2× vs 82×) — possible shift to more custom vehicle physics
- Same `.mox`/`.mtl`/`.ptx`/Lua pipeline as CT2
- Two exe builds: `HighwayNightsHi.exe` (high-spec) + `HighwayNightsLow.exe` (low-spec)
- Steam AppID 33620

---

*Generated from `HighwayNights/HighwayNightsHi.exe` (2.56 MB)*  
*Engine: Synetic Engine, Synetic GmbH 2009*