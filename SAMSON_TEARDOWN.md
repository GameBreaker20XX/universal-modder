# SAMSON (PC, UE5) — Teardown Documentation

**Game:** SAMSON (project `CJ`)  
**Platform:** PC (Windows 64-bit)  
**Developer:** Unknown  
**Publisher:** Unknown  
**Year:** 2023+ (UE5 + DLSS Frame Generation + VS2022 toolchain)  
**Engine:** **Unreal Engine 5** (verified)

---

## 1. Game Engine

**Engine:** **Unreal Engine 5** (verified: IoStore `.ucas` 12.9 GB + Bink 2 + VS2022/vc170 plugin DLLs + DLSS-G/Streamline)  
- **Middleware (verified via file evidence — no game executable in dump):**
  - **Wwise** (full Ak DSP suite: 40+ `Ak*.dll` — ChannelRouter, ConvolutionReverb, MasteringSuite, iZotope, ASIO…)
  - **Bink 2 Video** (`Intro.bk2` 219 MB, `Startup.bk2`, localized `Warning.bk2` ×6 + `.srt` subtitles DE/ES/FR/IT/TR)
  - **NVIDIA DLSS/Streamline/Reflex** (`nvngx_dlss/d/dlssg`, `sl.*.dll` — Frame Generation era)
  - **AMD FSR/FidelityFX** (signed FFX kits)
- **Executable:** None in dump (data + engine only)
- **Container:** `CJ-Windows.ucas` (12,914,062,240 bytes) + `.utoc` + `CJ-Windows.pak` (31 MB) + `global.ucas`
- **Key art:** `CJ/Content/Splash/Splash.bmp` (896×504) — SAMSON logotype over industrial-city crime saga art (muscle car `LOVECOP2` plate, melee fight)

**Evidence from dump:**
- `Engine/{Config,Content,Plugins,Programs}` + `CJ/{Content,Plugins,Movies,Paks,Splash}` (no `Binaries/` — exe stripped from dump)
- FBI-warning videos localized ×6 = AAA publishing footprint; dev/publisher unidentified

---

## 2. Key Technical Details

- Crime-saga aesthetic (industrial city, muscle cars, melee) on a full UE5 AAA middleware stack (Wwise + DLSS-G + FSR + Bink 2)
- Complete engine/data drop with the shipping binary removed — content-side forensics only

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\Samson\` (key art + middleware DLL inventory)*  
*Engine: Unreal Engine 5, Unknown Developer*