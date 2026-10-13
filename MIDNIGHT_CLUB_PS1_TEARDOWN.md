# Midnight Club: Street Racing (PS1) — Teardown Documentation

**Game:** Midnight Club: Street Racing  
**Platform:** PlayStation 1 (PSX)  
**Developer:** Angel Studios (Rockstar San Diego)  
**Publisher:** Rockstar Games  
**Year:** 2000  
**Format:** BIN/CUE (PS1 disc image)

---

## 1. Game Engine

**Engine:** Angel Studios proprietary PS1 engine  
- **Middleware:** None (custom PS1 engine)  
- **Format:** BIN/CUE (raw disc image)  
- **Graphics:** PS1 GPU (GTE + rasterizer)  
- **Audio:** PS1 SPU (ADPCM/VAG)  
- **Scripting:** None found (C/MIPS assembly)  
- **Physics:** Custom vehicle physics

**Evidence:**
- Angel Studios (later Rockstar San Diego) known for custom engines
- PS1 era - no middleware common
- Open-world streaming on PS1 (technical achievement)

---

## 2. File Formats (PS1 Standard)

| Format | Description |
|---|---|
| `.bin` / `.cue` | Disc image (raw sectors) |
| `.str` | PS1 video (MDEC) |
| `.xm` / `.mod` | Module audio (PS1 seq) |
| `.vag` | PS1 ADPCM audio |
| `.tim` | PS1 texture format (TIM) |
| `.mdl` / `.obj` | Custom model formats |
| `.map` | Level/map data |

---

## 3. Asset Structure (Expected PS1 Disc)

```
CD_ROOT/
├── SYSTEM.CNF         # Boot configuration
├── SLUS_XXX.XX        # Main executable (ELF)
├── DATA/              # Game data
│   ├── LEVELS/        # Track data
│   ├── CARS/          # Vehicle models
│   ├── TEXTURES/      # .tim textures
│   ├── AUDIO/         # .vag, .xm audio
│   └── VIDEO/         # .str movies
└── FMV/               # Full motion video
```

---

## 4. Documentation Notes

- **Angel Studios** - Later became Rockstar San Diego
- **Open-world racing** - First in genre on console
- **Streaming technology** - No loading screens (PS1 achievement)
- **No PC port** - PS1 exclusive (PC version was separate Midnight Club II)
- **Disc image** - Requires PS1 emulator or disc tools to extract

---

*Generated from `C:\Users\gmbad\Downloads\teardown\Research\Midnight Club - Street Racing (USA)\`*  
*Engine: Angel Studios proprietary PS1 engine, Angel Studios 2000*