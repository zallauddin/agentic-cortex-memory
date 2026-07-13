---
id: 90012
type: instruction
title: "SOLID Principles for AI Coding Agents"
confidence: 95
importance: 8
provenance: community
source_url: "https://github.com/ciembor/agent-rules-books"
created_at: "2026-07-13"
tags: ["community", "source:agent-rules-books", "solid", "principles"]
synced_at: "2026-07-13T05:12:29.921Z"
---

# SOLID Principles

## S — Single Responsibility Principle
- A class/module should have only ONE reason to change
- If you can think of more than one motivation for changing a class, it has too many responsibilities
- Ask: "What does this class DO?" — if the answer uses "and", split it

## O — Open/Closed Principle
- Software entities should be open for extension but closed for modification
- Add new behavior by adding new code, not by changing existing code
- Achieve through: interfaces, abstract classes, strategy pattern, plugin architecture
- If you're modifying a stable class to add a variant, you're violating OCP

## L — Liskov Substitution Principle
- Subtypes must be substitutable for their base types without altering correctness
- A derived class should not strengthen preconditions or weaken postconditions
- If code checks `instanceof` on a base class to handle subtypes differently, LSP is violated
- Ask: "Can I use this subclass anywhere the parent is expected without surprise?"

## I — Interface Segregation Principle
- No client should be forced to depend on methods it does not use
- Prefer many small, focused interfaces over one fat interface
- If an implementing class throws `NotImplementedError`, the interface is too broad

## D — Dependency Inversion Principle
- Depend on abstractions, not on concretions
- High-level modules should not depend on low-level modules; both should depend on abstractions
- Use dependency injection — never instantiate dependencies internally with `new`
- This is what makes code testable
