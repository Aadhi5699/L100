# Content Addressable Storage (CAS)

## 1. SHA-1 as Key
Git acts as a key-value store where the **key is the SHA-1 hash** of the content, and the **value is the content itself**.
- Unlike almost all other databases (where you choose the ID), in Git, the **content determines the ID**.
- **Demo Finding**: When I ran `git hash-object a.txt`, Git took the content "Hello", calculated the hash `4b849db...`, and would use that as the filename in `.git/objects/4b/849db...`.

## 2. Deduplication
Because the ID is derived solely from the content, two files with the exact same content will have the exact same Hash.
- Git will only store that blob **once**.
- If you copy `a.txt` to `b.txt`, Git doesn't grow in size significantly; it just points both directory entries to the same hash.

## 3. Immutability
Git objects are immutable. You cannot "change" an object.
- If you modify `a.txt`, the content changes.
- Therefore, the Hash changes.
- Git writes a **new** object for the new content. The old object remains untouched (history).

## Demo Execution Summary
In the `cas-demo` folder, I proved this behavior:
1.  **Input**: `echo "Hello" > a.txt`
2.  **Hashing**: `git hash-object a.txt` -> `4b849dbdb38e94b0a2d87aff8875832da7040c78`
3.  **Storage**: After `git add` and `git commit`, this object is stored in the `.git/objects` folder structure.
