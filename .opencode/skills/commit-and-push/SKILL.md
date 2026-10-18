---
name: commit-and-push
description: Commit the current project and push it to the Gitee remote at https://gitee.com/liu-tingxuan2251/advanced-web-design. Use when the user asks to 提交项目, commit and push, 推送代码, upload the project, or sync this repo to Gitee.
---

# Commit and Push Project

Commit the current project and push it to the Gitee remote
`https://gitee.com/liu-tingxuan2251/advanced-web-design`.

## Target remote

- URL: `https://gitee.com/liu-tingxuan2251/advanced-web-design`
- Remote name: `origin`

## Workflow

1. Inspect the repository state:

   ```powershell
   git status
   git remote -v
   git log --oneline -5
   ```

2. Stage all project files:

   ```powershell
   git add -A
   ```

3. Commit with a concise message that matches the repo style:

   ```powershell
   git commit -m "Add project files"
   ```

4. Make sure the `origin` remote points at the Gitee URL. If `origin`
   already exists with the correct URL, skip this step:

   ```powershell
   git remote add origin https://gitee.com/liu-tingxuan2251/advanced-web-design
   ```

   If `origin` exists but points elsewhere, update it:

   ```powershell
   git remote set-url origin https://gitee.com/liu-tingxuan2251/advanced-web-design
   ```

5. Push:

   ```powershell
   git push -u origin master
   ```

## Notes

- Never force-push, amend a published commit, or push secrets.
- If the push fails due to authentication, tell the user to configure a Gitee
  credential helper or personal access token; do not embed credentials.
- If the remote branch already has commits, prefer a normal `git push` and ask
  before using `--force`.
- Run `git status` after pushing to confirm a clean working tree.
