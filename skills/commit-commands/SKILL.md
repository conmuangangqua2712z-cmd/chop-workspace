---
name: "commit-commands"
description: "Git workflow automation: commit, commit-push-PR, clean stale branches"
---

# commit-commands

Git workflow tự động: commit, commit + push + PR, và dọn branches chết.

## Trigger

Use when the user wants to commit changes, push code, create PR, clean branches.
Trigger phrases: "tạo commit", "git commit", "commit code", "commit changes", "push code", "tạo PR", "create PR", "dọn branch", "clean branches", "gone branch", "git push"

## Operations

### 1. Quick Commit
Khi user muốn commit:

1. Lấy context:
   ```
   git status
   git diff HEAD
   git branch --show-current
   git log --oneline -10
   ```

2. Stage changes và tạo commit message phù hợp
3. Dùng `git add` + `git commit -m "..."` trong 1 lần

### 2. Commit + Push + PR
Khi user muốn commit và tạo PR:

1. Nếu đang ở `main` → tạo branch mới trước
2. Stage và commit
3. Push lên origin
4. Tạo PR với `gh pr create`
5. Làm tất cả trong 1 message, không hỏi thêm

### 3. Clean Gone Branches
Khi user muốn dọn các branch đã xóa trên remote:

1. Liệt kê branches: `git branch -v`
2. Xác định worktrees: `git worktree list`
3. Xóa worktrees và branches:
   ```bash
   git branch -v | grep '\[gone\]' | sed 's/^[+* ]//' | awk '{print $1}' | while read branch; do
     worktree=$(git worktree list | grep "\\[$branch\\]" | awk '{print $1}')
     if [ ! -z "$worktree" ] && [ "$worktree" != "$(git rev-parse --show-toplevel)" ]; then
       git worktree remove --force "$worktree"
     fi
     git branch -D "$branch"
   done
   ```

## Notes
- Luôn dùng Git CLI, không dùng GitHub API cho git operations
- Commit message nên ngắn gọn, descriptive (conventional commits style)
- Cho PR: include summary of changes trong description
