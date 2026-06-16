---
name: "agent-sdk-starter"
description: "Agent SDK project setup and validation best practices"
---

# agent-sdk-starter

Kit for Agent SDK projects: scaffold, validate, best practices.

## Trigger
Trigger phrases: "agent SDK", "new agent project", "validate agent"

## New Project
1. Ask: Python or TypeScript?
2. Ask: Agent type (simple chat, tool-using, multi-agent)?
3. Scaffold: src/agent.py + src/tools.py + src/config.py + tests/
4. Install anthropic SDK dependency
5. Create basic agent, verify runs

## Validation
1. Agent format correct, required fields present
2. Tools have valid input/output specs
3. Error handling covers failures gracefully
4. Tests cover main paths and edge cases
5. README explains usage

## Design Tips
- One job per agent (single responsibility)
- Short, clear system prompts
- Tool names are descriptive verbs
- Validate inputs early in tools
- Timeout external API calls
- Return structured JSON from tools
