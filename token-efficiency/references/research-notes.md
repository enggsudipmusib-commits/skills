# Research Notes: Token Efficiency

Why each rule in `SKILL.md` exists and where to read more. Every item below was checked against the linked page on 2026-10-11. Numbers come from each source's own tests and may not carry over to your setup.

## Findings checked against sources

### Cost grows faster than context length

Self-attention compares every token with every other token, so cost rises faster than linearly as input gets longer. This underlies most trouble with context cost.
Source: Vaswani et al., "Attention Is All You Need" (2017). https://arxiv.org/abs/1706.03762

### The middle of a long prompt is the weak spot

Liu et al. tested models on questions where the relevant passage moved around inside a long input. Results were best when it sat near the start or the end and dropped when it sat in the middle, including for models built for long inputs. Preprint in 2023, published in TACL in 2024.
Sources: https://arxiv.org/abs/2307.03172 and https://doi.org/10.1162/tacl_a_00638

### Token counts differ by language

Lundin et al. (2025) studied languages with rich word-building systems and little training data, using the AfriMMLU benchmark. In all ten models tested, a higher number of tokens per word went with lower accuracy. The authors also argue that cost grows with the square of the token count, so twice the tokens means about four times the training expense. The scope is those languages, not every non-English language.
Source: https://arxiv.org/abs/2509.05486

### Tool definitions are expensive

Anthropic's engineering post on advanced tool use gives these examples: a five-server setup with 58 tools used about 55K tokens before any conversation started; its GitHub server (35 tools) cost about 26K and Jira about 17K. With on-demand tool search the same kind of setup dropped from about 77K to about 8.7K tokens, which Anthropic describes as an 85% reduction.
Separate measurements by Unblocked (updated September 2026) put the full GitHub MCP server, with 93 tools, at roughly 42K to 55K tokens, and its standard 26-tool set at about 4.2K.
Takeaway: the bill depends heavily on which tools are enabled, so measure your own setup.
Sources: https://www.anthropic.com/engineering/advanced-tool-use and https://getunblocked.com/blog/github-mcp-token-cost/

### Models keep reasoning after they have answered

Min et al. (2026) report that, across five reasoning models, roughly 41% to 52% of the written-out reasoning comes after the answer was already settled.
Source: https://arxiv.org/abs/2605.17672

Methods aimed at this waste, all of them training or serving-pipeline techniques for high-volume use:

- **HALT-CoT** (Laaouach, 2025): stops generation once the entropy of the answer distribution falls under a set cutoff. Reports 15% to 30% fewer tokens with accuracy within 0.4 percentage points of full reasoning on its tests. It is a single-author poster at an ICML 2025 workshop, so treat it as early-stage work. https://icml.cc/virtual/2025/50550
- **Think Just Enough** (Sharma and Chopra, 2025): also uses entropy as a stopping signal and reports 25% to 50% compute savings. https://arxiv.org/abs/2510.08146
- **S-GRPO** (NeurIPS 2025): reinforcement learning that pays more for correct answers reached earlier. Reports outputs 35.4% to 61.1% shorter and accuracy up by 0.72 to 6.08 points on its benchmarks, using Qwen3 and DeepSeek-R1-Distill models. https://arxiv.org/abs/2505.07686
- **SemCoT** (NeurIPS 2025): swaps written-out reasoning for a few hidden "implicit" tokens to gain speed. Its absolute accuracy is modest on some tasks (about 10% on GSM8K for Llama-2-7b-chat), so read it as a direction, not a drop-in fix. https://arxiv.org/abs/2510.24940
- **MSIFR**, Multi-Stage In-Flight Rejection (Chowdhury, Zawad and Yan, 2026): built for synthetic-data generation. It checks a sample at several stages and drops failing ones early, reporting 11% to 77% fewer tokens. The paper gives two different figures for one benchmark, so use the range loosely. Not meant for chat. https://arxiv.org/abs/2605.14062

### Data formats

The TOON (Token-Oriented Object Notation) project's own benchmark, on 244 questions across four models, reports 72.2% accuracy for TOON versus 71.4% for JSON, with TOON's input being 42.6% smaller in token count. On flat tables, TOON and CSV accuracy are statistically indistinguishable, CSV is slightly smaller, and both are far smaller than JSON. Source: https://github.com/toon-format/toon

An independent study by Matveev (2026) had 21 models generate output in TOON versus JSON across four cases. Plain JSON scored higher on accuracy, and TOON helped mainly on large uniform data and hurt on deeply nested data. That tests writing the format, not reading it, so it is a different question from the project's benchmark. Source: https://arxiv.org/abs/2603.03306

Takeaway: for flat tables use CSV; try TOON only after measuring it on your own data.

## Corrections to an earlier version of these notes

Several figures in the earlier draft did not match their sources and were replaced:

- The MCP numbers ("94 tools at 17,600 tokens", "Atlassian at 10,000") were not found. The figures above replace them.
- "52% to 88% of reasoning tokens come after the answer" was not found. The paper located reports 41% to 52%.
- The TOON accuracy and token figures were out of date, and a claim that an independent test found it behind markdown tables was not found, so it was dropped.
- The token-tax paper covers African languages on one benchmark, not all non-Latin scripts, and the "8.92x" multiplier was not found.
- HALT-CoT was described as an ICML 2025 paper; it was a workshop poster.
- The Stanford label on the middle-of-prompt paper was dropped because the page checked does not list affiliations.

## Advice with no study behind it here

These are common practice, not conclusions drawn from a cited source: starting a fresh chat per topic, not re-uploading files, rounding unneeded precision, reranking to three to five chunks, structured output between agents, and keeping a skill's main body short.

## Who gets what

- **Everyday chat users:** mostly context hygiene. The reasoning-compression research is not meant for them.
- **Anyone building agents, RAG or MCP setups:** be selective about connected tools, rerank retrieved text before use, and require structured output.
- **People who train or serve models:** the only group that can act directly on the early-stopping and reasoning-compression methods.
