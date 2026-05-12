# Part 5 — Collaboration

> Work through this section **with your partner**.

---

## 5.1 Partner A Pushes First

Partner A: ensure your `about-<name>.md` is committed and pushed (see [Part 4](Part4-Basic-Git-Workflow.md)).

---

## 5.2 Partner B Clones and Adds Their File

Partner B: clone the shared repository, add your own file, commit, and push.

```bash
git clone git@github.com:<org>/<your-repo-name>.git
cd <your-repo-name>
# create about-me-partnerB.md in your text editor...
git add .
git commit -m "Add about-<name> file for <Partner B Name>"
git push origin main
```

> Name your file `about-<name>.md` (not the same name as Partner A's file) to avoid a conflict at this stage.

---

## 5.3 Partner A Pulls

Partner A: pull the new commit from Partner B.

```bash
git pull origin main
git log --oneline   # you should see both commits
```

---

## 5.4 Create a Merge Conflict (intentionally)

Both partners: **without pulling first**, each edit the same line in `README.md`, then commit.

- **Partner B pushes first.**
- **Partner A tries to push second** — Git will reject it.

Partner A resolves the conflict:

```bash
git pull origin main    # this triggers the merge conflict
# open README.md — find and edit the conflict markers:
#   <<<<<<< HEAD
#   your line
#   =======
#   partner B's line
#   >>>>>>> origin/main
git add README.md
git commit -m "Resolve merge conflict in README"
git push origin main
```

Partner B then pulls the resolution:

```bash
git pull origin main
```

**Deliverable:** Both partners should have a clean `git log --oneline` that includes the merge commit.

---

[Previous: Part 4 — Basic Git Workflow](Part4-Basic-Git-Workflow.md)  
[Next: Part 6 — Git Internals](Part6-Git-Internals.md)
