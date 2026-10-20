# Starping: rules for every coding session

Read this before changing anything. The full plan is in `docs/DESIGN.md`.

## Pillars

1. **Learn it in five seconds.** If a rule needs a sentence of explanation, cut it or show it in play.
2. **Mission-control honest.** The game looks like a real rocketry livestream: a lander over Mars at night, telemetry on screen, nothing cartoonish. Everything is drawn by code.
3. **A new verb, not a remake.** Scanning in the dark to find what to grab is the core verb. No reskins of arcade classics.
4. **Players meet through traces.** No chat, no lobbies, no free text. Only three initials.
5. **Money never buys score.**

## Theme: Starping / Mars

| Game rule | On screen |
| --- | --- |
| Player | Reusable lander, seen from above |
| Ping | Lidar scan (dashed ice-white ring) |
| Stars | Ice cores (white hexagons) |
| Golden star | Anomaly (gold diamond); the first pilot to land with it names a crater |
| Rocks | Boulders, shown as lidar point clouds |
| Lurkers | Dust devils that wake when scanned |
| Wormhole | Landing pad with orange lights |

## Look

- Everything is drawn with Canvas 2D at runtime. No image files, sprites or recorded audio.
- Night: the terrain stays dark except around the lander's lights; objects appear only when scanned or very close.
- Palette: void `#000000`, hull `#f2f4f6`, steel `#8d96a0`, rust `#b5532e`, plume `#ff7a2f`, ice `#bfefff`, anomaly gold `#ffc65c`, dust-devil red `#e0603a`. Color means something: ice white collect, gold rare, red danger, orange pad.
- Type: Archivo Expanded (wide uppercase, tracked) for labels; IBM Plex Mono for every number. No paragraphs during play.
- HUD: countdown clock, ice and score, 60-second mission timeline, lidar and heading gauges.
- Sound: Web Audio synth and filtered noise only.

## Engineering rules

- Keep the game playable from a single `index.html` until there is a real reason to add a build step.
- Gameplay values (speed, turn rate, ping timing, counts, scoring) do not change with the theme; change them only on purpose, one at a time.
- The daily mission must be identical for everyone: all world and terrain generation uses the seeded RNG from the UTC date. Never use `Math.random()` for anything that affects the layout or the score.
- Small, single-feature changes, each playable on a phone before the next one starts.
- Safety for young players: initials are filtered against the blocklist; collect no names, emails or locations.
