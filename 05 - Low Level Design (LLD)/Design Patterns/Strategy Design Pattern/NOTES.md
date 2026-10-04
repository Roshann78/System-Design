# Strategy Design Pattern — Study Notes

## 1. The Problem: Inheritance Explosion

Suppose we have a `Robot` with different behaviors:

* `Talkable` → `talk()`
* `Walkable` → `walk()`
* `Flyable` → `fly()`

Initially, inheritance looks convenient:

```text
Robot
 ├── Talkable
 │    ├── NormalTalk
 │    └── NonTalk
 │
 ├── Walkable
 │    ├── NormalWalk
 │    └── NonWalk
 │
 └── Flyable
      ├── NormalFly
      └── NonFly
```

But the problem appears when we create actual robot types.

For example:

```text
Normal Robot      → talks + walks + doesn't fly
Companion Robot   → talks + walks + flies
Worker Robot      → doesn't talk + walks + doesn't fly
...
```

### The problem

If behavior is handled using inheritance, every **combination of behaviors** may require a separate subclass.

As the number of behaviors and variations increases, the class hierarchy becomes very large and difficult to maintain.

### Example

If we have:

* 2 types of talking
* 2 types of walking
* 2 types of flying

Then potentially:

```text
2 × 2 × 2 = 8 combinations
```

With more behaviors, combinations grow rapidly.

This is commonly called **inheritance explosion** / **class explosion**.

---

## 2. The Core Problem

The real issue is:

> **Behavior is tightly coupled to the class hierarchy.**

If a behavior changes, we may need to:

* create a new subclass,
* modify the hierarchy,
* or duplicate behavior across classes.

For example:

```cpp
class NormalRobot : public Robot { ... };
class FlyingRobot : public Robot { ... };
class TalkingFlyingRobot : public Robot { ... };
class NonTalkingFlyingRobot : public Robot { ... };
```

This does not scale well.

---

## 3. The Key Idea Behind Strategy Pattern

Instead of inheriting behavior:

> **Take the behavior out of the main class and represent it as a separate object.**

Then the main class **has** behaviors rather than **is** a behavior.

### Before

```text
Robot
   ↓
Inheritance
   ↓
Different Robot subclasses
```

### After

```text
             ┌──────────────┐
             │    Robot     │
             └──────┬───────┘
                    │
       ┌────────────┼────────────┐
       ↓            ↓            ↓
   Talkable      Walkable      Flyable
       │            │            │
       ↓            ↓            ↓
   Strategy      Strategy      Strategy
```

The `Robot` delegates the actual behavior to these strategy objects.

---

## 4. Definition

> **Strategy Pattern defines a family of algorithms/behaviors, encapsulates each one separately, and makes them interchangeable at runtime.**

The important parts are:

### 1. Family of behaviors

Example:

```text
Talk
├── NormalTalk
└── NonTalk
```

```text
Walk
├── NormalWalk
└── NonWalk
```

```text
Fly
├── NormalFly
└── NonFly
```

### 2. Encapsulate separately

Each behavior gets its own class.

```cpp
class Talkable {
public:
    virtual void talk() = 0;
};
```

```cpp
class NormalTalk : public Talkable {
public:
    void talk() override {
        // normal talking
    }
};
```

```cpp
class NonTalk : public Talkable {
public:
    void talk() override {
        // cannot talk
    }
};
```

---

## 5. Composition Instead of Inheritance

This is the major design shift.

### Inheritance approach

```text
Robot
  ↓
Robot subclass
  ↓
More subclasses
  ↓
More combinations
```

### Strategy approach

```text
Robot
 ├── has a Talkable
 ├── has a Walkable
 └── has a Flyable
```

So:

> **Inheritance → "is-a" relationship**
> **Composition → "has-a" relationship**

Here:

```cpp
class Robot {
    Talkable* talkBehavior;
    Walkable* walkBehavior;
    Flyable* flyBehavior;
};
```

The robot **has** behaviors.

---

## 6. Strategy Structure

There are usually **3 important parts**.

### 1. Strategy Interface

Defines the common behavior.

```cpp
class Talkable {
public:
    virtual void talk() = 0;
};
```

### 2. Concrete Strategies

Different implementations of that behavior.

```cpp
class NormalTalk : public Talkable {
public:
    void talk() override {
        cout << "Talking normally";
    }
};

class NonTalk : public Talkable {
public:
    void talk() override {
        cout << "Cannot talk";
    }
};
```

### 3. Context

The class that **uses** the strategy.

Here:

```cpp
class Robot {
    Talkable* talkBehavior;

public:
    void talk() {
        talkBehavior->talk();
    }
};
```

So the `Robot` doesn't implement talking itself.

It delegates:

```text
Robot
  │
  │ talk()
  ↓
Talkable
  │
  ├── NormalTalk
  └── NonTalk
```

---

## 7. Robot Example

A cleaner implementation:

```cpp
class Talkable {
public:
    virtual void talk() = 0;
    virtual ~Talkable() {}
};
```

```cpp
class NormalTalk : public Talkable {
public:
    void talk() override {
        cout << "Talking normally\n";
    }
};

class NonTalk : public Talkable {
public:
    void talk() override {
        cout << "Cannot talk\n";
    }
};
```

Similarly:

