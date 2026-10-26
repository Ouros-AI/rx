# Agent RX

## System Abstract

RX is a coding agent that operates in the terminal. Given a task inside a project, it applies file edits and executes commands, presents the results for inspection, and retains session records for later review and continuation. The operator selects the model provider or connects a local model. This repository distributes RX binaries and user documentation; the implementation source is private. RX is proprietary software; each release includes its license and third-party notices.

Supported download targets: macOS on Apple silicon and Intel, and Linux x86_64 with glibc 2.36 or later. The system WebKit pixel renderer requires macOS; Linux uses terminal text and interactive page controls, without the macOS `rx-html` helper.

## Installation and Update

```sh
curl -fsSL https://github.com/Ouros-AI/rx/releases/latest/download/install.sh | sh
```

The installer places RX in `~/.local/share/rx` and links `~/.local/bin/rx`. Existing configuration and session records remain in place.

```sh
rx update --check
rx update
```

## Operation

```sh
rx login chatgpt
rx
```

Supported provider credentials include Anthropic, Google, xAI, the Vercel AI Gateway, and NVIDIA NIM; a local llama.cpp server can also be configured. Provider access and charges depend on the operator's own account. Selecting the Ouros gateway sends requests through Ouros; selecting another provider uses that configured route.

```sh
rx ask "Find and fix the failing test, then show what changed"
```

Direct shell execution requires an explicit option:

```sh
rx ask --raw 'printf "explicit shell command\n"'
```

### Model catalogue

```sh
rx models --refresh
rx models --provider vercel --json
```

The catalogue uses the configured provider's reported model identifiers and metadata. Source endpoints, fetch times, cache status, and discovery errors are reported explicitly; missing context or capability information stays unknown. Failed discovery adds no invented replacement models. Grok subscription discovery uses the official Grok CLI's model cache and labels it as cached data. Existing and current models remain selected during refresh, but are offered in the picker only when the source reports them. Choose an exact `provider/model` identifier in the picker or with `rx ask --model <provider/model>`.

## Interface and Specification

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

File, command, and browser tools depend on platform and configuration. Ordinary terminal sessions work in the host workspace; they are not universally isolated in a virtual machine. The agent's output and checks remain available for human review.

## References

[Download releases](https://github.com/Ouros-AI/rx/releases) · [Ouros](https://ouros.md)
