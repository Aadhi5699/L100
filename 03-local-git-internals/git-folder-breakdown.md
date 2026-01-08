Explain:

objects/
This directory stores all the content (blobs), directory trees, commits, and tags tracking your project history. They are stored as compressed, immutable objects identified by their SHA-1 hash.

refs/
This directory stores pointers (references) to commit objects. It helps Git give human-readable names to commits.
- refs/heads/: Local branches.
- refs/tags/: Tags.
- refs/remotes/: Remote-tracking branches.

HEAD
A special pointer that references the current branch or commit you are working on.
- Usually points to a branch ref (e.g., ref: refs/heads/main).
- In "detached HEAD" state, it points directly to a commit hash.

**Observation:**
- On `main` branch: `cat .git/HEAD` -> `ref: refs/heads/main`
- After `git checkout -b feature`: `cat .git/HEAD` -> `ref: refs/heads/feature`

index
Also known as the "staging area". It is a binary file that tracks the files in your working directory and prepares them for the next commit. It stores stat information (like timestamps) and pointers to the file content blobs tracking in the objects directory.