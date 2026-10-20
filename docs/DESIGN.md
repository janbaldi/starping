# Starping design plan (summary)

The full, editable plan lives in the Claude doc "Starping — Game Design Plan". This file keeps the decisions next to the code.

## Pitch

A 60-second space arcade game for phones and browsers, built for players from about 13. Ping to find stars, grab them, escape through the wormhole. One shared daily sector; the first player to bank the golden star names it forever.

## Core loop

1. Tap to start. The title shows today's sector and the top pilots.
2. Fly in the dark; hold your thumb to steer.
3. Tap to ping: a ring reveals stars, rocks and the wormhole for about two seconds. Pings recharge in 1.5 s.
4. Grab stars; quick pickups build a combo.
5. Lurkers sleep in the dark and chase you for a few seconds when a ping wakes them.
6. Fly into the wormhole to bank your stars. Crash or run out of time and they are lost.

Score: stars × combo + 2 points per second left. The key decision every run: one more star, or escape now?

## Shared world (async multiplayer)

| Trace | What it is | Status |
| --- | --- | --- |
| Daily board | Best score of the day per player | Built (claude.ai version) |
| Golden star | First to bank it names it with 3 initials | Built (claude.ai version) |
| Ghosts | Faint replay of the top runs and friends' best runs | Planned |
| Crates | Crashing drops your stars in a crate others can grab | Planned |
| Star map | All past sectors and their golden stars | Planned |

Anti-cheat later: upload the run's input log and let the server replay it with the same deterministic engine.

## Gamification

Beat your best, daily board, XP levels that unlock probe skins and trail colors, the golden star, and a streak with a weekly free freeze. No paid random rewards, no pay-to-win, no streak shaming.

## Release

1. Free prototype (this repo), shared with friends and a few teenagers for play-testing.
2. CrazyGames Basic Launch: goes live without their SDK and without ads, to collect playtest data.
3. Own website for share links and golden-star pages.
4. Later: CrazyGames Full Launch with ads through their SDK; app stores only once retention is proven.

## Monetization (later, not in this build)

Ad break between runs framed as "insert coin", rewarded ads for cosmetics or double XP, an ad-free plus skin pack purchase, and printable golden-star posters. Never sold: score, continues, the golden star, random paid rewards.

## Data to collect once there is a backend

Events: `run_start`, `ping`, `lurker_wake`, `crash`, `escape`, `crate_grab`, `golden_star`, `share`, `session_end`.

| KPI | Alpha target (assumption) |
| --- | --- |
| Time to first star | under 15 s |
| D1 / D7 / D30 retention | 40% / 20% / 8% |
| Runs per player per day | 5 or more |
| Escape rate | 50–70% of runs |
| Share rate | 10% of daily players |

## Roadmap

| Phase | Weeks | Content | Gate to the next phase |
| --- | --- | --- | --- |
| 0 Cabinet | 1–2 | Renderer, one-thumb controls on a phone | Controls feel good on a phone |
| 1 Fun alone | 3–6 | Ping, stars, lurkers, wormhole | Testers replay without being asked |
| 2 Shared traces | 7–10 | Backend, crates, ghosts, daily board | Server replays match client scores |
| 3 Star map and meta | 11–14 | Star map, golden star, levels, skins, share card, telemetry | Alpha D7 retention of 20% or more |
| 4 CrazyGames launch | 15–18 | Basic Launch, then Full Launch; own site | — |

This prototype already covers most of phases 0 and 1.

## Safety for young players

No chat or free text, initials filtered against a blocklist, no account needed, only anonymous gameplay data, ads only through the portal SDK.
