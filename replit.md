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

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.

## MeuDown - Baixador de Vídeos

A full-stack video downloader web app supporting YouTube, Instagram, TikTok, and more.

### Features
- Download videos without watermarks via yt-dlp
- Formats: MP4 (1080p, 720p, 480p, 360p) and MP3
- User authentication (email/password with cookie sessions)
- Download history for authenticated users
- Rate limiting: 3 downloads/day for anonymous, 20 for authenticated
- Download links expire after 1 hour
- Mobile-first dark mode UI in Brazilian Portuguese

### Key Files
- `artifacts/meudown/` — React + Vite frontend
- `artifacts/api-server/src/routes/auth.ts` — Auth endpoints (register, login, logout, me)
- `artifacts/api-server/src/routes/videos.ts` — Video info + download endpoints
- `artifacts/api-server/src/routes/downloads.ts` — Download history + stats
- `artifacts/api-server/src/lib/ytdlp.ts` — yt-dlp wrapper for video downloading
- `artifacts/api-server/src/lib/auth.ts` — Password hashing + session management
- `lib/db/src/schema/users.ts` — Users table
- `lib/db/src/schema/downloads.ts` — Downloads history table
- `lib/db/src/schema/sessions.ts` — Sessions table

### System Dependencies
- `yt-dlp` — installed via nix (`~/.nix-profile/bin/yt-dlp`)
- `bcrypt` — password hashing (npm package in api-server)
