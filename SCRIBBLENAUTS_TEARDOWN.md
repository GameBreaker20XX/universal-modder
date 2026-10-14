# Scribblenauts Collection (NDS) — Teardown Documentation

**Game:** Scribblenauts Collection (USA)  
**Platform:** Nintendo DS  
**Developer:** 5th Cell  
**Publisher:** Warner Bros. Interactive  
**Year:** 2013 (Scribblenauts Collection: Super Scribblenauts + Scribblenauts Remix era bundle)  
**Format:** NDS ROM (67,108,864 bytes, 18,517 files)

---

## 1. Game Engine

**Engine:** 5th Cell Objectnaut (verified by profile: extensionless object store)  
- **Middleware:** **NONE** — Nintendo NitroSDK only (evidenced: `.sadl`/`.sdat`, `.sbn`?)
- **ROM:** 64 MB, ARM9 565,016 bytes, **18,517 files** (densest DS ROM in the set)
- **Object store:** 18,509 extensionless files (Objectnaut object database — every word-object as a file)
- **Packages:** `.sarc` (1), `.sbdl` (1), `.smap` (1), `.bin` (1)
- **Audio:** `.sadl` (2) + `.sdat` (2)

**Evidence from dump:**
- Extensionless-file dominance is the Objectnaut fingerprint (cf. the retail Scribblenauts scripting postmortems: tens of thousands of data-driven objects)
- Collection build (multiple Scribblenauts titles in one ROM)

---

*Generated from `Scribblenauts Collection (USA).nds`*  
*Engine: 5th Cell Objectnaut (NitroSDK), 5th Cell 2013*