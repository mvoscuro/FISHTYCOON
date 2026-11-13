# Maldivian Fishery Tycoon — Stage 1 test build (3D)

HTML5 idle game with a 3D Maldivian island. No build step. Three files make the game: `index.html`, `assets/island.glb` (the fishing island, reef, dhonis, palms, buildings and people) and `assets/factory.glb` (the Stage 2 factory island), all modelled in Blender. Three.js r147 loads from the jsDelivr CDN, so the page needs an internet connection. It must be opened from a web address (GitHub Pages or a local server), not by double-clicking the file.

## Put it live on GitHub Pages

1. On github.com, click **+ → New repository**. Name it `maldivian-fishery-tycoon`, set it to **Public**, click **Create repository**.
2. On the new repo page, click **uploading an existing file**, drag in `index.html`, `README.md` and the whole `assets` folder (it must stay a folder named `assets` with `island.glb` and `factory.glb` inside), click **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)**, then **Save**.
4. Wait about a minute. The game is live at `https://<your-username>.github.io/maldivian-fishery-tycoon/`. Open that link on a phone to test in portrait.

To ship an update, upload the new `index.html` (and the `.glb` files if the models changed) over the old ones. Pages redeploys on every commit.

## What is in this build

- 3D island where workers act out every step: your fisherman walks to his boat, sails out, pole-and-lines tuna, sails back and unloads; cutters, smokers and cooks carry stock between buildings.
- You control the fisherman directly: drag anywhere on the island as a joystick (arrow keys or WASD on a computer), pinch or scroll to zoom. The camera follows him.
- A yellow arrow always points to the next thing to do, and the camera moves in closer while you fish or work at a station.
- Fishing is a real trip: walk down the jetty, step onto the dhoni at the white circle, steer out through the reef channel to the fishing ground under the seabirds, wait over the shoal while the hold fills, then sail back to land the catch.
- To work a station yourself, walk into its white circle and stay there. Hired staff do the same jobs on their own, carrying stock between buildings.
- Tap a building to upgrade it or hire its staff.
- Stage 1 loop from the Master GDD: Dhoni Fishing → Cutting → Smoking (Valhoamas) → Simmering (Rihaakuru) → local market sale.
- GDD numbers: cycle times 3/2/4/8 s, unit values 10/25/120/600 rf, unlock costs 0/100/1,200/15,000 rf, staff costs 500/2,000/10,000/50,000 rf, Island Supervisor 150,000 rf, goal 500,000 rf, cost growth 1.15, output x2 every 25 levels.
- Pearl shop at GDD prices: Golden Dhoni 300, Raw Material Crate 100, 2h warp 50, 24h warp 350. Pearl bundles are free in this build so testers can try everything.
- Work trips are stretched so they can be watched (a fishing trip is 9 s and lands 3x the catch); rf per second still matches the GDD.
- Simulated rewarded ads (spice rush x2 speed, double offline earnings).
- Autosave to the browser every 10 seconds. Reset under the gear icon.

## Stage 2: Industrial Processing Hub

- Buying the industrial island (500,000 rf) unlocks it. The 🏭 / 🏝️ button in the top bar moves you between your two islands; the first island keeps earning.
- Stations and numbers from the Master GDD: Dock Purchasing (150,000 rf; 1,500 rf buys 50 tuna every 5 s), Auto-Butchering (380,000 rf; 5 tuna → 5 loins, 280 rf each until a line uses them), Canning Line (1.5M rf; 2 loins → a 6,200 rf case), Vacuum Pouches (7M rf; 3 loins → an 18,500 rf pouch), Fish Meal Plant (23M rf; 10 waste → a 77,000 rf sack).
- Until you hire managers you run the quay and each line yourself by standing in its white circle. Harbor Master (600,000 rf) automates buying; Factory Floor Manager (1.85M rf) automates the lines; Quality Control Lead (7.7M rf) adds 10% output; Plant Operations VP (18.5M rf) adds 50% speed and 8-hour offline earnings.
- Goal: 75,000,000 rf to fund the export harbour. Stage 3 is not built yet.
- Testing shortcut (browser console): `__MFT.S.won = true; __MFT.S.mvr = 5e6;` then tap the 🏭 button.

## Tuning

All balance values are constants at the top of the `<script>` block in `index.html`. Values the GDD does not specify are marked `[TUNED]`.

For balance testing from the browser console, the game logic is exposed as `window.__MFT` (for example `__MFT.income(true)` for idle rf/s).
