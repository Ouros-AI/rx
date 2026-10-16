# RX

**A precise coding agent for your terminal, written in Rust.** It works inside
your project — running your builds and tests — and opens the pages it builds in
a live pane beside the chat, then drives them to check its own work.

Installs in one line. Brings your own model. Sends nothing to Ouros AI.

```sh
rx login chatgpt
rx
```

## Install

```sh
curl -fsSL https://github.com/Ouros-AI/rx/releases/latest/download/install.sh | sh
```

macOS on Apple silicon and Intel. RX installs to `~/.local/share/rx` and links
`~/.local/bin/rx`. From a downloaded archive:
`sh install.sh rx-aarch64-apple-darwin.tar.gz`.

## Sign in

```sh
rx login chatgpt   # ChatGPT Plus, Pro or Team
rx login claude    # Anthropic API key — console.anthropic.com
rx login grok
```

`ANTHROPIC_API_KEY` and `OPENAI_API_KEY` in your environment also work, and a
saved ChatGPT sign-in takes precedence over `OPENAI_API_KEY`. NVIDIA NIM and
local `llama.cpp` models are supported.

Claude Pro and Max subscriptions cannot be used: Anthropic permits only API keys
in third-party tools. Through the API, Claude Opus 5.5, Sonnet 5.5 and Haiku 5.5
are available, with prompt caching on the system prompt, the tools and the latest
turn. RX opens on a model you are signed in for; a Claude-only setup starts on
Sonnet 5.5.

## What it does differently

**It checks its own work.** RX renders the pages it writes in a live pane, then
clicks, scrolls and types through them — reading the result before it tells you
the job is done. `/view` and `/browser` open a pane yourself; `F8` hides it.

**Tabs keep their own mind.** Every tab holds its own conversation, context and
working directory, so a tab refactoring auth does not drag a second tab's context
along with it. Each tab cancels independently.

**Context you can see.** The system prompt describes only the tools the session
actually has, large tool outputs are offloaded rather than stuffed into the
window, and the context meter shows usage against the model's real limit.

**Memory that outlives the session.** Session checkpoints are encrypted per
project, searchable with `/recall`, and retain the model's reasoning for later
review.

**Your model, not ours.** A ChatGPT subscription, an Anthropic API key, Grok,
NIM, or a model running on your own machine.

## Keys

| Key | Action |
| --- | --- |
| Enter / Ctrl+J | Send / new line |
| F5 | Pick a model |
| F3 | Browse files and attach paths |
| F8 | Show or hide the HTML/browser pane |
| Ctrl+N, Alt+←/→ | New tab, switch tabs |
| Ctrl+C | Stop the current turn (twice to quit) |

Type `/` for commands. `rx ask "…"` runs one prompt and prints the answer.

## Updates

```sh
rx update          # install the latest release, keeping the previous one
rx update --check  # only check
```

RX checks for updates at most once a day and shows a one-line notice. Set
`RX_NO_UPDATE_CHECK=1` to turn the check off. See CHANGELOG.md for changes.

## Data

Credentials are stored in `~/.config/rx` with owner-only permissions. Session
checkpoints are encrypted in each project's `.ouros` directory. RX sends your
prompts and the files and command output the agent reads to the model provider
you choose, and nothing to Ouros AI. RX does not read a project's `.env` file.

## License

RX is proprietary software; see LICENSE. Open-source components are listed in
THIRD-PARTY-NOTICES.md.
