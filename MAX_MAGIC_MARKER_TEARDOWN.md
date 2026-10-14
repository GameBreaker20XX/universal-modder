# Max & the Magic Marker (NDS) — Teardown Documentation

**Game:** Max & the Magic Marker (USA En/Fr/De/Es/Nl)  
**Platform:** Nintendo DS  
**Developer:** Press Play  
**Publisher:** Ubisoft  
**Year:** 2010  
**Format:** NDS ROM (33,554,432 bytes, 183 files)

---

## 1. Game Engine

**Engine:** Press Play custom DS engine (unconfirmed — no dev strings recovered)  
- **Middleware:** **NONE** — Nintendo NitroSDK only (evidenced: `.sdat` audio)
- **ROM:** 32 MB, ARM9 545,208 bytes, 183 files
- **Levels:** `.bg_lz` (116 — LZ-compressed backgrounds, the dominant format)
- **Objects/scenes:** `.obj` + `.scn` (16 each — draw-physics object/scene pairs, the marker mechanic)
- **Textures:** `.texb` + `.tex` (4 each), `.bg` (1)
- **Locale:** `.loc` (2), raw `.wav` (1) + `.sdat`

**Evidence from dump:**
- Drawn-object/scene split (`.obj`/`.scn`) mirrors the game's draw-your-own-physics-objects design
- Backgrounds as individually compressed blobs (`.bg_lz`) — streaming-friendly level chunks

---

*Generated from `Max & the Magic Marker (USA) (En,Fr,De,Es,Nl).nds`*  
*Engine: Press Play custom DS engine (NitroSDK), Press Play 2010*