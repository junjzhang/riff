# riff

A Claude Code plugin for structured human-agent collaboration. Four workflows that produce rich visual HTML documents in a per-task workspace.

## Skills

| Skill | Command | Purpose |
|-------|---------|---------|
| **brief** | `/riff:brief 586` | Research an issue and produce a visual briefing: problem breakdown, architecture diagram, implementation plan |
| **learn** | `/riff:learn offload.py` | Deep-dive into code or references, distill key insights and data flows |
| **explain** | `/riff:explain record_stream` | Focused explanation of a single mechanism with diagrams and concrete examples |
| **design** | `/riff:design 586` | Propose architecture and data structures for review before implementation |

## How It Works

Each skill produces a self-contained HTML file in `.workspace/{task}/` (git-ignored). Open it in a browser to review.

```
.workspace/
└── 586-activation-offload/
    ├── brief.html          ← /riff:brief 586
    ├── learn.html          ← /riff:learn activation/offload.py
    ├── explain-record-stream.html  ← /riff:explain record_stream
    └── design.html         ← /riff:design 586
```

The typical flow: **brief** (what's the problem?) → **learn** (understand the code) → **design** (propose a solution) → implement.

`explain` is standalone — use it anytime you need a deep explanation of a specific mechanism.

## Install

```bash
# From GitHub marketplace
/plugin marketplace add cmriat/riff
/plugin install riff@riff

# Or during development
claude --plugin-dir /path/to/riff
```

## Style

All output uses the [Tokyo Night](https://github.com/enkia/tokyo-night-vscode-theme) color scheme. The CSS is inlined — no external dependencies.

## License

MIT
