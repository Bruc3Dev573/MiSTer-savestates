# MegaCD / Sega CD savestates: status

The current state of the MegaCD savestate core and its modified Main. Unofficial test builds, not MiSTer-devel releases. Each release lists only what changed in that version and links here for the rest.

## Current version

| Core | Main for disc images (`MiSTer`) | Main for a real CD drive (`MiSTer_Physical-CD`) |
|---|---|---|
| [v0.1.0-pre9](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre9) | [20261010-megacd-savestates-r7](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r7) | [v2.10.0-megacd-savestates-r7](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-megacd-savestates-r7) |

Use the core and a Main of the same row together: some fixes are split between the two. How to install them: [MiSTer-savestates](README.md#install).

Slots saved with earlier versions load in the current one. A slot saved with a newer version is not meant to load in an older one. Keep a copy of the slots you care about.

## Games fixed so far

| Game | What was wrong | Fixed in |
|---|---|---|
| Microcosm | After Start it showed "Document ends" and went back to the intro ([#66](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/66)) | core v0.1.0-pre2 |
| Mighty Morphin Power Rangers | Starting an episode went black for up to 80 s or skipped it ([#84](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/84)) | core v0.1.0-pre3 |
| Mighty Morphin Power Rangers | Froze a few seconds after loading a savestate, about once in 130 loads | core v0.1.0-pre5 |
| Ultraverse Prime | Over HDMI the picture sheared for about 2 s every 10 s ([#36](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/36)) | core v0.1.0-pre3 |
| Thunder Storm FX (Japan) | Froze on the Sega logo ([#111](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/111)) | Main r2, also with the official core |
| Flashback | With CHD images, hung after the level 2 machine cutscene ([#49](https://github.com/MiSTer-devel/MegaCD_MiSTer/issues/49)) | Main r2, also with the official core |

The other fixes are not tied to a known game: they make the hardware behave more like the real console.

## Known limits

- **Dune**: a save or a load during the intro videos can leave the game stuck, about once in ten. In our tests, loading the slot again got it going. Being looked into.
- When a game switches between the 256 and 320 pixel modes, or a state saved in the other mode is loaded, the new width shows 4 frames later.
- MGL files that point to `_Console/MegaCD` start this core too. Remove the RBF to go back.
- The Main for a real CD drive has been run on MiSTer with disc images only. No real drive has been tested.

## krikzz's mcd-verificator

[mcd-verificator](https://github.com/krikzz/mega-ed-pub/tree/8b72838f8b449e34e519b53d9e9b8fd2021a6044/mcd-verificator) measures the Mega CD hardware against the real console. With v0.1.0-pre9 and the r7 Main:

- The CD drive test passes, CDD SYNC included (since v0.1.0-pre9).
- The timing checks still report errors: VAR, IRQ, REG 8030, PCM CLOCK from channel 4, DEC IRQ and the DMA timings. They measure main CPU speed.
- CDC REGS reports error 01: it expects the 5-bit register of the CDX and Multi-Mega.

## The modified Main

The official MiSTer Main 20261010 plus these changes. The Physical Disc build is [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) v2.10.0 with the same changes.

Savestates:

- After a load the CD drive goes back where the game was, also when the save was made just after a CD command (play, seek, pause, resume) or while CD music played. CD data pauses while the core is frozen.
- Slots are kept on the SD card under the disc's name. Loading a slot does not write the slot file again.

CD drive and disc data:

- The drive does not take the command the console repeats every 1/75 of a second for a new play or seek (r3).
- Data sectors are sent whole: sync bytes (r3) and error-correction bytes (r6).
- The drive reports each sector's position about 3 ms after the sector, and keeps its 75 reports a second steady when Main is briefly busy (r7).

These also help the official MegaCD core:

- Thunder Storm FX (Japan) no longer freezes on the Sega logo, and CHD images are unpacked ahead of time, which fixes Flashback (r2).
- With CHD images the start of every CD music track no longer plays a moment twice (r4).
- Saving a file no longer loses free space on the SD card (r5, disc images only).

Other cores work as with the official Main.

## How each version is tested

On MiSTer, from disc images, before each release: krikzz's mcd-verificator and its CD drive test; 100 save/load cycles in Mighty Morphin Power Rangers; a save, a load and another save in 19 games (Crime Patrol, Dark Wizard, Dune, ESPN NBA Hangtime '95, ESPN Sunday Night NFL, F1 Circus CD, Flashback, Ground Zero Texas, Iron Helix, Jaguar XJ220, Johnny Mnemonic, The Lawnmower Man, Mad Dog McCree, Microcosm, Mighty Morphin Power Rangers, Ultraverse Prime, What is X'Eye, Thunder Storm FX and A-X-101); slots saved with earlier versions. Each release says what was run for it and what changed.

## Version history

| Core | Date | Main | What changed |
|---|---|---|---|
| [v0.1.0-pre9](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre9) | 2026-10-22 | r7 | CD drive timing closer to the real console |
| [v0.1.0-pre8](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre8) | 2026-10-20 | r6 | FM chip state saved; data sectors with error-correction bytes |
| [v0.1.0-pre7](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre7) | 2026-10-19 | r5 | Sound CPU saved while the main CPU holds its bus; CD drive after a pending command; SD free space |
| [v0.1.0-pre6](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre6) | 2026-10-18 | r4 | CD music and PCM sound after a load; CHD music track starts |
| [v0.1.0-pre5](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre5) | 2026-10-17 | r3 | Fewer freezes after a load (sound CPU); CD sector framing |
| [v0.1.0-pre4](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre4) | 2026-10-16 | r3 | CD controller and gate array fixes; drive command repeat |
| [v0.1.0-pre3](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre3) | 2026-10-13 | r2 | Ultraverse Prime over HDMI; Power Rangers episodes |
| [v0.1.0-pre2](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre2) | 2026-10-13 | r2 | Sub-CPU at its real 12.5 MHz; Microcosm |
| [v0.1.0-pre1](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre1) | 2026-10-11 | first | First savestate build |

## Source

| Repository | Branch | Base |
|---|---|---|
| [MegaCD_MiSTer](https://github.com/Bruc3Dev573/MegaCD_MiSTer) | `savestates` | [MiSTer-devel/MegaCD_MiSTer](https://github.com/MiSTer-devel/MegaCD_MiSTer) |
| [Main_MiSTer](https://github.com/Bruc3Dev573/Main_MiSTer) | `megacd-savestates` | [MiSTer-devel/Main_MiSTer](https://github.com/MiSTer-devel/Main_MiSTer) 20261010 |
| [Main_MiSTer_Physical_Disc](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc) | `megacd-savestates` | [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) v2.10.0 |

Some fixes are also on their own branches from the official sources, without the savestates:

- Core: [`fix-cdc-framing`](https://github.com/Bruc3Dev573/MegaCD_MiSTer/tree/fix-cdc-framing), [`fix-cdc-verificator`](https://github.com/Bruc3Dev573/MegaCD_MiSTer/tree/fix-cdc-verificator).
- Main: [`fix-megacd-play-repeat`](https://github.com/Bruc3Dev573/Main_MiSTer/tree/fix-megacd-play-repeat), [`fix-megacd-sector-fill`](https://github.com/Bruc3Dev573/Main_MiSTer/tree/fix-megacd-sector-fill), [`fix-megacd-chd-audio`](https://github.com/Bruc3Dev573/Main_MiSTer/tree/fix-megacd-chd-audio), [`fix-filesave-leak`](https://github.com/Bruc3Dev573/Main_MiSTer/tree/fix-filesave-leak), [`fix-megacd-sector-edcecc`](https://github.com/Bruc3Dev573/Main_MiSTer/tree/fix-megacd-sector-edcecc).

## Credits

Based on the [MiSTer-devel MegaCD core](https://github.com/MiSTer-devel/MegaCD_MiSTer) and [Main](https://github.com/MiSTer-devel/Main_MiSTer). Some CDC, PCM and gate array fixes come from retrorepair's [MegaCD_MiSTer-NukedMD](https://github.com/retrorepair/MegaCD_MiSTer-NukedMD), and four fixes from Jeremy O'Brien's [openfpga-megacd](https://github.com/neutralinsomniac/openfpga-megacd). The FM chip is Jose Tejada's [jt12](https://github.com/jotego/jt12), as in the official core. GPL, like the core.

## Report a problem

Open an [issue](https://github.com/Bruc3Dev573/MegaCD_MiSTer/issues) with the game, disc image or real drive, what you did and what happened. Saves during FMV, CD music and loading screens are the most useful cases.
