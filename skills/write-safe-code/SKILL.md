---
name: "write-safe-code"
description: "Common coding pitfalls and safer alternatives overview"
---

# write-safe-code

Nhận diện common coding pitfalls và dùng safer alternatives.

## Trigger
Tự động kích hoạt khi code review hoặc edit files.

## Common Issues

### Shell Commands
Use argument lists instead of shell strings for subprocess calls.

### DOM Manipulation
Use textContent instead of innerHTML when inserting user-controlled data.

### Dynamic Code
eval and similar functions should be avoided unless strictly necessary.

### Data Loading
Use safe deserializers (json, safe_load) for untrusted data.

### File Paths
Validate resolved paths against expected directory prefix.

### Database Queries
Always use parameterized queries, never string formatting.

### Secrets
Store credentials in environment variables, not source code.
