# Real Soccer 2009 (NDS) — Teardown Documentation

**Game:** Real Soccer 2009 (USA) — Gameloft's *Real Football 2009* under Ubisoft branding  
**Platform:** Nintendo DS  
**Developer:** Gameloft  
**Publisher:** Ubisoft  
**Year:** 2008 (2008–09 season)  
**Format:** NDS ROM (16,060,416 bytes, 388 files)

---

## 1. Game Engine

**Engine:** Gameloft proprietary DS sports engine (unconfirmed — no dev strings recovered)  
- **Middleware:** **NONE** — Nintendo NitroSDK only (evidenced)
- **ROM:** 16 MB, ARM9 1,160,608 bytes (largest ARM9 in the batch — simulation-heavy)
- **2D/UI:** `.bmp` (121!), NitroSDK 2D (`.ncgr`/`.nclr`/`.nanr`/`.ncer` ~50 each, `.nscr` 5)
- **3D:** `.mesh` (31) + `.smesh` (5) — Gameloft mesh formats, `.anim` (3)
- **Locale:** `.lang` (8)
- **Compression:** `lzma` + `blz` (2 each), `.tga` (5)

**Evidence from dump:**
- BMP-dominant UI (121 files) over a mesh-based 3D match engine — classic Gameloft DS sports split
- Multi-`lang` packaging for the Ubisoft international release

---

*Generated from `Real Soccer 2009 (USA).nds`*  
*Engine: Gameloft proprietary DS engine (NitroSDK), Gameloft 2008*