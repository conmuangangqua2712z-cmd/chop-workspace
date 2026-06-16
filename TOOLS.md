# TOOLS.md — Setup của Chớp

## Máy Chủ

```
OS:       Windows 11 (build 26200)
Kernel:   NT 10.0 (x64)
Shell:    PowerShell
Node:     v24.16.0
Python:   3.14.4
pip:      11.13.0
Git:      2.54.0.windows.1
```

## GPU & CUDA

- **Dedicated:** NVIDIA GeForce RTX 4050
- **Integrated:** AMD Radeon
- **CUDA:** 12.1 — đã cài
- **WSL:** Ubuntu — đã setup

## OpenClaw

```
Instance:  gateway (local)
Model:     DeepSeek V4 Flash
Workspace: C:\Users\conmu\.openclaw\workspace\
Channel:   Telegram (paired)
Skills:    13 skills ported từ claude-code-repo
```

## Tools Available

| Tool | Có? | Notes |
|------|-----|-------|
| git | ✅ 2.54.0 | GitHub CLI (gh) chưa cài |
| python3 | ✅ 3.14.4 | |
| pip | ✅ 11.13.0 | |
| node/npm | ✅ 24.16.0 | npx available |
| docker | ❌ Chưa cài | |
| winget | ✅ Có | Windows package manager |
| pwsh | ✅ PowerShell | Shell mặc định |

## Git Repos (trong workspace)

- `claude-code-repo/` — anthropics/claude-code (đã clone, để tham khảo)

## Chưa Có — Cần Setup

- **GitHub CLI (gh)** — nếu cần tạo PR / review PR qua CLI
- **Docker** — nếu cần sandbox hoặc chạy containers
- **Email** — chưa configure email provider
- **Calendar** — chưa integrate calendar
- **TTS Voice** — chưa test/set giọng ưa thích
- **Cameras** — không rõ máy có camera không

---

_Cập nhật: 2026-06-16_
