# Starping

A 60-second space game for phones and browsers. Fly a reusable lander low over Mars at night, fire lidar scans into the dark, recover ice cores, and touch down on the landing pad before the clock runs out.

Everyone flies the same mission each day. The first pilot to land with the day's anomaly names a crater.

## Play

Open `index.html` in any browser. It is one self-contained file: no build step, no install.

| Action | Phone or tablet | Laptop |
| --- | --- | --- |
| Steer | Hold your thumb on the screen | Mouse, or left/right arrows |
| Scan | Quick tap | Click or space bar |

To play it on your phone from this repo, turn on GitHub Pages (Settings → Pages → deploy from the `main` branch, root folder).

## How it plays

- **Scan** to light up the ground for two seconds.
- **Grab ice cores**; quick pickups build a combo.
- **Avoid boulders and dust devils.** Dust devils sleep until a scan hits them, then chase you.
- **Land on the pad** to bank your ice. Crash or run out of time and it is lost.
- Score: ice × combo, plus 2 points for every second left.
- **Launch windows:** a mission launches every 15 seconds. Everyone who presses Launch in the same window starts on the pad together and flies the same mission.
- **Phase shifts:** the 60 seconds are four 15-second phases. Night comes first; then dust storm (wind pushes you), solar flare (everything visible, dust devils hunt) and meteor shower (stay out of the red rings), in an order seeded per window. The timeline shows what is next.
- **Live pilots:** other pilots flying today show as blinking beacons. Their lidar scans light up the ground for you, and ice you grab while linked to a nearby pilot counts double.

## What is in this build

- Daily mission generated from the UTC date, identical for every player, including the terrain
- Launch windows every 15 s and four seeded phases per mission
- Live pilots, shared lidar and the link bonus (claude.ai version; offline builds play solo)
- Mission-control display: countdown, ice and score, 60-second timeline, lidar and heading gauges
- Synth sound with engine rumble, phone vibration
- Copyable result line for sharing
- Personal best per day, kept in the browser

The shared daily board and crater naming use the claude.ai artifact database. Outside claude.ai the game runs in offline mode: everything plays, but the board is not connected.

## Not built yet

Ghosts, cargo pods, mission patches, liveries, and a backend for a public daily board. See [docs/DESIGN.md](docs/DESIGN.md).

## Status

Free prototype, no ads or payments. Balancing (speed, number of dust devils, scan timing) still needs testing with real players.
