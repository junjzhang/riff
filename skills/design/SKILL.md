---
name: design
description: Propose architecture and data structure decisions for a feature, producing a visual HTML design document for review.
---

# Design

Produce a design document proposing how to build or refactor a feature. Typically follows a `brief` — the brief identifies *what* to do, the design proposes *how*.

## Input

The user references a task, issue, or an existing brief. Examples:
- `/riff:design 586`
- `/riff:design the new checkpoint pipeline`
- `/riff:design` (in a workspace that already has a brief — design builds on it)

## Process

1. **Review context**: Read the existing brief (if any), the relevant source code, and understand constraints.
2. **Create workspace**: Ensure `.workspace/{id}-{slug}/` exists. Add `.workspace/` to `.gitignore` if missing.
3. **Write `design.html`** in the workspace folder.

## Output Structure

1. **Title + subtitle** — what is being designed
2. **Constraints** — hard requirements that shape the design (performance budgets, API compatibility, dependency limits)
3. **Data Structures** — the core data types and their relationships. This is the most important section. Show struct/class definitions with field-level commentary.
4. **Flow** — ASCII diagram showing the data flow / call sequence through the proposed design
5. **API Surface** — public functions/methods, their signatures, and one-line descriptions. Show usage examples.
6. **Alternatives Considered** — 2–3 alternatives with a one-line reason each was rejected. Table format.
7. **Migration / Rollout** — if this changes existing behavior: what breaks, how to migrate, can it be done incrementally
8. **Open Decisions** — choices that need the user's input before implementation

## Style

Use the Tokyo Night dark theme. Inline the full CSS from `templates/style.css` as a `<style>` block.

## Rules

- HTML only, self-contained
- Data structures first — lead with types, not control flow
- Show concrete code for proposed APIs, not pseudocode
- Flag decisions that need user input with a visible callout (use `.callout` class)
- `lang="zh-CN"` — Chinese explanations, English technical terms
- Footer: `{project} / {identifier} / .workspace/{folder}/design.html`
- End with "pause for discussion" — do NOT start implementing after producing the design
