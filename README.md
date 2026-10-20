# Starping

A 60-second vector-arcade game for phones and browsers. Fly through a dark sector, tap to ping, grab the stars your ping reveals, and dive into the wormhole before the clock runs out.

Everyone gets the same sector each day. The first player to bank the day's golden star names it with three initials.

## Play

Open `index.html` in any browser. It is one self-contained file: no build step, no install.

| Action | Phone or tablet | Laptop |
| --- | --- | --- |
| Steer | Hold your thumb on the screen | Mouse, or left/right arrows |
| Ping | Quick tap | Click or space bar |

To play it on your phone from this repo, turn on GitHub Pages (Settings → Pages → deploy from the `main` branch, root folder).

## What is in this first build

- Daily sector generated from the UTC date, identical for every player
- Stars, rocks, lurkers that wake when pinged, a wormhole to escape through
- Combo scoring plus a time bonus on escape
- Vector look with glow and phosphor trails, synth sound, phone vibration
- Copyable result line for sharing
- Personal best per day, kept in the browser

The shared daily board and golden-star naming use the claude.ai artifact database. Outside claude.ai the game runs in offline mode: everything plays, but the board is not connected.

## Not built yet

Ghosts, crates, star map, XP and skins, and a backend for a public daily board. See [docs/DESIGN.md](docs/DESIGN.md) for the plan.

## Status

Free prototype, no ads or payments. Not yet play-tested on real phones; expect balancing changes to speed, lurker count and ping timing.
