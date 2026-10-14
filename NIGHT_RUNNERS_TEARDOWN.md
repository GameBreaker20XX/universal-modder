# NIGHT-RUNNERS PROLOGUE (PC) — Teardown Documentation

**Game:** NIGHT-RUNNERS PROLOGUE  
**Platform:** PC (Windows 64-bit)  
**Developer:** Planet Jem Software (`app.info`)  
**Publisher:** Unknown  
**Year:** Unknown (Unity 2018.4 era)  
**Engine:** **Unity 2018.4.26f1** (IL2CPP)

---

## 1. Game Engine

**Engine:** **Unity 2018.4.26f1** (verified: version string in `globalgamemanagers`; IL2CPP `GameAssembly.dll` 37 MB + `UnityPlayer.dll`)  
- **Middleware:** Unity standard set (version-evidenced; no third-party DLLs in dump)
- **Executable:** `NIGHT-RUNNERS PROLOGUE.exe` (650 KB bootstrap) + `UnityCrashHandler64.exe`
- **Container:** 20 levels (`level0`–`level19`) + `globalgamemanagers.assets`
- **Content:** `_LIVERY_TEMPLATES/` (livery customization content)
- **Scripting:** **C#** (IL2CPP)
- **Physics:** Unity PhysX (built-in)

---

## 2. Key Technical Details

- Touge-drift indie prologue on Unity 2018.4 LTS (final 2018 patch line)
- Livery-template content ships beside the build — customization-first design

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\NIGHT-RUNNERS PROLOGUE\`*  
*Engine: Unity 2018.4.26f1 (IL2CPP), Planet Jem Software*