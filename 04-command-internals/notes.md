# Git Command Internals

## `git reset` Internals
Git reset allows you to move the `HEAD` reference to a specific commit. How it affects the **Index** (staging area) and **Working Directory** depends on the mode used.

1.  **`git reset --soft <commit>`**:
    *   Only moves `HEAD` to point to `<commit>`.
    *   The Index and Working Directory are left touched.
    *   Essentially "undoes" a commit but keeps your work staged for the next commit.

2.  **`git reset --mixed <commit>`**:
    *   Moves `HEAD` to `<commit>`.
    *   Resets the **Index** to match `<commit>`.
    *   Working Directory changes are preserved but become unstaged.

3.  **`git reset --hard <commit>`**:
    *   Moves `HEAD` to `<commit>`.
    *   Resets **Index** AND **Working Directory** to match `<commit>`.
    *   **Destructive**: Any uncommitted changes are permanently deleted.

---

## How Git Preserves History Internals
Git history is not a linear list of changesets; it is a **Directed Acyclic Graph (DAG)** of snapshots.

1.  **Commit Objects**:
    *   Every commit contains a pointer to a **Tree** object (the snapshot of the directory).
    *   Crucially, it contains a pointer to its **Parent Commit(s)** (the SHA-1 hash).

2.  **The Chain**:
    *   Because each commit embeds the parent's hash, the history forms an unbroken chain.
    *   **Immutability**: Changing a single bit in an old commit changes its hash. This changes the parent hash stored in its child, changing the child's hash, and so on, rippling to the tip of the branch. This guarantees history integrity.

3.  **Reflog (Reference Logs)**:
    *   While the DAG preserves the structure, Git also logs every movement of `HEAD` and branch tips in `.git/logs/`.
    *   This acts as a safety net, allowing you to find commits that are no longer referenced by any branch (e.g., after a bad `reset --hard`) before the garbage collector deletes them.

### **Observation: Recovering Lost Commits w/ Reflog**

**Scenario**: I accidentally reset `--hard` and lost a commit.

1.  **Create a disaster**:
    echo "This is secret" > secret.txt
    git add .
    git commit -m "Add secret"
    git reset --hard HEAD~1
    *   Now `secret.txt` is gone, and `git log` doesn't show the commit.

2.  **Inspect the Reflog**:
    git reflog
    *   You will see an entry like: `HEAD@{1}: commit: Add secret`.
    *   Note the SHA-1 hash (e.g., `768458a`).

3.  **Recover**:
    git reset --hard <SHA-1>
    *   The commit is restored! Git never actually deleted the object immediately; it was just "dangling" until `gc` would eventually run.
