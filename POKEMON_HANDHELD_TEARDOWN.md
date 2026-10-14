# Pokémon Handheld Batch (DS + GBA) — Teardown Documentation

**Games:** Diamond (Rev 5) · Ranger: Shadows of Almia (NDS) · Emerald · FireRed (GBA)  
**Platforms:** Nintendo DS + Game Boy Advance  
**Developer:** GAME FREAK (Diamond/Emerald/FireRed) / Creatures Inc. (Ranger, `.fsb`/`.mes` pipeline)  
**Publisher:** Nintendo / The Pokémon Company  
**Format:** NDS ROMs (64 MB) + GBA ROMs (16 MB)

---

## 1. Pokémon Diamond (USA Rev 5, NDS, 2006)

- **Engine:** GAME FREAK proprietary DS engine
- **Middleware:** **NONE** — NitroSDK only
- **ROM:** 64 MB, ARM9 1,079,076 bytes, 269 files
- **Containers:** `.narc` (149 — Nintendo archives everywhere), `resdat` (30), `cldat` (7)
- **Assets:** `.nsbtx` (11), `.ncgr`/`.nclr` (10/8), `.nanr`/`.ncer` (5/4), `.nsbmd`/`.nsbca` (2 each), `.txt` (15), `.bin`/`.dat`
- Gen-IV landmark: NARC-containerized data design

## 2. Pokémon Ranger: Shadows of Almia (USA, NDS, 2008)

- **Engine:** Creatures Inc. proprietary DS engine (distinct pipeline from GAME FREAK's)
- **Middleware:** **NONE** — NitroSDK only
- **ROM:** 64 MB, ARM9 588,248 bytes, **7,666 files**
- **Containers:** `.fsb` (3,832!) / `.bin` (2,482) / `.lz` (883) / `.mes` (438)
- **2D:** `.ntfp`/`.ntft` (10 each), `.nclr` (4), `.nftr` (4), `.ncbr` (2), `.sdat` (1)
- Largest file count in the DS set — micro-chunked capture-loop data design

## 3. Pokémon Emerald (USA/EU, GBA, 2004, 16 MB) + FireRed (USA, GBA, 2004, 16 MB)

- **Engine:** GAME FREAK proprietary GBA engine
- **Middleware:** **NONE** — GBA BIOS only
- Gen-III pair, identical ROM size, same engine generation

---

*Generated from Research batch (NDS FAT profiles + GBA headers)*  
*Engines: GAME FREAK / Creatures Inc. proprietary handheld engines*