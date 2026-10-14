# TrackMania Wii – Build to Race (Wii) — Teardown Documentation

**Game:** TrackMania: Build to Race (USA En/Fr/Es)  
**Platform:** Nintendo Wii  
**Developer:** Firebrand Games  
**Publisher:** Focus Home Interactive (EU) / City Interactive? (US — unconfirmed)  
**Year:** 2010  
**Format:** RVZ (Dolphin compressed Wii image, 776 MB)

---

## 1. Game Engine

**Engine:** Firebrand Octane Engine, Wii variant (developer + lineage evidence; binary unverifiable — RVZ needs Dolphin toolchain)  
- **Middleware:** NitroSDK-descended Wii SDK (Revolution OS) standard; no licensed middleware evidenced at container level
- **Container:** `.rvz` (Dolphin RVZ — lossless compressed Wii disc image)
- **Scripting:** Lua expected (Octane family trait; unconfirmed without extraction)

**Evidence from dump:**
- Firebrand developed all TrackMania handheld/console ports of the era (DS 2009-10 on Octane — see `TRACKMANIA_DS_TEARDOWN.md`, `GRID_DS_TEARDOWN.md`); Wii title shares the lineage
- RVZ container verifies as a real Wii image (776 MB, Dolphin-compressed)

---

## 2. Documentation Notes

- Published as *TrackMania: Build to Race* (US) / *TrackMania Wii* (EU)
- Full analysis pending Dolphin `wit`/` DolphinTool` extraction (WBFS→files, then Octane `vfs.zip`/`.luac` checks)

---

*Generated from `TrackMania - Build to Race (USA) (En,Fr,Es).rvz`*  
*Engine: Firebrand Octane Engine (Wii), Firebrand Games 2010 — https://en.wikipedia.org/wiki/Firebrand_Games*