# Research → Plan → Implement

A workflow for solving complex implementation problems with an AI agent **without losing the context that got you there.**

> Adopted in my daily work and presented to **400+ engineers**. This is the flagship workflow of the repository.

## The idea in one line

Keep a single, curated markdown file as the agent's working memory — gather requirements, research the codebase, plan in steps, implement — and iterate freely without ever polluting the context.

## Why it matters

A chat history gets messy fast: requirements scroll away, retries pile up, and the valuable findings get buried. This pattern flips that — **one file**, persistent and clean, that you shape deliberately.

→ **[The significance](the%20significance.md)** — the core value in five points.

## How it works

You drive the agent through phases, capturing only what's worth keeping into a single "context absorber" file:

1. **Context** — requirements, the problem, relevant links
2. **Research** — identify the areas of the codebase that need to change (no code yet)
3. **Plan** — agree the steps before touching anything
4. **Implement** — execute step by step, the agent re-reading the same curated file each time

→ **[The prompt (context absorber file)](the%20prompt%20(context%20absorber%20file).md)** — the meta-prompt template you copy and fill in.

## See it in action

→ **[Demo usage — screenshots](demo%20usage%20-%20screenshots.md)** — walkthrough on real code from [dotnet/eShop](https://github.com/dotnet/eShop).

→ **[Exemplary flow — artifacts](exemplary%20flow%20-%20artifacts/)** — a full worked example: the PBI description, initial and final prompts, and the context that produced the result.

---

Part of **[AI-Assisted Developer Workflows](../../vision.md)**.
