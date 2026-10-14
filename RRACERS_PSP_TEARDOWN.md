# Ridge Racers 1 + 2 (PSP) — Teardown Documentation

**Games:** RIDGE RACER (ULUS10001, v1.00, FW 1.00) + RIDGE RACER 2 (UCES00422, v1.00, FW 2.71)  
**Platform:** PlayStation Portable (RR1 among the first US PSP titles — ULUS10001)  
**Developer:** Namco  
**Publisher:** Namco / Sony (RR2: Sony publisher per UCES ID)  
**Years:** 2004 (RR1) / 2006 (RR2)  
**Format:** UMD ISOs (906 MB / 1.52 GB)

---

## 1. Game Engine

**Engine:** Namco in-house PSP engine + **nuSound** streaming audio (verified in decrypted BOOT.BINs)  
- **Middleware (verified via binary evidence):**
  - **nuSound** (`nuSoundStreamReady`, `nuSoundStreamStart` — Namco streaming-audio system; `Ready` ×9 are these, NOT Ready at Dawn)
  - **PMF Video** (`.pmf` ×13/×15)
  - **ATRAC3 Audio** (`.at3` + `sceAtrac3plus`/`sceSasCore` imports)
- **Executables:** decrypted BOOT.BINs (2.59/2.73 MB, string-readable — unpacked, unlike Square/EA PSP binaries)
- **Modules:** 34 `.prx` (RR1 — Namco libraries) + `.dat`
- **Physics/scripting:** Unconfirmed (`Nx` ×5 in RR2 = opcode noise; no Havok/PhysX/Lua)

**Evidence from dump:**
- `PARAM.SFO`: ULUS10001/FW 1.00 (RR1 — first-wave US PSP title), UCES00422/FW 2.71 (RR2 Europe)
- RR1's 34 PRX modules vs RR2's leaner layout — engine consolidation between titles

---

## 2. Key Technical Details

- nuSound evidence links the PSP engine to Namco's in-house audio lineage (distinct from Firebrand/Cellius Ridge Racers — franchise engine-hopping, handheld chapter)
- Unpacked BOOT.BINs make these the most analyzable PSP binaries in the set

---

*Generated from `Ridge Racers 1 (USA)...iso` + `Ridge Racers 2 (Europe, Australia)...iso` (BOOT.BIN strings + PARAM.SFO)*  
*Engine: Namco in-house PSP + nuSound, Namco 2004/2006*