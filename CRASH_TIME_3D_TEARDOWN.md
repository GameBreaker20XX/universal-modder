# Crash Time 3D (3DS CIA) — Teardown Documentation

**Game:** Crash Time 3D (CTR-P-AFBP, v0.0.0, Worldwide)  
**Platform:** Nintendo 3DS  
**Developer:** Unknown (not evidenced — encrypted CIA)  
**Publisher:** Unknown (RTL franchise holder; unconfirmed from binary)  
**Year:** 2012 (3DS Crash Time release window)  
**Format:** CIA, `0004000000066200` (107,857,152 bytes)

---

## 1. Game Engine

**Engine:** Unknown (3DS) — content fully encrypted, no NCCH/ExeFS/RomFS plaintext  
- **Container:** Real CIA (0x20-byte header pattern matching the verified CIA batch; 107 MB content)
- **Middleware:** Unknown (NitroSDK baseline assumed, unverified)

**Evidence from dump:**
- Product code CTR-P-AFBP, worldwide build, v0.0.0
- Zero `NCCH`/`SMDH`/`IVFC`/`.code`/middleware plaintext across 107 MB — same encryption wall as the MK7/SM3DL/ACNL CIA batch

---

## 2. Documentation Notes

- Handheld Crash Time spinoff contemporaneous with the Synetic PC lineage (CT5 era) — developer/engine lineage to the PC games unconfirmed
- No relation claimable to Synetic's 3D Landscape Engine without decryption (console keys + seeddb)

---

*Generated from `0004000000066200 Crash Time 3D (CTR-P-AFBP) (v0.0.0) (W).standard.cia`*  
*Engine: Unknown 3DS engine (encrypted CIA)*