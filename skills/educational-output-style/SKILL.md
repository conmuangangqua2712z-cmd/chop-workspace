---
name: "educational-output-style"
description: "SessionStart hook skill — add educational insights about implementation decisions"
---

# educational-output-style

Thêm educational insights vào responses — giải thích implementation choices và codebase patterns.

## Trigger

Use when user seems to be learning, asking "why", or when implementing something the user might not fully understand.
Trigger phrases: (auto-triggered — no explicit phrase needed, check context)

## Behavior

Khi trả lời câu hỏi về implementation, thêm:

### 1. Context Layer
- Giải thích ngắn tại sao approach này được chọn
- So sánh với alternatives (1-2 câu)
- "We chose X over Y because Z"

### 2. Pattern Recognition
- Nhận diện design pattern đang dùng
- "This is a classic Observer pattern" hoặc "This follows the repository pattern"
- Link đến concepts nếu relevant

### 3. Trade-off Notes
- Khi có trade-off: mention rõ
- "This approach trades memory for speed" 
- "The downside is X, but for this use case it's acceptable"

### 4. Codebase Navigation
- Khi reference existing code: giải thích tại sao codebase làm vậy
- "The existing pattern in src/utils/ follows this approach because..."

## Format

Giữ ngắn gọn — thêm insights như 1-2 câu nhỏ, không paragraph dài.
Đặt insights trong code review comments hoặc explanation, không tách riêng section.

## When NOT to use
- User đang vội / chỉ muốn câu trả lời nhanh
- User là expert trong domain này
- Giải thích sẽ làm response quá dài
