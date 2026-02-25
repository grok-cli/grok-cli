<p align="center">
  <img src="assets/banner.svg" alt="GROK CLI" width="100%">
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/grokcli"><img src="https://img.shields.io/npm/v/grokcli?style=flat-square&color=c850c0&label=npm" alt="npm version"></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-4fc3f7?style=flat-square" alt="MIT License"></a>
  <a href="https://nodejs.org"><img src="https://img.shields.io/badge/node-%3E%3D18-00e676?style=flat-square" alt="Node 18+"></a>
  <a href="https://x.com/GrokAdams"><img src="https://img.shields.io/badge/𝕏-@GrokAdams-8b949e?style=flat-square" alt="X"></a>
  <a href="https://grokcli.bot"><img src="https://img.shields.io/badge/web-grokcli.bot-c850c0?style=flat-square" alt="Website"></a>
</p>

<p align="center">
  <strong>AI agent terminal + Solana token launcher — powered by <a href="https://x.ai">Grok</a></strong><br>
  <sub>Ask questions · Edit files · Run commands · Launch tokens · All from one prompt.</sub>
</p>

---

## Quick Start

```bash
# Install globally
npm install -g grokcli

# Or run directly (no install)
npx grokcli

# Set your Grok API key
export GROK_API_KEY="xai-your-key-here"

# Start
grok serve
```

> Get your API key free at **[x.ai](https://x.ai)** → API → Create Key

---

## Preview

<p align="center">
  <img src="assets/screenshot.svg" alt="GROK CLI Terminal" width="100%">
</p>

---

## Features

| | Feature | Description |
|:--|:--|:--|
| **▸** | **AI Console** | Chat with Grok models in real-time with WebSocket streaming |
| **△** | **Token Launcher** | Deploy Solana tokens on Meteora with one command |
| **📝** | **Text Editor** | View, create, edit files through natural language |
| **⚡** | **Bash Execution** | Run shell commands with AI safety confirmation |
| **🔍** | **Web Search** | Real-time web search powered by Grok |
| **🔌** | **MCP Protocol** | Connect external tools via Model Context Protocol |
| **🌿** | **Git Operations** | AI-powered commit messages, staging, push |
| **📋** | **14 Skills** | Extensible skills engine — code review, debug, refactor, docs, tests |

---

## Token Launcher

Launch Solana SPL tokens directly from the terminal — no wallet connection required. Server-side deployment via Meteora bonding curves.

<p align="center">
  <img src="assets/launch-wizard.svg" alt="GROK Launch Wizard" width="100%">
</p>

```
/launch          → Start the wizard
  Step 1: Name       (required)
  Step 2: Symbol     (required)
  Step 3: Twitter    (optional — type "skip")
  Step 4: Website    (optional — type "skip")
  Step 5: Image URL  (optional — type "skip")
  → Review receipt → Confirm → Deployed!
```

After launch, you get:
- **Contract address** (mint)
- **Solscan** explorer link
- **DexScreener** chart link
- **Meteora** pool link

Queue system handles concurrent launches — multiple users can deploy simultaneously.

---

## Installation

### npm (recommended)

```bash
npm install -g grokcli
```

### npx (no install)

```bash
npx grokcli
```

### Git Clone

```bash
git clone https://github.com/grok-cli/grok-cli.git
cd grok-cli
npm install
npm start
```

### Bun

```bash
bun install -g grokcli
```

---

## Configuration

Create a `.env` file or set environment variables:

```env
# Required — Grok AI
GROK_API_KEY=xai-your-api-key

# Optional — Model selection
GROK_MODEL=grok-3-fast
PORT=8080

# Optional — Token Launcher
WALLET_SECRET=your-base58-wallet-key
PINATA_JWT=your-pinata-jwt
SOLANA_RPC_URL=https://api.mainnet-beta.solana.com
```

### CLI Flags

```bash
grok serve                          # Start with defaults
grok serve --port 3000              # Custom port
grok serve --api-key xai-xxx        # Pass key directly
grok version                        # Show version
```

---

## Commands

| Command | Description |
|:--|:--|
| `/help` | Show all commands |
| `/launch` | Open token launcher wizard |
| `/launch-status` | Check deployment queue |
| `/model <name>` | Switch AI model |
| `/models` | List available models |
| `/skills` | Show skills registry |
| `/search <query>` | Web search via Grok |
| `/clear` | Clear conversation |
| `/compact` | Compress context window |
| `/version` | Show version |

---

## Models

Switch models on-the-fly with `/model`:

| Model | Context | Speed |
|:--|:--|:--|
| `grok-4-1-fast-reasoning` | 2M | ⚡ fast |
| `grok-4-fast-reasoning` | 2M | ⚡ fast |
| `grok-4` | 256K | normal |
| `grok-4-latest` | 256K | normal |
| `grok-code-fast-1` | 256K | ⚡ fast |
| `grok-3` | 131K | normal |
| `grok-3-fast` | 131K | ⚡ fast |
| `grok-3-mini-fast` | 131K | ⚡⚡ fastest |

---

## Deploy to Render

One-click cloud deployment:

1. Push to GitHub
2. Connect repo on [render.com](https://render.com)
3. Auto-detects `render.yaml`
4. Set environment variables:
   - `GROK_API_KEY` — your Grok key
   - `WALLET_SECRET` — deployer wallet (for launcher)
   - `PINATA_JWT` — Pinata token (for launcher)
   - `SOLANA_RPC_URL` — Helius/other RPC
5. Deploy → live at your custom domain

The `render.yaml` includes a 1GB persistent disk at `/data` for vanity keypairs and launch history.

### Docker

```bash
docker build -t grokcli .
docker run -p 8080:8080 \
  -e GROK_API_KEY=xai-xxx \
  -e WALLET_SECRET=xxx \
  -e PINATA_JWT=xxx \
  grokcli
```

---

## Project Structure

```
grok-cli/
├── server.js            # Express + WebSocket server
├── package.json         # Dependencies & scripts
├── render.yaml          # Render deployment config
├── Dockerfile           # Container deployment
├── .env.example         # Environment template
├── bin/
│   └── grok.js          # CLI entry point
├── public/
│   ├── index.html       # Web terminal (Console, Launch, Skills)
│   └── logo.png         # Pixel mascot
└── assets/
    ├── banner.svg       # GitHub banner
    ├── screenshot.svg   # Terminal preview
    └── launch-wizard.svg
```

---

## Tech Stack

- **Runtime**: Node.js 18+
- **Server**: Express 4 + WebSocket (ws)
- **AI**: Grok via OpenAI SDK (x.ai API)
- **Blockchain**: Solana Web3.js + Meteora Dynamic Bonding Curve SDK
- **Storage**: Pinata (IPFS) for token metadata
- **Frontend**: Vanilla JS, single-file SPA
- **Deploy**: Render / Docker / npm

---

## Links

- **Website**: [grokcli.bot](https://grokcli.bot)
- **npm**: [npmjs.com/package/grokcli](https://www.npmjs.com/package/grokcli)
- **GitHub**: [github.com/grok-cli](https://github.com/grok-cli)
- **𝕏**: [@GrokAdams](https://x.com/GrokAdams)
- **Grok API**: [x.ai](https://x.ai)

---

<p align="center">
  <img src="assets/logo.png" alt="GROK" width="48" style="border-radius:8px"><br>
  <sub>MIT License · Built with Grok</sub>
</p>
