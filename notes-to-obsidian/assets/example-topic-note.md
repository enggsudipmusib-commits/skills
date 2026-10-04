# Example: a completed topic note

This is the level of detail and tone Step 5 should produce — concrete, mechanism-first, and ready to paste into Obsidian as-is.

```markdown
---
tags: [cpp, fundamentals]
status: draft
---

# Topic 1: Program Anatomy & Compilation Pipeline

## Overview
Every C++ program goes through the same journey from source code to a running process. Understanding that journey — not just the `#include`/`int main()` boilerplate — is what makes linker errors and "why won't this compile" moments make sense later.

## Core Concepts

**`#include <iostream>`** pulls in declarations for `cout`/`cin` before compilation. Without it, the compiler has no idea what `cout` is and throws a compile error — it isn't a formality, the compiler is not being clever about it.

**`int main()`** is the OS's reserved entry point — the OS itself calls this function to start the program. It returns `int` specifically because the OS reads that return value as an exit/status code (`$?` on Linux, `%errorlevel%` on Windows): `0` conventionally means success, nonzero means something went wrong.

## How It Works
1. **Source (`.cpp`)** — what you write.
2. **Preprocessor** — resolves `#include`, `#define`, and other `#` directives, producing expanded source.
3. **Compiler** — translates expanded source into object code (`.o`/`.obj`), checking syntax and types.
4. **Linker** — combines object files and libraries into a single executable, resolving references between them.
5. **Executable** — the OS loads it into RAM and calls `main()`.

## Worked Examples
```cpp
#include <iostream>
int main() {
    std::cout << "I like pizza";
    return 0;
}
// Output: I like pizza
```
The string `"I like pizza"` is stored as a null-terminated char array in memory — that trailing `\0` is what tells `cout` where the string ends.

## ⚠️ Gotchas
Forgetting `#include <iostream>` gives a compile error mentioning `cout` as undeclared — easy to misread as a typo in your own code rather than a missing header.

## Open Questions
- Confirm whether the linker step is visible/separate in the IDE being used, or fully hidden behind "Run."

## See Also
- [[02 IO Streams]]
```

Notice what this example is doing that a plain syntax dump wouldn't:
- It states the *why* behind `int main()` returning `int`, not just the syntax.
- The pipeline is traced as a numbered sequence, not a paragraph.
- The worked example shows real output, and explains the underlying memory representation instead of stopping at "it prints the string."
- One genuine open question is carried forward rather than smoothed over.
