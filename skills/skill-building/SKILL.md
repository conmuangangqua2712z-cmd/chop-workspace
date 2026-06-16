---
name: "skill-building"
description: "Guidance for building and structuring OpenClaw skills"
---

# skill-building

Toolkit for building OpenClaw skills. Use when user asks to create/edit a skill.

## Trigger
Trigger phrases: "create skill", "build skill", "skill development", "phát triển skill", "tạo skill"

## Structure

Each skill is a directory:
```
skill-name/
  SKILL.md       — core instructions, lean
  references/    — optional deep docs
  examples/      — optional working examples
  scripts/       — optional utility scripts
```

## SKILL.md Format

YAML frontmatter + markdown body:
```markdown
---
name: "skill-name"
description: "Short trigger description"
---

# Title

## Trigger
When to activate.
Trigger phrases: "keyword1", "keyword2"

## Content
Main workflow instructions...
```

## Progressive Disclosure

1. **Core SKILL.md** — lean, actionable (500-1000 words)
2. **References/** — deep dives, loaded only when needed
3. **Examples/** — working examples with explanations

## Best Practices

- Specific trigger phrases: avoid false positives
- Keep core short: max 1000 words
- Imperative style: "Do X", not "You should do X"
- Third person in body content
- Quote frontmatter description
