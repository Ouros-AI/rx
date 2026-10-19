<div align="center">

# RX

### The terminal coding agent that looks at what it built.

[![Rust](https://img.shields.io/badge/Language-Rust-orange.svg?style=flat-square)](https://www.rust-lang.org/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-blue.svg?style=flat-square)](LICENSE)
[![Zero Telemetry](https://img.shields.io/badge/Telemetry-Zero-success.svg?style=flat-square)](#data--security)
[![Architecture](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux-lightgrey.svg?style=flat-square)](#)

<p align="center">
  Most coding agents edit code blindly, run <code>cargo check</code>, and assume everything works.<br/>
  <b>RX renders the UI directly beside your terminal, clicks buttons, scrolls pages, and inspects the live DOM before calling a job done.</b>
</p>

<!-- Place your terminal recording / demo GIF here -->
<img width="1200" height="802" alt="demo" src="https://github.com/user-attachments/assets/c7b302f0-cc4a-4205-a6d2-24ed67a21956" />

</div>

---

## The Blindspot in Terminal Agents

Every modern terminal agent suffers from the same failure mode: it edits frontends, dashboards, and client state without eyes. It runs tests, sees exit code `0`, and leaves broken hydration, misaligned grids, and dead event handlers for you to diagnose.

RX pairs a native, high-performance terminal engine with an integrated browser pane. When RX writes front-end logic, it launches the page, verifies layout states, interacts with the rendered DOM, and verifies visual fidelity autonomously.

---

## Capabilities

### 👁️ Autonomous Visual Verification
RX doesn't stop at file writes. It opens a live browser viewport directly alongside your session, executes end-to-end interactions (clicks, keyboard input, scrolls), and parses the rendered DOM tree to verify state before declaring the turn complete.
* Toggle the live engine manually via `F8` or summon it using `/view` and `/browser`.

### 🧠 Tab-Isolated Cognition
Don't contaminate your refactoring loop. Each tab maintains an independent memory space, working directory, and conversation context. Run a full auth redesign in Tab 1 while iterating on an exploratory API fix in Tab 2 without dragging 50k tokens of unrelated baggage across the wire.
* Spawn a fresh thread with `Ctrl+N` and cycle contexts with `Alt+←/→`.

### ⚡ Transparent Context & Token Efficiency
No bloated system prompts or silent context clipping. 
* System instructions dynamically reflect only the tools active in your session.
* Massive tool dumps and stdout buffers are lazily offloaded instead of hijacking your token window.
* A live token gauge measures consumption directly against the model's actual physical window.

### 🔒 Zero Telemetry, Local-First
* **Zero Ouros Intermediaries:** Prompts, context buffers, and tool evaluations stream straight to your chosen endpoint. Nothing is logged, proxied, or routed through Ouros servers.
* **Encrypted State:** Session history is encrypted locally inside each project's `.ouros` ledger and recallable anytime via `/recall`.
* **Sanitized Context:** RX never indexes or reads your `.env` secret files.

---

## Installation

Install the native binary via the standalone script:

```bash
curl -fsSL [https://github.com/Ouros-AI/rx/releases/latest/download/install.sh](https://github.com/Ouros-AI/rx/releases/latest/download/install.sh) | sh
``` 

## Self-Updates
RX monitors release channels once per day with a non-intrusive one-line indicator.
```
bash
rx update          # Install latest release, preserving previous fallback
rx update --check  # Probe release status
```

*Disable automated checking by setting RX_NO_UPDATE_CHECK=1 in your shell profile).*

## Model Providers & Runtime Matrix
Bring your own keys or leverage consumer subscriptions directly without markup:

```bash
# Direct subscription & API logins
rx login chatgpt   # Mounts ChatGPT Plus, Pro, or Team sessions directly
rx login claude    # Anthropic API key (Claude Opus 5.5, Sonnet 5.5, Haiku 5.5)
rx login grok      # xAI API key
```
Provider / Target,Auth Flow,Prompt Caching,Details
Claude (Sonnet/Opus 5.5),rx login claude / ANTHROPIC_API_KEY,Yes,"System prompt, active tools, and latest-turn caching enabled"
ChatGPT (Plus/Pro/Team),rx login chatgpt,Varies,Web-authenticated subscription sessions
OpenAI API,OPENAI_API_KEY,Yes,Standard API endpoint integration
Grok (xAI),rx login grok,No,xAI API access
NVIDIA NIM,Configurable baseURL,Custom,Microservice container endpoints
Local LLMs (llama.cpp),Custom endpoint,Local,"Zero-network, offline local inference"

## Execution Modes
Interactive Studio
Launch the full terminal workspace with integrated tabs and preview panes:

```bash
rx
```
## Headless & Pipeline Execution
Execute ad-hoc tasks, query repo architecture, or pipe stdin into an agent turn:

```bash
# Single-turn CLI execution
rx ask "Investigate why the hydration step fails on /dashboard"

# Shell pipeline integration
cat error.log | rx ask "Identify the root cause in src/core/engine.rs"
```
## Controls & Keybindings
Shortcut,Function
Enter,Submit instruction
Ctrl+J,Multi-line input newline
F8,Toggle live HTML / Browser verification pane
F5,Hot-swap active inference model
F3,Quick-search workspace files & pin to active turn
Ctrl+N,Open isolated session tab
Alt+← / Alt+→,Cycle active session tabs
Ctrl+C,Abort active tool execution (press twice to quit)
/,"Open built-in slash command menu (/view, /recall, etc.)"

## Data & Security
Credential Storage: User credentials reside in ~/.config/rx with strict 0600 owner-only file permissions.

Session Storage: Checkpoints are encrypted per project inside .ouros/.

Telemetry: Exactly 0 lines of telemetry or telemetry collectors. Data leaves your workstation strictly to contact the model API you specify.

License
Proprietary software. See LICENSE for terms. Open-source dependencies and acknowledgments are detailed in THIRD-PARTY-NOTICES.md.
