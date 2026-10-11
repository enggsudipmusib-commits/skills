# Token Efficiency

A Claude skill that checks prompts, skills, agents, RAG pipelines, and tool/MCP setups for wasted tokens and context cost, and gives concrete fixes for each.

## What's here

- **`SKILL.md`** — the skill itself. A short checklist organized by what's being reviewed: a prompt or chat habit, a skill or system prompt, a RAG pipeline, a tool-calling or agent setup, structured data sent to a model, or a reasoning-heavy pipeline.
- **`references/research-notes.md`** — the evidence behind each rule in `SKILL.md`: what each source actually found, where it's been corrected or narrowed, and a link to check it yourself.
- **`LICENSE`** — MIT.

## Using it

Place this folder where your Claude setup reads skills from. Claude loads `SKILL.md` automatically when a request matches its description — reviewing a prompt for waste, auditing a skill or agent loop, checking an MCP/tool setup, or asking why something is costing so many tokens.

## Why it exists

In most setups, the biggest source of token cost isn't clumsy wording — it's whatever is sitting in context that doesn't need to be there: unused tool schemas, un-reranked search results, a skill that loads its own background reading on every trigger. This skill is a compact, checkable list of where that waste tends to hide, built from the sources in `references/research-notes.md` rather than general impressions.

## License

MIT — see [LICENSE](LICENSE).
