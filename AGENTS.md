# AGENTS.md

## Overview
E-commerce website prototype ("Lymor"): a React frontend and an Express + MongoDB (Mongoose) backend. Early scaffold — the backend currently exposes only a health route.

## Layout
- `package.json` (root) — frontend dependencies (React 18, react-router-dom 6); the frontend app itself lives in the `lymor` gitlink.
- `lymor` — gitlink (submodule-like pointer, mode 160000) to the frontend project; there is no `.gitmodules` entry, so it is empty after a plain clone.
- `lymor_backend/server.js` — Express server: CORS, JSON body parsing, Mongoose connection via `process.env.DATABASE_URI`, `GET /`.
- `lymor_backend/package.json` — backend dependencies (express, cors, dotenv, mongoose).

## Commands
- Backend: `cd lymor_backend && npm install && node server.js` (needs `.env` with `DATABASE_URI` and optional `PORT`, default 5000).
- Root: `npm install` for the frontend dependencies.

## Rules
- Never commit `.env` or the MongoDB connection string; `node_modules/` (root and `lymor_backend/`) is gitignored — it was previously committed and has been untracked.
- Do not "fix" the `lymor` gitlink without being asked.
- Keep secrets in environment variables only.
