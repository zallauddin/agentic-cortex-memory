---
id: 90030
type: instruction
title: "Agent Self-Improvement: Learning Verification & Confidence Calibration"
confidence: 95
importance: 9
provenance: community
source_url: "https://github.com/zallauddin/agentic-cortex"
created_at: "2026-07-13"
tags: ["community", "source:research", "self-improvement", "verification", "confidence-calibration"]
synced_at: "2026-07-13T05:35:14.165Z"
---

# Learning Verification & Confidence Calibration

Agent learnings must be continuously verified against new evidence. A learning
that was correct last week may be wrong today. Confidence scores should track reality.

## Verification Triggers
- When a new observation is saved, check if it contradicts or reinforces existing learnings
- When a learning's confidence drops below 30, consider retiring it
- When a learning has been unchallenged for 30+ days with high confidence, it becomes a "rule"

## Confidence Adjustments

**Reinforcement** (new evidence supports the learning)
- Boost confidence by +5 (cap at 98)
- Record the reinforcing evidence ID
- If reinforced 5+ times, promote to "rule" status

**Contradiction** (new evidence conflicts with the learning)
- If learning is "soft" (confidence < 85): downgrade by -15
- If learning is "hardened" (confidence >= 85): flag for human review, don't auto-downgrade
- Record the contradicting evidence ID with a 'contradicts' relation

**Decay** (no verification activity for 30+ days)
- Soft learnings: confidence -= 2 per month of inactivity
- Hardened rules: no auto-decay (they've earned stability)

## Calibration Check
Periodically compare predicted confidence vs. actual outcomes:
- If high-confidence learnings (>85) frequently fail verification: the system is overconfident
- If low-confidence learnings (<50) frequently succeed: the system is underconfident
- Adjust the confidence model if calibration drifts beyond 20% error rate

## What NOT to Do
- Don't change confidence without recording the evidence (creates untraceable drift)
- Don't allow circular verification (learning A verifies learning B which verifies A)
- Don't let a single contradiction kill a well-evidenced learning — require multiple independent contradictions
