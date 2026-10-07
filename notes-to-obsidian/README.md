# notes-to-obsidian

A Claude skill that turns photographed or scanned handwritten study notes into honest ratings, technique breakdowns, and polished Obsidian-ready notes — one topic at a time.

notes-to-obsidian was created with Claude, directed and reviewed by Sudip Musib.

## What it does

Upload a photo or PDF of handwritten notes and get:

1. **Honest rating** (1–10) with specific evidence from your actual notes
2. **Technique identification** — names what you're already doing well so you can repeat it on purpose
3. **Concrete missing additions** — not a generic checklist, but the 3–4 things your notes are actually lacking
4. **Better/faster alternatives** — shows when the same problem has a more standard, efficient, or safer solution
5. **Obsidian topic notes** — one at a time, self-contained, ready to paste into your vault

Two optional follow-ons after notes exist:
- **Concept map** — Obsidian Canvas `.canvas` file showing how topics connect
- **Flashcards** — 5–10 cards per topic, pulled from the corrected note (not the raw source)

## Installation

- **Claude.ai:** zip this folder and upload it in Settings → Skills.
- **Claude Code:** copy this folder to `~/.claude/skills/notes-to-obsidian/`.

## Structure

```
notes-to-obsidian/
├── SKILL.md                          # Main skill instructions
├── README.md
├── assets/
│   └── example-topic-note.md         # Worked example of Step 5 output
└── references/
    ├── rating-criteria.md            # Rating rubric + technique checklist
    ├── obsidian-note-template.md     # Exact structure for topic notes
    ├── canvas-map-format.md          # Obsidian Canvas JSON format
    └── flashcard-format.md           # Per-topic flashcard rules
```

## How the pipeline works

| Step | What happens | Why it matters |
|------|-------------|----------------|
| **0** | Quick context check (only if genuinely unclear) | Infer subject/course; don't ask if it's obvious |
| **1** | Read every page completely | Handwritten notes are messy — don't skim the tidy parts and miss the rest |
| **2** | Rate the notes honestly (1–10) | Anchored to a rubric, not vibes or flattery |
| **3** | Name what's working + what's missing | Technique naming lets you repeat success on purpose |
| **4** | Surface better/faster alternatives | Same problem, more standard/efficient solution — applies to code and non-code |
| **5** | Build Obsidian notes, one topic at a time | One-at-a-time means you actually review each one before moving on |

Follow-ons (opt-in, never auto-run):
- **Concept map** — Obsidian Canvas with topic nodes grouped by unit
- **Flashcards** — 5–10 cards scoped to one topic, mechanism-first

## Rating rubric

| Band | What it means |
|------|---------------|
| **1–3** | Copies rules/syntax with no explanation of why; no self-checking |
| **4–6** | Correct and organized, but largely passive transcription |
| **7–8** | Explains mechanism, includes active-recall elements, precise phrasing |
| **9–10** | Mechanism-level throughout, verified examples, honest self-flagging |

## Techniques the skill looks for

- **Mechanism over syntax** — explains *why*, not just the rule
- **Systems tracing** — maps a full process end-to-end
- **Comparative tables** — puts related-but-different things side by side
- **Verified worked examples** — shows actual computed output, not just the formula
- **Metacognitive flagging** — marks confusion or unverified claims directly
- **Memory/mental-model thinking** — breaks concepts down to what's actually happening underneath

## Design choices

- **One topic at a time, not a dump.** A full batch means you'll never review ten topics with any care. Producing one and waiting forces real review.
- **Every topic note stands alone.** Anyone opening just that one file in their vault should understand the topic without needing the others first.
- **Flashcards come from the corrected note**, not the raw source. The note is the verified version; cards test that.
- **The canvas map only draws edges the notes support.** No invented relationships. If you're unsure, leave the edge out.
- **Subject-agnostic.** First built against C++ programming notes, but the rating rubric, technique-naming, and template apply to any subject with structured concepts.

## License

MIT
