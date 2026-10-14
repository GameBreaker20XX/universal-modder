# Pokémon Gen IV–V + Ranger: Guardian Signs (NDS) — Teardown Documentation

**Games:** HeartGold (IPKE) · SoulSilver (IPGE) · Platinum (CPUE) · White (IRAO, DSi-enhanced) · White 2 (IRDO) · Ranger: Guardian Signs (B3RE)  
**Platform:** Nintendo DS (/DSi for White)  
**Developers:** GAME FREAK (HG/SS/Platinum/White/White2) / Creatures Inc. (Ranger 3)  
**Publisher:** Nintendo / The Pokémon Company  
**Format:** NDS ROMs (128–512 MB)

---

## 1. Gen IV: HeartGold / SoulSilver (2009–10) + Platinum (2008)

- **Engine:** GAME FREAK proprietary DS engine (NARC-container era)
- **Middleware:** **NONE** — NitroSDK only
- **HG/SS** (128 MB, ARM9 762,644 bytes, 384 files): 265 extensionless files + `.narc` (44) + NitroSDK 2D (`.ncgr`/`.nclr`/`.nanr`/`.ncer`) + `.nsbtx`/`.nsbmd`/`.nsbca` + `.sdat`
- **Platinum** (128 MB, ARM9 1,057,784 bytes, 340 files): `.narc` (**215**) + `resdat` (30) + `cldat` (7) — same Diamond-generation profile (cf. `POKEMON_HANDHELD_TEARDOWN.md`)

## 2. Gen V: White (2010) + White 2 (2012)

- **Engine:** GAME FREAK proprietary DS engine, overlay-heavy redesign
- **Middleware:** **NONE** — NitroSDK only
- **White** (256 MB DSi-enhanced, ARM9 456,868 bytes, 247 files): **235 extensionless files** + `.narc` (3!) + DSi stubs (`.srl`, download `.char`/`.plt`)
- **White 2** (**512 MB** — largest DS ROM in the set, ARM9 472,780 bytes, 318 files): **308 extensionless files** + `.narc` (2)
- Gen V abandons NARC-per-area for extensionless overlay blobs + 3 remaining `.narc` archives

## 3. Ranger: Guardian Signs (2010, 128 MB, ARM9 421,012 bytes, 386 files)

- **Engine:** Creatures Inc. proprietary DS engine
- **Middleware:** **NONE** — NitroSDK only
- **Containers:** `.acz` (**382** — new container vs Almia's `.fsb`) + `.acf` (2) + `.sdat`

---

*Generated from Research batch (NDS headers + FAT profiles)*  
*Engines: GAME FREAK / Creatures Inc. proprietary handheld engines*