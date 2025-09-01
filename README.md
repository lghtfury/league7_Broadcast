# Quidditch Broadcast — Build Plan

This repo contains the evolving broadcast system for **League 7**.  
The goal: a single-link overlay + control panel setup that can scale from simple community matches to full event productions.

---

## Phase 1 (Must-build soon)

- [ ] **Single-link Dynamic Overlay (Router)**
  - One URL in OBS loads all views (`?view=startingsoon|gameplay|teamvsteam|roster|interview`).
  - Overlay listens to Firebase `scene.current`, `payload`, and `transition`.
  - Default fade and cut transitions.
  - **Acceptance:** Switching `scene.current` changes scene on-screen within 300 ms.

- [ ] **Producer Control Panel v2**
  - Tabs: Scenes / Ticker / Lower Thirds / Assets / Settings.
  - Lock toggle (`sceneLock=true`) blocks commentator requests.
  - Requests appear in a queue; producer can approve/deny.
  - **Acceptance:** When locked, commentator actions do nothing. When unlocked, they appear in queue.

- [ ] **Role-based Access**
  - Tokens in URL for now: `?role=producer` or `?role=commentator&room=L7`.
  - Later upgrade to Firebase Auth with custom claims.
  - **Acceptance:** Producer overrides always win; commentator cannot change scene when locked.

---

## Phase 2 (High value)

- [ ] **Commentator Web Deck**
  - Minimal buttons: Gameplay / Team vs Team / Roster / Starting Soon / Interview.
  - Posts `requestedView` with optional notes.
  - **Acceptance:** Commentator sees status update (pending/approved/denied) within 1 s.

- [ ] **Pitch Drawing Board**
  - Canvas with arrows, lines, zones.
  - Snap to pitch grid, team colors, undo, clear.
  - “Show on stream” toggle pushes drawing to overlay layer (auto-hide timer).
  - **Acceptance:** Drawings appear on overlay within 300 ms and clear instantly.

- [ ] **VDO Ninja Bridge Buttons**
  - Quick copy links for casters and producers.
  - Optional mute/solo labels (reference only, not direct control).

---

## Phase 3 (Stretch goals)

- [ ] **Producer Web Stream Deck**
  - Presets: one-click loads scene + ticker + lower third + background.
  - Touch-friendly for tablets, dockable in OBS.

- [ ] **Preview vs Program**
  - Preview iframe + Program iframe.
  - Producer presses “Take” to push live.
  - **Acceptance:** Program never flashes unexpected content.

- [ ] **Auto Assets from Google Sheet**
  - Columns: `Team | PrimaryColor | SecondaryColor | FontSize | Logo URL`.
  - Panel search + pick; overlay styles auto-update in <300 ms.

- [ ] **Ticker + Lower Third Templates**
  - Saved templates for common segments.
  - Timed tickers that auto-expire.
  - Lower third queue with animated in/out.

- [ ] **Alerts + Safety**
  - Panic button hides ticker + pitch instantly.
  - Safe mode: only producer scene changes apply.

---

## Firebase Schema (starter)

```json
{
  "room": "L7",
  "scene": {
    "current": "startingsoon",
    "lock": true,
    "requestedBy": null,
    "transition": "fade-300"
  },
  "requests": {
    "req_abc123": {
      "from": "commentator:flyrish",
      "view": "gameplay",
      "payload": {"matchId": "RVN-PHN-003"},
      "status": "pending",
      "ts": 1690000000
    }
  },
  "overlay": {
    "ticker": {"text": "Welcome to League 7", "active": true},
    "lowerThird": {"title": "Caster", "name": "Flyrish", "active": false},
    "pitch": {"shapes": [], "visible": false}
  },
  "permissions": {
    "producerTokens": ["abcd1234"],
    "commentatorTokens": ["efgh5678"]
  }
}
