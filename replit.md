# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Shadows of Power Game

Interactive Soviet history game built as a React + Vite web app.

**Architecture:**
- Pure frontend-only React game (no backend/API/database needed)
- All styling uses inline `React.CSSProperties` in a `styles` record at the bottom of App.tsx
- `index.css` is minimal (Google Fonts import, body reset, background gradient)
- Sprite data lives in `src/data/sprites.ts`, campaign data in `src/data/campaigns.ts`

**Game Features:**
- Character select: Stalin or "His People" (citizen) with 24×32 pixel art sprites
- Citizen sub-roles: Ukrainian Peasant Farmer, Factory Worker, Intellectual & Writer, Party Official — each with unique pixel sprites
- **2D movement system**: Players move their character with WASD/arrow keys on a canvas-rendered scene
- **Procedural backgrounds**: 12 scene types (village, kremlin, field, office, warroom, famine, street, border, ruins, bunker, palace, deathbed) drawn on canvas
- **Interactive elements**: Walk to NPCs/objects and press SPACE to trigger story events
- **Bombing mechanic**: Stalin's WWII chapter includes a War Room map where players can launch historically accurate bombing campaigns against Finland, Poland, Germany, Berlin, and Manchuria
- **Historical context**: Each event has detailed historical information accessible via overlay
- **Stats system**: Risk, Stability, Legacy meters affected by choices and bombing decisions
- **Stalin's full life**: 12 chapters from childhood in Gori (1890s) through death at Kuntsevo dacha (March 1953)
- Chapter map for progression

**Freeplay Mode:**
- Canvas-based action game with 5-wave system, NPC AI, bullets, cover objects
- **Stalin (Shooter)**: WASD move, mouse aim/shoot, collect coins from kills, upgrade gun through 5 tiers (Pistol → Machine Gun), 100 HP
- **Civilian (Survival)**: WASD move, dodge NPC bullets, collect food (+15 HP), click dead bodies (+8 HP), survive timed waves, 60 HP
- NPC friendly fire creates bodies for civilian to loot
- Wave timer for civilian mode (10 seconds per wave), kill-all for Stalin mode
- Canvas size: 800×500

**Key Files:**
- `artifacts/shadows-of-power/src/App.tsx` — Main app with all screens, GameCanvas component, BombingOverlay, PixelSprite, mode select
- `artifacts/shadows-of-power/src/FreeplayGame.tsx` — Full freeplay action game component
- `artifacts/shadows-of-power/src/data/sprites.ts` — All 6 character sprite pixel data + palettes
- `artifacts/shadows-of-power/src/data/campaigns.ts` — Campaign events, sub-roles, bombing targets with historical data

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
