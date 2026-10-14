# Pony Friends 1 + 2 (NDS) — Teardown Documentation

**Games:** Pony Friends (USA) + Pony Friends 2 (USA)  
**Platform:** Nintendo DS  
**Developer:** Unknown (`.rbh`/`.xml` pipeline both titles)  
**Publisher:** Eidos Interactive (franchise publisher; unconfirmed from binary)  
**Years:** 2007 / 2009 (est.)  
**Format:** NDS ROMs (64 MB each)

---

## 1. Game Engine

**Engine:** Shared custom DS engine across both titles (identical format profile)  
- **Middleware:** **NONE** — NitroSDK only (evidenced: `.sdat`, `.nbfc`/`.nbfp`)
- **Pony Friends 1:** ARM9 628,636 bytes, 3,831 files — `.rbh` (2,060), `.map` (672), `.d` (589), `.tga` (187), `.swav` (164), `.xml` (136), `.vx` (8 Mobiclip), `.wav` (8)
- **Pony Friends 2:** ARM9 675,144 bytes, 5,789 files — `.rbh` (5,222!), `.tga` (233), `.swav` (187), `.xml` (140)
- **Config:** XML-driven (136–140 files) + `.args` (3)
- **Video:** Mobiclip `.vx` (sequel drops it — PF2 has none)
- **Audio:** `.swav` (streamed WAV) + `.sdat`

**Evidence from dump:**
- `.rbh`-dominant design (resource bundle hash?) scaling 2,060 → 5,222 files between titles — same engine, grown content
- `.map` + `.d` level data present in PF1 only (restructured in sequel)

---

*Generated from `Pony Friends (USA).nds` + `Pony Friends 2 (USA).nds`*  
*Engine: Shared custom DS engine (NitroSDK), Unknown Developer*