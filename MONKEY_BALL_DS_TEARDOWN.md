# Super Monkey Ball: Touch & Roll (NDS) — Teardown Documentation

**Game:** Super Monkey Ball: Touch & Roll (USA)  
**Platform:** Nintendo DS  
**Developer:** Sega (Amusement Vision lineage)  
**Publisher:** Sega  
**Year:** 2005  
**Format:** NDS ROM (67,108,864 bytes, 2,651 files)

---

## 1. Game Engine

**Engine:** Sega proprietary DS engine (LZ-compressed asset pipeline)  
- **Middleware:** **NONE** — Nintendo NitroSDK only (evidenced: `.nsbmd`, `.nbfc`/`.nbfp`, `.sdat`)
- **ROM:** 64 MB, ARM9 909,432 bytes
- **Compression:** `.lz` (2,626 files — nearly the entire ROM individually LZ-compressed)
- **Level formats:** `.grd` + `.pln` + `.rdp` (6 each — grid/plane/map triplets per stage)
- **3D:** `.nsbmd` (4 shared models)

**Evidence from dump:**
- LZ-per-file packaging (2,626/2,651 files) — decompress-on-load stage design fitting Monkey Ball's discrete-level structure
- Minimal model count (4 NSBMD) — stages built from `.grd`/`.pln`/`.rdp` grid data, not meshes

---

*Generated from `Super Monkey Ball - Touch & Roll (USA).nds`*  
*Engine: Sega proprietary DS engine (NitroSDK), Sega 2005*