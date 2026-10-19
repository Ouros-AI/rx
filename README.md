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
<img src="demo.gif" alt="RX in action with live browser pane" width="100%" style="border-radius: 8px; border: 1px solid #333;" />

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
