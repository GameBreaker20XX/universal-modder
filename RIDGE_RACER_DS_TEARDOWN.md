# Ridge Racer DS (NDS) — Teardown Documentation

**Game:** Ridge Racer DS (USA, Europe)  
**Platform:** Nintendo DS  
**Developer:** Namco (in-house DS team — proprietary `ds*` pipeline, NOT Firebrand)  
**Publisher:** Namco  
**Year:** 2004 (DS launch window)  
**Format:** NDS ROM (33,554,432 bytes, 637 files)

---

## 1. Game Engine

**Engine:** Namco proprietary DS engine (`ds*` container family)  
- **Middleware:** **NONE** — Nintendo NitroSDK only (evidenced: `.nbfc`/`.nbfp`, `.srl`, `.txt`)
- **ROM:** 32 MB, ARM9 670,360 bytes
- **Containers:** `.lot` (271 — level/track lots?), `.dsbc` (116) / `.datc` (112) / `.dsoc` (33) / `.dstc` (9) / `.dsb` (7) / `.dso` (2) / `.dst` (2) — DS-prefixed binary chunks
- **Data:** `.dat` (66), `.bin` (15)

**Evidence from dump:**
- Entirely bespoke container family — zero overlap with the Firebrand Octane profile (no `vfs.zip`, no `.luac`, no `.dcsc`, no NitroSDK 2D/3D model formats), confirming a separate Namco in-house effort predating the Firebrand NDS era
- No download-play content beyond a single `.srl`

---

## 2. Key Technical Details

- Franchise engine-hopping case study continues: arcade proprietary → DS proprietary (Namco) → 3DS proprietary (Namco) → Octane (Firebrand, Unleashed) → Cellius (Vita) → Unity (Draw & Drift) → Bugbear/ROMU (Unbounded)
- The `ds*` family (`.dsbc`/`.datc`/`.dsoc`/`.dstc`) is a clean reverse-engineering target (637 files, small ROM)

---

*Generated from `Ridge Racer DS (USA, Europe).nds`*  
*Engine: Namco proprietary DS engine (NitroSDK), Namco 2004*