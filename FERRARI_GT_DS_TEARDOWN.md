# Ferrari GT Evolution (NDS) — Teardown Documentation

**Game:** Ferrari GT - Evolution (USA Rev 1)  
**Platform:** Nintendo DS  
**Developer:** Unknown (French-leaning micro-studio profile; ROM title `FERRARI GT`, code KFRE, maker `GL`)  
**Publisher:** Unknown  
**Year:** Unknown (Rev 1)  
**Format:** NDS ROM (15,551,488 bytes, 13 files)

---

## 1. Game Engine

**Engine:** Custom micro-studio DS engine (unconfirmed — no dev strings recovered)  
- **Middleware:** **NONE** — NitroSDK only (evidenced)
- **ROM:** 15.5 MB, ARM9 1,230,752 bytes, tiny 13-file layout
- **Config:** `ecp/*.cfg` (`champion/game/ia/tuning` — `ia` = French *intelligence artificielle*, hinting at a French-speaking developer)
- **Data:** `6R67.DAT` + `.OFF`, `nftr/` fonts (3), BLZ manual pages, `.sdat` + `.wav` audio
- **Distribution:** NO download-play stubs (no `.srl`) — single-card only

**Evidence from dump:**
- NDS header: title `FERRARI GT`, game code KFRE, maker GL
- Minimal footprint (13 files) + plaintext tuning configs = small-team arcade racer profile

---

## 2. Documentation Notes

- Possible Gameloft-adjacent mobile-port lineage (15 MB scope matches Gameloft DS ports) — unconfirmed, no strings to prove it
- Narrowest ROM in the DS set; notable for shipping raw `.wav` alongside `.sdat`

---

*Generated from `Ferrari GT - Evolution (USA) (Rev 1).nds`*  
*Engine: Custom DS engine (NitroSDK), Unknown Developer*