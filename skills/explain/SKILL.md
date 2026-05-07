---
name: explain
description: Explain a specific mechanism or concept in depth with visual diagrams, code walkthrough, and concrete examples.
---

# Explain

Produce a focused, visual explanation of a single mechanism or concept. Unlike `learn` (broad survey), `explain` goes deep on one thing.

## Input

The user names a specific mechanism. Examples:
- `/riff:explain record_stream`
- `/riff:explain how FSDP2 mixed precision works`
- `/riff:explain the prefetch logic in activation offload`
- `/riff:explain CP sharding`

## Process

1. **Understand the mechanism**: Read relevant source code, trace execution paths, identify the core invariant.
2. **Create workspace**: Ensure `.workspace/{topic-slug}/` exists. Add `.workspace/` to `.gitignore` if missing.
3. **Write `explain-{topic}.html`** in the workspace folder. Use a slugified topic name.

## Output Structure

1. **Title** — the mechanism name
2. **One-line summary** — what it does in one sentence
3. **Mental Model** — ASCII diagram or visual that captures the core idea. This is the most important section — if the reader only sees this, they should get the gist.
4. **Step-by-step Walkthrough** — numbered steps tracing execution through the actual code, with code snippets and `file:line` references
5. **Concrete Example** — a specific scenario (with real numbers: tensor shapes, memory sizes, timing) showing the mechanism in action
6. **Why It Matters** — what breaks if this mechanism is wrong or removed
7. **Common Mistakes** — pitfalls when modifying or extending this code

## Style

Use the Tokyo Night dark theme. Inline the full CSS from `templates/style.css` as a `<style>` block.

## Rules

- HTML only, self-contained
- One mechanism per document — if the user asks about two things, produce two files
- Diagrams are mandatory — every explain must have at least one ASCII diagram
- Use concrete numbers, not abstract descriptions ("a 32MB tensor" not "a large tensor")
- `lang="zh-CN"` — Chinese explanations, English technical terms
- Footer: `{project} / {topic} / .workspace/{folder}/explain-{topic}.html`
