# Drop & Shoot

An Atari 2600 game, 4K, written in 6502 assembly. One trooper, one parachute, eight levels of rock shaft between you and the landing pad.

`bin/dropshoot.bin` is the game. It runs in Stella and on real hardware from a Harmony cartridge (NTSC).

## The idea

You hang under your canopy at one height on the screen while the shaft scrolls up past you. Steer left and right, shoot, and get to the bottom. When the ground rises into view, land on the orange pad. Miss it and you lose a canopy; lose all three and the run is over. Eight levels, each a little faster and each adding one new thing. The eighth repeats.

Scores are low on purpose. A landing is a point. The game is about getting down, not about the number.

## Controls

| Input | Action |
|---|---|
| Stick left / right | Steer. The canopy leans and you drift; it takes a moment to build speed and a moment to stop. |
| Button + left or right | Fire sideways. The recoil kicks you the other way, hard: a side shot is also a sideways jump, and it out-pulls the strongest wind. |
| Button, stick centred | Drop a slug straight down. |
| Stick down | Nothing. (A dive was tried and cut as a cheat.) |

One bullet at a time; about half a second to reload. A kill halves the remaining reload.

## Console switches

| Switch | In the game |
|---|---|
| Reset | Restart at the current level. |
| Select (on the title) | Choose the starting level, 1 to 8. The wall colour shows which. |
| Colour / B·W at B·W | Pause. Flip back to continue. |
| Left difficulty A | Music off. |


Stella: F1 Select, F2 Reset, F4 Colour/B·W, F5/F6 left difficulty, F7/F8 right difficulty. On a Mac keyboard hold fn with the function key.

## What you meet

**Birds** patrol sideways as they rise past you. Shoot one from above with the slug and it drops its supplies where it was; shoot it from the side and it just falls away. From level 6 birds are hawks: they lean toward your column while they are well below you, then commit to a straight climb. The slug does not kill a hawk; only a side shot does.

**Supply drops** (a crate under a small gold canopy) are worth a point. Fly into one. In a gust they blow downwind, faster than you do.

**Bombs** come up from the bottom, never sideways, and go off the moment they reach your height: a blast twice their width for a few frames, with a jolt of the rock. Do not be above one when it arrives. They cannot be shot, except while a gust is blowing. From level 3 they sometimes come in pairs.

**Jets** dive from the top straight down your line. Shoot one for a point or step aside. A jet that reaches the bottom leaves a bomb; a jet that hits you is spent and leaves nothing.

**Wind socks** stand on the wall the wind comes from. While one is on screen, and for a few seconds after it leaves, a gust pushes you its way, and the sock leaves a bomb downwind of you when it goes. Socks cannot be shot. The air goes still once the ground is in view.

**Missiles** (from level 5) launch from the bottom at your column and climb straight up in about a second. They cannot be shot. Move.

## Canopies

You start with three, shown bottom left. One is lost to any hit: rock, bird, jet, bomb, blast, missile, or a missed landing. After a hit you are invulnerable for a second and the trooper blinks; one event can only ever cost one canopy. A bonus canopy comes at 10 points and again at 20, up to three.

When you are down to your last canopy, every beat of the drum is a thump.

## Landing

The landing test is the hardware's own collision: if any pixel of a foot is over the pad on the frame the ground reaches you, you have landed. On levels with an off-centre pad the pad appears on both sides; either counts.

## The levels

| Level | New |
|---|---|
| 1 | Birds, supply drops, the funnel |
| 2 | Bombs, and the wind: socks, gusts, the sock's bomb |
| 3 | Jets; bomb pairs |
| 4 | Stronger wind |
| 5 | Missiles |
| 6 | Hawks; objects twice as often |
| 7 | The sock's bomb is followed by a jet |
| 8 | Strongest wind, black rock; repeats |

The wall colour tells you the level: red, orange, gold, green, blue, indigo, violet, black.

## Sound

A slow march on the title. In play, a drum cadence that quickens and gets louder as the ground gets closer, a radar ping while a jet is diving, and the wind while a gust blows.

## Building

Source and build files live alongside this repo in the project folder. `make` assembles with DASM (`-f3 -v0 -Isrc`); `make run` opens the result in Stella.
