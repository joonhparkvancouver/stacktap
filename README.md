# Stacktap

A one-tap block-stacking arcade game. Single HTML file, zero dependencies, works on desktop and mobile.

**Play:** tap (or Space) to drop the moving block on the tower. Any overhang gets sliced off, so the tower narrows with every sloppy drop. Land within 7px of center for a **perfect** — perfects chain into combos that multiply your score, and 3+ combos regrow the block width. Miss completely and it's game over.

## Run locally

```sh
cd game
python3 -m http.server 4173
# open http://localhost:4173
```

Or just open `index.html` directly in a browser — no server required.

## Deploy (free)

The whole game is one static file. Any of these work in under 5 minutes:

- **Netlify / Vercel** — drag-and-drop the folder, get a URL instantly. Add a custom domain (~$10/yr) when ready to monetize.
- **GitHub Pages** — push to a repo, enable Pages.
- **itch.io** — upload as an HTML5 game for immediate distribution to an existing player audience.

## Revenue path (in order of effort)

1. **Web game portals (fastest to first dollar).** Submit to [CrazyGames](https://developer.crazygames.com), [Poki](https://developers.poki.com), and [GameDistribution](https://gamedistribution.com). They host the game, run the ads, and pay revenue share — no ad account or traffic needed. They each have a small SDK (an "ad break" call between runs); the natural hook point is the game-over screen, before the retry.
2. **AdSense on your own domain.** Once the game is on your own domain with some traffic, apply for AdSense. The `#ad-slot` div at the bottom of `index.html` is reserved for a banner unit (set its height to ~60px when installing). An interstitial on game-over (every N deaths, not every death) earns far more than banners.
3. **Keep players coming back** (multiplies everything above): the Share button already posts scores; next-best additions are a daily challenge seed, streaks, and a "1 more block than your best" nudge on game over.

## Testing hook

`window.__stacktap` exposes `start()`, `step(dt)`, `drop()`, and `info()` for headless/scripted testing of the game logic. Harmless in production; remove before shipping if you prefer.
