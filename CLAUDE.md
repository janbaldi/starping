# Starping: rules for every coding session

Read this before changing anything. The full plan is in `docs/DESIGN.md`.

## Pillars

1. **Learn it in five seconds.** If a rule needs a sentence of explanation, cut it or show it in play.
2. **Cabinet-honest.** Every screen must pass the test "could a 1981 vector cabinet have drawn this?"
3. **A new verb, not a remake.** Pinging in the dark to find what to grab is the core verb. No reskins of arcade classics.
4. **Players meet through traces.** No chat, no lobbies, no free text. Only three initials.
5. **Money never buys score.**

## Cabinet limits (the game screen)

- Vector lines only on black. No bitmaps, gradients or filled shapes in play.
- Palette: phosphor cyan `#7df9ff`, star yellow `#ffe66d`, danger red `#ff4d6d`, wormhole violet `#c77dff`, white. Glow and short persistence trails are allowed.
- One uppercase monospace font for HUD text; no paragraphs during play.
- Sound: simple Web Audio synth voices (square, triangle, sine, saw, noise). No recorded samples.
- Input: hold to steer, tap to ping. Mouse and keyboard must also work.
- A run is 60 seconds.

Menus outside play (title, score screen) may use HTML, in the same palette.

## Engineering rules

- Keep the game playable from a single `index.html` until there is a real reason to add a build step.
- The daily sector must be identical for everyone: all world generation uses the seeded RNG from the UTC date. Never use `Math.random()` for anything that affects the layout or the score.
- Small, single-feature changes, each playable on a phone before the next one starts.
- Safety for young players: initials are filtered against the blocklist; collect no names, emails or locations.
