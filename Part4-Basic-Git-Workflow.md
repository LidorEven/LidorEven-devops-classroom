# Part 4 — Basic Git Workflow

Both partners should complete the steps in this section **independently on their own machine**, then collaborate in Part 5.

---

## 4.1 Add a File

Create a file named `about-<name>.md` and write 3–5 sentences about yourself:

```bash
# create the file in your text editor, then:
git status          # shows the file as "untracked"
git add about-<name>.md
git status          # now shows the file as "staged"
```

---

## 4.3 Commit the File

```bash
git commit -m "Add about-<name> file for <Your Name>"
git log --oneline   # verify the commit appears
```

---

## 4.4 Push to GitHub

```bash
git push origin main
```

Refresh your repository page on GitHub — your file should now be visible there.

---

## 4.5 Pull Changes

After your partner pushes their file (Part 5), update your local copy:

```bash
git pull origin main
git log --oneline   # both commits should now appear
```

---

[Previous: Part 3 — Clone the Repository](Part3-Clone-Repository.md)  
[Next: Part 5 — Collaboration](Part5-Collaboration.md)