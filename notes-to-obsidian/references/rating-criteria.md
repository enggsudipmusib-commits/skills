# Rating criteria & technique checklist

Use this to keep ratings consistent across runs instead of re-deriving "what makes good notes" from scratch each time.

## Techniques to look for (name them explicitly when found)

- **Mechanism over syntax** — explains *why* something works, not just the rule to follow. ("include iostream or the compiler doesn't know what cout is" beats "include iostream to use cout.")
- **Systems tracing** — maps a full process end-to-end (a pipeline, a sequence of steps, a cause-and-effect chain) rather than describing steps in isolation.
- **Comparative tables** — puts two related-but-different things side by side on the same dimensions, forcing the distinction to be explicit instead of fuzzy.
- **Verified worked examples** — shows an actual computed output for a real input, not just the formula or syntax. This is the difference between "I could do this" and "I did this and checked it."
- **Metacognitive flagging** — marks their own confusion or unverified claims directly in the notes ("not sure why," "not verified," a question mark in the margin). This is usually the single biggest tell of a strong learner: they're marking what to revisit instead of writing down an answer and moving on.
- **Memory/mental-model level thinking** — breaks a concept down to what's actually happening underneath (e.g. reasoning through *why* a byte value maps to a character) rather than treating it as a black-box rule to memorize.

## What to flag as weaknesses

- Fragmented or hard-to-follow sections, especially ones that read like transcription-while-thinking rather than a settled explanation.
- Loose or informal definitions used in place of the real term (e.g. calling a type alias a "shortform for datatypes") — note the imprecision and give the tighter phrasing.
- Claims or calculations with no verification — if the student didn't check it against a reference or worked it out, say so plainly rather than assuming it's right.
- Missing prerequisites a snippet or claim silently depends on (an unstated header/import, an assumed prior fact).

## Additions to suggest when missing

Don't dump all of these every time — pick the ones the actual notes are missing:

- A "gotchas" callout per topic — the mistake a learner would actually make, not a restatement of the rule.
- A one-page cheat sheet at the end of a chapter/unit — syntax or key facts only, no explanation, built for fast revision.
- A table of contents at the front, once the note collection is more than a few topics.
- Any header/import/prerequisite the notes use but never state.
- Cross-links between topics that clearly relate to each other.

## Rating rubric (1–10)

Anchor the score to these bands rather than a gut feeling. State which band it's in and why.

- **1–3**: Copies rules or syntax with no explanation of why; no self-checking; would function as a lookup table at best.
- **4–6**: Correct and reasonably organized, but largely passive transcription — states facts without tracing mechanism or checking work.
- **7–8**: Explains mechanism in multiple places, includes at least one active-recall element (a table, a worked example, a self-flagged question), and is precise in most of its phrasing.
- **9–10**: Mechanism-level explanation throughout, verified worked examples, honest self-flagging of open questions, and precise language with only minor gaps.

A rating with no specific evidence attached isn't a rating — every point above or below the middle of the scale should trace back to something identifiable in the actual notes.
