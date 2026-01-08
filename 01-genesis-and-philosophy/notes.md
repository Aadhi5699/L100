## Why Git Was Created
Git was created due to the collapse of BitKeeper access for Linux kernel developers.

## Key Philosophy Shifts
- Snapshots over diffs
   Diff-Based (SVN): These systems store a base file and then a list of changes (deltas) over time. To see a file from 100 commits ago, the system must "calculate" the result by replaying all 100 changesets.
   Snapshot-Based (Git): These systems store a complete copy of the file at each commit. To see a file from 100 commits ago, the system can simply retrieve the file from the 100th commit.
- Local-first operations
- Branches as pointers, not copies unlike Subversion(SVN) so git doesn't need to copy a directory to create a branch.
- Git is more than just a version control system it is fundamentally architected as a content-addressable filesystem—essentially a high-performance key-value database.