```cpp
class Walkable {
public:
    virtual void walk() = 0;
};
```

```cpp
class NormalWalk : public Walkable {
public:
    void walk() override {
        cout << "Walking normally\n";
    }
};

class NonWalk : public Walkable {
public:
    void walk() override {
        cout << "Cannot walk\n";
    }
};
```

And:

```cpp
class Flyable {
public:
    virtual void fly() = 0;
};
```

---

## 8. Robot as the Context

```cpp
class Robot {
protected:
    Talkable* talkBehavior;
    Walkable* walkBehavior;
    Flyable* flyBehavior;

public:
    Robot(Talkable* t, Walkable* w, Flyable* f)
        : talkBehavior(t),
          walkBehavior(w),
          flyBehavior(f) {}

    void talk() {
        talkBehavior->talk();
    }

    void walk() {
        walkBehavior->walk();
    }

    void fly() {
        flyBehavior->fly();
    }
};
```

Now:

```cpp
Robot* r = new Robot(
    new NormalTalk(),
    new NormalWalk(),
    new NonFly()
);
```

Another robot can simply use:

```cpp
Robot* r2 = new Robot(
    new NonTalk(),
    new NormalWalk(),
    new NormalFly()
);
```

**No new Robot subclass is required.**

---

## 9. The Main Benefit

Without Strategy:

```text
Behavior combination
        ↓
New subclass
        ↓
More inheritance
        ↓
Class explosion
```

With Strategy:

```text
Behavior combination
        ↓
Choose appropriate strategies
        ↓
Compose them into object
```

So behavior can be **changed independently**.

---

## 10. Runtime Change

One major advantage of Strategy is that the behavior can potentially be changed **at runtime**.

For example:

```cpp
robot.setTalkBehavior(new NormalTalk());
```

Later:

```cpp
robot.setTalkBehavior(new NonTalk());
```

The `Robot` itself doesn't change.

Only its strategy changes.

This is why the definition says:

> **"They can be changed at runtime."**

---

## 11. Why Strategy Solves the Original Problem

### Original design

```text
Robot
 ├── NormalRobot
 ├── FlyingRobot
 ├── TalkingRobot
 ├── TalkingFlyingRobot
 ├── NonTalkingFlyingRobot
 └── ...
```

The class hierarchy tries to represent **every possible combination**.

### Strategy design

```text
                 Robot
            /       |       \
           ↓        ↓        ↓
       Talkable  Walkable  Flyable
          ↓         ↓         ↓
       Normal     Normal     Normal
       Non        Non        Non
```

Each dimension of behavior is independent.

Therefore:

> **Adding a new way of talking does not require creating new classes for every possible walking/flying combination.**

---

## 12. Important Design Principle

Strategy is an example of:

> **Composition over inheritance**

Instead of saying:

```text
"Robot IS a NormalTalkRobot"
```

we say:

```text
"Robot HAS a TalkBehavior"
```

And that behavior can be:

```text
NormalTalk
NonTalk
FutureTalkBehavior
...
```

---

## 13. When to Use Strategy

Use Strategy when:

* You have **multiple ways of performing the same behavior**.
* Behavior can vary independently from the main class.
* You see many subclasses differing mainly in behavior.
* You want to avoid a growing inheritance hierarchy.
* You want to change behavior dynamically.
* You want to add new behaviors without modifying the main class heavily.

### Typical examples

```text
Payment
 ├── CreditCardPayment
 ├── UpiPayment
 └── PayPalPayment
```

```text
Sorting
 ├── QuickSort
 ├── MergeSort
 └── HeapSort
```

```text
Navigation
 ├── CarRoute
 ├── WalkingRoute
 └── BikeRoute
```

```text
Compression
 ├── ZipCompression
 ├── GzipCompression
 └── RarCompression
```

---

## 14. Strategy Pattern — Interview Summary

### Problem

> Too many subclasses are created because different classes need different combinations of behaviors.

### Solution

> Extract each varying behavior into its own strategy class and compose those strategies with the main class.

### Structure

```text
Context
   │
   ├── Strategy A
   ├── Strategy B
   └── Strategy C

Strategy
   ├── ConcreteStrategy1
   ├── ConcreteStrategy2
   └── ...
```

### Key principle

> **Encapsulate what varies.**

### Main advantage

> **Behavior varies independently of the object using it.**

### Relationship

```text
Inheritance  → IS-A
Composition  → HAS-A
```

### One-line memory trick

> **"Don't create a new class for every behavior combination; extract behaviors into strategies and compose them."**

---

## Strategy Pattern in one picture

```text
              ┌──────────────┐
              │    Robot     │
              │   (Context)  │
              └──────┬───────┘
                     │
        ┌────────────┼────────────┐
        │            │            │
        ↓            ↓            ↓
   Talkable       Walkable      Flyable
   Strategy       Strategy      Strategy
        │            │            │
    ┌───┴───┐    ┌───┴───┐    ┌───┴───┐
    ↓       ↓    ↓       ↓    ↓       ↓
 Normal    Non Normal   Non Normal   Non
 Talk      Talk Walk    Walk Fly     Fly
```

**Core takeaway:**
The problem isn't that inheritance itself is bad. The problem is using inheritance to represent **independent, changing behaviors**. Strategy separates those behaviors so they can be combined freely.
