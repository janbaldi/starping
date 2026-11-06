# Starping

A 60-second Mars arcade game for phones and browsers. Every mission is four 15-second stages that pay tribute to arcade and Nintendo-era classics, then a lunar-lander touchdown. A mission launches every 15 seconds, and everyone in the same launch window plays it together.

## Play

Open `index.html` in any browser. It is one self-contained file: no build step, no install.

| Action | Phone or tablet | Laptop |
| --- | --- | --- |
| Move | On-screen D-pad | Arrows or WASD, or a gamepad |
| Action | A (or B) | Space, Z or X |

To play it on your phone from this repo, turn on GitHub Pages (Settings → Pages → deploy from the `main` branch, root folder).

## How it plays

- **Ice Maze** (maze chase): eat the ice, dodge the dust devils; gold pellets turn the tables.
- **Meteor Storm** (space shooter): auto-fire at swooping drones and splitting meteors; A fires a scan blast.
- **Canyon Dash** (platformer): jump craters, stomp devils, bump ? blocks for power-ups.
- **Ice Shelf** (block breaker): break ice bricks, catch capsules for multi-ball and a wider paddle.
- **Touchdown** (lunar lander, always last): follow the ice trail and land softly on a 5X pad for the big bonus.

Three hearts, one healed per stage, a 1UP every 30 ice. Finish a stage without a hit to raise your multiplier; fly next to another live pilot for ×2.

## Multiplayer

Launch windows, live pilots with initials, a live rank, a race for the day's anomaly (the first pilot to land with it names a crater), and a daily board. The live features and the board use the claude.ai artifact room and database; elsewhere the game plays solo.

## Excitement metrics

The results screen shows a thrill report (action rate, quietest stretch, close calls, lead changes) against the targets in `CLAUDE.md`. See `docs/DESIGN.md` for the latest bot play-test numbers.

## Status

Free prototype, no ads or payments.
