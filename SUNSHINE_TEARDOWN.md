# Super Mario Sunshine (GameCube RVZ) — Teardown Documentation

**Game:** Super Mario Sunshine (USA)  
**Platform:** Nintendo GameCube  
**Developer:** Nintendo EAD  
**Publisher:** Nintendo  
**Year:** 2002  
**Format:** RVZ (Dolphin compressed GC image, 1,176,265,108 bytes)

---

## 1. Game Engine

**Engine:** Nintendo EAD proprietary GameCube engine (Super Mario 64 lineage, FLUDD-era iteration) — unconfirmed from binary (RVZ unextracted, no DolphinTool available)  
- **Container:** Dolphin RVZ (lossless GC image compression)
- **Middleware:** Nintendo SDK baseline (assumed, unverified)

## 2. Documentation Notes

- Extraction path: DolphinTool `convert -i ...rvz -o ...iso`, then GC-REVOLUTION forensics (boot.bin → GMSE01 game ID, `opening.bnr`, THP video, DSP audio)
- Sibling container to the Mario Power Tennis RVZ (`MPTENNIS_TEARDOWN.md`)

---

*Generated from `Super Mario Sunshine (USA).rvz` (container-level only)*  
*Engine: Nintendo EAD proprietary GameCube (unverified without extraction)*