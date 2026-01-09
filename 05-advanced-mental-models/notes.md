# Advanced Git Mental Models

## Git Fetch
- Downloads objects and refs from another repository.
- Does not modify your working directory or current branch.
- Updates remote-tracking branches (e.g., `origin/main`).

## Git Pull
- Essentially `git fetch` followed by `git merge FETCH_HEAD`.
- Updates the current branch with changes from the remote.
- Can be configured to rebase instead of merge (`git pull --rebase`).

## Git Push
- Uploads local repository content to a remote repository.
- Updates remote refs to match local refs.
- Requires that your local history is up-to-date with the remote (unless forcing).

## Git Push -f (Force)
- Overwrites the remote repository's history with your local history.
- Dangerous: Can cause other developers to lose work if they have based work on the overwritten commits.
- Useful when you have rebased local commits and need to update the remote.

## Git Rebase
- Moves or combines a sequence of commits to a new base commit.
- Rewrites history (changes commit hashes).
- Linearizes history, avoiding unnecessary merge commits.

## Packfiles
- Git's mechanism for compressing objects.
- Loose objects are individually compressed files.
- Packfiles combine multiple objects into a single file to save space and improve performance (delta compression).
- `git gc` triggers packing.

## Rebase Observation (Experiment)

### Before Rebase (The Fork)
```text
* 4f14dfa (HEAD -> master) C4: Main commit
| * 66c3ca1 (feature) C3: Feature commit
|/
* ca8fb92 C2: Second commit
* d7db359 C1: Initial commit
```
*Note the branching structure where both C3 and C4 stem from C2.*

### After Rebase (The Linearization)
```text
* 54012ea (HEAD -> feature) C3: Feature commit
* 4f14dfa (master) C4: Main commit
* ca8fb92 C2: Second commit
* d7db359 C1: Initial commit
```
*Observations:*
1. **Linear History**: `feature` now sits directly on top of `master` (C4). The fork is gone.
2. **Rewritten History**: The hash for "C3: Feature commit" changed from `66c3ca1` to `54012ea`. This proves rebase creates a **new commit**.
3. **Mechanism**: Git "unplugged" C3 from C2 and "replayed" it on top of C4.
