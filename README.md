# MiSTer savestates

Savestates for MiSTer cores that do not have them yet. These are unofficial test builds, not MiSTer-devel releases. Please report problems in the repository of each core, not on the official repos.

## TurboGrafx16 / PC Engine

Savestates for HuCard, SuperGrafx and CD games. Latest release: [v0.2.0-pre2](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/releases/tag/v0.2.0-pre2).

1. Copy `TurboGrafx16_SS_20261011.rbf` to `_Console` on the SD card. HuCard and SuperGrafx games need nothing else.
2. For CD games, also use the modified Main. Replace the file below, or [select it per core](#use-a-different-main-for-each-core):
   - disc images: [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates), replaces `MiSTer`
   - real discs with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc): [v2.10.0-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-pcecd-savestates), replaces `MiSTer_Physical-CD`, not checked with this core

   > **Warning**
   > CD savestates require the modified Main. With the official Main, CD slots are not saved under the disc's name and can overwrite the slots of a HuCard loaded earlier in the same session. Loading a slot from another game can hang the core. HuCard savestates do not require a modified Main.

3. Set **MB128** to **Disabled** in the OSD. If MB128 was enabled, reload the core with it disabled before using savestates. Back up existing slots; compatibility between core versions is not guaranteed.

## MegaCD / Sega CD

Savestates for MegaCD games. Latest release: [v0.1.0-pre2](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre2).

1. Copy `MegaCD_SS_20261013.rbf` to `_Console` on the SD card.
2. Use the modified Main. Replace the file below, or [select it per core](#use-a-different-main-for-each-core):
   - disc images: [20261010-megacd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates), replaces `MiSTer`
   - real discs with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc): [v2.10.0-megacd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-megacd-savestates), replaces `MiSTer_Physical-CD`, not checked with this core

If you use both cores, you can use the combined Main listed under About the Main, or select separate Mains per core as shown below.

## Use

Both cores save with Alt+F1-F4 and load with F1-F4. The OSD has the same actions. Each release explains the pad controls and the known limits.

## About the Main

The Main is the MiSTer program in `/media/fat`. The modified Main pauses CD data while the core is frozen and keeps CD slots on the SD card under the disc's name. The MegaCD version also puts the CD drive back where the game was after a load. Other cores work as with the official Main.

Keep a copy of the original file before you replace it. `update_all` and Physical Disc Support updates can put the original file back.

| Savestates for | Disc images, replaces `MiSTer` | Real discs, replaces `MiSTer_Physical-CD` |
|---|---|---|
| MegaCD and TurboGrafx16 | [20261010-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-savestates) | [v2.10.0-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-savestates) |
| MegaCD | [20261010-megacd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates) | [v2.10.0-megacd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-megacd-savestates) |
| TurboGrafx16 | [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) | [v2.10.0-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-pcecd-savestates) |

Each build comes from its own branch, and `savestates` is `megacd-savestates` and `pcecd-savestates` merged. TurboGrafx16 `v0.2.0-pre2` was checked on MiSTer with the disc-image Main [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates): 50 Sherlock restores, Rondo intro and gameplay save/load with CD audio, and Bonk movement and save/load. These were targeted checks, not the full suite. The combined Main was not checked with this core, and the builds for real discs have not been tested with a real drive.

MegaCD `v0.1.0-pre2` was checked on MiSTer with the disc-image Main [20261010-megacd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates): Crime Patrol and Flashback save/load, eight games without savestates, Microcosm and mcd-verificator. These were targeted checks, not the full suite. The combined Main and the build for real discs were not checked with this core.

## Use a different Main for each core

Instead of replacing the official Main, you can keep it as `MiSTer` and select the modified binaries through `MiSTer.ini`. Only one Main runs at a time.

1. Back up `MiSTer.ini` and keep the official `MiSTer` executable at the SD root.
2. Download `MiSTer` from [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) and rename it to `MiSTer_PCECD_SS`. For MegaCD, download `MiSTer` from [20261010-megacd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates) and rename it to `MiSTer_MegaCD_SS`.
3. Power off and use a computer to copy the renamed files to the SD root, alongside `MiSTer`. Add the following to your existing `MiSTer.ini`. If a section already exists, add its `main=` line there rather than creating a duplicate section.

```ini
[TGFX16]
main=MiSTer_PCECD_SS

[MegaCD]
main=MiSTer_MegaCD_SS
```

Use only the section you need if you have just one of these cores. The names in `main=` must match the files on the card.

`TGFX16` and `MegaCD` are core IDs, not RBF filenames. The `[TGFX16]` rule also applies to the official TurboGrafx16 core, because it uses the same ID.

Main switches automatically when you load a core. With no other `main=` rules, Menu and other cores use the official `MiSTer`. Check any existing `main=` entries in `[MiSTer]`, `[MENU]` or matching core sections; later matching settings can override earlier ones.

To check the selection over SSH, run `ps -eo pid,args` after loading a core and look for the executable named in its `main=` entry. If the file is missing or its name is wrong, MiSTer can stay on the current Main instead of switching. Loading the core alone does not prove that the right Main is running.

When updating a modified Main, repeat the download and rename steps for that file. This example is for CD images. Physical Disc Support uses its own profiles and `MiSTer_Physical-CD`; follow [its configuration guide](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc#misterini-configuration).

The `main=` option is part of the [official MiSTer.ini example](https://github.com/MiSTer-devel/Main_MiSTer/blob/738cb7acc246c830739d02d862c0cc2a275738bb/MiSTer.ini), not a savestate-specific setting.

## Source

| Repository | Upstream | Branches |
|---|---|---|
| [TurboGrafx16_MiSTer](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer) | [MiSTer-devel/TurboGrafx16_MiSTer](https://github.com/MiSTer-devel/TurboGrafx16_MiSTer) | `savestates` |
| [MegaCD_MiSTer](https://github.com/Bruc3Dev573/MegaCD_MiSTer) | [MiSTer-devel/MegaCD_MiSTer](https://github.com/MiSTer-devel/MegaCD_MiSTer) | `savestates` |
| [Main_MiSTer](https://github.com/Bruc3Dev573/Main_MiSTer) | [MiSTer-devel/Main_MiSTer](https://github.com/MiSTer-devel/Main_MiSTer) | `savestates`, `megacd-savestates`, `pcecd-savestates` |
| [Main_MiSTer_Physical_Disc](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc) | [Anime0t4ku/Main_MiSTer_Physical_Disc](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) | `savestates`, `megacd-savestates`, `pcecd-savestates` |

## Report a problem

Open an issue in the repository of the core: [TurboGrafx16](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/issues) or [MegaCD](https://github.com/Bruc3Dev573/MegaCD_MiSTer/issues). Say which game, HuCard, disc image or real drive, what you did and what happened.
