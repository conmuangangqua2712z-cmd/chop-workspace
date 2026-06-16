---
name: "ralph-iterative-loop"
description: "Self-referential iterative loop — keep working on task until completion"
---

# ralph-iterative-loop

Self-referential iterative loop: chạy 1 task liên tục, kiểm tra tiến độ, lặp lại tới khi hoàn thành.

## Trigger

Use when user wants autonomous iteration — keep working until a task is done.
Trigger phrases: "lặp tới khi xong", "auto-iterate", "loop until done", "keep iterating", "ralph loop", "tự động chạy tiếp", "iterate tự động"

## How It Works

### Loop Structure
```
1. Define task (user cung cấp hoặc rõ ràng)
2. Check current state — what's done, what's remaining
3. Do 1 unit of work
4. Verify progress
5. If NOT done → update status, repeat from step 2
6. If done → summarize, stop
```

### Key Rules
- **Mỗi lần chỉ làm 1 unit**: không làm quá nhiều, để user có thể review
- **Luôn verify**: sau mỗi iteration, kiểm tra work quality
- **Báo progress**: mỗi lần xong 1 unit, update user
- **Biết dừng**: nếu stuck >3 lần, hỏi user hướng khác
- **Git commit thường xuyên**: commit sau mỗi logical change

### Iteration Unit
Chọn unit phù hợp với task:
- File changes: 1-2 files per iteration
- Feature work: 1 component hoặc 1 function
- Bug fixing: 1 bug per iteration
- Refactoring: 1 module per iteration

### Stop Conditions
- Task complete (mọi items done)
- User gửi lệnh dừng
- Gặp blocking issue không tự giải quyết được >3 lần
- Quality check fail liên tục

## Loop Prompt Template
```
Current task: {task_description}
Progress: {done_items} / {total_items}
Current state: {git status / files changed / test results}
Next step: {specific next work unit}
Continue? (Y/n)
```
