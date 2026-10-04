---
name: notes-to-obsidian
description: Turn photographed or scanned handwritten class/study notes (PDF or images) into a qualitative rating, a skills-used breakdown, better/faster alternatives for any code or technique shown, and complete polished notes formatted to paste straight into Obsidian. Use this whenever the user uploads a photo or PDF of handwritten or scanned notes and asks Claude to read, grade, rate, review, "make this better," clean up, digitize, or convert their notes — even if they never say the word "Obsidian." Also use it when the user asks to turn a prior notes-review conversation into finished notes, wants notes built "one topic at a time," or asks how their notes compare to normal/basic notes. Also covers two optional follow-ons once topic notes exist — a visual Obsidian Canvas concept map of how topics connect, and spaced-repetition flashcards for a completed topic.
---

# Notes → Obsidian

Converts messy handwritten study notes into two things the student actually needs: an honest read on how good their notes already are, and a clean, linkable, Obsidian-ready rewrite they can build a vault out of over time.

This is a pipeline of five core steps plus two optional follow-ons. Don't skip or collapse the core steps — each one produces something the student reacts to before the next one runs, and Step 5 deliberately outputs *one topic at a time*, not a dump. See "Why one topic at a time" below before you're tempted to batch it. The follow-ons (concept map, flashcards) are opt-in extras layered on top once topic notes exist — never run them unasked in place of a core step.

## Step 0 — Quick context check (only if genuinely unclear)

Skim for the subject/course and, if it's a subject with a clear exam format (e.g. a language with a specific proficiency test, a course that obviously follows a standard syllabus), whether the student's preparing for something specific. Most of the time this is obvious from the notes themselves (headers, terminology, problem style) — infer it silently and move on. Only ask if it would genuinely change Step 2's rating criteria or Step 5's note structure and you can't tell from the notes — e.g. the handwriting mixes what looks like two different courses, or it's ambiguous whether this is intro or advanced material. Keep it to one quick question, and never let this step delay or replace Step 1.

## Step 1 — Read the whole thing first

Before analyzing anything, read every page of the upload (PDF or images) completely. Handwritten notes are often out of order, have margin notes, arrows, cross-outs, and asides — don't skim the tidy parts and miss the messy ones. If a page is genuinely illegible, say so explicitly rather than guessing at content and presenting it with confidence.

If the file is a PDF, check for a locally installed PDF-reading skill for the extraction/rasterization approach before doing anything ad hoc.

## Step 2 — Rate the notes honestly

Read `references/rating-criteria.md` before writing the rating — it's the rubric, and using it keeps the score grounded in specifics rather than vibes or flattery. Produce:

- What's genuinely *above* the level of typical notes on this subject, with a concrete example from their actual notes for each point (not a generic compliment — quote or paraphrase what they wrote and say why it's better).
- Where the notes are weaker: fragmented sections, loose/imprecise definitions, unverified claims, gaps.
- A single 1–10 rating with the reasoning stated plainly, anchored to the rubric in the reference file. Don't inflate it — a rating that means something is more useful to a student than a flattering one. If it's a 6, say 6.

## Step 3 — Name what's already working, and what's missing

List which specific note-taking techniques the notes demonstrate (see the technique list in `references/rating-criteria.md` — mechanism-over-syntax, metacognitive flagging, comparative tables, verified worked examples, systems tracing, etc.), pointing at where each shows up. Naming the technique explicitly is what lets the student repeat it on purpose next time instead of by accident.

Then suggest concrete additions the notes are missing — a gotchas box, an end-of-chapter cheat sheet, a table of contents, missing prerequisites (e.g. an import/header a code snippet silently depends on), cross-links between related topics. Keep these concrete and few — three or four real suggestions beat a checklist of ten generic ones.

## Step 4 — Surface better/faster alternatives

This step is about showing the student that the same problem often has a more standard, more efficient, or safer solution than the one they wrote down — that's the "how many ways can we solve it" instinct behind this whole skill, and it applies beyond code:

- **Code**: for each snippet, check whether the language has since offered a safer, clearer, more idiomatic, or more efficient construct for what they hand-wrote (a built-in function replacing a manual formula, a modern cast replacing a C-style one, a compound operator replacing a longhand expression). Show the original next to the alternative with a one-line reason it's better — don't just replace it silently, the point is for them to see the option exists, not to memorize new syntax blindly.
- **Non-code subjects**: the same instinct applies to a shortcut proof technique, a more standard notation, a faster calculation method, or a more current terminology — anywhere their version is correct but there's a more standard or efficient way practitioners actually do it.
- Also directly answer any question the student flagged in their own notes (a margin note like "why does this work?" or "not verified") — these are usually the highest-value thing to resolve, since the student already told you exactly where their understanding is shaky.

## Step 5 — Build the Obsidian notes, one topic at a time

Read `references/obsidian-note-template.md` for the exact structure to follow, and `assets/example-topic-note.md` for a complete worked example at the right level of detail.

**Why one topic at a time:** the point of this step is for the student to review, correct, and actually file each note into their vault as it lands — a full dump defeats that, because they'll never review ten topics at once with any care, and errors compound silently across the batch. So:

1. Ask (or infer from the notes' own structure) what the natural topic order is, and say what that order will be before starting.
2. Produce ONE complete topic note, fully polished and ready to paste as-is — not a placeholder, not an outline to fill in later.
3. Cross-link it to adjacent topics with `[[wikilinks]]` even before those notes exist — the links are placeholders for what's coming.
4. Stop and wait. Don't continue to the next topic until the student says "next" (or equivalent). If they push back on the note you just produced, revise that one before moving on — don't carry a disputed note forward into the sequence.

Every individual topic note must be self-contained and complete — someone should be able to open just that one file in their vault and understand the topic, not need to have read the others first.

## Optional follow-on — Concept map as an Obsidian Canvas

Once at least two or three topic notes exist (this session or a prior one), the student may ask to *see* how the topics connect — "map this out," "show me a mind map," "visualize how these relate." Mention this capability **at most once per note set** — right after the 2nd or 3rd topic note is the natural point — and never again in that sequence whether or not they take you up on it. Repeating the offer after every topic is noise, not help.

When asked, read `references/canvas-map-format.md` and produce a `.canvas` file (Obsidian's native JSON Canvas format) with one node per topic, grouped by unit/chapter if the notes have that structure, and edges drawn between topics that the notes themselves connect (via shared prerequisites, explicit cross-references, or `[[wikilinks]]` already placed in Step 5). Don't invent relationships the notes don't support.

## Optional follow-on — Flashcards for a completed topic

Mention that flashcards are available **once, after the first topic note** of a set is accepted — a single line is enough ("say the word if you want flashcards for this one"). Don't repeat the offer on later topics in the same set; by then the student already knows it's on the table. Never generate flashcards unasked. If the student takes you up on it at any point (or asks directly — "quiz me on this," "make flashcards for this topic"), read `references/flashcard-format.md` and generate 5–10 cards scoped to *that one topic only*, drawn from its Core Concepts, Worked Examples, and Gotchas sections. This is a study aid downstream of the note, not a replacement for it — the polished topic note is still the thing that goes in the vault.

## A note on subject matter

This skill was first built against handwritten C++ programming notes, so Step 4's code branch is the most detailed one. But nothing else here is C++- or programming-specific — the rating rubric, the technique-naming step, and the Obsidian template all apply to any subject with structured concepts (math, biology, history, language learning). Apply Step 4's non-code branch when the subject isn't code.
