---
kind: game
title: "Firebrand's Octane pipeline in the unreleased DS Blur beta"
game: "Blur DS"
games_also: ["Blur"]
game_version: "Unreleased European DS beta, ~2010 (the DS counterpart to the 2010 console racer; no build distributed with this note)"
platform: console
engine: native
route: data
tools: ["7-Zip", "Python (header and string reader)"]
anti_cheat: "none; a single-player-capable handheld beta with no online service layer"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [nintendo-ds, unreleased-beta, firebrand, octane-engine, vfs-zip, mobiclip, lua]
---

# Firebrand's Octane pipeline in the unreleased DS Blur beta

> What a static read of the unreleased European DS beta of Blur shows about Firebrand's Octane engine:
> almost the whole ROM is one zip-style VFS (~3,100 files) using the short-extension asset set from
> TrackMania Turbo DS, with Lua 5.1 bytecode, Mobiclip video and a NitroSDK 2D layer. Nothing was booted,
> and per this repo's leaks rule the build itself is left out - no files, links or hashes.

## Setup
- **Copy used:** a circulated unreleased European DS beta of Blur (the DS counterpart to the 2010 console racer; the DS version never shipped). Per this repo's leaks rule the build is left out: no files, links or hashes for fetching it.
- **Tools:** 7-Zip to open the asset container, a one-off Python script for the NDS header and string scans. Nothing was run on hardware or an emulator.
- **Header read:** Nintendo DS; region Europe; publisher Activision (maker code `36`); about 64 MB, most of it content. Strings in the binary name Firebrand repeatedly, plus `Octane`, `Mobiclip` and `Actimagine`.

## Route and why
Route: **data** - the interesting part is the asset container, and the engine is a first-party-SDK build with no plugin surface. Hooking or patching the code was considered and skipped: this is a read-only study of an unreleased build, so the durable output is what the archive and the formats tell us, not a mod.

## How the game works (what we had to learn)
- **One VFS holds nearly everything.** The ROM's own file table is tiny - a dozen entries (two DSi download-play binaries, three Mobiclip movies, two SDAT sound banks and the container). Everything else - models, scenes, collision, 2D graphics, scripts, strings - lives inside a single `vfs.zip` of about 25 MB and roughly 3,100 files, with small `vfs.bin`/`vfs.dat` companions. In practice the VFS *is* the game.
- **Asset profile = Firebrand's Octane pipeline.** Around two thousand `.n` models, roughly 190 `.dcsc` scenes (each paired with a `.tsf` track-section file), about 28 `.hzc` collision files, plus Firebrand's own `.p`/`.c`/`.s` internal data, `.na`/`.nm` and `.bin`/`.str` strings. That mix is the same one behind TrackMania DS, Turbo DS and GRID DS - and the short `.n` model extension specifically matches the newer Turbo DS layout rather than the original TrackMania DS (which used `.nsbmd`). Prior Firebrand tooling is a family-level starting point, not a drop-in fit.
- **2D graphics are plain NitroSDK formats** - `.ncgr` tiles, `.ncer` cells, `.nanr` animation, `.nclr` palettes, about a hundred of each. A UI/graphics mod therefore sits on a well-documented path.
- **Scripting is Lua 5.1 bytecode** - about eighteen `.luac` files in the archive. That is where gameplay logic would be edited once decompiled.
- **Video is Mobiclip (Actimagine)** - three `.mob` movies (an attract movie, a Firebrand logo, a tutorial test). Proprietary-ish codec; needs a dedicated decoder to view or convert.
- **Audio is SDAT** - `sound_data.sdat` plus a network-flavoured variant, the standard DS sound archive.
- **The only "middleware" is the platform SDK.** Nintendo's NitroSDK is the base; no third-party audio, physics or UI middleware is present, so research effort belongs in the VFS and the Lua, not in vendor stacks.
- **DSi-era distribution was being staged:** two DSi download-play stubs (EU and US) and a DWC utility ship beside the game - the beta was prepared for a distribution push that never happened.

## Build steps (reproduce this pass)
1. Read the NDS header: title, region, publisher maker code, ROM size.
2. List the ROM's own file table - note how small it is relative to the ROM.
3. Extract `vfs.zip` and group its entries by extension; that grouping is the whole content inventory.
4. Strings-scan the ROM and the archive for engine and middleware fingerprints (Firebrand, Octane, Mobiclip, Actimagine, Lua).

## Verification
- **Verified (static):** the header fields above; the single-container layout and the content mix by extension and rough counts; the presence of Lua 5.1 bytecode, Mobiclip movies, SDAT audio, NitroSDK 2D graphics and the DSi download-play stubs; the engine fingerprints in the strings.
- **Not verified:** nothing was booted - no emulator or hardware run. No model, scene or collision file was parsed beyond its extension, the executable was only strings-scanned, and no asset was edited or re-injected. The exact VFS directory layout is unconfirmed, and no mod was built or played.

## Gotchas
1. **Symptom.** The ROM looks almost empty in a file browser (a dozen files). **Cause:** the content sits inside `vfs.zip`, not in the ROM filesystem. **Fix:** open the VFS first; the ROM-level entries are only movies, audio and distribution stubs.
2. **Symptom.** Older Firebrand tooling does not recognise the models. **Cause:** this beta uses the newer Turbo-DS short extensions (`.n`), not the original TrackMania DS `.nsbmd` naming. **Fix:** assume the newer pipeline and verify one model end-to-end before any batch work.
3. **Symptom.** You hunt for licensed middleware (Wwise, FMOD, Scaleform ...) and find none. **Cause:** a handheld build on a first-party SDK - there is none by design. **Fix:** spend the time on the VFS and the Lua bytecode instead.
4. **Symptom.** You expect retail update/DLC plumbing. **Cause:** this is an unreleased beta with DSi download-play stubs; the game never shipped. **Fix:** don't infer a retail release structure from it.

## Assets
None - this was a read-only reconnaissance pass; no art, audio or models were produced or changed.

## Open questions
- How `vfs.zip` is mounted and addressed (name lookup, offsets) and whether it can be repacked with a modified asset.
- What the roughly eighteen Lua scripts do - not decompiled here.
- Whether the EU and US download-play stubs differ beyond region headers.
- Whether the `.n`/`.dcsc`/`.hzc` formats are byte-compatible with the shipped TrackMania Turbo DS files, which would let existing tools be reused.
