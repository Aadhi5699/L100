# L100
A deep dive into Git

A comprehensive study of Git internals, architecture, and advanced mental models.

## 📚 Syllabus & Progress
- [x] **01. Genesis & Philosophy**
  - *Why Git exists, Snapshots vs. Deltas, Content-Addressable Storage.*
  - [View Notes](./01-genesis-and-philosophy/notes.md)

- [x] **02. Git Architecture**
  - *CAS (Content Addressable Storage), DAG (Directed Acyclic Graph).*
    - [View Notes](./02-git-architecture/cas-demo/cas.md)
    - [View Notes](./02-git-architecture/cas-demo/dag.md) 
- [x] **03. Local Git Internals**
  - *Breakdown of the `.git` directory.*
    - [View Notes](./03-local-git-internals/git-folder-breakdown.md)
- [ ] **04. Command Internals**
  - *Deep dive into `add`, `commit`, and `push`.*
  
- [ ] **05. Advanced Mental Models**
  - *Why Git is safe, reflogs, and recovery.*

## 🔗 Resources & References
**01. Genesis & Philosophy**
- [GitInit: Snapshot vs Delta Storage](https://blog.git-init.com/snapshot-vs-delta-storage/)
- [Medium: Git Under the Hood](https://medium.com/@davide.rubinetti97/git-under-the-hood-snapshots-not-deltas-006c04b9d892)

**02. Git Architecture**
- [Medium: How Git Stores Your Code: A Simple Guide to Blobs, Trees, and Commits](https://medium.com/@rym.chaouch/how-git-stores-your-code-a-simple-guide-to-blobs-trees-and-commits-fef3c480e2ba)
- [GitInit: How Does Git Store Files](https://blog.git-init.com/how-does-git-store-files/#:~:text=Tree:%20A%20tree%20object%20is,a%20leaf%20in%20the%20DAG.)
- [Megakemp: The Case for Pull Rebase](https://megakemp.com/2019/03/20/the-case-for-pull-rebase/#:~:text=Git%20still%20fetched%20commit%20D%20but%20instead,%2C%20thus%20giving%20us%20a%20linear%20history.)

**03. Local Git Internals**
- [GitInit: What is HEAD in Git](https://blog.git-init.com/what-is-head-in-git/#:~:text=Fallon%20Michael%20/%20Unsplash-,HEAD%20answers%20the%20question:%20Where%20am%20I%20right%20now%20in,any%20local%20changes%20are%20based.)

- [Git Book: Recording Changes to the Repository](https://git-scm.com/book/ms/v2/Git-Basics-Recording-Changes-to-the-Repository#:~:text=If%20you%20commit%20now%2C%20the,:%20README%20modified:%20CONTRIBUTING.md)

- [Miller: Git Add Patch](https://millerb.co.uk/2021/11/16/git-add-patch.html)