# Playr

**AI-powered game generation platform — turn natural language prompts into playable HTML5 games.**

[Live App](https://playrapp.live)

---

## Demo

[![Playr Demo](https://img.youtube.com/vi/QfaNgn0oMiI/maxresdefault.jpg)](https://youtu.be/QfaNgn0oMiI)

*Click the image above to watch the full demo on YouTube.*

---

## What is Playr?

Playr transforms natural language descriptions into fully functional HTML5 games. Describe the game you want, and Playr's AI pipeline handles everything — game logic, assets, bundling — and delivers a playable game in seconds. Browse and play other users' creations through a TikTok-style infinite feed.

---

## How It Works

```
User Prompt
     |
[1] Template Detection (Claude Haiku)
     |  Classifies prompt into one of 10 game types
     |
[2] Game Spec Generation (Claude Sonnet)
     |  Generates full game parameters as structured JSON
     |
[3] Asset Generation (Gemini + Claude Haiku)
     |  Creates 6-12 sprites per game with optimized prompts
     |
[4] Config Mapping
     |  Converts game spec into engine-specific config values
     |
[5] HTML Bundling + Storage
     |  Packages game + assets into a playable bundle
     |  Content-addressable storage with SHA-256 deduplication
     |
[6] Delivered to Player
     ~$0.045 per game generated
```

---

## Key Technical Highlights

**Multi-Model LLM Pipeline**
- Three-model strategy: Claude Haiku (classification), Claude Sonnet (game spec), Claude Opus (custom games)
- Gemini for sprite generation with batch-optimized prompts
- Average cost of ~$0.045 per complete game generation

**13-Agent Parallel Template System**
- Built with Claude Opus for automated game template creation
- Three-wave execution: planner agent designs the full spec, 11 worker agents generate code in parallel, testing agent validates
- Supports 10 game types (dodge, flappy, runner, jumper, stacker, snake, tetris, breakout, quiz, custom)

**TikTok-Style Infinite Feed**
- Instantly playable user-generated games on mobile and web
- Real-time SSE streaming for generation progress
- Content-addressable storage with SHA-256 deduplication
- 85% client memory reduction through asset optimization

---

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React, TypeScript, Tailwind CSS, Vite |
| **Backend** | Node.js, Fastify, TypeScript |
| **Database** | PostgreSQL (Supabase), Redis |
| **Job Queue** | BullMQ |
| **AI/LLM** | Claude (Haiku/Sonnet/Opus), Gemini |
| **Auth** | Supabase Auth (Google OAuth, email/password) |
| **Storage** | Supabase Storage (content-addressable) |
| **Deployment** | Vercel (frontend), Railway (backend) |

---

## Architecture

```
┌─────────────────────────────────────────┐
│           React + Vite Frontend          │
│     Tailwind CSS, SSE client, Feed UI    │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│          Fastify API Server              │
│   Game generation, auth, feed, storage   │
└───┬──────────┬──────────┬───────────────┘
    │          │          │
┌───▼───┐ ┌───▼────┐ ┌───▼──────────────┐
│ LLM   │ │  Redis  │ │   PostgreSQL     │
│ APIs  │ │  Cache  │ │   (Supabase)     │
│Claude │ │+ BullMQ │ │   + Storage      │
│Gemini │ │         │ │                  │
└───────┘ └────────┘ └──────────────────┘
```

---

## Repository

This is the public overview repo. The source code is in a private repository.

---

## Contact

- **Email:** farhaanp9@gmail.com
- **LinkedIn:** [linkedin.com/in/fpishori](https://www.linkedin.com/in/farhaan-pishori-73939a201/)
- **GitHub:** [github.com/farhaanp9](https://github.com/Farhaanp9)
