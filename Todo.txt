Perfect — let’s treat this like a broadcast control panel + overlay rebrand project. Here’s a **master to-do list** before you overhaul:

---

## 🎛 Control Panel (Function + UX)

* [ ] Remove the Preview section (it’s redundant with Streamlabs).
* [ ] Reorganize layout into sections:

  * Match Setup
  * Scoreboard
  * Series Display (renamed from TVT)
  * Rosters
  * Logos (optional / future)
  * Ticker
  * Active Screen
* [ ] Add **Simplified vs Advanced toggle**:

  * Simplified = Match ID, scores, ticker, active screen, Push All
  * Advanced = colors, per-overlay pushes, debug/testing
* [ ] Implement **Universal Push All** button as the default producer workflow.
* [ ] Keep per-overlay push buttons (Scoreboard, Rosters, Series, Ticker, Logos) as ghost/secondary in Advanced view.
* [ ] Rename “Push TVT” → **Push Series** everywhere.
* [ ] Update control panel button styles → clear hierarchy (primary = bold gold/blue, secondary = ghost).

---

## 🖼 Overlay Screens (Visuals)

* [ ] Update **Starting Soon screen** → matte black + metallic gold theme, centered L7 logo, ticker bar, watermark.
* [ ] Update **Series screen** → black & gold frame with team head-to-head, L7 logo top center, watermark bottom.
* [ ] Update **Rosters screen** → black/gold header, roster cards styled in gold outlines, L7 logo top, watermark bottom.
* [ ] Add new **Thank You screen** → “Thanks to casters, producers, teams” text in gold, L7 logo, next matchup ticker, watermark.
* [ ] Add new **Intermission (Countdown) screen** → large countdown timer, matte black/gold background, next matchup info, L7 logo, watermark.
* [ ] Ensure **all overlays except gameplay** follow the black + gold L7 branding.
* [ ] Apply consistent placement:

  * L7 logo top/center or header area
  * “Made by lghtfury” watermark bottom corner (40% opacity)

---

## ⚙️ Router & Workflow

* [ ] Add **router.html** as the single Streamlabs Browser Source.
* [ ] Make sure router screen list includes:

  * Starting Soon
  * Gameplay
  * Series
  * Rosters
  * Intermission (Countdown)
  * Thank You
* [ ] Ensure router passes `?overlay=...` parameter to all overlays so they stay linked to Firestore data.
* [ ] Test Universal Push → confirm all overlays update seamlessly with one click.
* [ ] Add intermission controls in control panel (time picker or “+5 / +10 / +15 min” quick buttons).
* [ ] Add Thank You Screen to Active Screen dropdown.

---

## 🛠 Infrastructure / Cleanup

* [ ] Clean up GitHub repo structure (one folder for overlays, one for panel/router).
* [ ] Update README with producer instructions (Simplified workflow vs Advanced).
* [ ] Test overlays at 1920×1080 with scaling in Streamlabs to ensure everything lines up.
* [ ] Verify all Firestore doc references are consistent (`overlays`, `tvt/series`, `ticker`, `router`).
* [ ] Double-check asset paths for logos, fonts, and gold/black theme elements.

---

👉 Question for you: do you want me to make a **prioritized version of this list** (like “do these 5 first to get Simplified + router working, then the cosmetic rebrand can follow”), or keep it as one big checklist?
