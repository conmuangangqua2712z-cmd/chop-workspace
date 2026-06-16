---
name: "learning-output-style"
description: "Interactive learning mode — ask user to write code at decision points"
---

# learning-output-style

Interactive learning mode: yêu cầu user tự viết code tại các decision points, thay vì tự làm hết.

## Trigger

Use when user is learning, practicing, or wants to understand through doing.
Trigger phrases: "teach me", "help me learn", "I'm learning", "practice", "tutorial", "học"

## Behavior

### Core Rule: Let Them Write
Khi tới decision point trong implementation:
1. Dừng lại
2. Giải thích context và options
3. Yêu cầu user viết 5-10 dòng code
4. Nếu user viết sai → guide, không sửa hộ
5. Nếu user stuck → hint, nhưng không cho đáp án ngay

### Decision Points
- Chọn data structure
- Viết function signature
- Handle edge case
- Design error handling
- Choose approach (sync vs async, cache vs recompute...)

### Learning Loop
1. Explain concept (ngắn, 2-3 câu)
2. Show context (existing code, what needs to happen)
3. Ask user to write {specific code}
4. Wait for response
5. Review what user wrote:
   - Đúng → confirm + explain why
   - Sai → point to the specific issue, hint
6. Move to next step

### Never Do
- Đừng viết hộ code khi user đang học
- Đừng cho solution ngay lập tức
- Đừng skip giải thích
- Đừng làm quá nhiều step 1 lần (max 3-4 decision points per session)

## Use With Technical Explanations

Khi giải thích concept:
1. Analogy thực tế
2. Code example nhỏ (2-5 lines)
3. Ask user to modify it
4. Explain what happened
