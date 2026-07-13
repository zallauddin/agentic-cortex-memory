---
id: 90002
type: instruction
title: "Clean Code: Comments and Formatting Rules"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-13"
tags: ["community", "source:agent-rules-books", "clean-code", "comments"]
synced_at: "2026-07-13T05:12:29.917Z"
---

# Clean Code Comments & Formatting

## Comments
- The proper use of comments is to compensate for our failure to express intent in code
- Comments lie — code changes, comments don't always follow
- **Never write a comment that restates what the code does** — that's noise
- Comments should explain the WHY, not the WHAT or HOW
- TODO comments are acceptable only if tracked in an issue tracker

## Good Comments
- Legal comments (copyright, license)
- Informative comments (regex explanation, complex algorithm reference)
- Warning of consequences (e.g., "// This trim is load-bearing: removing it breaks IE11")
- Amplification of importance

## Bad Comments (Avoid)
- Redundant/restating comments
- Journal comments (use git history instead)
- Position markers (// End of loop, // Constructor, etc.)
- Closing-brace comments
- Commented-out code (delete it — it lives in git history)
- HTML in comments (use documentation generators)

## Formatting
- Consistent formatting across the codebase is non-negotiable
- Vertical density: related concepts should be vertically close
- Vertical ordering: dependent functions should be close; callers above callees
- Horizontal alignment: maximum 80-120 characters per line
- Use the team's formatter consistently (prettier, black, gofmt, etc.)
