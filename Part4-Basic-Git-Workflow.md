# Part 1 — Create a GitHub Account

> Reference: https://github.com/nirgeier/GitHub-Labs/blob/main/Labs/00-Setup/02-Setup-GitHub.md

---

## 1.1 Sign Up

1. Go to [https://github.com](https://github.com) and click **Sign up**.
2. **Use your academic email address** (e.g., `AfekaNetUser@s.afeka.ac.il`). This is required — accounts registered with personal emails will not receive full credit.
3. Choose a password and a username. Pick a professional username; it will appear on your public profile.
4. Complete the verification puzzle and confirm your email address via the link GitHub sends you.

---

## 1.2 Configure Your Profile

1. Click your avatar (top-right) → **Your profile** → **Edit profile**.
2. Add your **full name**, a short **bio**, and your **location**.
3. Upload a profile picture (optional but recommended).

---

## 1.3 Create a Personal Access Token (Classic)

GitHub requires a token instead of your password when pushing from the command line.

### Step 1 — Open token settings

1. Click your avatar (top-right) → **Settings**.
2. Scroll down the left sidebar and click **Developer settings**.
3. In the left sidebar click **Personal access tokens** → **Tokens (classic)**.

### Step 2 — Generate a new token

1. Click **Generate new token** → **Generate new token (classic)**.
2. In the **Note** field write something descriptive, e.g. `DevTools course laptop`.
3. Set **Expiration** to at least the end of the semester (e.g. 90 days).

### Step 3 — Select scopes

Check the following scopes:

| Scope | Why |
| --- | --- |
| `repo` | Full access to your repositories (read, write, push) |

### Step 4 — Generate and copy the token

1. Scroll to the bottom and click **Generate token**.
2. **Copy the token immediately** — GitHub will never show it again.  
   Store it somewhere safe (e.g. a password manager).

### Step 5 — Use the token when Git asks for a password

When you run `git clone`, `git push`, or `git pull` for the first time, Git will prompt for credentials:

```text
Username:                       ← your GitHub username
Password:                       ← paste your token here (not your GitHub password)
```

### Step 6 — Save credentials so you are not prompted every time

Run the following three commands, replacing the values with your own:

```bash
git config --global user.name  "Your Full Name"
git config --global user.email "AfekaNetUser@s.afeka.ac.il"
git config --global credential.helper store
```

After entering the token once during your first `git push` or `git pull`, Git will save it and reuse it automatically.

---

## 1.4 Replacing Saved Credentials

If your token expires, is revoked, or you generate a new one, Git will start returning a **403** or **Authentication failed** error. Follow these steps to replace it.

### Step 1 — Delete the stored token

The `store` helper saves credentials in a plain-text file at `~/.git-credentials`. Remove the stale entry:

```bash
git credential reject <<EOF
protocol=https
host=github.com
EOF
```

Or delete the file entirely and let Git re-prompt on the next operation:

```bash
# Windows
del %USERPROFILE%\.git-credentials

# macOS / Linux
rm ~/.git-credentials
```

### Step 2 — Generate a new token on GitHub

Repeat [steps 1–4 of section 1.3](#13-create-a-personal-access-token-classic) to create a fresh token with the `repo` scope.

### Step 3 — Re-enter the token

Run any Git operation that contacts GitHub (e.g. `git pull`) and enter your credentials when prompted:

```text
Username:                       ← your GitHub username
Password:                       ← paste the new token
```

Git will save the new token automatically and stop prompting.

---

[Next: Part 2 — Accept the GitHub Classroom Assignment](Part2-GitHub-Classroom.md)