---
id: 90034
type: instruction
title: "Cursor Rules Best Practices: .mdc Format, Types, and Composition"
confidence: 95
importance: 9
provenance: community
source_url: "https://docs.cursor.com/context/rules-for-ai"
created_at: "2026-07-13"
tags: ["community", "source:cursor", "rules", "cursorrules", "configuration"]
synced_at: "2026-07-13T17:25:11.404Z"
---

# Cursor Rules System: Best Practices for Agent Instructions

From Cursor's official documentation. These patterns apply to any rule-based
agent configuration system (Cursor, Claude Code, OpenCode, Copilot).

## Rule File Format (.mdc)
- Use Markdown Control (.mdc) files in `.cursor/rules/` directory
- Each file has YAML frontmatter (metadata) and Markdown content (the rules)
- Frontmatter fields: `alwaysApply`, `description`, `globs`

## Rule Application Types

**1. Always Apply (`alwaysApply: true`)**
- Included in every chat session and every request
- Use for: coding standards, security rules, project conventions
- Limit these to essentials — too many always-applied rules dilute context

**2. Apply Intelligently (with `description`)**
- Agent decides relevance based on the description metadata
- Use for: domain-specific rules, technology-specific patterns
- Example: `description: "Rules for React component patterns and hooks usage"`

**3. Apply to Specific Files (with `globs`)**
- Rule activates only when editing files matching the glob pattern
- Use for: file-type conventions, test patterns, config patterns
- Example: `globs: ["**/*.test.ts", "**/*.spec.ts"]` for test-specific rules

**4. Apply Manually (via @mention)**
- Invoked explicitly by the user with `@RuleName` in chat
- Use for: templates, boilerplate generators, rarely-needed workflows

## Composition Best Practices
- **Keep rules focused**: Each rule file should address ONE concern (under 500 lines)
- **Compose, don't monolith**: Use multiple small, focused rules rather than one huge file
- **Point to examples**: Reference canonical code examples rather than copying code into rules
- **Use AGENTS.md for flat instructions**: Project-root AGENTS.md for simple, flat rules that don't need frontmatter metadata
- **Nested AGENTS.md override parents**: Rules in subdirectories take precedence over parent directories

## What Makes a Good Rule
- Specific enough to be actionable ("Use Zod for validation" not "Write good code")
- Scoped to relevant files via `globs` when possible
- Updated when conventions change (rules rot faster than code)
- Reviewed periodically: unused rules should be removed
