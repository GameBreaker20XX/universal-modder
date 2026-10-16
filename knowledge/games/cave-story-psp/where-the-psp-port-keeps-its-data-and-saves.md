---
kind: game
title: "Where the PSP port keeps its data and saves"
game: "Cave Story PSP"
games_also: ["Cave Story"]
game_version: "RC1 homebrew port by -Z., 8 July 2007 (freeware release archive)"
platform: console
engine: native
route: data
tools: ["7-Zip", "Python (one-off string and header reader)"]
anti_cheat: "none; offline homebrew with no online layer"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [homebrew, psp, cave-story, data-pack, saves, widescreen]
---

# Where the PSP port keeps its data and saves

> Static teardown of the 2007 homebrew PSP port of Cave Story: the whole game ships as one compressed
> data pack, the saves are the Windows original's, and the author's readme documents what widescreen
> breaks. Nothing was run on hardware or an emulator and no mod was built - this note records where
> the editable data lives and what still needs checking.

## Setup
- **Copy used:** the public freeware RC1 release archive (`cavestory-psp-rc1.zip`) published by the port author in July 2007. It is freeware, so there is no ownership question.
- **Install layout:** the archive unpacks to a `cavestory/` folder meant for the memory stick's homebrew GAME folder. Its readme targets firmware 1.0 (unmodded), 1.5 (kxploit) and 3.XX OE custom firmware.
- **Tools:** 7-Zip for the archive, a one-off Python script for sizes, string scans and header peeks. Nothing was executed on a PSP or in PPSSPP.
- **What is in the folder:** `EBOOT.PBP` (the port's executable package, 818,511 bytes), `data.csz` (the entire game data as one compressed file, 1,532,782 bytes), `readme.txt` (install notes plus the author's own known-bugs list), and after playing, saves `Profile.dat` / `290.rec`.

## Route and why
Route: **data** - this pass existed to locate editable game data, not to change it. The port has no loader or plugin infrastructure, so any future mod works by unpacking, editing and repacking the data pack (binary patching the executable was the alternative and nobody has done it). Emulating in PPSSPP to watch a change live was considered for verification and skipped; the analysis stayed static.

## How the game works (what we had to learn)
- The port is a native re-implementation, not an emulator: the homebrew EBOOT *is* the engine, ported from the Windows original.
- All game data ships as a single compressed pack (`data.csz`) instead of the PC version's loose `data/` folder. The internal compression scheme was not decoded here - we only confirmed it contains no plaintext strings, i.e. content is packed.
- Saves keep the Windows original's names (`Profile.dat`, `290.rec`, ...) and the readme states they are compatible with the PC version, so the ported code kept the original's file naming conventions. The readme also warns that filename casing matters.
- The readme documents the widescreen side effects per area (Balrog fight, Egg Corridor, Labyrinth, Hell, credits): the port renders a wider frame than the original's 4:3, so art and text authored for the narrower frame can spill off-screen. That list is the port's own known-issues record, not a finding of ours.
- The PBP's internal sections were not unpacked; we only recorded its size.

## Build steps (reproduce this pass)
1. Unpack the release archive.
2. Read `readme.txt` first - firmware targets, install path, known script bugs.
3. List the folder with sizes; confirm the two payloads (`EBOOT.PBP`, `data.csz`).
4. Strings-scan `data.csz` (expect nothing readable - it is packed).
5. Compare the save filenames against the PC version's save set to check the compatibility claim.

## Verification
- **Verified:** file inventory and sizes; the readme's own statements (firmware targets, save compatibility, per-area widescreen bugs); absence of plaintext strings in the data pack; save filenames match the PC original's naming.
- **Not verified:** nothing was booted - no PSP hardware, no PPSSPP. `data.csz` was never decompressed, so the formats inside (graphics, sound, scripts) are unconfirmed. No edit was made, so there is no in-game change to show for this note.

## Gotchas
1. **Symptom.** You look for the PC version's `data/` folder and find one opaque file. **Cause:** the port ships every asset inside a single compressed pack. **Fix:** treat `data.csz` as the archive to crack open first - everything else depends on it.
2. **Symptom.** Sprites or text sit outside the visible screen in certain rooms or cutscenes. **Cause:** the port renders a wider frame than the art was authored for. **Fix:** check the readme's per-area bug list before blaming your own edit.
3. **Symptom.** A rewritten save is ignored. **Cause:** the ported code kept the original's case-sensitive filename comparisons. **Fix:** keep the exact original casing (`Profile.dat`, not `profile.dat`).

## Open questions
- What compression `data.csz` uses, and whether unpacking it yields the PC data set 1:1 - that comparison is the fastest route to mapping the port's asset formats.
- Whether the port ever falls back to loose files next to the pack (some homebrew ports do; the readme does not say).
- What the PBP holds beyond the executable (no unpacking was done).
