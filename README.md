# RX

A fast coding agent for your terminal. It works in your project, runs your
builds and tests, and shows the pages it builds in a live pane beside the chat.

## Install

```sh
curl -fsSL https://github.com/Ouros-AI/rx/releases/latest/download/install.sh | sh
```

Or, from a downloaded archive: `sh install.sh rx-aarch64-apple-darwin.tar.gz`.
RX installs to `~/.local/share/rx` and links `~/.local/bin/rx`. macOS on Apple
silicon and Intel.

## Sign in

```sh
rx login chatgpt   # ChatGPT Plus, Pro or Team subscription
rx login claude    # Anthropic API key (console.anthropic.com)
```

`ANTHROPIC_API_KEY` and `OPENAI_API_KEY` in your environment also work. Grok
(`rx login grok`) and local llama.cpp models are supported.

Claude Pro and Max subscriptions cannot be used: Anthropic only permits API keys
in third-party tools.

## Use

Run `rx` in a project and type what you want done.

| Key | Action |
| --- | --- |
| Enter / Ctrl+J | Send / new line |
| F5 | Pick a model |
| Ctrl+N, Alt+←/→ | New tab, switch tabs |
| F3 | Browse files and attach paths |
| F8 | Show or hide the HTML/browser pane |
| Ctrl+C | Stop the current turn (twice to quit) |

Type `/` for commands. `rx ask "…"` runs one prompt and prints the answer.

## Updates

```sh
rx update          # install the latest release
rx update --check  # only check
```

RX checks for updates at most once a day and shows a one-line notice. Set
`RX_NO_UPDATE_CHECK=1` to turn the check off. See CHANGELOG.md for changes.

## Data

Credentials are stored in `~/.config/rx` with owner-only permissions. Session
checkpoints are encrypted in each project's `.ouros` directory. RX sends your
prompts and the files and command output the agent reads to the model provider
you choose, and nothing to Ouros AI.

RX is proprietary software; see LICENSE. Open-source components are listed in
THIRD-PARTY-NOTICES.md.

Execution boundaries now retain a durable handoff instead of exhausting rounds
without an answer. See the execution-budget notes
for configuration defaults, checkpoint inspection, uncertain-call reconciliation,
and the deterministic launcher reproduction.
