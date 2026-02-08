# Awesome OpenClaw [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> The most comprehensive, curated collection of OpenClaw resources, hosting guides, cost comparisons, security hardening, skills, tutorials, and community links.

**OpenClaw** (formerly Clawdbot → Moltbot) is a free, open-source autonomous AI agent created by **Peter Steinberger** (@steipete). It runs on your own hardware, connects to messaging platforms (WhatsApp, Telegram, Slack, Discord, Signal, iMessage, Google Chat, Microsoft Teams), and orchestrates AI agent workflows with persistent memory and 24/7 operation.

[![GitHub Stars](https://img.shields.io/github/stars/openclaw/openclaw?style=flat&logo=github&label=Stars&color=gold)](https://github.com/openclaw/openclaw)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/openclaw/openclaw/blob/main/LICENSE)
[![Contributors](https://img.shields.io/github/contributors/openclaw/openclaw?label=Contributors&color=green)](https://github.com/openclaw/openclaw/graphs/contributors)

**176,000+ stars | 29,000+ forks | 500+ contributors | 8,817 commits | MIT License**

---

## Table of Contents

- [What is OpenClaw?](#what-is-openclaw)
- [Name History](#name-history)
- [Architecture](#architecture)
- [System Requirements](#system-requirements)
- [Quick Start (1 Minute)](#quick-start-1-minute)
- [Setup Methods (1-10 Minutes)](#setup-methods-1-10-minutes)
- [Hosting Providers Comparison](#hosting-providers-comparison)
  - [Free Tier ($0/month)](#free-tier-0month)
  - [Budget VPS ($2-8/month)](#budget-vps-2-8month)
  - [Mid-Range ($5-25/month)](#mid-range-5-25month)
  - [Serverless & PaaS](#serverless--paas)
  - [Managed Hosting (Setup for You)](#managed-hosting-setup-for-you)
  - [Local Hardware](#local-hardware)
- [Master Cost Comparison Table](#master-cost-comparison-table)
- [AI Model API Costs](#ai-model-api-costs)
- [Total Real-World Cost Examples](#total-real-world-cost-examples)
- [Cloudflare Workers (Moltworker) Deep Dive](#cloudflare-workers-moltworker-deep-dive)
- [DigitalOcean 1-Click Deploy](#digitalocean-1-click-deploy)
- [Hetzner Setup Guide](#hetzner-setup-guide)
- [Hostinger VPS Setup](#hostinger-vps-setup)
- [Oracle Cloud Free Tier Setup](#oracle-cloud-free-tier-setup)
- [Raspberry Pi Setup](#raspberry-pi-setup)
- [Docker Deployment](#docker-deployment)
- [Security & Hardening](#security--hardening)
  - [Known CVEs](#known-cves)
  - [Security Best Practices](#security-best-practices)
  - [Skills Marketplace Risks](#skills-marketplace-risks)
- [Configuration](#configuration)
  - [Model Providers](#model-providers)
  - [Messaging Channels](#messaging-channels)
  - [Local LLM Integration](#local-llm-integration)
  - [MCP Server Integration](#mcp-server-integration)
- [Performance Benchmarks](#performance-benchmarks)
- [OpenClaw vs Claude Code](#openclaw-vs-claude-code)
- [Alternatives & Competitors](#alternatives--competitors)
- [Moltbook (AI Social Network)](#moltbook-ai-social-network)
- [Skills & Plugins](#skills--plugins)
- [Browser Automation](#browser-automation)
- [Tutorials & Guides](#tutorials--guides)
- [Video Tutorials](#video-tutorials)
- [Community](#community)
- [Media Coverage](#media-coverage)
- [Common Issues & Troubleshooting](#common-issues--troubleshooting)
- [Cost Calculator & Optimization](#cost-calculator--optimization)
- [Key Contributors](#key-contributors)
- [Related Repositories](#related-repositories)

---

## What is OpenClaw?

OpenClaw is an **agentic AI interface** that:

- Runs **locally on your own hardware** (Mac Mini, VPS, Raspberry Pi, or serverless)
- Connects to **10+ messaging platforms** simultaneously
- Has **persistent memory** across sessions (saves files, breadcrumbs, chat histories)
- Handles **tasks spanning hours or days** without losing context
- Operates **24/7 autonomously** focusing on automation and integration
- Supports **5,700+ community-built skills** via ClawHub
- Works with **multiple AI providers** (Anthropic, OpenAI, Google, OpenRouter, DeepSeek, local LLMs)

### Core Architecture (6 Layers)

| Layer | Purpose |
|-------|---------|
| **Gateway** | Central control plane — message routing, sessions, plugins, tool execution policy |
| **Channels** | Adapters normalizing Telegram/WhatsApp/Discord/iMessage into standard message shapes |
| **Routing + Sessions** | Determines which agent handles specific conversations |
| **Agent Runtime** | Processes context, calls model providers, streams responses, requests tools |
| **Tools** | Capabilities — web fetch, browser control, command execution, device pairing |
| **Surfaces** | Interaction points — chat apps, web dashboard, macOS menu bar |

---

## Name History

| Date | Name | Reason |
|------|------|--------|
| Nov 2025 | **Clawdbot** | Original name at launch |
| Jan 27, 2026 | **Moltbot** | Anthropic trademark complaint (similarity to "Claude") |
| Jan 30, 2026 | **OpenClaw** | Final rebrand, community vote |

> When the team dropped the @clawdbot Twitter handle to transition to @moltbot, professional "handle snipers" immediately grabbed it. Scammers used the hijacked account to launch a fake CLAWD token on Solana.

---

## System Requirements

### Minimum

| Component | Requirement |
|-----------|-------------|
| **OS** | macOS 11+ / Ubuntu 22.04+ / Windows (WSL2) |
| **Runtime** | Node.js 22+ |
| **RAM** | 2 GB (may crash during onboarding) |
| **CPU** | 2 cores |
| **Storage** | 10 GB SSD |
| **Network** | Stable internet connection |

### Recommended

| Component | Requirement |
|-----------|-------------|
| **RAM** | 4-8 GB (cloud models) / 16-24 GB (local LLMs) |
| **CPU** | 2-4 cores |
| **Storage** | 30-50 GB SSD |
| **GPU** | 12-24 GB VRAM (for local model inference) |

---

## Quick Start (1 Minute)

```bash
# Install OpenClaw globally
npm install -g openclaw@latest

# Run the onboarding wizard
openclaw onboard --install-daemon

# Start the gateway
openclaw gateway --port 18789 --verbose
```

That's it. The wizard walks you through API key setup, channel configuration, and security settings.

---

## Setup Methods (1-10 Minutes)

| Method | Time | Difficulty | Best For |
|--------|------|------------|----------|
| **npm install** | 1 min | Easy | Developers with Node.js |
| **SimpleClaw** | 1 min | Easy | Non-technical users |
| **DigitalOcean 1-Click** | 2 min | Easy | Quick cloud deploy |
| **Railway Template** | 2 min | Easy | PaaS users |
| **Docker** | 5 min | Medium | Isolation & reproducibility |
| **Cloudflare Workers** | 5 min | Medium | Serverless enthusiasts |
| **Manual VPS** | 10 min | Medium | Full control |
| **Raspberry Pi** | 10 min | Medium | Low-power, always-on |

### Method 1: Official Installer Script

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
openclaw onboard --install-daemon
```

### Method 2: npm / pnpm

```bash
npm install -g openclaw@latest
# or
pnpm add -g openclaw@latest
```

### Method 3: Docker

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
./docker-setup.sh
```

### Method 4: One-Click Cloud Deploys

| Platform | Link | Notes |
|----------|------|-------|
| **DigitalOcean** | [1-Click Deploy](https://marketplace.digitalocean.com/apps/openclaw) | Security-hardened, pre-configured |
| **Railway** | [Template](https://railway.com/deploy/openclaw) | Web-based /setup wizard |
| **Render** | [render.yaml](https://docs.openclaw.ai/render) | Infrastructure as Code |
| **SimpleClaw** | [simpleclaw.com](https://www.simpleclaw.com/) | Deploy in under 1 minute |
| **Zeabur** | One-click template | Auto-scaling |

---

## Hosting Providers Comparison

### Free Tier ($0/month)

| Provider | Free Resources | Limits | Permanent? | Setup Time | Best For |
|----------|---------------|--------|------------|------------|----------|
| **Oracle Cloud** | 4 ARM CPUs, 24 GB RAM, 200 GB storage, 10 TB/mo transfer | ARM architecture only | Yes (forever) | ~3 hours | Power users wanting $0 hosting |
| **Google Cloud Run** | 180K vCPU-sec, 360K GiB-sec, 2M requests/mo | Cold starts, stateless | Yes | 30 min | Serverless testing |
| **Azure Container Apps** | 180K vCPU-sec, 360K GiB-sec, 2M requests/mo | Cold starts | Yes | 30 min | Enterprise users |
| **Render** | Web service (spins down after 15 min), 1 GB PostgreSQL | Slow wake-up (~60s) | Yes | 5 min | Testing only |
| **AWS Free Tier** | t2.micro (1 vCPU, 1 GB RAM) | 12 months only, 1 GB RAM | No (12 mo) | 15 min | AWS-familiar users |
| **Railway** | $5 one-time credit | 30 days trial | No | 2 min | Quick testing |

### Budget VPS ($2-8/month)

| Provider | Plan | Price/mo | vCPU | RAM | Storage | Bandwidth | Region |
|----------|------|----------|------|-----|---------|-----------|--------|
| **LumaDock** | Basic | $1.99 | 1 | 1 GB | 20 GB SSD | 1 TB | US/EU |
| **Vultr** | Regular Cloud | $2.50 | 1 | 512 MB | 10 GB | 0.5 TB | 32 locations |
| **Vultr** | Standard | $3.50 | 1 | 1 GB | 25 GB NVMe | 1 TB | 32 locations |
| **Hetzner** | CX22 | €3.79 (~$4.15) | 2 | 4 GB | 40 GB SSD | 20 TB | EU (DE/FI) |
| **Contabo** | Cloud VPS S | $4.95 | 4 | 8 GB | 50 GB SSD | Unlimited | US/EU/Asia |
| **Hostinger** | KVM 1 | $4.99 | 1 | 4 GB | 50 GB NVMe | 4 TB | Global |
| **Linode** | Shared 1GB | $5 | 1 | 1 GB | 25 GB | 1 TB | Global |
| **Vultr** | High-Performance | $6 | 1 | 1 GB | 25 GB NVMe | 2 TB | 32 locations |
| **DigitalOcean** | Basic Droplet | $6 | 1 | 1 GB | 25 GB | 1 TB | Global |
| **Hetzner** | CX32 | €6.80 (~$7.45) | 4 | 8 GB | 80 GB SSD | 20 TB | EU (DE/FI) |
| **Contabo** | Cloud VPS M | $7.95 | 4 | 8 GB | 200 GB SSD | Unlimited | US/EU/Asia |

### Mid-Range ($5-25/month)

| Provider | Plan | Price/mo | vCPU | RAM | Storage | Notes |
|----------|------|----------|------|-----|---------|-------|
| **DigitalOcean** | Premium Droplet | $7 | 1 | 1 GB | 25 GB NVMe | 1-Click Deploy available |
| **DigitalOcean** | Standard 2GB | $12 | 1 | 2 GB | 50 GB | Recommended for OpenClaw |
| **Hostinger** | KVM 2 | $6.99 | 2 | 8 GB | 100 GB NVMe | Best Hostinger value |
| **GCP** | e2-medium | ~$12 | 2 | 4 GB | 30 GB SSD | $300 free credit (90 days) |
| **Linode** | Dedicated 4GB | $36 | 2 (dedicated) | 4 GB | 40 GB | Consistent performance |
| **Azure** | B1ms VM | ~$15 | 1 | 2 GB | 32 GB | Enterprise compliance |

### Serverless & PaaS

| Platform | Starting Price | Free Tier? | Persistent Storage | WebSocket | Auto-Scale | Notes |
|----------|---------------|------------|-------------------|-----------|------------|-------|
| **Cloudflare Workers** | $5/mo (paid plan required) | 100K req/day (free) | R2 ($0.015/GB/mo) | Via Sandbox | Yes | Moltworker PoC |
| **Railway** | $5/mo (Hobby) | $5 credit trial | Yes (volumes) | Yes | Yes | Best PaaS UX |
| **Render** | $7/mo (web service) | Free w/ limits | Yes (disks) | Yes | Yes | YAML IaC |
| **Fly.io** | Pay-as-you-go | None (removed) | Yes (volumes) | Yes | Yes | Global edge |
| **AWS Lightsail** | $3.50/mo | None | Yes | Yes | No | Simple AWS VPS |

### Managed Hosting (Setup for You)

| Provider | Price/mo | Setup Time | Technical Skill | What's Included |
|----------|----------|------------|-----------------|-----------------|
| **Agent37.com** | $0.99 | 30 sec | None | Cheapest managed option |
| **SimpleClaw** | TBD | < 1 min | None | 1-click deploy, managed |
| **xCloud** | $24 | 5 min | None | Telegram/WhatsApp pre-configured, 7-day guarantee, support |
| **OpenClawd.ai** | TBD | Minutes | None | Fully managed, security built-in |

---

## Master Cost Comparison Table

| Provider | Monthly Cost | Setup Time | Difficulty | 1-Click? | Docker? | Best For |
|----------|-------------|------------|------------|----------|---------|----------|
| Oracle Cloud | **$0** | 3 hours | Hard | No | Yes | Free-forever hosting |
| Google Cloud Run | **$0** | 30 min | Medium | No | Yes | Serverless testing |
| LumaDock | **$1.99** | 15 min | Medium | No | Yes | Cheapest VPS |
| Vultr | **$2.50** | 10 min | Medium | Yes | Yes | Global presence |
| Hetzner CX22 | **$4.15** | 10 min | Medium | No | Yes | Best price/performance |
| Contabo VPS S | **$4.95** | 15 min | Medium | No | Yes | Unlimited bandwidth |
| Hostinger KVM 1 | **$4.99** | 10 min | Easy | Yes | Yes | Docker templates |
| Cloudflare Workers | **$5** | 5 min | Medium | No | No | Serverless |
| Railway Hobby | **$5** | 2 min | Easy | Yes | Yes | Best PaaS experience |
| Linode 1GB | **$5** | 10 min | Medium | No | Yes | Consistent performance |
| DigitalOcean | **$6** | 2 min | Easy | **Yes** | Yes | Best docs + 1-Click |
| Render | **$7** | 5 min | Easy | Yes | Yes | YAML Infrastructure |
| DigitalOcean 2GB | **$12** | 2 min | Easy | **Yes** | Yes | Recommended production |
| xCloud Managed | **$24** | 5 min | **None** | **Yes** | N/A | Non-technical users |
| Raspberry Pi 5 | **$0** (after $80 hw) | 30 min | Medium | No | Yes | Low-power, always-on |
| Mac Mini | **$0** (electricity) | 10 min | Easy | No | Optional | Privacy-first, local |

---

## AI Model API Costs

The **real cost** of running OpenClaw is the AI model API, not infrastructure.

### Provider Pricing (per 1M tokens)

| Provider | Model | Input Cost | Output Cost | Notes |
|----------|-------|-----------|-------------|-------|
| **Anthropic** | Claude 3.5 Haiku | $0.80 | $4.00 | Best budget option |
| **Anthropic** | Claude 3.5 Sonnet | $3.00 | $15.00 | Best balance |
| **Anthropic** | Claude Opus 4.5 | $15.00 | $75.00 | Most capable, expensive |
| **OpenAI** | GPT-4o | $2.50 | $10.00 | Good alternative |
| **OpenAI** | GPT-4o-mini | $0.15 | $0.60 | Very cheap |
| **Google** | Gemini 2.0 Flash | $0.10 | $0.40 | Cheapest hosted |
| **Google** | Gemini Flash-Lite | **Free tier** | **Free tier** | Zero cost option |
| **DeepSeek** | DeepSeek V3 | $0.27 | $1.10 | Best value reasoning |
| **Moonshot** | Kimi K2.5 | $3.00 | $3.00 | Great agentic performance |
| **OpenRouter** | Various | Varies | Varies | Unified API for 200+ models |
| **Ollama/Local** | Any | **$0** | **$0** | Requires hardware (16 GB+ RAM) |

### Monthly API Cost Estimates

| Usage Level | Description | Monthly Cost |
|-------------|-------------|-------------|
| **Minimal** | Few messages/day, Gemini free tier | $0-5 |
| **Light** | ~50 messages/day, Claude Haiku | $5-15 |
| **Moderate** | ~200 messages/day, mixed models | $15-50 |
| **Heavy** | 500+ messages/day, Claude Sonnet | $50-150 |
| **Power User** | All-day usage, Claude Opus | $150-500+ |

### Cost Optimization Tips

1. Use **smart model routing** — cheap models (Haiku/Flash) for simple tasks, expensive (Sonnet/Opus) for complex
2. Enable **prompt caching** — Anthropic auto-applies 5-min cache, reducing repeat costs
3. Use **local LLMs** via Ollama for zero API cost (requires 16 GB+ RAM)
4. Set **budget alerts** in your AI provider dashboard
5. Use [OpenClaw Cost Calculator](https://calculator.vlvt.sh/) to estimate your spend

---

## Total Real-World Cost Examples

| Setup | Infrastructure | API | Total/month | Notes |
|-------|---------------|-----|-------------|-------|
| **Free Tier Max** | Oracle Cloud ($0) | Gemini free ($0) | **$0** | Limited but functional |
| **Ultra Budget** | LumaDock ($2) | Haiku ($5) | **$7** | Basic personal assistant |
| **Sweet Spot** | Hetzner CX22 ($4) | Mixed models ($15) | **$19** | Best value-to-capability |
| **Standard** | DigitalOcean ($12) | Sonnet ($40) | **$52** | Production-ready |
| **Managed Easy** | xCloud ($24) | Mixed ($30) | **$54** | Zero technical setup |
| **Cloudflare Serverless** | Workers ($5+$30) | Mixed ($20) | **$55** | Serverless architecture |
| **Local LLM** | Raspberry Pi 5 ($0/mo) | Ollama ($0) | **$0** | After $80 hardware purchase |
| **Power User** | DigitalOcean ($24) | Opus ($200) | **$224** | Heavy professional use |
| **Extreme** | Dedicated ($50) | All models ($573) | **$623** | One developer's real report |

---

## Cloudflare Workers (Moltworker) Deep Dive

[Moltworker](https://github.com/cloudflare/moltworker) is Cloudflare's official adaptation of OpenClaw for Workers.

### Architecture

- **Container**: Sandbox (standard-1: 1/2 vCPU, 4 GiB RAM, 8 GB disk)
- **Storage**: R2 for persistence (auto-sync every 5 minutes)
- **Auth**: Cloudflare Access (Zero Trust) + gateway token + device pairing
- **Status**: Proof-of-concept (not an official Cloudflare product)

### Setup

```bash
git clone https://github.com/cloudflare/moltworker.git
cd moltworker
npm install

npx wrangler secret put ANTHROPIC_API_KEY
export MOLTBOT_GATEWAY_TOKEN=$(openssl rand -hex 32)
npx wrangler secret put MOLTBOT_GATEWAY_TOKEN

npm run deploy
```

Access: `https://your-worker.workers.dev/?token=YOUR_GATEWAY_TOKEN`

### Cost Breakdown (24/7 Operation)

| Component | Monthly Cost |
|-----------|-------------|
| Workers Paid Plan | $5.00 |
| Memory (~4 GiB) | ~$26.00 |
| CPU | ~$2.00 |
| Disk (8 GB) | ~$1.50 |
| **Total** | **~$34.50** |

> Set `SANDBOX_SLEEP_AFTER=10m` for infrequent use to reduce costs significantly.

### Limitations

- **Cannot support Telegram bots** (requires persistent connection for long-polling)
- Containers hibernate when not receiving HTTP requests
- Webhook mode fails due to auth middleware blocking Telegram callbacks
- Use VPS deployment for Telegram integration

### Resources

- [GitHub - cloudflare/moltworker](https://github.com/cloudflare/moltworker)
- [Blog - Introducing Moltworker](https://blog.cloudflare.com/moltworker-self-hosted-ai-agent/)
- [Guide - Deploy OpenClaw on Cloudflare](https://rohitai.com/blog/openclaw-cloudflare-workers-moltworker-guide)

---

## DigitalOcean 1-Click Deploy

The fastest path to a production OpenClaw instance.

### Steps

1. Go to [DigitalOcean Marketplace](https://marketplace.digitalocean.com/apps/openclaw)
2. Click "Create OpenClaw Droplet"
3. Choose $12/mo plan (2 GB RAM recommended)
4. Select region, SSH key
5. Deploy (ready in ~90 seconds)

### What's Pre-configured

- OpenClaw 2026.1.24-1 pre-installed
- Docker container isolation
- Unique gateway token per deployment
- Security-hardened out of the box
- Automatic HTTPS via Caddy

### Post-Deploy

```bash
ssh root@your-droplet-ip
openclaw onboard
```

### Resources

- [DigitalOcean Blog - Introducing OpenClaw](https://www.digitalocean.com/blog/moltbot-on-digitalocean)
- [Technical Deep Dive - Security Hardening](https://www.digitalocean.com/blog/technical-dive-openclaw-hardened-1-click-app)
- [Tutorial - How to Run OpenClaw](https://www.digitalocean.com/community/tutorials/how-to-run-openclaw)

---

## Hetzner Setup Guide

Best price-to-performance ratio for OpenClaw hosting.

### Recommended Plans

| Plan | Price/mo | vCPU | RAM | Storage | Bandwidth |
|------|----------|------|-----|---------|-----------|
| **CX22** | €3.79 | 2 | 4 GB | 40 GB SSD | 20 TB |
| **CX32** | €6.80 | 4 | 8 GB | 80 GB SSD | 20 TB |
| **CAX11 (ARM)** | €3.79 | 2 | 4 GB | 40 GB | 20 TB |

### Quick Setup

```bash
# SSH into your Hetzner server
ssh root@your-server-ip

# Install Node.js 22
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt-get install -y nodejs

# Install OpenClaw
npm install -g openclaw@latest
openclaw onboard --install-daemon

# Configure firewall
ufw allow ssh
ufw allow 443/tcp
ufw enable
```

### Resources

- [Hetzner - OpenClaw Docs](https://docs.openclaw.ai/platforms/hetzner)
- [Deploy OpenClaw on Hetzner with Pulumi + Tailscale](https://www.pulumi.com/blog/deploy-openclaw-aws-hetzner/)

---

## Hostinger VPS Setup

### Plans

| Plan | Price/mo | vCPU | RAM | Storage | Bandwidth |
|------|----------|------|-----|---------|-----------|
| **KVM 1** | $4.99 | 1 | 4 GB | 50 GB NVMe | 4 TB |
| **KVM 2** | $6.99 | 2 | 8 GB | 100 GB NVMe | 8 TB |
| **KVM 4** | $10.99 | 4 | 16 GB | 200 GB NVMe | 16 TB |

> Renewal prices are ~2x. Lock in annual pricing.

### Setup

1. Order VPS from [Hostinger](https://www.hostinger.com/vps-hosting)
2. Choose Ubuntu 22.04 with Docker template
3. SSH in and run:

```bash
npm install -g openclaw@latest
openclaw onboard --install-daemon
```

### Resources

- [How to Install OpenClaw on Hostinger VPS](https://www.hostinger.com/support/how-to-install-openclaw-on-hostinger-vps/)
- [How to Secure OpenClaw on Hostinger](https://www.hostinger.com/support/how-to-secure-and-harden-openclaw-security/)

---

## Oracle Cloud Free Tier Setup

**Truly free forever** — no trials, no expiration, no credit card charges.

### Free Resources

- 4 ARM Ampere A1 cores
- 24 GB RAM
- 200 GB block storage
- 10 TB/month outbound transfer

### Setup Steps

1. Create [Oracle Cloud Account](https://www.oracle.com/cloud/free/)
2. Create ARM compute instance (Ampere A1.Flex, 4 OCPU, 24 GB RAM)
3. SSH in:

```bash
# Install Node.js 22
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt-get install -y nodejs git

# Install OpenClaw
npm install -g openclaw@latest
openclaw onboard --install-daemon

# Firewall
sudo iptables -I INPUT -p tcp --dport 18789 -j ACCEPT
```

### Caveats

- ARM architecture — some binaries may need x86 emulation
- High demand — instance provisioning can fail during peak hours (keep retrying)
- Accounts may be terminated without warning if not upgraded to Pay-As-You-Go (add a credit card for safety — you won't be charged)

### Resources

- [Oracle Cloud - OpenClaw Docs](https://docs.openclaw.ai/platforms/oracle)
- [Openclaw on Oracle's Free Tier: Always-On AI for $0/month](https://ryanshook.org/blog/posts/openclaw-on-oracle-free-tier-always-on-ai-for-free/)
- [Self-Host OpenClaw on a Free VPS](https://cognio.so/clawdbot/self-hosting)

---

## Raspberry Pi Setup

Low-power, always-on home server for OpenClaw.

### Recommended Hardware

| Device | Price | RAM | Performance | Verdict |
|--------|-------|-----|-------------|---------|
| **Pi 5 (8 GB)** | $80 | 8 GB | Fast | Best choice |
| **Pi 5 (4 GB)** | $60 | 4 GB | Fast | Good budget option |
| **Pi 4 (8 GB)** | $55 | 8 GB | 2-2.5x slower than Pi 5 | Viable |
| **Pi 4 (4 GB)** | $35 | 4 GB | 2-2.5x slower | Minimum viable |

### Setup

```bash
# Install Node.js 22 on Raspberry Pi OS (64-bit required)
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo bash -
sudo apt-get install -y nodejs

# Install OpenClaw
npm install -g openclaw@latest
openclaw onboard --install-daemon
```

### Resources

- [OpenClaw on Raspberry Pi - ajfisher](https://ajfisher.me/2026/02/03/openclaw-raspberrypi-howto/)
- [OpenClaw on Raspberry Pi - Adafruit](https://learn.adafruit.com/openclaw-on-raspberry-pi)
- [OpenClaw Raspberry Pi Setup Guide](https://zenvanriel.nl/ai-engineer-blog/openclaw-raspberry-pi-setup-hardware-guide/)

---

## Docker Deployment

Docker is the recommended deployment method for VPS hosting.

### Quick Start

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
./docker-setup.sh
```

### Manual Docker Compose

```yaml
version: '3.8'
services:
  openclaw:
    image: openclaw/openclaw:latest
    ports:
      - "127.0.0.1:18789:18789"
    volumes:
      - ~/.openclaw:/root/.openclaw
      - ~/openclaw/workspace:/root/openclaw/workspace
    restart: unless-stopped
    environment:
      - ANTHROPIC_API_KEY=${ANTHROPIC_API_KEY}
```

### Useful Commands

```bash
# Approve Telegram pairing
docker compose run --rm openclaw-cli pairing approve telegram <CODE>

# Get dashboard URL
docker compose run --rm openclaw-cli dashboard --no-open

# Run security audit
docker compose run --rm openclaw-cli security audit --deep
```

### Resources

- [Docker - OpenClaw Docs](https://docs.openclaw.ai/install/docker)
- [Running OpenClaw in Docker - Simon Willison](https://til.simonwillison.net/llms/openclaw-docker)
- [Run OpenClaw Safely with Docker - Medium](https://medium.com/@ozbillwang/run-openclaw-moltbot-clawdbot-safely-with-docker-a-practical-guide-for-beginners-94112a9b57be)

---

## Security & Hardening

### Known CVEs

| CVE | Severity | Description | Fixed In |
|-----|----------|-------------|----------|
| **CVE-2026-24763** | High | Docker PATH Command Injection | v2026.1.29 |
| **GHSA-g8p2-7wf7-98mq** | Critical (8.8) | gatewayUrl Token Exfiltration (1-click RCE) | v2026.1.29 |
| **GHSA-q284-4pvr-m585** | High | sshNodeCommand Injection | v2026.1.29 |
| **CVE-2026-25593** | Critical | Unauthenticated Local RCE via WebSocket config.apply | v2026.1.30 |
| **CVE-2026-25475** | High | Local File Inclusion via MEDIA: Path Extraction | v2026.1.30 |

> **Update immediately to v2026.1.30+** to patch all known vulnerabilities.

### Security Best Practices

1. **Network Binding**
   - Bind to `127.0.0.1` only (never `0.0.0.0`)
   - Use SSH tunnels or [Tailscale Serve](https://tailscale.com/kb/1242/tailscale-serve) for remote access
   - Never expose port 18789 directly to the internet

2. **API Key Management**
   - Use auth profiles (system keychain): `openclaw auth set ANTHROPIC_API_KEY`
   - Never commit keys to Git
   - Rotate keys regularly

3. **Firewall Configuration**
   ```bash
   ufw default deny incoming
   ufw default allow outgoing
   ufw allow ssh
   ufw allow 443/tcp
   ufw enable
   ```

4. **Sandboxing**
   - Use Docker deployment for container isolation
   - Configure tool execution policies
   - Limit agent self-modification privileges

5. **Regular Audits**
   ```bash
   openclaw security audit          # Read-only scan (50+ checks)
   openclaw security audit --deep   # Adds live WebSocket probe
   openclaw security audit --fix    # Auto-fix safe issues
   openclaw doctor                  # Identify risky configurations
   ```

6. **Updates**
   - Monitor [GitHub releases](https://github.com/openclaw/openclaw/releases) for patches
   - Subscribe to security advisories
   - Auto-update with `npm update -g openclaw`

### Skills Marketplace Risks

> **~15% of community skills contain malicious instructions** (per security researchers)

- **341 malicious skills discovered** (12% of audited packages) in "ClawHavoc" campaign
- **280+ skills leak API keys and PII** ([Snyk research](https://snyk.io/blog/openclaw-skills-credential-leaks-research/))
- Some skills execute `curl` commands to exfiltrate data to external servers
- **Bitdefender Labs** found "hidden payloads" in community skills

**Mitigations:**
- Audit every skill before installation
- Use VirusTotal-verified skills only
- Check for data exfiltration commands (outbound HTTP calls)
- Use the built-in skill scanner: `src/security/skill-scanner.ts`

### Security Resources

- [OpenClaw Setup Guide - Don't Launch Before Reading This (Habr)](https://habr.com/en/articles/891538/)
- [Personal AI Agents like OpenClaw Are a Security Nightmare (Cisco)](https://blogs.cisco.com/ai/personal-ai-agents-like-openclaw-are-a-security-nightmare)
- [Bitdefender - OpenClaw Malicious Skill Trap](https://www.bitdefender.com/en-us/blog/labs/helpful-skills-or-hidden-payloads-bitdefender-labs-dives-deep-into-the-openclaw-malicious-skill-trap)
- [Snyk - 280+ Leaky Skills](https://snyk.io/blog/openclaw-skills-credential-leaks-research/)
- [The Register - OpenClaw Security Issues](https://www.theregister.com/2026/02/02/openclaw_security_issues/)
- [centminmod/explain-openclaw - Deep Security Analysis](https://github.com/centminmod/explain-openclaw)

---

## Configuration

### Model Providers

OpenClaw supports multiple AI providers configured in `~/.openclaw/openclaw.json`:

| Provider | Config Key | Free Tier? | Notes |
|----------|-----------|------------|-------|
| **Anthropic** | `ANTHROPIC_API_KEY` | No | Primary, best quality |
| **OpenAI** | `OPENAI_API_KEY` | No | GPT-4, GPT-4o |
| **Google** | `GOOGLE_API_KEY` | Yes (Gemini Flash-Lite) | Cheapest hosted option |
| **OpenRouter** | `OPENROUTER_API_KEY` | No | 200+ models via unified API |
| **DeepSeek** | `DEEPSEEK_API_KEY` | No | Excellent value |
| **Moonshot** | `MOONSHOT_API_KEY` | No | Kimi K2.5 (great agentic) |
| **MiniMax** | `MINIMAX_API_KEY` | No | M2.1 native support |
| **Fireworks AI** | Built-in | No | Model hosting |
| **Workers AI** | Built-in | Yes (limits) | Cloudflare models |
| **Ollama** | Local | **Free** | Requires local hardware |
| **LM Studio** | Local | **Free** | Requires local hardware |

### Messaging Channels

| Channel | Setup Complexity | Auth Method | Notes |
|---------|-----------------|-------------|-------|
| **Telegram** | Easy (2 min) | BotFather token | Fastest setup |
| **WhatsApp** | Easy (2 min) | QR code scan | Scan from terminal |
| **Discord** | Medium (5 min) | Bot application | Requires developer portal |
| **Slack** | Medium (5 min) | Bot token scopes | api.slack.com/apps |
| **Signal** | Medium (5 min) | Direct integration | Privacy-focused |
| **iMessage** | Hard (10 min) | BlueBubbles bridge | macOS only |
| **Microsoft Teams** | Medium (5 min) | Enterprise integration | Business users |
| **Google Chat** | Medium (5 min) | Workspace integration | Google Workspace |
| **Matrix** | Medium (5 min) | E2E encryption | Best for privacy |

### Local LLM Integration

#### Ollama (Recommended)

```bash
# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Pull a model
ollama pull llama3.1

# Configure OpenClaw
# In ~/.openclaw/openclaw.json:
{
  "provider": "openai",
  "baseUrl": "http://localhost:11434/v1",
  "model": "llama3.1"
}
```

#### LM Studio

```json
{
  "provider": "openai",
  "baseUrl": "http://localhost:1234/v1",
  "model": "your-model-name"
}
```

### MCP Server Integration

OpenClaw supports Model Context Protocol (MCP) servers for extended capabilities.

**Plugins:**

| Plugin | Source | Features |
|--------|--------|----------|
| **openclaw-mcp-plugin** | [GitHub](https://github.com/lunarpulse/openclaw-mcp-plugin) | HTTP/SSE transport, multi-server, unified interface |
| **openclaw-mcp-adapter** | [npm](https://www.npmjs.com/package/openclaw-mcp-adapter) | Registers MCP tools as native agent tools |

---

## Performance Benchmarks

### Inference Speed (by Hardware)

| Hardware | Tokens/sec | Notes |
|----------|-----------|-------|
| **RTX 4090** | ~80 t/s | Best GPU performance |
| **MacBook Air M2** | ~3.2 t/s | CPU-only, usable |
| **Typical CPU** | ~13.5 t/s | Non-time-critical tasks |
| **Oracle ARM (7B)** | 5-10 t/s | Free tier, acceptable |
| **Raspberry Pi 5** | 2-5 t/s | Slow but works |
| **CPU/RAM offload** | 0.5-2 t/s | Painfully slow |

### Memory Requirements for Local Models

| Model Size | RAM Required | GPU VRAM |
|------------|-------------|----------|
| 3B (quantized) | 4 GB | 4 GB |
| 7B (quantized) | 8 GB | 8 GB |
| 13B (quantized) | 16 GB | 12-16 GB |
| 34B (quantized) | 32 GB | 24 GB |
| 70B (quantized) | 64 GB | 48 GB+ |

### Bottleneck

Memory bandwidth and VRAM capacity are the primary bottlenecks for local inference, not CPU speed.

---

## OpenClaw vs Claude Code

OpenClaw and Claude Code are **complementary tools**, not competitors.

| Feature | Claude Code | OpenClaw |
|---------|------------|----------|
| **Lives in** | Terminal / IDE | Messaging apps |
| **Focus** | Coding, development | Automation, integration |
| **Memory** | Session-based | Persistent (24/7) |
| **Operation** | Interactive | Autonomous |
| **Context** | Files in working directory | Long-term memory + daily notes |
| **Runtime** | Per-session | Always-on daemon |
| **Integration** | Git, tests, dev tools | Email, calendar, messaging, home automation |
| **Best for** | Multi-file refactoring, test creation | Inbox monitoring, reminders, web scraping |
| **Price** | Pay-per-use API | Infrastructure + API |

### Common Setup: Run Both

Many engineers run both simultaneously:
- **Claude Code** for focused coding sessions in the terminal
- **OpenClaw** for everything else (WhatsApp reminders, monitoring, device control)

---

## Alternatives & Competitors

| Alternative | Type | Size | Best For | Key Advantage |
|-------------|------|------|----------|---------------|
| **Nanobot** | Lightweight | 4,000 lines (99% smaller) | Minimalists | Entire codebase understandable in days |
| **NanoClaw** | Security-first | Small | Security-conscious | AI runs in isolated containers |
| **memU** | Memory-focused | Small | Budget users | Local knowledge graph, cheaper |
| **Jan.ai** | Offline chat | Medium | Privacy absolutists | 100% offline operation |
| **AnythingLLM** | Doc-to-chatbot | Medium | Knowledge bases | Turn PDFs/code into interactive chatbots |
| **Claude Code** | Coding agent | N/A | Developers | Best-in-class coding assistant |
| **Microsoft Copilot** | Enterprise AI | N/A | Enterprise | Compliance, security |
| **eesel AI** | Business agent | N/A | Help desks | Customer service automation |
| **Emergent** | Personal AI | N/A | WhatsApp/Telegram | Delivers core OpenClaw promise simply |

---

## Moltbook (AI Social Network)

Created by OpenClaw agent "Clawd Clawderberg" (built by Matt Schlicht, Cofounder of Octane AI).

| Stat | Value |
|------|-------|
| **Launched** | January 28, 2026 |
| **Registered AI agents** | 1.6M+ |
| **Posts & responses** | 7.5M+ AI-generated |
| **Format** | Reddit-style forum for AI agents |
| **Human access** | Read-only observation |

AI agents generate posts, comment, argue, joke, and upvote each other. Posting is restricted to verified AI agents (primarily OpenClaw instances). Human users can only observe.

> *"Most interesting place on the internet right now"* — Fortune

### Coverage

- [TechCrunch - OpenClaw's AI assistants are now building their own social network](https://techcrunch.com/2026/01/30/openclaws-ai-assistants-are-now-building-their-own-social-network/)
- [Fortune - Moltbook, where AI agents hang together](https://fortune.com/2026/01/31/ai-agent-moltbot-clawdbot-openclaw-data-privacy-security-nightmare-moltbook-social-network/)
- [CNBC - From Clawdbot to Moltbot to OpenClaw](https://www.cnbc.com/2026/02/02/openclaw-open-source-ai-agent-rise-controversy-clawdbot-moltbot-moltbook.html)

---

## Skills & Plugins

### ClawHub (Official Registry)

- **URL**: [clawhub.ai](https://clawhub.ai/)
- **Skills**: 5,705 community-built (as of Feb 2026)
- **GitHub**: [openclaw/clawhub](https://github.com/openclaw/clawhub)

### Awesome OpenClaw Skills

- **URL**: [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills)
- **Skills**: 3,009 curated
- **Quality**: Verified and tested

### Install a Skill

```bash
openclaw skill install <skill-name>
```

### Security Warning

Always audit skills before installation. ~15% contain malicious instructions. See [Security & Hardening](#skills-marketplace-risks).

---

## Browser Automation

OpenClaw supports three browser control modes:

| Mode | Description | Use Case |
|------|-------------|----------|
| **Extension Relay** | Control existing Chrome tabs with logged-in sessions | Personal browsing automation |
| **OpenClaw-managed** | Isolated automation in dedicated browser instance | Web scraping, testing |
| **Remote CDP** | Distributed cloud deployments | Scale at cloud level |

### Capabilities

- Chrome DevTools Protocol (CDP) support
- Element interaction via AI or ARIA snapshots
- Screenshots (full page or element)
- Tab management (list/open/focus/close)
- Act commands (click/type/drag/select)
- PDF exports
- Video recording

### Resources

- [Browser - OpenClaw Docs](https://docs.openclaw.ai/tools/browser)
- [Mastering OpenClaw Browser Capabilities](https://help.apiyi.com/en/openclaw-browser-automation-guide-en.html)
- [OpenClaw Browser Relay Guide 2026](https://rohitai.com/blog/openclaw-browser-relay-guide)

---

## Tutorials & Guides

### Getting Started

- [Official Getting Started](https://docs.openclaw.ai/start/getting-started) - OpenClaw Docs
- [OpenClaw Tutorial: Installation to First Chat](https://www.codecademy.com/article/open-claw-tutorial-installation-to-first-chat-setup) - Codecademy (20 min)
- [OpenClaw Full Tutorial for Beginners](https://www.freecodecamp.org/news/openclaw-full-tutorial-for-beginners/) - freeCodeCamp
- [Master OpenClaw in 30 Minutes](https://creatoreconomy.so/p/master-openclaw-in-30-minutes-full-tutorial) - Creator Economy
- [Stop Watching Install Tutorials — How to Actually Tame It](https://medium.com/activated-thinker/stop-watching-openclaw-install-tutorials-this-is-how-you-actually-tame-it-f3416f5d80bc) - Medium

### Cloud Provider Guides

- [How to Run OpenClaw with DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-run-openclaw) - Official
- [How to Set Up OpenClaw on AWS](https://dev.to/brayanarrieta/how-to-set-up-openclaw-ai-on-aws-3a0j) - DEV Community
- [Deploy on AWS/Hetzner with Pulumi + Tailscale](https://www.pulumi.com/blog/deploy-openclaw-aws-hetzner/) - Pulumi Blog
- [OpenClaw on Google Cloud Platform](https://rizwantheanalyst.com/2026/02/04/openclaw-on-google/) - Complete Guide
- [Deploying OpenClaw on Azure Windows 11 VM](https://techcommunity.microsoft.com/blog/azuredevcommunityblog/complete-guide-to-deploying-openclaw-on-azure-windows-11-virtual-machine/4492001) - Microsoft
- [Openclaw on Oracle's Free Tier](https://ryanshook.org/blog/posts/openclaw-on-oracle-free-tier-always-on-ai-for-free/) - Ryan Shook
- [How to set up OpenClaw on Hostinger](https://www.hostinger.com/tutorials/how-to-set-up-openclaw) - Hostinger

### Serverless & Docker

- [Introducing Moltworker](https://blog.cloudflare.com/moltworker-self-hosted-ai-agent/) - Cloudflare Blog
- [Running OpenClaw in Docker](https://til.simonwillison.net/llms/openclaw-docker) - Simon Willison
- [Run OpenClaw Safely with Docker](https://medium.com/@ozbillwang/run-openclaw-moltbot-clawdbot-safely-with-docker-a-practical-guide-for-beginners-94112a9b57be) - Medium

### Local Hardware

- [No Mac Mini, no worries: running OpenClaw on a Raspberry Pi](https://ajfisher.me/2026/02/03/openclaw-raspberrypi-howto/) - ajfisher
- [OpenClaw on Raspberry Pi](https://learn.adafruit.com/openclaw-on-raspberry-pi) - Adafruit
- [OpenClaw + Ollama Setup Guide](https://codersera.com/blog/openclaw-ollama-setup-guide-2026/) - Codersera
- [OpenClaw + LM Studio Setup Guide](https://codersera.com/blog/openclaw-lm-studio-setup-guide-2026/) - Codersera

### Security Guides

- [Deploy OpenClaw Securely on Cloudflare](https://medium.com/@williamogou/deploy-openclaw-securely-on-cloudflare) - William OGOU
- [How to Install and Secure OpenClaw](https://proflead.com/blog/openclaw-install-secure/) - Proflead
- [OpenClaw Complete Guide 2026: Security & Cost Control](https://www.moltbook-ai.com/blog/openclaw-guide-2026) - Moltbook-AI

### Deep Dives

- [OpenClaw vs Claude Code: Agent Architecture Deep Dive](https://claude-world.com/articles/openclaw-vs-claude-code/) - ClaudeWorld
- [OpenClaw Memory Architecture Explained](https://medium.com/@shivam.agarwal.in/agentic-ai-openclaw-moltbot-clawdbots-memory-architecture-explained-61c3b9697488) - Medium
- [Deep Dive: How OpenClaw's Memory System Works](https://snowan.gitbook.io/study-notes/ai-blogs/openclaw-memory-system-deep-dive) - GitBook
- [centminmod/explain-openclaw](https://github.com/centminmod/explain-openclaw) - Multi-AI security analysis (73 files)

---

## Video Tutorials

| Title | Platform | Duration | Topics |
|-------|----------|----------|--------|
| **OpenClaw Full Tutorial for Beginners** | freeCodeCamp (YouTube) | Long | Installation, models, memory, Docker, skills |
| **Master OpenClaw in 30 Minutes** | Creator Economy (YouTube) | 30 min | Safe setup, 5 real use cases, memory |
| **How OpenClaw's Creator Uses AI** | Creator Economy | 1 hour | Full demo with Peter Steinberger |
| **OpenClaw Google Workspace Setup** | YouTube | Medium | Gmail, Calendar, Drive integration |

---

## Community

| Platform | URL | Members | Best For |
|----------|-----|---------|----------|
| **Discord** | [OpenClaw Discord](https://docs.openclaw.ai/channels/discord) | 8,000+ active | Quick questions, troubleshooting |
| **Discourse (CoClaw)** | [coclaw.com](https://coclaw.com/) | 15,000+ registered | Long-form discussion, bug reports |
| **X/Twitter Community** | [OpenClaw Community](https://x.com/i/communities/2013441068562325602) | 12,200+ | News, updates, demos |
| **GitHub Issues** | [openclaw/openclaw/issues](https://github.com/openclaw/openclaw/issues) | N/A | Bug reports, feature requests |
| **GitHub Discussions** | [openclaw/openclaw/discussions](https://github.com/openclaw/openclaw/discussions) | N/A | Q&A, show-and-tell |
| **Hacker News** | [Search OpenClaw](https://hn.algolia.com/?q=openclaw) | N/A | Technical discussion |
| **Reddit** | Various subreddits | N/A | User experiences |

---

## Media Coverage

### Mainstream Media

- [CNBC - From Clawdbot to Moltbot to OpenClaw](https://www.cnbc.com/2026/02/02/openclaw-open-source-ai-agent-rise-controversy-clawdbot-moltbot-moltbook.html) (Feb 2, 2026)
- [TechCrunch - OpenClaw's AI assistants are now building their own social network](https://techcrunch.com/2026/01/30/openclaws-ai-assistants-are-now-building-their-own-social-network/)
- [Fortune - Moltbook may be 'the most interesting place on the internet right now'](https://fortune.com/2026/01/31/ai-agent-moltbot-clawdbot-openclaw-data-privacy-security-nightmare-moltbook-social-network/)
- [VentureBeat - What the OpenClaw moment means for enterprises](https://venturebeat.com/technology/what-the-openclaw-moment-means-for-enterprises-5-big-takeaways)

### Security Coverage

- [The Register - OpenClaw ecosystem still suffering severe security issues](https://www.theregister.com/2026/02/02/openclaw_security_issues/) (Feb 2, 2026)
- [The Register - OpenClaw skills marketplace leaky security](https://www.theregister.com/2026/02/05/openclaw_skills_marketplace_leaky_security/) (Feb 5, 2026)
- [The Hacker News - OpenClaw Bug Enables One-Click RCE](https://thehackernews.com/2026/02/openclaw-bug-enables-one-click-remote.html)
- [Cisco Blogs - Personal AI Agents Are a Security Nightmare](https://blogs.cisco.com/ai/personal-ai-agents-like-openclaw-are-a-security-nightmare)
- [Bitdefender Labs - OpenClaw Malicious Skill Trap](https://www.bitdefender.com/en-us/blog/labs/helpful-skills-or-hidden-payloads-bitdefender-labs-dives-deep-into-the-openclaw-malicious-skill-trap)
- [Snyk - 280+ Leaky Skills](https://snyk.io/blog/openclaw-skills-credential-leaks-research/)
- [Dark Reading - OpenClaw's Gregarious Insecurities](https://www.darkreading.com/cloud-security/openclaw-gregarious-insecurities-safe-usage)

### Opinion & Analysis

- [XDA Developers - Please stop using OpenClaw](https://www.xda-developers.com/please-stop-using-openclaw/)
- [Nature - OpenClaw AI chatbots are running amok](https://www.nature.com/articles/d41586-026-00439-0)
- [Pragmatic Engineer - The creator of Clawd: "I ship code I don't read"](https://newsletter.pragmaticengineer.com/p/the-creator-of-clawd-i-ship-code)

---

## Common Issues & Troubleshooting

| Issue | Cause | Fix |
|-------|-------|-----|
| Crash during onboarding | < 2 GB RAM | Upgrade to 4 GB+ RAM |
| API key not working | Incorrect format or expired | Re-enter via `openclaw auth set` |
| Telegram not connecting | Using Cloudflare Workers | Switch to VPS (Telegram needs persistent connection) |
| Slow inference (3.5s/token) | CPU-only with large model | Use smaller model or add GPU |
| Port conflict on 18789 | Another service using port | Change port: `openclaw gateway --port 18790` |
| Docker sandbox issues | Permissions or config | Run `openclaw doctor` |
| Skills not loading | Corrupt installation | Reinstall: `openclaw skill remove <name> && openclaw skill install <name>` |
| Messages lost between channels | Known bug | Update to latest version |
| High token consumption | ~35,600 tokens injected per message (workspace context) | Reduce workspace files, use cheaper models |
| Rate limiting (GitHub #5159) | Aggressive retry loops | Update to latest (fix uses exponential backoff) |
| Browser automation brittle | CDP connection issues | Use `openclaw-managed` mode, not relay |

### Diagnostic Commands

```bash
openclaw doctor                    # Check for common issues
openclaw security audit            # Security scan
openclaw security audit --deep     # Deep scan with WebSocket probe
openclaw security audit --fix      # Auto-fix safe issues
node --version                     # Must be 22+
```

---

## Cost Calculator & Optimization

### Tools

- [OpenClaw Cost Calculator](https://calculator.vlvt.sh/) - Estimate your monthly spend
- [API Usage and Costs Docs](https://docs.openclaw.ai/reference/api-usage-costs) - Official reference
- [eesel.ai Pricing Guide](https://www.eesel.ai/blog/openclaw-ai-pricing) - Realistic cost breakdown

### Key Cost Drivers

1. **Model selection** — Claude Haiku vs Opus = 5-25x cost difference
2. **Message volume** — Each message consumes input + output tokens
3. **Tool usage** — Web search, browser, commands add tokens
4. **Memory search** — Vector + FTS queries consume API calls
5. **Session compaction** — Summarizing long sessions uses tokens
6. **Media transcription** — Images/audio cost extra
7. **Workspace context injection** — ~35,600 tokens per message overhead ([Issue #9157](https://github.com/openclaw/openclaw/issues/9157))

### Monthly Budget Targets

| Budget | Strategy |
|--------|----------|
| **$0** | Oracle Cloud + Gemini free tier + Ollama for local |
| **$10** | Hetzner ($4) + Claude Haiku ($6) |
| **$25** | DigitalOcean ($12) + mixed models ($13) |
| **$50** | DigitalOcean ($12) + Claude Sonnet ($38) |
| **$100** | Managed hosting ($24) + heavy API ($76) |

---

## Key Contributors

| Contributor | Role | GitHub |
|-------------|------|--------|
| **Peter Steinberger** | Creator | [@steipete](https://github.com/steipete) |
| **Mario Zechner** | Pi creator, security pen-tester | [@badlogicc](https://github.com/badlogicc) |
| **Maxim Vovshin** | Blogwatcher skill | [@Hyaxia](https://github.com/Hyaxia) |
| **Nacho Iacovino** | Location parsing (Telegram + WhatsApp) | [@nachoiacovino](https://github.com/nachoiacovino) |
| **500+ contributors** | Community | [All contributors](https://github.com/openclaw/openclaw/graphs/contributors) |

---

## Related Repositories

| Repository | Stars | Description |
|------------|-------|-------------|
| [openclaw/openclaw](https://github.com/openclaw/openclaw) | 176K+ | Main repository |
| [openclaw/clawhub](https://github.com/openclaw/clawhub) | - | Official skill directory |
| [cloudflare/moltworker](https://github.com/cloudflare/moltworker) | - | Cloudflare Workers adaptation |
| [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | - | 3,009 curated skills |
| [centminmod/explain-openclaw](https://github.com/centminmod/explain-openclaw) | 26 | Deep security analysis (73 files, multi-AI) |
| [lunarpulse/openclaw-mcp-plugin](https://github.com/lunarpulse/openclaw-mcp-plugin) | - | MCP server integration plugin |
| [phioranex/openclaw-docker](https://github.com/phioranex/openclaw-docker) | - | Docker deployment configs |

---

## Contributing

Contributions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

- Add a resource via pull request
- Report broken links via issues
- Suggest new sections or improvements

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

This list is released under CC0 1.0 Universal (Public Domain).
