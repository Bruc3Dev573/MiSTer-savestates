# MiSTer savestates

Savestates for MiSTer cores that do not have them yet. Unofficial test builds, not MiSTer-devel releases. Report problems in the repository of each core, not on the official repos.

| Core | Latest release | Copy to `_Console` | Modified Main needed |
|---|---|---|---|
| TurboGrafx16 / PC Engine | [v0.2.0-pre2](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/releases/tag/v0.2.0-pre2) | `TurboGrafx16_SS_20261011.rbf` | CD games only |
| MegaCD / Sega CD | [v0.1.0-pre4](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre4) | `MegaCD_SS_20261016.rbf` | Yes |

## Install

1. Copy the RBF to `_Console` on the SD card and remove older `*_SS_*.rbf` files of the same core. Back up your slots; compatibility between core versions is not guaranteed.
2. Install the modified Main from [the table below](#which-main), either by replacing `MiSTer` or, to keep the official Main for every other core, through [`MiSTer.ini`](#use-a-different-main-for-each-core).
3. TurboGrafx16 only: set **MB128** to **Disabled** in the OSD, then reload the core. With MB128 on, Save state and Restore state stay greyed out.

> [!WARNING]
> CD savestates need the modified Main. With the official Main, CD slots are not kept under the disc's name and can overwrite the slots of a HuCard loaded earlier in the same session, and loading a slot from another game can hang the core.

## Controls

| | TurboGrafx16 | MegaCD |
|---|---|---|
| Keyboard | **Alt+F1-F4** save to slot 1-4, **F1-F4** load | same |
| Pad | Hold the button mapped to **Savestates**, then **Down** save, **Up** load, **Left/Right** change slot | Hold **Savestate**, then **Mode+Down** save, **Mode+Up** load, **Left/Right** change slot |
| OSD | Save state and Restore state | same, with a slot selector |
| Notes | Enable **Savestates to SDCard** to keep slots on the SD card. Writing a slot to the SD card can cause a short CD audio gap. | Set the region in the OSD; F1-F3 no longer change it. |

Load a state with the same game or disc, BIOS and region you saved it with. Each release lists its known limits.

## Which Main

The Main is the MiSTer program at the SD root. You can replace it, keeping a copy of the original (`update_all` and Physical Disc Support updates put the original back), or keep it and [select the modified one per core in `MiSTer.ini`](#use-a-different-main-for-each-core).

| Savestate cores you use | Disc images (`MiSTer`) | Real CD drive with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) (`MiSTer_Physical-CD`) |
|---|---|---|
| MegaCD | [20261010-megacd-savestates-r3](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r3) | [v2.10.0-megacd-savestates-r3](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-megacd-savestates-r3) |
| TurboGrafx16 | [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) | [v2.10.0-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-pcecd-savestates) |
| Both | [20261010-savestates-r3](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-savestates-r3) | [v2.10.0-savestates-r3](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/v2.10.0-savestates-r3) |

Only the single-core builds for disc images were tested on MiSTer with the latest cores; the combined build for disc images was checked with the MegaCD core only. The builds for real drives were not tested on MiSTer, and no real drive was tested. If you use both cores, [one Main per core](#use-a-different-main-for-each-core) keeps you on the tested builds.

The MegaCD builds also fix Thunder Storm FX (Japan) on the Sega logo and the Flashback hang after the level 2 machine cutscene with CHD images. These two fixes apply to the official MegaCD core too; other cores work as with the official Main. Use r3 with the MegaCD core v0.1.0-pre4: its other fixes need both.

<details>
<summary>What was tested</summary>

- TurboGrafx16 v0.2.0-pre2 with [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates): 50 Sherlock restores, Rondo intro and gameplay save/load with CD audio, and Bonk movement and save/load.
- MegaCD v0.1.0-pre4 with [20261010-megacd-savestates-r3](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r3): krikzz's mcd-verificator, 40 save/load cycles and saves without loading in Power Rangers, save and load in a Crime Patrol mission, slots from earlier versions in Crime Patrol and Flashback, and ten games without savestates.

These were targeted checks, not the full suite. Details are in each release.

</details>

## Use a different Main for each core

Keep the official `MiSTer` and let MiSTer start the modified Main only for the savestate cores, with the `main=` option of `MiSTer.ini`. This is an [official MiSTer setting](https://github.com/MiSTer-devel/Main_MiSTer/blob/738cb7acc246c830739d02d862c0cc2a275738bb/MiSTer.ini), not part of the savestate builds.

1. Download the Main of each core from [the table above](#which-main) and rename it:

   | Core | Download `MiSTer` from | Rename to |
   |---|---|---|
   | MegaCD | [20261010-megacd-savestates-r3](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-megacd-savestates-r3) | `MiSTer_MegaCD_SS` |
   | TurboGrafx16 | [20261010-pcecd-savestates](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/20261010-pcecd-savestates) | `MiSTer_PCECD_SS` |

2. Power off and copy the renamed files to the SD root, next to `MiSTer`. Leave `MiSTer` as it is.
3. Back up `MiSTer.ini` and add the sections you need. If a section already exists, add the `main=` line to it instead of a second copy.

   ```ini
   [MegaCD]
   main=MiSTer_MegaCD_SS

   [TGFX16]
   main=MiSTer_PCECD_SS
   ```

MiSTer switches Main when you load a core; Menu and the other cores keep the official one.

- `MegaCD` and `TGFX16` are core names, not file names. The official MegaCD and TurboGrafx16 cores have the same names, so they also start the modified Main. That is fine: other games run as with the official Main, and the MegaCD fixes for Thunder Storm FX and Flashback help the official core too.
- The names after `main=` must match the files on the card exactly. If a file is missing, MiSTer stays on the Main it is running. To check over SSH, run `ps -eo pid,args` after loading the core and look for that file name.
- Existing `main=` lines in `[MiSTer]`, `[MENU]` or a matching core section can override these.
- To update a modified Main, download it again and rename it the same way.
- For real CD drives, Physical Disc Support selects `MiSTer_Physical-CD` with its own profiles; see [its configuration guide](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc#misterini-configuration).

## Source

| Repository | Upstream | Branches |
|---|---|---|
| [TurboGrafx16_MiSTer](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer) | [MiSTer-devel/TurboGrafx16_MiSTer](https://github.com/MiSTer-devel/TurboGrafx16_MiSTer) | `savestates` |
| [MegaCD_MiSTer](https://github.com/Bruc3Dev573/MegaCD_MiSTer) | [MiSTer-devel/MegaCD_MiSTer](https://github.com/MiSTer-devel/MegaCD_MiSTer) | `savestates` |
| [Main_MiSTer](https://github.com/Bruc3Dev573/Main_MiSTer) | [MiSTer-devel/Main_MiSTer](https://github.com/MiSTer-devel/Main_MiSTer) | `savestates`, `megacd-savestates`, `pcecd-savestates` |
| [Main_MiSTer_Physical_Disc](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc) | [Anime0t4ku/Main_MiSTer_Physical_Disc](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) | `savestates`, `megacd-savestates`, `pcecd-savestates` |

## Report a problem

Open an issue in the repository of the core: [TurboGrafx16](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/issues) or [MegaCD](https://github.com/Bruc3Dev573/MegaCD_MiSTer/issues). Say which game, HuCard, disc image or real drive, what you did and what happened.
