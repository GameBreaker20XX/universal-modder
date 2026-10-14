# Final Fantasy Type-0 (PSP CHD) — Teardown Documentation

**Game:** Final Fantasy Type-0  
**Platform:** PlayStation Portable (MAME CHD compressed dump)  
**Developer:** Square Enix  
**Publisher:** Square Enix  
**Year:** 2011 (Japan; English fan translation / HD remaster 2015)  
**Format:** CHD v5 (`MComprHD`, 2,468,825,699 bytes — needs `chdman` to extract)

---

## 1. Game Engine

**Engine:** Square Enix proprietary PSP engine (unconfirmed — CHD contents unextracted, no chdman available)  
- **Container:** MAME Compressed Hunks of Data v5 (block size from header)
- **Middleware:** Unknown (PSP-native audio/video expected: ATRAC3/PMF)

## 2. Documentation Notes

- xlsx carries this title as Crystal Tools (prior data, unverified here)
- Extraction path: `chdman extracthd -i 'Final Fantasy Type-0.chd' -o type0.iso`, then UMD forensics (PARAM.SFO → ULJM/NPJH disc ID, BOOT.BIN strings)

---

*Generated from `Final Fantasy Type-0.chd` (container-level only)*  
*Engine: Square Enix proprietary PSP (unverified without extraction)*