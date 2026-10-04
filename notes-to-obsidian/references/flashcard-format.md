# Flashcard format (per-topic study aid)

Scope: 5–10 cards for the ONE topic note just completed. Not a full-chapter deck, not a substitute for the note itself.

## Where cards come from

Pull from the finished topic note, not the raw handwritten source — the note is already the corrected, verified version:

- **Core Concepts** → definition/mechanism cards ("What is X, and why does it work that way?" rather than a bare definition — the note's whole point is mechanism over syntax, so the cards should test that, not just recall).
- **Worked Examples** → problem cards using the same input, asking for the computed output.
- **Gotchas** → "what's the mistake here" cards, framed as a scenario rather than a direct restatement of the warning.
- **Better/Faster Alternatives** (if present) → "what's the more idiomatic/efficient way to do X" cards.

Skip Overview and See Also — they're navigation, not testable content.

## Output format

Plain markdown, simple enough to paste into Obsidian or a spaced-repetition plugin:

```markdown
## Flashcards: <Topic Title>

**Q:** <question>
**A:** <answer>

**Q:** <question>
**A:** <answer>
```

## Rules

- Every answer must be checkable against the topic note — don't introduce facts the note doesn't contain.
- Vary question types: don't make all 10 cards simple recall. Mix in at least one "why" question and one worked-example-style question per topic where the note supports it.
- Keep answers short — a flashcard answer is a memory trigger, not a re-explanation. If the real answer needs paragraphs, that's a sign the concept belongs back in the note, not on a card.
- These are ungraded, self-review cards — no scoring mechanism needed unless the student asks for one.
