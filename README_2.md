# Maldivian Fishery Tycoon — Stage 1 test build (3D)

Single-file HTML5 idle game with a 3D island. No build step. The only outside dependency is Three.js r149, loaded from the jsDelivr CDN, so the page needs an internet connection. Open `index.html` in any browser, or host it on GitHub Pages.

## Put it live on GitHub Pages

1. On github.com, click **+ → New repository**. Name it `maldivian-fishery-tycoon`, set it to **Public**, click **Create repository**.
2. On the new repo page, click **uploading an existing file**, drag in `index.html` and `README.md`, click **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)**, then **Save**.
4. Wait about a minute. The game is live at `https://<your-username>.github.io/maldivian-fishery-tycoon/`. Open that link on a phone to test in portrait.

To ship an update, upload a new `index.html` over the old one. Pages redeploys on every commit.

## What is in this build

- 3D island where workers act out every step: your fisherman walks to his boat, sails out, pole-and-lines tuna, sails back and unloads; cutters, smokers and cooks carry stock between buildings.
- You control the fisherman directly: drag anywhere on the island as a joystick (arrow keys or WASD on a computer), pinch or scroll to zoom. The camera follows him.
- Fishing is a real trip: walk down the jetty, step onto the dhoni at the white circle, steer out to the fishing ground under the seabirds, wait over the shoal while the hold fills, then sail back to land the catch.
- To work a station yourself, walk into its white circle and stay there. Hired staff do the same jobs on their own, carrying stock between buildings.
- Tap a building to upgrade it or hire its staff.
- Stage 1 loop from the Master GDD: Dhoni Fishing → Cutting → Smoking (Valhoamas) → Simmering (Rihaakuru) → local market sale.
- GDD numbers: cycle times 3/2/4/8 s, unit values 10/25/120/600 rf, unlock costs 0/100/1,200/15,000 rf, staff costs 500/2,000/10,000/50,000 rf, Island Supervisor 150,000 rf, goal 500,000 rf, cost growth 1.15, output x2 every 25 levels.
- Pearl shop at GDD prices: Golden Dhoni 300, Raw Material Crate 100, 2h warp 50, 24h warp 350. Pearl bundles are free in this build so testers can try everything.
- Work trips are stretched so they can be watched (a fishing trip is 9 s and lands 3x the catch); rf per second still matches the GDD.
- Simulated rewarded ads (spice rush x2 speed, double offline earnings).
- Autosave to the browser every 10 seconds. Reset under the gear icon.

## Tuning

All balance values are constants at the top of the `<script>` block in `index.html`. Values the GDD does not specify are marked `[TUNED]`.

For balance testing from the browser console, the game logic is exposed as `window.__MFT` (for example `__MFT.income(true)` for idle rf/s).
