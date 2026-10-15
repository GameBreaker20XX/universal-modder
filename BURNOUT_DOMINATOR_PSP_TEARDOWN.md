# Burnout Dominator (PSP) — Teardown Documentation

**Game:** Burnout Dominator (USA)  
**Platform:** PlayStation Portable  
**Developer:** Criterion Games  
**Publisher:** Electronic Arts  
**Year:** 2007  
**Engine:** **FusionCore** (Criterion proprietary PSP engine) — `EBOOT.BIN` header `FusionCore`

---

## 1. Game Engine

**Engine:** **FusionCore** (Criterion internal PSP engine, post-RenderWare)  
- **Middleware (verified via ISO contents):**
  - **EA Online/Connect** (`EACN/` — `bundle.big` 2.3 MB, fonts, icons, locale, PRX modules)
  - **EA Fonts** (`.mfn` — 9 font files in `EACN/fonts/`)
  - **PMF Video** (`ICON1.PMF` 272 KB)
  - **ATRAC3+** (`audiocodec.prx`, `mpegbase.prx` in `EACN/prx/kmodule/`)
- **Executable:** `EBOOT.BIN` (5.15 MB, header `~PSP` + `FusionCore`, 85× `EA` strings, 3× `lua`)
- **Container:** `EACN/bundle.big` (EA bigfile archive) + loose PRX/fonts/locale
- **Key Formats:**
  - `.big` — EA Bundle archive (EACN bundle, 2.3 MB)
  - `.mfn` — EA Font format
  - `.loc` — Localization (English.loc 32 KB)
  - PRX modules — PSP system libraries (net, adhoc, audio, video)

**Falsified:** No RenderWare/Criterion/FMOD/Havok/PhysX/Bink/Marmalade/Firebrand strings in EBOOT. `lua` ×3 = likely false positive (substrings).

---

## 2. Key Technical Details

- Successor to RenderWare on PSP — Criterion's "FusionCore" engine (name in EBOOT header)
- EA Connect (EACN) integration for online features — bundle.big + fonts + locale
- Minimal loose files — most assets packed in `bundle.big`
- 2007 build date (ISO created 2007-02-02)

---

*Generated from `Burnout Dominator (USA).iso` (691 MB)*  
*Engine: FusionCore (Criterion), Criterion Games 2007*