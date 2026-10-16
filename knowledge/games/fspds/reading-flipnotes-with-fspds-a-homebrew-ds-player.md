---
kind: game
title: "Reading flipnotes with FSPDS, a homebrew DS player"
game: "FSPDS"
games_also: []
game_version: "V1.0 homebrew build (FSPDS-V1.0.79212842R.nds, 749,568 bytes)"
platform: console
engine: native
route: data
tools: ["7-Zip", "Python (NDS header and string reader)"]
anti_cheat: "none; offline homebrew"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [homebrew, nintendo-ds, flipnote, nitro-romfs, fat-storage, devkitpro]
---

# Reading flipnotes with FSPDS, a homebrew DS player

> Static teardown of FSPDS, the homebrew player that plays Flipnote Studio notes on a stock DS without
> a DSi: what the ROM header says, why the ROM looks fileless, and where the flipnotes actually come
> from. Nothing was run on hardware or an emulator, so the storage path is recorded as a claim to
> check, not a result.

## Setup
- **Copy used:** the public homebrew release `FSPDS-V1.0.79212842R.nds` (749,568 bytes) - freely distributed homebrew, no ownership question.
- **What it is:** a player for Flipnote Studio flipnotes on an original DS, so notes can be watched without DSi hardware. Its strings credit a devkitPro build and the "Flipnote Collective".
- **Tools:** a one-off Python reader for the NDS header fields plus a string scan over the binaries. No emulator run, no hardware run.

## Route and why
Route: **data** - read-only identification of where flipnote content comes from and how the ROM is put together. There is no modding goal yet; the useful knowledge for the next agent is the storage path and the ROM layout, not code hooks. Loading it in an emulator to watch which folder it scans was the obvious next step and was not taken.

## How the game works (what we had to learn)
- It is devkitPro homebrew (libnds), not a retail engine: the header carries title `HOMEBREW` and game code `####` - placeholder values that retail-style tooling keys on, so code-based identification fails.
- The ROM's file table has zero entries: devkitPro-style builds do not populate the Nitro ROM filesystem. The payload sits in and behind the ARM9 binary (about 711 KB per the header), so anything you want to inspect has to come out of the binaries, not a file listing.
- Flipnote content is read from FAT-formatted removable storage, not from the ROM. Embedded strings also show a cached config path (it remembers where it last looked) and a set of built-in example flipnotes.
- Strings reference per-region DSi identifiers - consistent with the player coping with notes written by region-specific DSi-era Flipnote Studio builds - but that interpretation was not confirmed by running anything.

## Build steps (reproduce this pass)
1. Read the NDS header: title, game code, file count, ARM9 offset/size.
2. String-scan the ARM9 binary for devkitPro markers, path strings, region identifiers.
3. Note the zero file count before assuming a bad dump.
4. To go further: run it (emulator or flashcart) and watch which folder it scans - that step was not done here.

## Verification
- **Verified:** header fields read directly from the ROM (title `HOMEBREW`, code `####`, empty file table, ARM9 around 711 KB); embedded strings (devkitPro build credit, "Flipnote Collective", config-path caching, built-in flipnotes, region identifiers).
- **Not verified:** no playback test at all - nothing was run. The folder it scans was never observed, the built-in flipnotes were not extracted, and its flipnote parsing was not examined.

## Gotchas
1. **Symptom.** ROM browsers and checkers report the dump as empty or invalid. **Cause:** the file table genuinely has no entries - homebrew builds leave it unpopulated. **Fix:** work from the ARM9/ARM7 binaries instead of the file list.
2. **Symptom.** Tools cannot identify the game; the title looks generic (`HOMEBREW`) and the code is `####`. **Cause:** placeholder header fields, not a corrupted header. **Fix:** skip code-based lookups and identify by strings and size instead.
3. **Symptom.** It shows no flipnotes on first launch. **Cause:** flipnotes live on removable FAT storage and the app remembers a config path from a previous run. **Fix:** check the player's config for the folder it expects before concluding the files are unsupported.

## Open questions
- Which storage path it scans on real hardware (flashcart SD vs a Slot-2 adapter) - one observed run would settle it.
- What the built-in flipnotes are, and whether the region identifiers are used to validate or decode external notes.
- Which regional/format revisions of DSi flipnotes it accepts - the region strings hint at handling differences, unconfirmed.
