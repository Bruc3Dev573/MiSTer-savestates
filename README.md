# MiSTer savestates

Savestates for MiSTer cores that do not have them yet. These are unofficial test builds, not MiSTer-devel releases. Please report problems in the repository of each core, not on the official repos.

## TurboGrafx16 / PC Engine

Savestates for HuCard, SuperGrafx and CD games. Latest release: [v0.2.0-pre1](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/releases/tag/v0.2.0-pre1).

1. Copy `TurboGrafx16_SS_v0.2.0-pre1.rbf` to `_Console` on the SD card. HuCard and SuperGrafx games need nothing else.
2. For CD games, also replace the Main:
   - disc images: [tg16-savestates-v0.2.0-pre1](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/tg16-savestates-v0.2.0-pre1), replaces `MiSTer`
   - real discs with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc): [tg16-savestates-physdisc-v0.2.0-pre1](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/tg16-savestates-physdisc-v0.2.0-pre1), replaces `MiSTer_Physical-CD`
3. Set **MB128** to **Disabled** in the OSD. With MB128 on, Save state and Restore state stay greyed out for every game.

## MegaCD / Sega CD

Savestates for MegaCD games. Latest release: [v0.1.0-pre1](https://github.com/Bruc3Dev573/MegaCD_MiSTer/releases/tag/v0.1.0-pre1).

1. Copy `MegaCD_SS_v0.1.0-pre1.rbf` to `_Console` on the SD card.
2. Replace the Main:
   - disc images: [savestates-20261011](https://github.com/Bruc3Dev573/Main_MiSTer/releases/tag/savestates-20261011), replaces `MiSTer`
   - real discs with [Physical Disc Support](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc): [savestates-20261011](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc/releases/tag/savestates-20261011), replaces `MiSTer_Physical-CD`

## Use

Both cores save with Alt+F1-F4 and load with F1-F4. The OSD has the same actions. Each release explains the pad controls and the known limits.

## About the Main

The Main is the MiSTer program in `/media/fat`. The modified Main pauses CD data while the core is frozen and keeps CD slots on the SD card under the disc's name. The MegaCD version also puts the CD drive back where the game was after a load. Other cores work as with the official Main.

Keep a copy of the original file before you replace it. `update_all` and Physical Disc Support updates can put the original file back.

The savestates-20261011 releases have three builds each: MegaCD and TurboGrafx16 CD together, MegaCD only, and TurboGrafx16 CD only. Each build comes from its own branch, and `savestates` is the other two merged. The TurboGrafx16 CD changes in these builds have not been tested with that core yet. Until then, use the tg16 Mains for TurboGrafx16 CD games.

## Source

| Repository | Upstream | Branches |
|---|---|---|
| [TurboGrafx16_MiSTer](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer) | [MiSTer-devel/TurboGrafx16_MiSTer](https://github.com/MiSTer-devel/TurboGrafx16_MiSTer) | `savestates` |
| [MegaCD_MiSTer](https://github.com/Bruc3Dev573/MegaCD_MiSTer) | [MiSTer-devel/MegaCD_MiSTer](https://github.com/MiSTer-devel/MegaCD_MiSTer) | `savestates` |
| [Main_MiSTer](https://github.com/Bruc3Dev573/Main_MiSTer) | [MiSTer-devel/Main_MiSTer](https://github.com/MiSTer-devel/Main_MiSTer) | `savestates`, `megacd-savestates`, `pcecd-savestates` |
| [Main_MiSTer_Physical_Disc](https://github.com/Bruc3Dev573/Main_MiSTer_Physical_Disc) | [Anime0t4ku/Main_MiSTer_Physical_Disc](https://github.com/Anime0t4ku/Main_MiSTer_Physical_Disc) | `savestates`, `megacd-savestates`, `pcecd-savestates` |

## Report a problem

Open an issue in the repository of the core: [TurboGrafx16](https://github.com/Bruc3Dev573/TurboGrafx16_MiSTer/issues) or [MegaCD](https://github.com/Bruc3Dev573/MegaCD_MiSTer/issues). Say which game, HuCard, disc image or real drive, what you did and what happened.
