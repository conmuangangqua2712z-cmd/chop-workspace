---
name: "hookify-patterns"
description: "Create custom behavior rules by analyzing conversation patterns and user instructions"
---

# hookify-patterns

Tạo custom behavior rules từ conversation patterns — detect và prevent unwanted behaviors.

## Trigger

Use when user wants to enforce rules, prevent certain behaviors, or analyze conversation patterns for issues.
Trigger phrases: "enforce rule", "prevent behavior", "stop doing X", "always do Y", "đặt luật", "create hook", "hookify"

## How Hookify Works (OpenClaw Edition)

Claude Code hooks (PreToolUse, PostToolUse) không available trong OpenClaw, nhưng ta có thể làm tương tự qua:

### Method 1: SKILL.md Rules
Thêm instructions vào SKILL.md để model tự enforce:
```markdown
## Rules
- NEVER run `rm -rf` without user confirmation
- ALWAYS ask before modifying config files
- When editing package.json, verify syntax before saving
```

### Method 2: Workspace Instructions
Viết vào AGENTS.md hoặc workspace guidelines:
```
## Enforced Rules (from hookify analysis)
{list of rules based on pattern analysis}
```

### Method 3: Session Start Reminder
Dùng cron job để nhắc nhở:
- Schedule: mỗi session start hoặc heartbeat
- Prompt: "Remind yourself of these workspace rules: {rules}"

## Pattern Analysis Workflow

Khi user phát hiện vấn đề lặp lại:

1. **Identify pattern** — "You keep doing X when I ask for Y"
2. **Create rule** — Convert pattern thành rule rõ ràng
3. **Add to workspace** — AGENTS.md hoặc SOUL.md
4. **Test** — Xem lần sau có còn bị không
5. **Iterate** — Refine rule nếu cần

## Common Patterns

| Pattern | Rule |
|---------|------|
| Unsolicited code generation | "NEVER write code unless user explicitly asks" |
| Verbose responses | "Keep responses under 3 paragraphs unless asked for details" |
| Assuming too much | "Ask clarifying questions before implementing" |
| Modifying files without asking | "Always show diff before writing to files" |
| Wrong project context | "Read project README before suggesting architecture" |
