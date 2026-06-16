---
name: "feature-dev-workflow"
description: "7-phase feature dev workflow: discover, explore, clarify, architect, implement, review, wrap"
---

# feature-dev-workflow

Một quy trình phát triển tính năng có cấu trúc 7 phase, codebase exploration, architecture design, và quality review.

## Trigger

Use this skill when the user asks to implement a new feature, add functionality, build something new. 
Trigger phrases: "implement feature", "phát triển tính năng", "build this feature", "làm tính năng", "feature mới", "implement X"

===
Không trigger khi: chỉ hỏi về feature đơn giản (< 30 phút làm), fix bug đơn giản, hoặc config thông thường.

## Workflow

Follow this 7-phase process in order. Each phase must complete before the next.

### Phase 1: Discovery
- Tạo todo list với tất cả phases
- Nếu feature chưa rõ, hỏi user: vấn đề gì? yêu cầu? constraints?
- Summarize và confirm

### Phase 2: Codebase Exploration
- Spawn 2-3 sub-agents để explore codebase song song
- Mỗi agent focus vào 1 aspect khác nhau (similar features, architecture, UX)
- Yêu cầu agents trả về danh sách 5-10 files quan trọng
- Đọc tất cả files đó để build context

### Phase 3: Clarifying Questions
- Identify underspecified aspects: edge cases, error handling, integration points
- Present questions to user và WAIT cho answers trước khi design

### Phase 4: Architecture Design
- Spawn 2-3 sub-agents với focuses khác nhau (minimal changes, clean architecture, pragmatic)
- Review approaches, recommend cái phù hợp nhất
- Hỏi user chọn approach nào

### Phase 5: Implementation
- Chờ user approval
- Đọc relevant files
- Implement theo architecture đã chọn
- Follow codebase conventions

### Phase 6: Quality Review
- Spawn 3 reviewer agents song song (simplicity, bugs, conventions)
- Present findings, hỏi user fix gì

### Phase 7: Summary
- Mark todos complete
- Summarize: what was built, key decisions, files modified, next steps

## Agent Templates

### code-explorer agent prompt
```
You are an expert code analyst. Analyze {target_feature/area} comprehensively:
1. Find entry points (APIs, UI, CLI)
2. Trace call chains and data flow
3. Map architecture layers
4. Identify patterns and dependencies
Return: file:line references, execution flow, key components, essential files to read.
```

### code-architect agent prompt
```
You are a senior architect. Design architecture for {feature}:
1. Extract existing patterns from {file_list}
2. Make decisive architecture choices
3. Specify every file to create/modify
4. Design data flow and integration
Return: complete implementation blueprint with file paths, component design, build sequence.
```

### code-reviewer agent prompt
```
Review the implementation for {focus_area}:
- Confidence scoring: only report issues with confidence >= 80
- Check: {bugs / simplicity / conventions / security}
- Include file:line references and concrete fix suggestions
```
