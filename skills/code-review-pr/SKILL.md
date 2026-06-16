---
name: "code-review-pr"
description: "Multi-agent PR review with confidence scoring, parallel review, validation, inline comments"
---

# code-review-pr

Multi-agent automated code review cho pull requests, với specialized agents và confidence-based filtering.

## Trigger

Use when asked to review a pull request, PR, code changes.
Trigger phrases: "review PR", "review pull request", "review hộ", "review changes", "code review PR", "rà soát code"

## Workflow

### Step 1: Pre-check (Haiku-level, nhanh)
Kiểm tra xem PR có cần review không:
- PR closed? → skip
- PR draft? → skip  
- Đã có review từ Claude trước? → skip (check `gh pr view <PR> --comments`)

### Step 2: Context Gathering
- Lấy CLAUDE.md files (hoặc file hướng dẫn project) relevant
- Dùng 1 sonnet agent để summary PR changes

### Step 3: Parallel Review (4 agents)
Spawn 4 agents song song:

**Agent 1+2**: CLAUDE.md compliance (sonnet)
- Audit changes cho CLAUDE.md compliance
- Chỉ consider CLAUDE.md files cùng path hoặc parent

**Agent 3**: Bug detection (focus on diff)
- Scan obvious bugs trong diff
- Không cần đọc context ngoài diff
- Chỉ flag significant bugs

**Agent 4**: Security/Logic issues (focus on new code)
- Security issues, incorrect logic trong introduced code
- Chỉ look tại changed code

### Step 4: Validation
Với mỗi issue từ agents 3+4, spawn validation sub-agents:
- Bugs/logic → dùng sonnet-level để validate
- CLAUDE.md violations → verify rule scope và actual violation

### Step 5: Filter
Chỉ keep issues validated ở Step 4.

### Step 6: Output
- Nếu có issues → list với description
- Nếu không → "No issues found"

### Step 7: Inline Comments (optional)
Nếu PR có `--comment` flag + có issues:
- Tạo inline comments qua GitHub API
- Mỗi issue 1 comment, kèm suggestion block nếu fix nhỏ
- Không duplicate comments

## Review Guidelines (for sub-agents)

**HIGH SIGNAL ONLY** — flag issues where:
- Code fail compile/parse (syntax, type, missing imports)
- Code definitely produces wrong results
- Clear CLAUDE.md violations (quote exact rule)

**DO NOT flag:**
- Code style/quality concerns
- Potential issues phụ thuộc specific inputs
- Subjective suggestions
- Pre-existing issues
- Pedantic nitpicks senior engineer wouldn't flag

**Confidence scoring:**
- 0-50: Don't report
- 50-80: Maybe, check again
- 80+: Report with evidence
- 100: Absolutely certain
