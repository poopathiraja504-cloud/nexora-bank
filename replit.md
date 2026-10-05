# NEXORA BANK

A premium digital banking prototype that lets users explore a realistic, mock-only financial cockpit and supporting banking workflows.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/nexora-bank/src/App.tsx` — route-aware product UI, mock data, and local interaction state.
- `artifacts/nexora-bank/src/index.css` — NEXORA visual system, responsive layout, and motion tokens.
- `artifacts/nexora-bank/package.json` — React/Vite app scripts and UI dependencies.
- `artifacts/api-server` — shared API scaffold retained for future backend work; the current prototype intentionally uses local mock data.

## Architecture decisions

- The first release is frontend-only and uses local mock state because the brief explicitly requires simulated banking actions and prohibits real credentials, payments, and account connections.
- The app is a multi-route React/Vite artifact with a shared responsive shell so the landing, auth, dashboard, and banking tools feel like one product.
- Demo-state copy is visible in the shell and key screens to distinguish prototype balances and actions from real financial functionality.
- Theme preference is persisted in local storage; no sensitive user information is persisted.

## Product

NEXORA BANK includes a branded landing page, simulated login and OTP flow, banking dashboard, transfer wizard, transaction history and filters, NOVA financial assistant, analytics, virtual card controls, loan and EMI tools, investments, security center, fraud-alert simulation, bill payment confirmation, support chat, settings, dark mode, notifications, toasts, and mobile navigation.

## User preferences

All financial data and interactions must remain demo-only and must not collect or store real credentials, card numbers, PINs, OTPs, or bank details.

## Gotchas

- The frontend workflow supplies `PORT` and `BASE_PATH`; run it through the managed artifact workflow rather than starting Vite from the workspace root.
- This is a prototype, not a banking system. Do not attach payment, bank-account, or identity integrations without an explicit product change.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
