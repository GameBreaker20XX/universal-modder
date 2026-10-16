---
kind: game
title: "StreetPass Mii Plaza on SD: one game, three title IDs"
game: "StreetPass Mii Plaza"
games_also: []
game_version: "SD install on my own 3DS (title 00040000-00022800, 94 MB update, separate DLC title)"
platform: console
engine: native
route: data
tools: ["Nintendo 3DS console (software list)", "SD card file listing"]
anti_cheat: "system app; StreetPass/SpotPass is local radio, no online match was touched"
status: in-progress
agents: ["OpenCode (Big Pickle)"]
humans: ["GeoffreyMba"]
date: 2026-10-16
links: []
tags: [nintendo-3ds, ctr-sdk, sd-install, dlc, extdata, encrypted-content, layeredfs, romfs]
---

# StreetPass Mii Plaza on SD: one game, three title IDs

> What a system-bundled 3DS title looks like from outside the console: a base app, a separate update title, and a
> *third* title holding the paid minigames - plus a per-console extdata slot. Read-only inspection of my own
> console; nothing was decrypted and nothing on the card was changed.

## Setup
- **Copy used:** my own 3DS. StreetPass Mii Plaza is the plaza that ships with the system, installed here under title `00040000-00022800` with a 94 MB update. Inspected through the console's own software list and the SD card's folder layout; no decryption keys were used.
- **Tools:** the console's software list and a plain SD-card file listing. Nothing was launched from outside the console and no title content was read.
- **On the card:** the base app in the application slot; an update in the `0004000e-00022800` slot; a paid-content title in the `0004008c-00022800` slot; and one small extdata slot (`00000228`) with roughly a dozen files.

## Route and why
Route: **data** - the plaza's content is sealed like any installed title, so the workable route is to replace files at runtime through a LayeredFS RomFS overlay, the same route the community Mario Kart 7 mod uses. Editing the card directly was dropped on sight: the stored content is encrypted per console, so there is nothing to read or patch there without keys.

## How the game works (what we had to learn)
- **Three titles, one product.** Application titles (`00040000-...`), updates (`0004000e-...`) and add-on content (`0004008c-...`) are three *separate* titles with their own IDs and their own sealed content. "How big is this game" has three answers, and size lists online usually quote only one of them.
- **The paid minigames are add-on content, not a patch.** They live in the `0004008c-...` title, so they have their own RomFS. An overlay that fixes or retextures the plaza itself does not cover the minigames, and vice versa - you may be targeting two different titles.
- **extdata is the per-user state.** The small `00000228` slot holds the things that are not content: Miis met, puzzle pieces, greetings, progress and the entitlement bookkeeping for the add-on title. It is not game content and it is not the app.
- **The content is per-console encrypted.** A copied title folder is opaque: no readable code, textures or strings. Reading it needs the console's keys, which is out of scope here.
- **The engine is Nintendo first-party on the 3DS SDK family (CTR SDK).** Older notes call this "NitroSDK", which is the DS SDK and the wrong generation for any 3DS title.
- **RomFS is the modding surface.** Because code and content are sealed, the practical lever is a layered filesystem: a loader presents replacement files ahead of the game's own RomFS at runtime.

## Build steps (reproduce this pass)
1. On the console, open the software list and note the plaza's title ID and installed size.
2. On a PC, open the SD card's Nintendo 3DS tree and find the folder for that ID, then the update folder and the add-on-content folder for the same title.
3. Find the extdata folder for the same title and count its files.
4. Record the three IDs and the extdata slot so you can tell app, update, add-on and user state apart before touching anything.
5. Confirm the wall: open the largest file in the title folder - there is no plaintext inside without console keys.

## Verification
- **Verified:** that the plaza is installed on my own console; its application title ID; that a separate ~94 MB update title exists; that a distinct add-on-content title exists in the `0004008c-...` range; that a small extdata slot exists with about a dozen files; and that the stored content is not readable without keys.
- **Not verified:** nothing inside the sealed content was read - no code, textures, strings or file lists. The exact minigame roster was not read from the card (the set is eShop knowledge, not a measurement). No overlay was built, installed or tested.

## Gotchas
1. **Symptom.** You size up the plaza from its folder and it looks far too small for the content you see in game. **Cause.** The update and the paid minigames are separate titles with their own IDs. **Fix.** Add app + update + add-on content before drawing any conclusion.
2. **Symptom.** A plaza retexture works but a minigame still looks stock. **Cause.** The minigames live in the add-on-content title, which has its own RomFS. **Fix.** Overlay the second title too, or accept that you only changed the plaza.
3. **Symptom.** You back up the title folder and the user's progress still seems missing. **Cause.** Progress is extdata, stored outside the title. **Fix.** Back up the extdata slot separately; it is the part that actually changes.
4. **Symptom.** You open the biggest file on the card looking for assets. **Cause.** Per-console encryption on installed titles. **Fix.** Work through a runtime LayeredFS layer; do not expect plaintext from the card.

## Assets
None - reconnaissance only; nothing was authored, decrypted or written.

## Open questions
- Whether the add-on-content RomFS uses the same path layout as the base app, which would let one overlay cover both.
- How much of the 94 MB update replaces base files versus adding SpotPass content, without decrypting either title.
