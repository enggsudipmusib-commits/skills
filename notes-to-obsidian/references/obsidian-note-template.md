# Obsidian topic note template

Follow this structure for every topic note produced in Step 5. Omit a section only if it genuinely doesn't apply (e.g. "Comparison" when nothing in the topic has a near-synonym or competing approach) — don't leave a section header with nothing under it.

```markdown
---
tags: [<subject>, <topic-slug>]
status: draft
---

# Topic <N>: <Topic Title>

## Overview
One or two sentences: what this topic covers and where it sits in the bigger sequence.

## Core Concepts
For each concept: state it, then explain the mechanism — why it works this way, not just that it does. This is the "why," not just the "what."

## How It Works
Only if the topic has a process, pipeline, or sequence (e.g. compilation steps, a life cycle, an algorithm's flow). Trace it step by step.

## Comparison: <X> vs <Y>
Only if the topic has two related-but-different things worth putting side by side.

| Aspect | <X> | <Y> |
|---|---|---|
| ... | ... | ... |

## Worked Examples
Real input → actual computed/verified output. Not just the formula or syntax — show it run.

## ⚠️ Gotchas
The mistake a learner would actually make here, phrased as a warning — not a restatement of the rule above.

## Better/Faster Alternatives
Anywhere the standard/idiomatic approach beats what a beginner would naturally write, shown side by side with a one-line reason. Only include this if Step 4 actually found something for this topic.

## Open Questions
Anything still unverified or genuinely unresolved — carried over from the original handwritten notes, or newly surfaced during conversion. It's fine for this section to be short or absent once things are resolved.

## See Also
- [[Previous Topic Name]]
- [[Next Topic Name]]
```

## Notes on filling it in

- Every topic note must stand alone — someone opening only this file in their vault should be able to follow it without having read the others.
- Use real `[[wikilinks]]` for the previous/next topics even if those notes don't exist yet in the vault — they're placeholders for the sequence and will resolve once the rest of the notes are created.
- Keep code blocks in fenced blocks with the right language tag (` ```cpp `, ` ```python`, etc.) so Obsidian syntax-highlights them.
- Worked examples should show the actual output, not "output: correct" — e.g. `pow(2, 10) // 1024`, not `pow(2, 10) // works correctly`.
