# Mario Power Tennis (GameCube RVZ) — Teardown Documentation

**Game:** Mario Power Tennis (GameCube, Rev 1)  
**Platform:** Nintendo GameCube  
**Developer:** Camelot Software Planning  
**Publisher:** Nintendo  
**Year:** 2004  
**Format:** RVZ v1 (Dolphin compressed GC image, 630,381,740 bytes)

---

## 1. Game Engine

**Engine:** Camelot proprietary GameCube engine (unconfirmed — RVZ contents unextracted, no DolphinTool available)  
- **Container:** Dolphin RVZ v1 (lossless GC image compression)
- **Middleware:** Nintendo SDK baseline (assumed, unverified)

## 2. Documentation Notes

- Extraction path: DolphinTool `convert -i ...rvz -o ...iso`, then GC-REVOLUTION forensics (boot.bin → GM4P/GM4E game ID, `opening.bnr`, THP video, DSP audio)
- Camelot Mario-sports lineage (Mario Golf/Tennis shared tech family)

---

*Generated from `Mario Power Tennis (GameCube) (Rev 1).rvz` (container-level only)*  
*Engine: Camelot proprietary GameCube (unverified without extraction)*