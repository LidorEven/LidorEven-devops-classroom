# Part 6 — Git Internals: The `.git` Directory

> Reference: [nirgeier/GitLabs — 000-warmup](https://github.com/nirgeier/GitLabs/tree/main/Labs/000-warmup)

This part teaches you what Git is actually doing under the hood.

---

## Lab 1 — Blobs, Trees, and Commits

**Goal:** See how Git stores your files as objects.

### Inspect the object store

```bash
tree .git/objects        # see the SHA-1 hash folders
cat .git/HEAD            # which branch HEAD points to
cat .git/refs/heads/main # the SHA-1 of the latest commit
```

### Walk the object graph

```bash
# replace <sha> with the hash from refs/heads/main
git cat-file -t <sha>         # prints "commit"
git cat-file -p <sha>         # prints the commit object (tree, author, message)

# copy the "tree" SHA from the output above
git cat-file -t <tree-sha>    # prints "tree"
git cat-file -p <tree-sha>    # prints the blob entry for about-<name>.md

# copy the blob SHA for about-<name>.md
git cat-file -t <blob-sha>    # prints "blob"
git cat-file -p <blob-sha>    # prints the contents of your about-<name>.md file
```

---

## The Three States: Working Directory, Staging Area, Repository

**Goal:** See how Git tracks files across its three states.

### Explore the three states

```bash
echo "sample file" >> file.txt
git status                    # "modified" — working directory
git add file.txt
git status                    # "staged"
git ls-files -s               # inspect the staging area: SHA-1 + filename
git diff --staged             # compare staging area vs. last commit
```

### Try interactive staging (patch mode)

```bash
echo -e "line A\nline B\nline C" > multi.txt
git add multi.txt
git commit -m "Add multi.txt"
echo -e "line A\nline B changed\nline C\nline D" > multi.txt
git add -p multi.txt          # choose which hunks to stage interactively
```

### Undo a staged change

```bash
git restore multi.txt         # discards working-directory changes
```

---

[Previous: Part 5 — Collaboration](Part5-Collaboration.md)  
[Next: Part 7 — Review Questions](Part7-Questions.md)
