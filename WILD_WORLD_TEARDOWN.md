# Animal Crossing: Wild World (NDS) — Teardown Documentation

**Game:** Welcome to Animal Crossing: Wild World (USA) — full title *Welcome to Animal Crossing*  
**Platform:** Nintendo DS  
**Developer:** Nintendo EAD  
**Publisher:** Nintendo  
**Year:** 2005  
**Format:** NDS ROM (33,554,432 bytes, 9,504 files)

---

## 1. Game Engine

**Engine:** Nintendo EAD proprietary Animal Crossing DS engine  
- **Middleware:** **NONE** — Nintendo NitroSDK only (evidenced)
- **ROM:** 32 MB, ARM9 839,728 bytes
- **Textures:** `.nsbtx` (**3,015** — densest texture set in the DS batch, seasonal variants)
- **Archives:** `.arc` (2,064 — Nintendo ARC containers)
- **Messages:** `.bmg` (1,791 — Nintendo message binaries, all villagers/dialogue)
- **Models/anim:** `.nsbmd` (767), `.nsbca` (591), `.nsbtp` (391), `.nsbva` (42), `.nsbta`/`.nsbma` (6/4)
- **Save/event:** `.bch` + `.bsc` + `.bpl` (384/175/175 — behavior/event scripting trio?)
- **Data:** `.bin` (96)

**Evidence from dump:**
- BMG message count (1,791) + NSBTX texture count (3,015) = the full Wild World dialogue + seasonal-asset footprint
- `.bch`/`.bsc`/`.bpl` behavior triplets alongside `.nsbca` animation — event-scripting layer over the life sim

---

*Generated from `Welcome to Animal Crossing - Wild World (USA).nds`*  
*Engine: Nintendo EAD proprietary DS engine, Nintendo EAD 2005*