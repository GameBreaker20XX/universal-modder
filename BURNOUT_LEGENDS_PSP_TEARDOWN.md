# Burnout Legends (PSP) — Teardown Documentation

**Game:** Burnout Legends (USA)  
**Platform:** PlayStation Portable  
**Developer:** Criterion Games  
**Publisher:** Electronic Arts  
**Year:** 2005  
**Engine:** Criterion RenderWare (PSP) — `EBOOT.BIN` header `Burnout`, EA middleware stack

---

## 1. Game Engine

**Engine:** **RenderWare** (Criterion PSP branch) — verified by file formats and EA lineage  
- **Middleware (verified via ISO contents):**
  - **RenderWare** (`.txd` texture dictionaries, `.kfs` Khao format scenes)
  - **EA Music** (`.mus` — 23 licensed tracks: `EATrax00`–`EATrax23`)
  - **EA VDB** (`.vdb.xml` + `.bin` — audio bank descriptors)
  - **MPEG-2 Video** (`.m2v` — 4 regional intros: EU/JP/KO/US)
  - **PMF Video** (`.pmf` — PSP native video: `counlock.pmf`, `ICON1.PMF`)
  - **ATRAC3+** (`libatrac3plus.prx` module)
- **Executable:** `EBOOT.BIN` (5.1 MB, header `~PSP` + `Burnout`, 71× `EA` strings)
- **Container:** Loose files in `PSP_GAME/USRDIR/data/` + `music/` + `ovid/`
- **Key Formats:**
  - `.txd` — RenderWare Texture Dictionary (Frontend.txd 4.7 MB, Global.txd 976 KB, DemoScrn.txd 529 KB)
  - `.kfs` — Khao Format Scene (After.kfs, Intro.kfs)
  - `.bin` — Binary data (LoadScrn.bin 2.5 MB, stagehed.bin 401 KB, PrgData.bin 22 KB, upload.dat 5 MB)
  - `.vdb.xml` — Audio bank index (88 KB)
  - `.mus` — EA Music container (ATRAC3+ encoded)

---

## 2. Key Technical Details

- Criterion's RenderWare PSP port — same engine family as Burnout Dominator PSP
- Licensed soundtrack as loose `.mus` files (EA Trax branding)
- Video in both MPEG-2 (`.m2v`) and PSP PMF (`.pmf`) formats
- `amodule/` PRX modules for audio/video/codec support (atrac3plus, mpeg, pspnet_adhoc*)
- No Lua/FMOD/Havok/PhysX/Bink/Marmalade strings in EBOOT

---

*Generated from `Burnout Legends (USA) (En,Fr,De,Es,It,Nl) (v2.00).iso` (505 MB)*  
*Engine: RenderWare (Criterion PSP), Criterion Games 2005*