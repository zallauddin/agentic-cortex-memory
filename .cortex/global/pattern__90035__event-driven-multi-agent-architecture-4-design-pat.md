---
id: 90035
type: pattern
title: "Event-Driven Multi-Agent Architecture: 4 Design Patterns"
confidence: 95
importance: 8
provenance: community
source_url: "https://www.confluent.io/blog/event-driven-multi-agent-systems/"
created_at: "2026-07-13"
tags: ["community", "source:confluent", "multi-agent", "event-driven", "architecture", "kafka"]
synced_at: "2026-07-13T17:25:11.405Z"
---

# Event-Driven Multi-Agent Design Patterns

From Confluent's engineering guide on scaling multi-agent systems. These patterns
use event-streaming (Kafka-like) to coordinate agents at production scale.

## 1. Orchestrator-Worker
A central orchestrator agent assigns tasks to a pool of worker agents.

- **How**: Orchestrator publishes tasks to a topic. Worker consumer group
  processes tasks in parallel via key-based partitioning.
- **Use when**: Tasks are independent, the set of steps is known upfront,
  and you need uniform load distribution across workers.
- **Key detail**: Partition by task ID for ordering; use consumer groups for parallelism.

## 2. Hierarchical Agent
Recursive orchestrator-worker pattern. Non-leaf nodes manage subtrees of agents.

- **How**: A top-level agent decomposes the task into subtasks. Each subtask
  is delegated to a sub-orchestrator that further decomposes or executes.
- **Use when**: Complex problems benefit from recursive decomposition
  (e.g., "refactor entire monolith" → "refactor auth module" → "extract UserService").
- **Key detail**: Each level encapsulates complexity; leaf agents only see their slice.

## 3. Blackboard
Agents interact asynchronously by reading/writing to a shared event stream.

- **How**: Agents publish observations and partial results to a shared topic.
  Other agents consume and contribute. No direct agent-to-agent communication.
- **Use when**: Multiple agents need to contribute to a shared understanding
  without tight coupling (e.g., code analysis + security scan + style check all
  contribute findings to a shared review topic).
- **Key detail**: Eliminates brittle point-to-point connections; agents can
  join/leave without disrupting the system.

## 4. Market-Based
Agents compete or negotiate via bidding and asking topics.

- **How**: Agents publish "asks" (tasks they need done) and "bids" (offers to
  do tasks). A market-maker aggregator matches bids to asks.
- **Use when**: Tasks have varying cost/quality tradeoffs and you want decentralized
  allocation (e.g., multiple specialized agents bid on "fix this bug" based on
  their domain expertise).
- **Key detail**: Eliminates quadratic connection complexity; new agent types
  can join the market without reconfiguring existing agents.

## Universal Principles for Agent Coordination
- **Decouple via events**: Never have agent A call agent B directly.
- **Own your state**: Each agent owns its state; share facts, not state.
- **Design for failure**: Agents crash, time out, produce wrong output.
  Every pattern must handle partial failure gracefully.
- **Observability is non-negotiable**: Every agent must emit structured logs,
  metrics, and traces for debugging distributed agent systems.
