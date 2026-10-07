# clarify-on-confusion

A drop-in behavior pack that tells Claude to spot likely misunderstandings early and resolve them with one to three pointed questions instead of guessing.

clarify-on-confusion was created with Claude and inspired by Trail of Bits' ask-questions-if-underspecified skill and Clarify-Intent by irfanannaafi19. The wording is original, not copied.

## What it does

Once installed, Claude acts on its own whenever a conversation shows one of these signs:

- The person disagrees with or overrides the most recent reply.
- The same request comes back again in different words, or the tone sounds frustrated.
- Two reasonable readings of the request would produce very different results.
- The latest message contradicts itself or something said earlier.
- A needed detail is absent, and getting it wrong would waste the person's effort.
- The message looks garbled, truncated, or dictation-typed, so its meaning is uncertain.
- Claude realizes it is about to assume something significant about the person or their situation.

When one of these applies, Claude states in a single sentence what it has understood, then asks one to three concrete questions with ready-made options — flagging a best guess as "(recommended)" when one exists. Hard-to-reverse actions wait for the person's answer; cheap-to-retry ones proceed with the assumption stated in one line.

## Installation

- **Claude Code:** copy this folder to `~/.claude/skills/clarify-on-confusion/`.
- **Claude.ai:** package this folder as a `.zip` and add it under Settings → Skills.
- **opencode:** copy this folder to `~/.config/opencode/skills/clarify-on-confusion/`.

## Structure

~~~
clarify-on-confusion/
├── SKILL.md   # Trigger list, clarification rules, worked examples
└── README.md
~~~

## License

MIT