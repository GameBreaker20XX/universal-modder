# Mercenaries 2: World in Flames (PC) — Teardown Documentation

**Game:** Mercenaries 2: World in Flames  
**Platform:** PC (Windows)  
**Developer:** Pandemic Studios (`Pandemic_CentralTechAndTools`, `Pandemic Studios, Inc.`)  
**Publisher:** Electronic Arts  
**Year:** 2008  
**Engine:** Pandemic Pangea engine (verified: `D:\projects\Mercs2_PC\Pangea\Src\Pc` build paths)

---

## 1. Game Engine

**Engine:** Pandemic Pangea in-house engine (verified via source paths)  
- **Middleware (verified via binary/DLL evidence):**
  - **Havok 4.x** (`Havok-4.1.0-r1` + `Havok-4.5.0-b1` version strings — animation/HKX)
  - **Bink Video** (`MovieBink%i`, `%sMovies\%s.bik`, `Bink::Start()` + `binkw32.dll`)
  - **Ogg Vorbis + MP3** (`ogg.dll`, `vorbis.dll`, `vorbisfile.dll`, `mpglib.dll` — engine audio codecs)
  - **SecuROM** (×47: profiler pipe, `Software\SecuROM` — real DRM)
  - **Games for Windows Live** (`GDFBinary.dll`)
  - **DirectX 9** (`D3DX` ×98; debug `d3dx9d_*` + retail DLLs side by side)
- **Executable:** `Mercenaries2.exe` (53,944,080 bytes, unpacked) + `Mercenaries2.exe_` backup
- **Scripting:** None evidenced (`Lua` ×68 = x86 code-byte noise, no Lua API/version strings)
- **Physics:** Havok 4.x (no PhysX strings)

**Falsified:** `XACT` ×62 = Windows HRESULT noise. `CRI` ×40 = EA DLC/store strings (`fcms`, `LONG/SHORT_DESCRIPTION` — EA First Class Management, not CRIWARE). `Nx` ×129 = opcode noise. No RenderWare (×0/53 MB), FMOD, Miles, Steam, Unreal, Ogg→(real DLLs, see above).

**Evidence from dump:**
- `Data/`, `Extras/`, `Precache/`, `Support/` dirs; `Mercs2.ini` (1.3 KB), `GL.ini` (167 KB), `d3d.log`
- Modded d3d9.dll (ENB-style proxy), `paul.dll`, `winui.dll`, VC71/VC80 CRT mix, scene URL + HOW-TO file (third-party artifacts)

---

## 2. Key Technical Details

- **Pangea + Havok 4.x + Bink + SecuROM** = the Pandemic PC stack; RenderWare fully exited (zero references — same pattern as Criterion's Paradise finding)
- CentralTechAndTools strings place it on Pandemic's shared-tech branch (not a one-off fork)

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\Mercenaries 2 World in Flames\Mercenaries2.exe`*  
*Engine: Pandemic Pangea + Havok 4.x, Pandemic Studios 2008*