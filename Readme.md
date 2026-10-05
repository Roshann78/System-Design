# 📐 System Design

A structured, self-study repository covering **System Design** from the ground up — starting with core programming paradigms, through design principles and patterns, all the way to high-level distributed system architecture.

> *"If DSA is the brain, LLD is the skeleton of your application."*

> [!IMPORTANT]
> ## 🚧 This repository is still under active development. New content is being added regularly — stay tuned!

---

## 📚 Table of Contents

| # | Module | Key Topics |
|---|--------|------------|
| 01 | [Introduction](#01---introduction) | What is LLD, DSA vs LLD vs HLD, Core principles |
| 02 | [OOPS](#02---oops) | Abstraction, Encapsulation, Polymorphism (Static & Dynamic) |
| 03 | [SOLID Principles](#03---solid-principles) | SRP, OCP, LSP, ISP, DIP |
| 04 | [UML Diagrams](#04---uml-diagrams) | Class Diagrams, Sequence Diagrams, Relationships |
| 05 | [High Level Design (HLD)](#05---high-level-design-hld) | Servers, Scaling, Databases, Caching, CDNs, Kafka |
| 06 | [Low Level Design (LLD)](#06---low-level-design-lld) | Design Patterns (Strategy, Factory) |

---

## 01 - Introduction

> Foundations of Low-Level Design — what it is, why it matters, and how it differs from DSA and HLD.

| File | Description |
|------|-------------|
| [Intro.md](01%20-%20Introduction/Intro.md) | LLD definition, DSA vs LLD comparison, core principles (Scalability, Maintainability, Reusability) |

**Key Takeaways:**
- **DSA** solves isolated algorithmic problems
- **LLD** defines the structure, entities, and interactions
- **HLD** defines overall system architecture & tech stack

---

## 02 - OOPS

> Object-Oriented Programming concepts with C++ code examples.

| File | Description |
|------|-------------|
| [OOPs1.md](02%20-%20OOPS/OOPs1.md) | Abstraction & Encapsulation — theory, real-world analogies, code |
| [OOPs2.md](02%20-%20OOPS/OOPs2.md) | Additional OOP notes |
| [Abstraction.cpp](02%20-%20OOPS/Abstraction.cpp) | Abstract classes & pure virtual functions |
| [Encapsulation.cpp](02%20-%20OOPS/Encapsulation.cpp) | Access modifiers, getters/setters |
| [StaticPolymorphism.cpp](02%20-%20OOPS/StaticPolymorphism.cpp) | Function & operator overloading |
| [DynamicPolymorphism.cpp](02%20-%20OOPS/DynamicPolymorphism.cpp) | Virtual functions, runtime dispatch |
| [All4OOPs.cpp](02%20-%20OOPS/All4OOPs.cpp) | Combined example of all four OOP pillars |

**Four Pillars:** Abstraction · Encapsulation · Inheritance · Polymorphism

---

## 03 - SOLID Principles

> The five design principles that make object-oriented code flexible, maintainable, and scalable.

| File | Description |
|------|-------------|
| [NOTES.md](03%20-%20SOLID%20PRINCIPLES/NOTES.md) | Comprehensive notes with bad-design → better-design examples for each principle |

| Principle | One-liner |
|-----------|-----------|
| **S** — Single Responsibility | One class, one reason to change |
| **O** — Open/Closed | Extend behavior without editing existing code |
| **L** — Liskov Substitution | Subtypes must honor the parent's contract |
| **I** — Interface Segregation | Don't force clients to depend on things they don't use |
| **D** — Dependency Inversion | Depend on abstractions, not concretions |

---

## 04 - UML Diagrams

> Visual modeling of software structure and behavior using Unified Modeling Language.

| File | Description |
|------|-------------|
| [NOTES..md](04%20-%20UMLdiagrams/NOTES..md) | Class diagrams, sequence diagrams, relationships (Association, Aggregation, Composition, Inheritance) |
| [UMLdiagramsnotes.pdf](04%20-%20UMLdiagrams/UMLdiagramsnotes.pdf) | Detailed reference (PDF) |

**Diagram Types Covered:**
- **Static** → Class Diagrams (structure)
- **Dynamic** → Sequence Diagrams (behavior over time)

---

## 05 - High Level Design (HLD)

> Distributed systems architecture — from single servers to planet-scale systems.

| # | File | Topics |
|---|------|--------|
| 01 | [Introduction, Servers, Deployment & Metrics](05%20-%20High%20Level%20Design%20(HLD)/01%20-%20Introduction,%20Servers,%20Deployment%20%26%20Metrics.md) | Client-Server, Deployment, Latency & Throughput |
| 02 | [Scaling & Back-of-the-Envelope Estimation](05%20-%20High%20Level%20Design%20(HLD)/02%20-%20Scaling%20%26%20Back-of-the-Envelope%20Estimation.md) | Vertical vs Horizontal Scaling, Estimation techniques |
| 03 | [Databases, Replication, Sharding & CAP Theorem](05%20-%20High%20Level%20Design%20(HLD)/03%20-%20Databases,%20Replication,%20Sharding%20%26%20CAP%20Theorem.md) | SQL vs NoSQL, Replication, Sharding, CAP |
| 04 | [Monolithic vs Microservices Architecture](05%20-%20High%20Level%20Design%20(HLD)/04%20-%20Monolithic%20vs%20Microservices%20Architecture.md) | Monolith, Microservices, trade-offs |
| 05 | [Caching Strategies & Redis Deep Dive](05%20-%20High%20Level%20Design%20(HLD)/05%20-%20Caching%20Strategies%20%26%20Redis%20Deep%20Dive.md) | Caching patterns, Redis |
| 06 | [Blob Storage, CDNs & Message Brokers](05%20-%20High%20Level%20Design%20(HLD)/06%20-%20Blob%20Storage,%20CDNs%20%26%20Message%20Brokers.md) | Object storage, CDNs, Message Queues |
| 07 | [Event-Driven Architecture, Kafka & Real-Time Pub-Sub](05%20-%20High%20Level%20Design%20(HLD)/07%20-%20Event-Driven%20Architecture,%20Kafka%20%26%20Real-Time%20Pub-Sub.md) | EDA, Kafka, Pub/Sub |

---

## 06 - Low Level Design (LLD)

> Design patterns and fundamentals for building well-structured, maintainable code.

### Design Patterns

| Pattern | Files | Description |
|---------|-------|-------------|
| Strategy | [NOTES.md](06%20-%20Low%20Level%20Design%20(LLD)/Design%20Patterns/Strategy%20Design%20Pattern/NOTES.md), [Example.cpp](06%20-%20Low%20Level%20Design%20(LLD)/Design%20Patterns/Strategy%20Design%20Pattern/Examlpe.cpp) | Encapsulate interchangeable behaviors, avoid inheritance explosion |
| Factory | *Coming soon* | Object creation without exposing instantiation logic |

### Fundamentals

> *Section in progress*

---

## 🗺️ Learning Path

```
Introduction → OOP Basics → SOLID Principles → UML Diagrams → HLD → LLD (Design Patterns)
```

1. **Start with the basics** — understand what LLD/HLD are and why they matter
2. **Master OOP** — the foundation of all design
3. **Learn SOLID** — principles that guide good design decisions
4. **Read UML** — the language of software blueprints
5. **Dive into HLD** — architect distributed systems at scale
6. **Practice LLD** — apply design patterns to real problems

---

## 🛠️ Tech Stack Used

- **Language:** C++ (code examples)
- **Diagrams:** UML (Class & Sequence diagrams)
- **Notes:** Markdown

---

## 📝 License

This repository is for personal learning and reference purposes.
