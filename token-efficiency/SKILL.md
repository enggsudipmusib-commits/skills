---
name: token-efficiency
description: Use when judging or reducing token and context cost in prompts, long chats, agents, RAG pipelines, MCP or tool setups, or other Claude skills. Fits requests such as "why does this cost so many tokens?", "trim this prompt", or "is this skill bloated?". Not for general coding help that has nothing to do with token or context cost.
---

# Token Efficiency

Short checks for finding wasted tokens. Evidence and caveats live in `references/research-notes.md`; open that file only when someone asks for proof or needs a specific figure.

## The main idea

A model rereads everything in its context on every turn, and long contexts get costly faster than they get long. So the first question is almost always "what is sitting in context that this task does not need?" and only after that "how should I word this?"

## Choose the section that matches the situation

Use only the part that applies. A casual chat does not need pipeline advice.

### Prompts and chat habits

- In a lengthy prompt, place the key instruction or question first or last. Text buried halfway through is used less reliably.
- Keep one thread per task. Earlier turns are reprocessed with every new message, relevant or not.
- If a file is already in the chat, leave it there rather than sending it a second time.
- Trim precision the task does not need: long decimals, full-length IDs, exact timestamps.

### Skills and system prompts

- Everything in the main body loads each time the skill triggers. Move long tables, pasted documents and research write-ups into a `references/` file and point to it in one line.
- Keep the rules short and keep the reasoning behind them elsewhere.
- Put every "when to use this" cue in the description, because it is the one part that is always in context.

### RAG pipelines

- Do not pass raw top-k search hits to the model. Rerank them, for example with a cross-encoder, and keep roughly the best three to five chunks.
- Summarize or trim older retrieved text and chat history so it does not grow without limit.

### Tools and agents

- Connect only the tools the task needs. Each connected tool's definition is paid for on every request, used or not, and large servers can add tens of thousands of tokens.
- Prefer on-demand tool loading (tool search) when the platform offers it.
- Have agents pass structured output (JSON or tool calls) to each other instead of chatty prose.

### Data sent to a model

- Rows that share the same columns: send CSV rather than JSON, since JSON repeats every key on every row.
- Do not assume a newer compact format such as TOON always wins. Measured accuracy gaps are small and depend on the data, so test on your own.

### Reasoning-heavy pipelines

- This matters only at high volume. Models frequently hold their answer long before the written reasoning ends, so part of those tokens is overhead. Early-stopping and concise-reasoning methods can trim it, but they are changes to training or to the serving pipeline, not something to apply in a single chat.

## Avoid

- Telling people to stop asking a model to explain its reasoning in ordinary conversation.
- Promising a specific percentage saving. Describe figures as what a study reported, nothing more.
- Cutting anything the model needs in order to answer correctly.
