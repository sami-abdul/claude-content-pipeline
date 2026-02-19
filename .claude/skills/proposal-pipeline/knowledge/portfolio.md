# Portfolio

Past work to reference in proposals. Lead with the single most relevant project.

---

## Polymarket Projects

### Market Making Bot (General)

Production-grade automated trading system providing liquidity on Polymarket prediction markets.

- **Tech**: Node.js, TypeScript, Ethers.js, SQLite, Express, React
- **Live**: https://mm.polymaxr.com
- Join best bid/ask with inventory-based price skewing
- Position limits and capital isolation per market
- 3-layer fill detection (API, on-chain, settlement lag)
- Graceful shutdown, pre-resolution exit, FORCED_EXIT for emergencies
- Real-time web dashboard with WebSocket monitoring

**Lead with this when:** Market making jobs, liquidity provision, any Polymarket bot work.

---

### Market Making Bot (Crypto 15 mins)

Auto-discovered 15-minute crypto market making engine.

- **Tech**: Node.js, TypeScript, Ethers.js, SQLite, Express, React
- **Live**: https://gabriel-odds-bot.polymaxr.com/
- Auto-discovers and trades 15-minute crypto markets
- Same risk management stack as general MM bot

**Lead with this when:** Short-duration crypto markets, auto-discovery requirements.

---

### Multi-Strategy Trading Bot

Four parallel strategies running independently with capital isolation.

- **Tech**: Node.js, TypeScript, Ethers.js, SQLite, Express, React
- **Live**: https://odds.polymaxr.com/
- Four strategies: Odds Bot, Scalping, Arbitrage, Apple Store
- Capital isolation with separate wallets per strategy
- WebSocket-first architecture with REST fallback
- Circuit breakers with automatic trading halts
- Stop-loss system with 500ms monitoring, bid sorting protection, GTC cancellation safeguards
- Telegram interface for live notifications and commands

**Lead with this when:** Multi-strategy systems, risk management, circuit breakers, capital isolation.

---

### Full-Stack Trading Platform

Production-grade platform for automated market-making on Polymarket.

- **Tech**: Node.js, Express, Next.js, React, TypeScript, PostgreSQL/SQLite, Wagmi, RainbowKit, PM2
- **Live**: https://app.polymaxr.com
- Multi-user bot management with health monitoring and auto-recovery
- Custodial wallet management with AES-256 encryption
- Gas automation and proxy contract deployment
- Polygon blockchain connectivity with wallet signature auth

**Lead with this when:** Full platform builds, multi-user trading systems, Web3 integration, wallet infrastructure.

---

## AI Agent Projects

### Sam (Upwork Job Hunter)

AI agent that automates freelance job discovery and proposal generation.

- **Tech**: OpenClaw, Node.js, TypeScript, Telegram, GCP Compute Engine, systemd
- Automated job scanning with configurable filters (rating, budget, keywords)
- Client quality scoring (A/B/C/D) based on hire rate, spend, reviews
- Tailored proposal generation with portfolio matching
- Persistent memory for job tracking and preferences
- 24/7 operation on GCP

**Lead with this when:** AI agent jobs, automation, job-matching systems, autonomous agents.

---

### Clawdia (WhatsApp Digital Twin)

AI agent that mirrors a user's communication style on WhatsApp.

- **Tech**: OpenClaw, Node.js, TypeScript, WhatsApp, GCP Compute Engine
- **Demo**: https://www.loom.com/share/fe23a90a19b14561a32810d9ccef9df7
- Personality mirroring and consistent tone across conversations
- Voice note handling and rich media support
- Persistent memory with relationship tracking
- WhatsApp native (group + direct messages)

**Lead with this when:** WhatsApp bots, digital twins, personality AI, conversational agents.

---

### Ava (Website Manager)

Autonomous agent managing a production landing page.

- **Tech**: OpenClaw, React 18, Vite 5, Express, Heroku, GCP Compute Engine, Telegram
- **Live**: https://appin60.com
- Health checks, deployments, portfolio sync, content updates
- Dual environment workflow (dev branch, approval gate, production merge)
- Telegram control interface

**Lead with this when:** Autonomous website management, deployment automation, self-healing systems.

---

### Finch (Twitter/X Co-Pilot)

AI ghostwriter for Twitter/X thought-leadership content.

- **Tech**: OpenClaw, Node.js, TypeScript, Twitter/X API, Telegram, GCP Compute Engine
- 240+ lines of anti-AI-slop voice rules
- Research, draft, approve workflow (never publishes without approval)
- Supports multiple content formats (How-To, Case Study, Myth-Busting)

**Lead with this when:** Twitter automation, content generation agents, social media bots.

---

### Kai (LinkedIn Co-Pilot)

AI ghostwriter for LinkedIn professional long-form content.

- **Tech**: OpenClaw, Node.js, TypeScript, LinkedIn API, Telegram, GCP Compute Engine
- LinkedIn-optimized format (punchy openers, bold-labeled takeaways)
- Shared anti-AI-slop voice engine with Finch
- Autonomous research and ready-to-review draft production

**Lead with this when:** LinkedIn automation, professional content agents.

---

### Muse (Article Writer)

Autonomous article writer and publisher for a prediction market website.

- **Tech**: OpenClaw, Node.js, TypeScript, Gemini 2.5 Flash, GitHub API, Telegram, GCP Compute Engine
- End-to-end pipeline: research, write (700-1200 words), generate hero image, approve, publish
- AI hero image generation with Gemini 2.5 Flash + Pollinations.ai fallback
- GitHub API publishing (no git clone required)

**Lead with this when:** Content automation, CMS integration, end-to-end publishing pipelines.

---

### Agentic Org (Multi-Agent Platform)

Multi-tenant SaaS dashboard for deploying, monitoring, and managing AI agents.

- **Tech**: Next.js 15, Supabase, GCP Compute Engine, GCP Secret Manager, Pub/Sub, Stripe, Turborepo
- Full agent lifecycle (deploy, monitor, restart, destroy)
- Multi-tenant with Row-Level Security and RBAC
- One-click deployment via 4-step wizard with template catalog
- BYOK credentials (Anthropic, OpenAI, Gemini) with model routing
- Stripe billing with per-org subscriptions and quota enforcement
- 30+ installable skills from curated catalog

**Lead with this when:** SaaS platforms, multi-tenant systems, agent orchestration, infrastructure management.
