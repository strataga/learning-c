# Learning C - Agent Guide

Educational C systems-programming repo. The global Codex playbook applies; this file captures the local teaching and simplicity goals.

## Project Shape

- Language: C99-oriented learning code.
- Common local compile/run pattern:
  - `gcc -o build/app src/main.c && ./build/app`
- Supporting editor/build files include `.clang-format`, `compile_flags.txt`, and `.vscode/`.

## Working Rules

- Optimize for learning value. Prefer clear, idiomatic C with small examples over clever abstractions.
- Explain non-obvious C concepts in comments only when they help future Jason, not as noisy narration.
- Keep memory ownership explicit. Avoid hiding allocation/free behavior behind vague helper layers.
- Do not jump ahead to a large build system, framework, or architecture unless the repo has grown enough to justify it.
- Preserve formatting conventions from `.clang-format`.

## Verification

- Compile the touched example or program with the current project command.
- When changing memory, pointer, or parsing behavior, run the resulting binary and include the exact command used.
