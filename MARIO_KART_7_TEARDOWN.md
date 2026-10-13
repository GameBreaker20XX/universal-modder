# Mario Kart 7 (3DS, SD-installed) — Teardown Documentation

**Game:** Mario Kart 7 (00040000-00030700 + 5MB update)  
**Platform:** Nintendo 3DS  
**Developer:** Nintendo EAD  
**Publisher:** Nintendo  
**Year:** 2011  
**Format:** SD-installed eShop title (per-console encrypted)

---

## 1. Game Engine

**Engine:** Nintendo EAD proprietary MK7 engine (PICA200, stereoscopic 3D)  
- **Middleware:** NitroSDK (standard; binary unverifiable — SD crypto)
- **Install:** 638 MB app + 5 MB update (`0004000e-00030700`), extdata `00000307` (3 files)
- **Graphics:** Forward+ style 60fps stereoscopic 3D showcase
- **Audio:** CSND (BCSAR archive, typical)
- **Scripting:** None (C++ only)
- **Physics:** Custom kart physics (glider/underwater additions in MK7)

**Evidence from dump:**
- Title ID `00040000-00030700` confirmed from console (user-checked)
- Largest single app on the card after ACNL:WA; update present (v1.1 balance patch era)

---

## 2. Documentation Notes

- **Base game for CTGP-7** (see `CTGP7_TEARDOWN.md`) — the mod's `gamefs/` overrides this title's RomFS
- No binary analysis possible (SD content encrypted without console keys)
- First-party Nintendo EAD network play (NEX) title

---

*Generated from `.../nintendo 3ds/.../title/00040000/00030700` (console-verified name)*  
*Engine: Nintendo EAD proprietary 3DS engine, Nintendo EAD 2011*