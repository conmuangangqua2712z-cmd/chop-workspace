---
name: "pr-review-toolkit"
description: "6 specialized PR review agents: comments, tests, errors, types, quality, simplify"
---

# pr-review-toolkit

Bộ 6 specialized agents cho PR review: comments, tests, errors, type design, code quality, code simplification.

## Trigger

Use when the user wants comprehensive PR review with multiple aspects.
Trigger phrases: "full PR review", "comprehensive review", "review all aspects", "pr-review-toolkit"

## Review Aspects

Có thể chạy 1 hoặc nhiều aspects. Mặc định: chạy tất cả.

### 1. Comment Analyzer
- Review comments trong code: outdated, misleading, wrong, or missing
- Check: TODO/FIXME comments có còn cần không? Comment có đúng với implementation không?
- Output: list comments cần update/remove

### 2. PR Test Analyzer
- Check: PR có tests không? Coverage có đủ không?
- Edge cases có được test không?
- Test structure có match existing patterns không?
- Output: test gaps và suggestions

### 3. Silent Failure Hunter
- Tìm lỗi silent: promise không catch, error bị swallow, fallback không hoạt động
- Network calls không handle failure
- Async operations không có timeout
- Output: potential silent failures + fix

### 4. Type Design Analyzer
- Types có quá loose không (any, unknown thay vì union)?
- Type exports có đủ không?
- Generics có over-engineered không?
- Output: type improvements

### 5. Code Reviewer
- Code quality: duplication, complexity, naming
- Project convention adherence
- Architecture consistency
- Output: quality issues prioritized

### 6. Code Simplifier
- Tìm code phức tạp không cần thiết
- Nested conditionals, long functions, redundant abstractions
- Output: simplified alternatives

## Workflow

1. User chọn aspects (hoặc mặc định all)
2. Spawn agents song song cho từng aspect
3. Collect results, deduplicate
4. Prioritize: Critical > Important > Nice-to-have
5. Present summary với recommendations
6. Post inline comments nếu yêu cầu
