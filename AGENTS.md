## Overview
A web app for our jewelry shop where employees log daily sales, owners track performance on a live dashboard, and an AI assistant answers questions about the data (e.g., "What are Bilal's sales this month?"). The app also includes team chat and stock management.

## Tech Stack
- Frontend: TypeScript, Next.js, Tailwind CSS
- Backend: Python, FastAPI (managed with uv)
- Database/Auth/Storage: Supabase (Postgres, Auth, Storage, Realtime)

## Project Structure
- Frontend/ — Next.js app
- Backend/ — FastAPI app

## Commands
Frontend:
- Create: npx create-next-app@latest --typescript --tailwind
- Dev: npm run dev
- Build: npm run build
- Lint: npm run lint

Backend:
- Create env: uv init
- Install deps: uv sync
- Add package: uv add <package_name>
- Run dev server: uv run uvicorn main:app --reload
- Lint/format: uv run ruff check . && uv run ruff format .

## Coding Conventions
- Python: PEP 8, enforced with ruff
- TypeScript: strict mode, no `any`
- Pydantic model for every API input and output

## Business Rules
- Login only, no public signup
- Roles: Owner, SalesPerson
- SalesPerson can create sales; only Owner can update/delete sales

## Security Rules
- RLS on every table
- Backend validates the Supabase JWT on every request
- Secrets live in `.env` (never committed; use `.env.example` as template)

## Database
- Schema changes via Supabase migrations (`supabase migration new <name>`, `supabase db push`)
