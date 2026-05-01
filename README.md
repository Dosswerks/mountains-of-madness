# Mountains of Madness

A single-file HTML5 Canvas arcade game inspired by Satan's Hollow, set in H.P. Lovecraft's Antarctic horror universe. Part of the Dosswerks Arcade collection and the first entry in the Lovecraft Arcade series.

## Play

Open `index.html` in any modern browser. No build step or server required.

## Controls

| Key | Action |
|-----|--------|
| ← → | Move |
| Z | Fire |
| X | Shield |
| ↑ | Enter Ice Cave (when seal is destroyed) |
| P | Pause / Resume |
| R | Restart |
| Q | Quit to title |

Touch controls appear automatically on mobile (≤500px viewport).

## Gameplay

1. Fight waves of Elder Things on the Ruined Campsite screen
2. Collect TNT crates and carry them to the sealed cave entrance on the right
3. Explosives detonate on a 3-second fuse — stay clear of the blast radius
4. Destroy all Cyclopean Stone seal segments to open the cave
5. Press Up to enter the Ice Cave and battle the Shoggoth boss
6. Shoggoths require 3 hits per phase (full → 2 halves → 4 quarters), flashing yellow on each hit
7. Defeat all Shoggoths to advance to the next level with increased difficulty

## Architecture

The entire game lives in a single HTML file: markup, CSS, and all JavaScript. Key design decisions:

- **Canvas**: 480×600 internal resolution, CSS-scaled responsively
- **Namco pixel font**: 8×8 bitmap font rendered at configurable scales for all in-game text, matching the Lovecraft Arcade series visual style
- **Serif footer**: Georgia/Times New Roman for credits, consistent across Lovecraft Arcade titles
- **Delta-time movement**: All speeds and timers are frame-rate independent (60fps baseline)
- **AABB collision**: Axis-aligned bounding box checks for all entity interactions
- **Asset fallbacks**: Every sprite and audio asset has a procedural fallback so the game is fully playable without external files
- **Finite State Machine**: 8 game states govern all transitions and system activation

## Asset Customization

### Sprites

Place PNG files in `assets/` matching these keys. The game draws procedural fallbacks when sprites are missing.

| Key | Description | Dimensions |
|-----|-------------|------------|
| `player.png` | Player ship | 50×50 |
| `elder_thing_1.png`, `elder_thing_2.png` | Elder Thing animation frames | 48×72 |
| `shoggoth_full_1/2.png` | Full Shoggoth frames | 256×192 |
| `shoggoth_half_1/2.png` | Half Shoggoth frames | 160×128 |
| `shoggoth_quarter_1/2.png` | Quarter Shoggoth frames | 96×80 |
| `tnt_crate.png` | TNT explosive crate | 20×20 |
| `bonus_flyover.png` | Bonus UFO | 40×40 |
| `bonus_drop.png` | Dropped bonus pickup | 40×40 |
| `seal_boulder.png` | Cave seal boulder | 36×30 |
| `campsite.png` | Barrier/campsite structure | 96×72 |
| `bg_campsite.png` | Campsite background | 480×600 |
| `bg_icecave.png` | Ice Cave background | 480×600 |
| `bg_gameover.png` | Game Over background | 480×600 |
| `box_art.png` | Start screen art | 480×600 |
| `transition_icecave.png` | Ice Cave transition graphic | 120×120 |
| `transition_campsite.png` | Campsite transition graphic | 120×120 |

### Audio

Place MP3 files in `assets/`. All audio fails gracefully to silence.

- `music_campsite.mp3` — Campsite stage loop (starts during "Returning to Campsite" transition)
- `music_icecave.mp3` — Ice Cave stage loop (starts during "Entering the Ice Cave" transition)
- `sfx_player_fire.mp3`, `sfx_player_hit.mp3`
- `sfx_elder_destroy.mp3`, `sfx_elder_fire.mp3`
- `sfx_shoggoth_split.mp3`, `sfx_shoggoth_destroy.mp3`
- `sfx_bonus_appear.mp3`, `sfx_bonus_hit.mp3`, `sfx_bonus_collect.mp3`
- `sfx_piece_pickup.mp3`, `sfx_piece_place.mp3`
- `sfx_bomb_place.mp3`, `sfx_seal_explosion.mp3`
- `sfx_campsite_complete.mp3`, `sfx_barrier_hit.mp3`
- `sfx_transition.mp3`, `sfx_wave_start.mp3`
- `sfx_game_over.mp3`, `sfx_game_start.mp3`, `sfx_boss_start.mp3`

## Mobile Touch Controls

- Left/Right: Yellow round buttons with black triangle arrows
- Fire: Red round button
- Shield: Blue round button
- Cave (Up): Purple round button, centered between the groups

## Difficulty Scaling

Difficulty increases per level with caps:

| Parameter | Start | Cap |
|-----------|-------|-----|
| Elder Things per wave | 8 | 16 |
| Seal segments | 3 | 8 |
| Enemy fire interval | 120 frames | 40 frames |
| Enemy speed multiplier | 1.0× | 2.5× |
| Projectile speed | 3.0 px/frame | 6.0 px/frame |

## Debug Mode

Press backtick (`` ` ``) to toggle debug overlay. Debug commands:
- `N` — Skip to next stage
- `S` — Spawn a Shoggoth
- `E` — Spawn an Elder Thing
- `I` — Toggle invincibility

## Recent Changes

- All in-game text now uses the Namco 8×8 pixel font at configurable scales, matching the Lovecraft Arcade series style
- Footer/credits use Georgia serif font, consistent across Lovecraft Arcade titles
- Center-screen text (title, game over, paused, transitions) rendered at 2–3× scale for visibility
- "Destroy all seal segments" hint moved to center screen for better visibility
- TNT crate uses custom sprite (`tnt_crate.png`) with brown crate fallback instead of white square
- Shoggoths now require 3 hits per phase with yellow flash on each hit
- Shoggoth projectile fire rate significantly reduced for better playability
- Bonus drop falls much faster after shooting the flyover
- Sound effects added for bomb placement and bonus collection
- Mobile touch buttons redesigned: round, color-coded (Fire=red, Shield=blue, Cave=purple, Move=yellow with black triangles), Cave button centered
- Music starts during transition screens (ice cave music on "Entering the Ice Cave", campsite music on "Returning to Campsite")
- Transition screens include centered graphic placeholders (sprites: `transition_icecave.png`, `transition_campsite.png`)
- First level instruction text appears immediately with a brief delay before enemies spawn
- Elder Thing explosions are larger with yellow particles and flash effect
- "Returning to Campsite" transition shows level number prominently

## License

© 2026 Andrew Doss. All Rights Reserved.
