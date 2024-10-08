# BugfixedHL-Custom

This repository contains my fork of [BugfixedHL by Lev](https://github.com/LevShisterov/BugfixedHL). This version is mainly used by [AG Mod X](https://github.com/rtxa/agmodx) and other mods I made (Zombie Mod, Zombie Escape, Deathrun, etc.).

## Highlights

- Added `mp_respawn_fix` to fix players exploit with high fps with `mp_respawn_delay` set to 0.95 ( this is the fast you can spawn at 125fps with the old behaviour) https://github.com/rtxa/BugfixedHL/commit/d3cd5545c31fbea4f62daf48dfc4ef857b7271c2 -> https://github.com/rtxa/BugfixedHL/commit/3ea80f8a2cc9e22c77ca9b353fe2ec2893d9eccf. See https://github.com/rtxa/agmodx/issues/31#issuecomment-1453581300 for more info about the calculation.
- Added `mp_wallgauss` from AG: multiplier value to control how much damage does the gauss through walls https://github.com/rtxa/BugfixedHL/commit/07ee3910d06074fcf1e4b6b0c3085ce8c8b8e645
- Added `mp_rpg_fix` from AG: Avoids self-damage on rocket launch when moving at high speeds or closer to a wall. https://github.com/rtxa/BugfixedHL/commit/5076586a9069a187bb2f89340568b0edb4c901f9
- Added `mp_blastradius` from AG: multiplier for radius of explosions https://github.com/rtxa/BugfixedHL/commit/3aafbeb26061b6488d9366d7bdbe84aca585ed31
- Disabled ladder crouch fix for being gameplay changing (fix made by Lev who didn't account for client prediction issues) https://github.com/rtxa/BugfixedHL/commit/c914701c7aaae3ce356d321b0dd11469cc352bb9
- Fixed bots not being send to welcome cam. `m_bInWelcomeCam` didn't reset when the player leaves the game. https://github.com/rtxa/BugfixedHL/commit/198bd787a38a5f3ed0ed715a4d7ae65a9f70b2f4#diff-23610fb94802bf7249a995f703d8590ea9d3d86632a98910b80cbbf7c22a2649R336
- Fixed chat anti-flood muting the player indefinitely when the game is paused. It uses server uptime instead of game time because it doesn't run on server pause. Side-effects: server uptime is affected by Unix time problem on year 2038, so we need a better way to get time. https://github.com/rtxa/BugfixedHL/commit/1a1f75ba6ac369958becca8d0f00caddba512f30
- Increased delay for leaving welcome cam to 0.5 to give plugins more time to send to spec. AMXX's  `set_task()` only allows a minimum value of 0.1. https://github.com/rtxa/BugfixedHL/commit/198bd787a38a5f3ed0ed715a4d7ae65a9f70b2f4 -> https://github.com/rtxa/BugfixedHL/commit/9bebd59859e95f2d134b153e7e87f5b6b64a0b3f Why do we need this? See https://github.com/rtxa/agmodx/issues/47
- Allow to disable cooldown for sending `spectator` to players. This allows plugins to send to spec players without worrying about the command being blocked by setting `spectator_cmd_delay` to `0`. Useful if we don't trust on game data being updated regularly. https://github.com/rtxa/BugfixedHL/commit/b7c1e5088a1b9ce2af95151a3cd70ba8f66d5066

## Installation

1. Download latest release from https://github.com/rtxa/BugfixedHL/releases
2. Copy all files to your server folder (`valve`) and replace all if asked.

## Thanks

* Valve for HLSDK release.
* Willday for his HLSDK patch.
* BubbleMod and Bigguy from hlpp.thewavelength.net for parts of spectator code.
* Uncle Mike from hlfx.ru for his Xash3D engine which was very helpful in hard moments.
* KORD_12.7 for constant helping and nice suggestions.
* AGHL.RU community for bug reporting and suggestions.
* JetBrains company for free access to great developer tools.

