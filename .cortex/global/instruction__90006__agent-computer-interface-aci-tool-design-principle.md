---
id: 90006
type: instruction
title: "Agent-Computer Interface (ACI): Tool Design Principles"
confidence: 95
importance: 8
provenance: community
source_url: "https://www.anthropic.com/engineering/writing-tools-for-agents"
created_at: "2026-07-13"
tags: ["community", "source:anthropic", "tool-design", "aci"]
synced_at: "2026-07-13T05:12:29.919Z"
---

# Agent-Computer Interface Design

From Anthropic's guide on writing effective tools. Treat tools as carefully designed interfaces — as important as your prompts.

## Core Principles

**1. Design for Ergonomics**
- Test tools against realistic, complex real-world tasks, not toy examples
- Example: instead of testing "Search logs", test "Find all logs related to this customer error"

**2. Context Efficiency**
- LLM context space is limited and expensive
- Return high-signal, relevant data — never dump raw bulk content
- Use pagination, filtering, and range selection
- Offer `ResponseFormat` options (concise vs detailed)

**3. Clear Namespacing**
- Use prefixes to prevent confusion when similar tools exist: `jira_search`, `github_search`
- Group related tools logically

**4. Use Meaningful Identifiers**
- Replace cryptic UUIDs with semantic, natural-language identifiers
- LLMs hallucinate less with meaningful names

**5. Prompt-Engineer Tool Specs**
- Document tools like you would for a junior developer
- Include: purpose, parameters (with types), return format, edge cases, examples
- Define boundaries clearly: what this tool CAN and CANNOT do

**6. Poka-Yoke (Error-Proofing)**
- Design tool arguments so it's harder to make mistakes than to get it right
- Require absolute paths if relative paths cause ambiguity
- Validate inputs before executing
