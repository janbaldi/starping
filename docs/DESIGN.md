# Starping design plan

## Pitch

A 60-second Mars arcade game for phones and browsers, built for players from about 13. Each mission is four 15-second stages, three of them drawn from a set of tributes to classic arcade and Nintendo-era games, and always ending with a lunar-lander touchdown. A mission launches every 15 seconds; everyone who launches in the same window plays the same mission at the same time.

## Stages

| Stage | Tribute | You do | A button | Hazards | Rewards |
| --- | --- | --- | --- | --- | --- |
| Ice Maze | Maze chase, 1980 | Eat the ice in a mirrored canyon maze (new layout per window) | Speed boost | 3 dust devils that chase | Ice; gold anomaly pellets make devils edible (100, 200, 400…) |
| Meteor Storm | Space shooters, 1979–81 | Auto-fire at drone formations that swoop in and dive | Scan blast (clears a ring) | Diving drones, their shots, meteors that split | Kills, ice from meteors, power capsules |
| Canyon Dash | Platformer, 1985 | Auto-scrolling run over craters | Jump (twice in the air) | Pits, walking devils (stomp them) | Ice arcs, ? blocks with power-ups |
| Ice Shelf | Block breaker, 1976 | Bounce a rock to break ice bricks | Launch | Losing the ball (safety net for the first 5 s and after each miss) | Ice per brick, capsules: wide, multi-ball, shield, heart |
| Touchdown (always last) | Lunar lander, 1979 | Land softly on a 2X, 3X or 5X pad; repeat | Thrust | Speed (shown green/red), falling rocks | Landing bonus = pad × (60 + 6 × ice) + fuel; an ice trail shows the way |

Stage changes are a 1-second morph: the old stage's pieces fly into the new layout while the palette and music change and a banner shows the stage name, the year it pays tribute to, and a one-line hint.

## Making it easy to learn

- One D-pad and one button everywhere; B is a second A.
- Three hearts. A hit costs one heart and gives 2.5 s of blinking safety. Every new stage heals one heart. Every 30 ice is a 1UP (up to 5 hearts).
- Friendlier physics: coyote time and a generous minimum hop in Canyon Dash, a wider paddle, slower devils, a rescue bounce instead of a second pit penalty, and a respawn at the start square in the maze.
- The countdown screen shows the mission plan, the controls and the two multipliers in three lines.

## Scoring

- Ice 10, kills 100–200, chains double (maze devils, stomps), close calls 25, stage clear 100, wave/maze/shelf clear 300–500, anomaly 500, landings as above.
- **No-hit multiplier:** finishing a stage without a hit raises the multiplier ×2, ×3, ×4. A hit resets it.
- **Link:** flying within 40 px of another live pilot doubles everything you score.

## Multiplayer

| Feature | What it is | Status |
| --- | --- | --- |
| Launch windows | Same seeded mission for everyone launching in the same 15 s window | Built |
| Live pilots | Other pilots in your window appear as colored ghosts with initials | Built (claude.ai room) |
| Link bonus | ×2 score while close to another live pilot | Built |
| Live rank | 1ST OF 3 in the HUD; lead changes play a jingle | Built |
| Anomaly race | One gold anomaly per mission; the first pilot in the window to grab it removes it for everyone else, and the first of the day names a crater | Built |
| Window results | Standings of everyone who flew your window | Built |
| Daily board | Best score of the day per pilot | Built (claude.ai db) |
| Ghost replays, crates, star map | From the earlier plan | Planned |

## Measuring excitement

Every run records events (pickups, kills, power-ups, close calls, landings, stage clears, lead changes) and computes the thrill report shown on the results screen. Targets are in `CLAUDE.md`. The last 40 runs per pilot are stored in `runs/<id>` so the owner can compare builds.

Bot play-test of this build (an "average player" autopilot, 6 missions, fixed 60 Hz):

| Metric | Result | Target |
| --- | --- | --- |
| Missions finished | 6 of 6 | — |
| Action rate | 14.8 per 10 s (9.5–22.5) | 8+ |
| Quietest stretch | 5.4 s average (3.4–8.4) | 3 s or less: **not met yet** |
| Close calls | 3.3 (1–5) | 5+: **not met yet** |
| Hits taken | 1.8 (0–4) | 1–2 |
| First reward | 1.1–2.9 s | under 3 s |

A random button-masher survives 15–60 s, so the game is forgiving without being automatic. The quietest stretches mostly fall in the Touchdown finale and in the maze when the nearby ice is gone; those are the next things to tune, together with close calls. Lead changes need real multi-player sessions to measure.

## Monetization (later, not in this build)

Ad break between runs framed as "insert coin", rewarded ads for cosmetics or double XP, an ad-free plus skin pack purchase, and printable crater certificates. Never sold: score, continues, the anomaly, random paid rewards.

## Release

1. Free prototype (this repo and the claude.ai artifact), play-tested with friends and a few teenagers.
2. CrazyGames Basic Launch without ads to collect play data.
3. Own website for share links and crater pages.
4. Later: CrazyGames Full Launch with ads; app stores only once retention is proven.

## Safety for young players

No chat or free text, initials filtered against a blocklist, no account needed, only anonymous gameplay data, ads only through the portal SDK.
