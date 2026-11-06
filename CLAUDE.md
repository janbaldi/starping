# Starping: rules for every coding session

Read this before changing anything. The full plan is in `docs/DESIGN.md`.

## Pillars

1. **Learn it in five seconds.** One D-pad and one button (A; B does the same). Every stage shows a one-line hint while it loads. Getting hit costs a heart, never the whole mission, and each new stage heals one heart.
2. **Arcade fusion, on purpose.** A Mars mission played as a medley of clear tributes to Atari and early Nintendo classics: maze chase, space shooter, platformer, block breaker, lunar lander. Pixel art, chiptune, power-ups, 1UPs. References are welcome; copying names, logos or exact level layouts is not.
3. **Measurably exciting.** Every run records a thrill report (below). A change that makes the numbers worse needs a reason.
4. **Multiplayer first.** Launch windows put players in the same mission at the same moment. Live pilots, a shared race for the anomaly, a live rank and a link bonus make playing together better than playing alone. No chat, no free text: three initials only.
5. **Money never buys score.**

## Thrill targets (per 60-second mission)

| Metric | Target | Where it comes from |
| --- | --- | --- |
| Action rate | 8 or more events per 10 s | pickups, kills, power-ups, close calls, landings, stage clears |
| Quietest stretch | 3 s or less | longest gap between events |
| Close calls | 5 or more | hazards that pass within a few pixels without a hit |
| Hits taken | 1–2 on average | more is frustrating, 0 every time is boring |
| First reward | under 3 s | time to the first event |
| Lead changes | 1 or more when 2+ pilots share a window | live rank |

The game shows these on the results screen and stores the last 40 runs per pilot in `runs/<id>` (owner-readable) for tuning.

## Look and sound

- One 192×224 canvas, scaled with crisp pixels. Everything is drawn by code; no image files or recorded audio.
- 3×5 pixel font. Mars palette: void `#000000`, hull `#f2f4f6`, rust `#b5532e`, ice `#bfefff`, gold `#ffc65c`, danger `#e0603a`, plume `#ff7a2f`. Ice is always what you collect, gold is rare, red-orange is danger.
- Square-wave chiptune: one short tune per stage, jingles for clears, 1UPs, power-ups and landings.

## Engineering rules

- Keep the game playable from a single `index.html` until there is a real reason to add a build step.
- Gameplay randomness comes from the seeded RNG (`R.rng`, seeded by UTC date, launch window and stage). `Math.random()` is only for particles and screen effects.
- The simulation runs at a fixed 60 Hz step so it feels the same on every phone.
- Tune one value at a time and re-run the bot play-test (`window.__bot`, `window.__plan`, `window.__sp` are the hooks).
- Everything multiplayer must degrade to a complete solo game when the platform offers no room or database.
- Safety for young players: initials are letters only and filtered against the blocklist; collect no names, emails or locations.
