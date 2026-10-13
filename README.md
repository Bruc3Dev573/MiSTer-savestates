# MiSTer savestates

Savestates for MiSTer cores that do not have them yet. Unofficial test builds, not MiSTer-devel releases. Report problems in the repository of each core, not on the official repos.

| Core | Latest release | Copy to `_Console` | Modified Main needed |
|---|---|---|---|
| TurboGrafx16 / PC Engine | [v0.2.0-pre2](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/releases/tag/v0.2.0-pre2) | `TurboGrafx16_SS_20261011.rbf` | CD games only |
| MegaCD / Sega CD | [v0.1.0-pre3](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre3) | `MegaCD_SS_20261013b.rbf` | Yes |

## Install

1. Copy the RBF to `_Console` on the SD card and remove older `*_SS_*.rbf` files of the same core. Back up your slots; compatibility between core versions is not guaranteed.
2. Replace the Main with the one from [the table below](#which-main), or [select it per core](#use-a-different-main-for-each-core).
3. TurboGrafx16 only: set **MB128** to **Disabled** in the OSD, then reload the core. With MB128 on, Save state and Restore state stay greyed out.

> [!WARNING]
> CD savestates need the modified Main. With the official Main, CD slots are not kept under the disc's name and can overwrite the slots of a HuCard loaded earlier in the same session, and loading a slot from another game can hang the core.

Both cores save with **Alt+F1-F4** and load with **F1-F4**. The OSD has the same actions. Each release lists the pad controls and the known limits.

## Which Main

The Main is the MiSTer program at the SD root. Keep a copy of the original file before you replace it; `update_all` and Physical Disc Support updates put the original back.

| Savestate cores you use | Disc images, replaces `MiSTer` | Real CD drive with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc), replaces `MiSTer_Physical-CD` |
|---|---|---|
| MegaCD | [20261010-megacd-savestates-r2](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r2) | [v2.10.0-megacd-savestates-r2](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-megacd-savestates-r2) |
| TurboGrafx16 | [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) | [v2.10.0-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-pcecd-savestates) |
| Both | [20261010-savestates-r2](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-savestates-r2) | [v2.10.0-savestates-r2](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-savestates-r2) |

Only the single-core builds for disc images were tested on MiSTer with the latest cores. The combined builds and the builds for real drives were not, and no real drive was tested. If you use both cores, [one Main per core](#use-a-different-main-for-each-core) keeps you on the tested builds.

The r2 MegaCD builds also fix Thunder Storm FX (Japan) on the Sega logo and the Flashback hang after the level 2 machine cutscene with CHD images. These two fixes apply to the official MegaCD core too; other cores work as with the official Main.

<details>
<summary>What was tested</summary>

- TurboGrafx16 v0.2.0-pre2 with [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates): 50 Sherlock restores, Rondo intro and gameplay save/load with CD audio, and Bonk movement and save/load.
- MegaCD v0.1.0-pre3 with [20261010-megacd-savestates-r2](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r2): Ultraverse Prime over HDMI, the Flashback level 2 machine cutscene, save/load in Cobra Command, slots from earlier versions in Crime Patrol and Flashback, and ten games without savestates.

These were targeted checks, not the full suite. Details are in each release.

</details>

## Use a different Main for each core

Instead of replacing the official Main, you can keep it as `MiSTer` and select the modified binaries through `MiSTer.ini`. Only one Main runs at a time.

1. Back up `MiSTer.ini` and keep the official `MiSTer` executable at the SD root.
2. Download `MiSTer` from [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) and rename it to `MiSTer_PCECD_SS`. For MegaCD, download `MiSTer` from [20261010-megacd-savestates-r2](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r2) and rename it to `MiSTer_MegaCD_SS`.
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
