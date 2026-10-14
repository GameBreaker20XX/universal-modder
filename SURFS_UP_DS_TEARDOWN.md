# Surf's Up (NDS) — Teardown Documentation

**Game:** Surf's Up (USA)  
**Platform:** Nintendo DS  
**Developer:** Unknown (Ubisoft-published; middleware-heavy profile)  
**Publisher:** Ubisoft  
**Year:** 2007  
**Format:** NDS ROM (33,554,432 bytes, 7,409 files)

---

## 1. Game Engine

**Engine:** Unknown licensed-heavy DS engine (unconfirmed — no dev strings recovered)  
- **Middleware (verified via file evidence):**
  - **Mobiclip/Actimagine Video** (`.vx` ×45 — largest Mobiclip footprint in the DS set)
- **ROM:** 32 MB, ARM9 1,535,096 bytes (largest DS ARM9 in the batch — simulation-heavy)
- **Object store:** 7,326 extensionless files (data-driven object design)
- **Animation:** `.aap` + `.atb` (14 each), `.apl` + `.atk` (3 each — player/attack script pairs?)
- **Audio:** `.sdat` (1) + `.bin` (3)

**Evidence from dump:**
- Mobiclip video at Surf's Up scale (45 files) points to a licensed-engine pipeline (Ubisoft's DS movie-game stack), not a bespoke build
- Extensionless-object design mirrors the Objectnaut pattern at smaller scale

---

*Generated from `Surf's Up (USA).nds`*  
*Engine: Unknown (Mobiclip-licensed DS pipeline), 2007*