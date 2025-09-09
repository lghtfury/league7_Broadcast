# 🎮 League 7 Broadcast Control Panel & Overlay Overhaul

This is the step-by-step gameplan for cleaning, rebranding, and upgrading the system this week.  
Check things off as you complete them ✅.

---

## Phase 0 — Snapshot
- [ ] Create backup branch: `v1-archive`
- [ ] Export current Streamlabs scene collection

---

## Phase 1 — Repository Cleanup
- [ ] Create folder structure: `/overlays`, `/control`, `/assets`, `/docs`
- [ ] Move overlay files → `/overlays`  
  - gameplay_overlay.html  
  - series.html (rename from teamvsteam.html)  
  - rosters.html  
  - starting_soon.html  
  - intermission.html (new)  
  - thank_you.html (new)  
  - deck_board.html  
  - quidditchboard.html
- [ ] Move panel + router → `/control`
- [ ] Move images, logos, overlay.png, fonts → `/assets`
- [ ] Move README.md + Todo.md → `/docs`
- [ ] Remove duplicates (ex: `logo_rosters` vs `logos_rosters.html`)
- [ ] Standardize filenames → lowercase_with_underscores
- [ ] Update README quick start: “Use router.html as single Browser Source”

---

## Phase 2 — Brand System (Non-Gameplay)
- [ ] Define black + gold palette (matte black, metallic gold, white/gray text)
- [ ] Standardize fonts (headline + UI font)
- [ ] Set logo placement rules (top/center or header area)
- [ ] Add **“Made by lghtfury”** watermark (bottom corner, ~40% opacity)

---

## Phase 3 — Apply Theme to Overlays
- [ ] **Starting Soon** → black/gold theme, ticker at bottom, logo top, watermark
- [ ] **Series** → head-to-head in black/gold frame, logo top, watermark
- [ ] **Rosters** → gold headers/cards, logo top, watermark
- [ ] **Intermission** → countdown timer, next match info, logo, watermark
- [ ] **Thank You** → thanks text, next matchup ticker, logo, watermark
- [ ] **Deck Board / Quidditch Board** → wrap in black/gold frame
- [ ] Confirm **Gameplay Overlay** stays in team color theme (no rebrand)

---

## Phase 4 — Control Panel UX
- [ ] Remove Preview section
- [ ] Add Simplified vs Advanced toggle  
  - Simplified: Match ID, scores, ticker, active screen, Push All  
  - Advanced: color pickers, per-overlay pushes, debug
- [ ] Rename **Push TVT** → **Push Series**
- [ ] Add **Universal Push All** (big primary button)
- [ ] Demote individual pushes → ghost buttons in Advanced view

---

## Phase 5 — Router Workflow
- [ ] Add `router.html` in `/control`
- [ ] Router screens list:  
  - Starting Soon  
  - Gameplay  
  - Series  
  - Rosters  
  - Intermission  
  - Thank You
- [ ] Confirm router passes `?overlay=...` to overlays
- [ ] Test **Push All** → updates Scoreboard, Series, Rosters, Ticker
- [ ] Add Intermission time controls (date/time or +5/10/15m quick picks)
- [ ] Add Thank You Screen to Active Screen dropdown

---

## Phase 6 — QA Checklist
- [ ] Verify all overlay URLs load from GitHub Pages
- [ ] Confirm Match ID selection auto-fills teams/colors
- [ ] Confirm **Push All** updates every overlay correctly
- [ ] Confirm Active Screen changes in router within 1–2 seconds
- [ ] Confirm Intermission shows countdown + next match
- [ ] Confirm Thank You screen shows casters/teams/socials
- [ ] Streamlabs test: single Browser Source, 1920×1080, no auto-refresh/shutdown
- [ ] Dry run flow: Starting Soon → Gameplay → Intermission → Gameplay → Thank You

---

## Phase 7 — Producer Docs
- [ ] Write Simplified “Show Flow” guide:  
  1. Select Match ID  
  2. Update Ticker  
  3. Push All  
  4. Switch Active Screen  
- [ ] Write Advanced “Power Tips” guide for setup/troubleshooting

---
