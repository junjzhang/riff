---
name: learn
description: Deep-dive into source code, papers, or references and distill key insights into a visual HTML document.
---

# Learn

Research a codebase area, algorithm, or external reference and produce a structured learning document. The goal is to build shared understanding between human and agent before making changes.

## Input

The user points at what to study. Examples:
- `/riff:learn src/models/shared/activation/offload.py`
- `/riff:learn how torchtune does activation offloading`
- `/riff:learn the reconcile system`

## Process

1. **Read sources**: Read the target files, follow imports, trace the call chain. For external references, use WebSearch/WebFetch.
2. **Create workspace**: Ensure `.workspace/{topic-slug}/` exists. Add `.workspace/` to `.gitignore` if missing.
3. **Write `learn.html`** in the workspace folder.

## Output Structure

1. **Title + subtitle** — what was studied and why
2. **Overview** — 2–3 sentence summary of the component/algorithm
3. **Data Flow / Architecture** — ASCII diagram of the key data structures and their relationships
4. **Key Mechanisms** — each mechanism as an `<h3>` section:
   - What it does (1–2 sentences)
   - Code snippet showing the core logic (with file:line reference)
   - Why it matters / subtle invariants
5. **Edge Cases & Gotchas** — things that would surprise a reader
6. **Comparison** (optional) — if studying an external reference, side-by-side table of their approach vs ours
7. **Open Questions** — things that remain unclear or need the user's input

## Style

Use the Tokyo Night dark theme. Inline the full CSS from `templates/style.css` as a `<style>` block.

## Rules

- HTML only, self-contained
- Show code, not just describe it — include actual snippets with `file:line` references
- `lang="zh-CN"` — Chinese explanations, English technical terms
- Footer: `{project} / {topic} / .workspace/{folder}/learn.html`
- After writing, tell the user the path and highlight 1–2 most surprising findings
