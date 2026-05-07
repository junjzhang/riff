---
name: brief
description: Research an issue or task and produce a visual HTML briefing with problem breakdown, architecture diagram, and implementation plan.
---

# Brief

Produce a concise, visual HTML briefing for a feature or bug. The output is a self-contained `.html` file the user opens in a browser.

## Input

The user provides an issue number, a topic, or a description. Examples:
- `/riff:brief 586`
- `/riff:brief refactor the data pipeline`
- `/riff:brief why is grad_norm NaN`

## Process

1. **Gather context**: Read the GitHub issue (if number given via `gh issue view`), then read the relevant source files. Understand current state before proposing changes.
2. **Create workspace**: Ensure `.workspace/{id}-{slug}/` exists (create if not). The `.workspace/` directory must be in `.gitignore` — add it if missing.
3. **Write `brief.html`** in the workspace folder.

## Output Structure

The HTML must contain these sections in order:

1. **Title + subtitle** — issue number (if any) and one-line summary
2. **Current Architecture** — ASCII diagram (inside `<div class="diagram">`) showing how the relevant components connect today
3. **Status Box** — what to KEEP, CHANGE, ADD, REMOVE (use `.keep`/`.change`/`.add`/`.remove` classes)
4. **Problem Breakdown** — each problem tagged with priority badges (`.tag-p1` through `.tag-p4`), a table or code snippet illustrating the issue
5. **Implementation Plan** — table with Phase, Change, Risk, Effort columns
6. **What We Keep** — explicit non-goals to prevent scope creep
7. **Related Issues** — connections to other open issues (if any)

## Style

Use the Tokyo Night dark theme. Inline the full CSS from `templates/style.css` (in the plugin root) as a `<style>` block — the HTML must be fully self-contained.

Available CSS classes: `.tag-p1`–`.tag-p4`, `.status-box`, `.diagram`, `.keep`/`.change`/`.add`/`.remove`, `.callout`, `.subtitle`, `.footer`.

## Rules

- HTML only, self-contained, no external resources
- Concise — each problem section 1–3 paragraphs max, prefer tables and code over prose
- `lang="zh-CN"` — explanatory text in Chinese, technical terms in English
- Footer: `{project} / {identifier} / .workspace/{folder}/brief.html`
- After writing the file, tell the user the path so they can open it
