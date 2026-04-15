# Game UI Overhaul & Historical Context

## What & Why
Redesign the character selection screen, add citizen sub-role selection with risk badges, and add a historical context panel to each game event. These changes make the game more immersive and educational.

## Done looks like
- Character selection screen shows pixel sprites displayed side-by-side horizontally (not as card buttons). Player clicks a character to highlight/select them, then presses a "PLAY >>>" button below to proceed.
- When the player selects "Soviet Citizen" (his people), a new sub-role selection screen appears titled "WHAT DO YOU DO?" with 4 occupation options displayed as full-width rows: (1) Ukrainian peasant farmer — EXTREME RISK, (2) Factory worker in Leningrad — MEDIUM RISK, (3) Intellectual and writer — HIGH RISK, (4) Communist Party official — HIGH RISK. Each row shows the occupation description on the left and a colored risk badge on the right (red for extreme, orange/amber for high, yellow for medium). Selecting a sub-role sets the starting stats and flavor text accordingly, then proceeds to the map.
- Stalin path skips the sub-role screen and goes directly to the map.
- Every game event/chapter screen has a "Historical Context" button on the side. Clicking it opens a slide-out or overlay panel with a short paragraph of real historical context for that specific event, so the player understands what actually happened.
- Historical context data is added to the campaign data for each event (a new `historicalContext` field).

## Out of scope
- Changing the actual campaign event choices or outcomes
- Adding new chapters
- Changing the map or end screens

## Tasks
1. **Redesign character selection screen** — Display Stalin and Soviet Citizen as horizontal pixel art sprites with names below them. Add selection highlight state and a "PLAY >>>" button at the bottom center. Remove the card-button layout.

2. **Add citizen sub-role selection screen** — Create a new screen that appears after selecting Soviet Citizen, titled "WHAT DO YOU DO?" with 4 occupation rows showing description text and a colored risk-level badge. Each sub-role should set different starting stats (risk/stability/legacy). Add sub-role data to the campaign data file.

3. **Add historical context to campaign data** — Add a `historicalContext` string field to each event in both campaigns with a short, accurate paragraph about the real history behind each scenario.

4. **Add historical context button and panel to the game screen** — Place a "Historical Context" button on the side of the game event panel. When clicked, it opens a slide-out or overlay panel showing the historical context text for the current event. Include a close button to dismiss.

## Relevant files
- `artifacts/shadows-of-power/src/App.tsx`
- `artifacts/shadows-of-power/src/data/campaigns.ts`
- `artifacts/shadows-of-power/src/index.css`
