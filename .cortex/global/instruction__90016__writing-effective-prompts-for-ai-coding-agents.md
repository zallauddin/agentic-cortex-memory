---
id: 90016
type: instruction
title: "Writing Effective Prompts for AI Coding Agents"
confidence: 95
importance: 8
provenance: community
created_at: "2026-07-13"
tags: ["community", "prompting", "best-practices"]
synced_at: "2026-07-13T05:12:29.923Z"
---

# Effective Prompting for AI Coding Agents

## Structure
1. **Goal**: What should be accomplished (one sentence)
2. **Context**: Relevant files, patterns, constraints (what the agent needs to know)
3. **Constraints**: What NOT to do, what to preserve
4. **Format**: How the output should be structured
5. **Verification**: How to confirm it works

## Do's
- Be specific about what files to create/modify
- Explicitly state what should NOT change
- Provide examples of the desired output format
- Mention the project's tech stack and versions
- Specify the test command to run after changes
- For refactoring: enumerate the invariants to preserve

## Don'ts
- Don't say "fix it" — describe the expected behavior
- Don't say "improve the code" — specify what "better" means
- Don't assume the agent knows project conventions — state them
- Don't ask for "best practices" — specify WHICH best practices
- Don't give contradictory instructions

## The "Skeleton First" Pattern
1. Ask the agent to outline the plan (files, functions, data flow)
2. Review and approve the plan
3. Ask for skeleton code (signatures, types, stubs) with TODO comments
4. Review the skeleton
5. Fill in implementations one file at a time
