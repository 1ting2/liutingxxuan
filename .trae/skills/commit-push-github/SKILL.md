---
name: commit-push-github
description: Commit all changes in this repo and push to GitHub remote git@github.com:1ting2/liutingxxuan.git. Use when the user says commit, push, 提交到github, 同步到github, or wants to publish this project to GitHub. Do not use for pushing to Gitee or other remotes.
---

# Commit and Push to GitHub

This skill handles the full publish flow for this repo → `git@github.com:1ting2/liutingxxuan.git`.

## 1. Ensure the GitHub remote exists

Run:
```powershell
git remote -v
```

- If a remote named **github** already points to `git@github.com:1ting2/liutingxxuan.git`, keep it.
- Otherwise add it:
  ```powershell
  git remote add github git@github.com:1ting2/liutingxxuan.git
  ```
- If an existing `github` remote points elsewhere, update the URL:
  ```powershell
  git remote set-url github git@github.com:1ting2/liutingxxuan.git
  ```

Do NOT overwrite the existing `origin` (which points to Gitee) unless the user explicitly asks.

## 2. Check git identity

Before committing, verify user.name and user.email are configured. Prefer a **local** config for this repo so we do not pollute global settings:

```powershell
git config user.name
git config user.email
```

If missing, set local values:
```powershell
git config user.name "刘庭轩"
git config user.email "1625338749@qq.com"
```

## 3. Stage everything

```powershell
git add -A
```

## 4. Commit

PowerShell does NOT support bash heredoc. Use single-line `-m`:

```powershell
git commit -m "Update: $(Get-Date -Format 'yyyy-MM-dd HH:mm')"
```

If the user provided a specific message, use that instead.

## 5. Push

```powershell
git push github master
```

(Use the current branch name — `git branch --show-current` — if it is not `master`.)

## 6. Verify

Report back:
- The commit hash (`git rev-parse --short HEAD`)
- The branch pushed
- The remote URL
- Number of files changed if the commit was new

## Notes

- SSH key is already set up on this machine; no gh login step needed.
- Keep CRLF/LF warnings non-blocking — they come from the local Windows checkout.
- If `github` push fails with permission denied, surface the exact error instead of silently retrying.
