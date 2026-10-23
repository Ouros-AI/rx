# Agent-RX

RX is a coding agent that works in your terminal. Give it a task inside a
project, follow its file edits and commands, inspect the results, and keep the
session records for later review and continuation. You choose the model provider
or connect a local model.

This repository distributes RX binaries and user documentation. The implementation
source is private. RX is proprietary software; each release includes its license
and third-party notices.

## Install and update

```sh
curl -fsSL https://github.com/Ouros-AI/rx/releases/latest/download/install.sh | sh
```

Downloads support macOS on Apple silicon and Intel, and Linux x86_64 with
glibc 2.36 or later. The installer puts RX in `~/.local/share/rx` and links
`~/.local/bin/rx`. Existing configuration and session records stay in place.

```sh
rx update --check
rx update
```

The system WebKit pixel renderer requires macOS. Linux uses terminal text and
interactive page controls, without the macOS `rx-html` helper.

## Start a task

```sh
rx login chatgpt
rx
```

You can also use supported provider API credentials, including Anthropic,
Google, xAI, Vercel AI Gateway and NVIDIA NIM, or configure a local llama.cpp
server. Provider access and charges depend on your own account. Selecting the
Ouros gateway sends requests through Ouros; selecting another provider uses that
configured route.

```sh
rx ask "Find and fix the failing test, then show what changed"
```

Direct shell execution requires an explicit option:

```sh
rx ask --raw 'printf "explicit shell command\n"'
```

## Models come from their source

```sh
rx models --refresh
rx models --provider vercel --json
```

The catalogue uses the configured provider's reported model IDs and metadata.
F5 opens the provider and model picker; `r` refreshes it in the background.
Choose an exact `provider/model` ID in the picker or with
`rx ask --model <provider/model>`.

Source endpoints, fetch times, cache status and discovery errors are explicit.
Missing context or capability information stays unknown. Failed discovery adds
no invented replacement models. Grok subscription discovery uses the official
Grok CLI's model cache and labels it as cached data. Existing/current models
stay selected during refresh, but are offered in the picker only when the source
reports them.

## Working in the terminal

| Control | Action |
| --- | --- |
| F5 / `/settings` | Choose a provider and model |
| `/soul` | Edit bounded response-style guidance |
| F8 / `/split` | Show or hide the live page pane |
| `/view path.html` | Follow a saved HTML file |
| `/browser <URL>` | Open a page in the pane |
| F7 | Focus page interaction |
| `/recall` | Search retained session history |
| Ctrl+C | Cancel current work |

File, command and browser tools depend on platform and configuration. Ordinary
terminal sessions work in the host workspace; they are not universally isolated
in a virtual machine. The agent's output and checks remain available for human
review.

[Download releases](https://github.com/Ouros-AI/rx/releases) ·
[Ouros](https://ouros.md)
