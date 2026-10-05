# System Design

Personal notes and code covering system design end-to-end — from OOP basics to distributed systems.

> **This repo is a work in progress.** Content is being added as I learn.

---

## Contents

| # | Topic | What's inside |
|---|-------|---------------|
| 01 | [Introduction](01%20-%20Introduction/) | What is LLD, how it differs from DSA and HLD |
| 02 | [OOPS](02%20-%20OOPS/) | Abstraction, Encapsulation, Polymorphism — notes + C++ code |
| 03 | [SOLID Principles](03%20-%20SOLID%20PRINCIPLES/) | All five principles with bad vs better design examples |
| 04 | [UML Diagrams](04%20-%20UMLdiagrams/) | Class diagrams, sequence diagrams, relationships |
| 05 | [High Level Design](05%20-%20High%20Level%20Design%20(HLD)/) | Servers, scaling, databases, caching, CDNs, Kafka |
| 06 | [Low Level Design](06%20-%20Low%20Level%20Design%20(LLD)/) | Design patterns (Strategy, Factory), fundamentals |

---

### 01 - Introduction

- LLD definition and core principles (scalability, maintainability, reusability)
- DSA vs LLD vs HLD — what each one solves

### 02 - OOPS

- Abstraction, Encapsulation, Inheritance, Polymorphism
- Static polymorphism (overloading) and dynamic polymorphism (virtual functions)
- C++ implementations for each concept

### 03 - SOLID Principles

| | Principle | Idea |
|-|-----------|------|
| S | Single Responsibility | One class, one reason to change |
| O | Open/Closed | Extend behavior without editing existing code |
| L | Liskov Substitution | Subtypes must honor the parent's contract |
| I | Interface Segregation | Don't force clients to depend on things they don't use |
| D | Dependency Inversion | Depend on abstractions, not concretions |

### 04 - UML Diagrams

- Class diagrams — structure, attributes, methods, visibility
- Sequence diagrams — behavior over time
- Relationships — association, aggregation, composition, inheritance

### 05 - High Level Design (HLD)

1. Introduction, Servers, Deployment & Metrics
2. Scaling & Back-of-the-Envelope Estimation
3. Databases, Replication, Sharding & CAP Theorem
4. Monolithic vs Microservices Architecture
5. Caching Strategies & Redis Deep Dive
6. Blob Storage, CDNs & Message Brokers
7. Event-Driven Architecture, Kafka & Real-Time Pub/Sub

### 06 - Low Level Design (LLD)

- **Strategy Pattern** — encapsulate interchangeable behaviors, avoid inheritance explosion
- **Factory Pattern** — *(coming soon)*
- **Fundamentals** — *(coming soon)*

---

### Study order

```
Introduction → OOP → SOLID → UML → HLD → LLD
```
