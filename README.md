# RA ROM Checker

Hello Fellow Retro Achievement Gamers,

Don’t you hate it when you open up a game ready to play and then you see the dreaded popup saying, “Retro achievements not found”?

RA ROM Checker v1.0 (BETA) is this new application that will scan your ROM directory and display which games do not have retro achievements and which games failed the hash check.
Now you know which ones will work without having to open the game to find out.




This application scans a folder of ROMs and checks each file's hash
against RetroAchievements' database. It reports two things:

- **Not on RetroAchievements** — no achievement set exists for this game (the
  hash isn't recognized, and the filename doesn't clearly match any title RA
  has a set for on that system).
- **Hash mismatch** — RetroAchievements has a set for what this file probably
  is, but your copy's hash isn't one of the accepted dumps (bad rip, patched/
  translated ROM, wrong region, etc).

ROM files are read locally and never uploaded; only hash lookups go to `retroachievements.org`.

## Supported systems

| System | Format |
|---|---|
| NES / Famicom | `.nes` |
| SNES / Super Famicom | `.sfc`, `.smc` |
| Genesis / Mega Drive | `.md`, `.smd`, `.gen` |
| Game Boy | `.gb` |
| Game Boy Color | `.gbc` |
| Game Boy Advance | `.gba` |
| PlayStation | `.chd`|


## Getting a Web API key

1. Log into [retroachievements.org](https://retroachievements.org).
2. Go to **Settings → Keys**.
3. Copy your Web API key and paste it into the app. It's kept in memory for
   the current tab only — it's never written to disk, localStorage, or sent
   anywhere except directly to RetroAchievements' API.


## Identifying "not on RA" vs "mismatch"

RetroAchievements has no "look up a game by filename" endpoint, so when a
hash doesn't match, this app makes a best-effort guess by normalizing the
filename (stripping region/language/revision tags like `(USA)`, `(Rev 1)`,
handling `Title, The` article ordering) and comparing it against every game
title RA has a set for on that console. If nothing looks like a close match,
the file is classified as "not on RetroAchievements"; if something does, it's
classified as a "hash mismatch" against that likely title. This is a
heuristic, not ground truth — double-check the "likely" title shown for
mismatches before assuming your file is simply a bad dump.

********Special Note: This app was created with the help of AI. If you find anything that needs fixing or any bugs, please let me know. 
