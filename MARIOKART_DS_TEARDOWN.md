# Mario Kart DS (Stock, USA) — Teardown Documentation

**Game:** Mario Kart DS (USA, Australia)  
**Platform:** Nintendo DS  
**Developer:** Nintendo EAD  
**Publisher:** Nintendo  
**Year:** 2005  
**Format:** NDS ROM (33,554,432 bytes, 606 files)

---

## 1. Game Engine

**Engine:** Nintendo EAD proprietary NDS engine (MKDS)  
- **Middleware:** **NONE** — Nintendo NitroSDK only
- **ROM:** 32 MB, ARM9 947,508 bytes
- **Course archives:** `.carc` (286 — the format CTGP Nitro mods build on)
- **Models/textures:** `.nsbmd` (82), `.nsbtx` (56), `.nsbca` (21), `.nsbma` (2), `.nsbtp` (6)
- **2D/UI:** `.nclr` (35), `.ncgr` (33), `.nscr` (32)
- **Parameters:** `.prm` (8 — also reused by CTGP mods)

**Evidence from dump:**
- Stock layout that the CTGP Nitro ROM hacks (`CTGP_NITRO_TEARDOWN.md`) preserve: `.carc` course packs + `.prm` params are native MKDS formats, not mod inventions
- Nitro Wi-Fi-era online stubs (DWC shapes in ARM9 region, unconfirmed by strings)

---

## 2. Key Technical Details

- **Modding baseline**: documents the stock formats that CTGP Nitro Revolution (626 files) and CTGP Nitro (930 files) extend
- First-party Nintendo EAD network-play (Nintendo WFC) title

---

*Generated from `Mario Kart DS (USA, Australia).nds`*  
*Engine: Nintendo EAD proprietary NDS engine, Nintendo EAD 2005*