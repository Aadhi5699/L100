# Reflections — L100: Git Internals

## Initial Understanding

Before starting L100, I viewed Git primarily as a command-line tool used to save code versions and collaborate with others. Commands like `add`, `commit`, `reset`, and `rebase` felt procedural and sometimes risky. My understanding was mostly syntax-driven, and mistakes felt permanent.

## What Changed in My Confidence

Before L100:
- Blind usage of commands or tools like fork.
- I avoided `reset --hard`.
- Data loss was a constant worry.

After L100:
- I understand what happens between git add to commit
- I know data is never lost just the pointer moved, can always use reflog to recover.
- I reason about Git behavior instead of memorizing commands.
- I clearly understand the flow of data: `Working Directory -> Staging Area (Index) -> .git/objects`
