---
name: "model-upgrade-checklist"
description: "Checklist for upgrading between model versions"
---

# model-upgrade-checklist

Kiểm tra cần làm khi upgrade model version.

## Trigger
Trigger phrases: "upgrade model", "new model version", "change model"

## Checklist

### String Updates
Tìm và update model identifier cũ trong config, API calls, env vars, docs.

### API Diff
Kiểm tra changelog: params mới, fields removed, response format, rate limits.

### Prompt Tuning
Model mới có thể cần adjusted prompt format, tool syntax, context window size.

### Feature Check
Feature nào không còn support, feature mới nào nên dùng.

### Testing
Run full test suite. Compare output quality. Test edge cases.

### OpenClaw
Update config.yaml. Verify via session_status. Test sample queries.
