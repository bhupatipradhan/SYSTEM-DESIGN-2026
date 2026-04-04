# 🗺️ Dev Mastery Roadmap: Design Patterns · LLD · HLD · System Design

> **Target Audience:** Mid-level dev aiming for senior/staff engineer mastery
> **Total Timeline:** ~9–12 months (part-time, ~1–2 hrs/day)
> **Philosophy:** Learn → Code → Apply → Refactor → Explain → Repeat

---

## 📌 Overview

| Phase | Focus | Duration |
|-------|-------|----------|
| Phase 1 | Foundations & Design Patterns | Months 1–3 |
| Phase 2 | Low-Level Design (LLD) | Months 3–5 |
| Phase 3 | High-Level Design (HLD) | Months 5–7 |
| Phase 4 | System Design (End-to-End) | Months 7–10 |
| Phase 5 | Mastery & Interview Prep | Months 10–12 |

---

## 📅 Weekly Execution Template (5 Days/Week)

> **The #1 reason people fail:** They study but never build. This template converts knowledge → skill.
> **Weekends are off.** Consistency over intensity — 5 focused days beats 7 burnt-out ones.

| Day | Activity | Time |
|-----|----------|------|
| **Monday** | Learn concept — read + watch 1 video + take raw notes | 60 min |
| **Tuesday** | Code from scratch — no copy-paste, no tutorials | 60 min |
| **Wednesday** | Apply in a mini-project or extend Tuesday's code | 60 min |
| **Thursday** | Refactor + write unit tests + find it in a real codebase | 60 min |
| **Friday** | Write explanation in your own words + answer 1 interview-style question aloud | 45 min |

> 💡 **Rule:** Never move to the next concept until you can explain the current one to a junior dev without notes.

**Example: Learning Strategy Pattern (Mon–Fri)**
```
Monday    → Read refactoring.guru/strategy + watch ByteByteGo video, note: "use when algo varies"
Tuesday   → Code PaymentStrategy with CreditCard, UPI, NetBanking from scratch
Wednesday → Plug PaymentStrategy into a full Order checkout flow
Thursday  → Write JUnit tests, refactor to use DI, find Strategy in Spring Security source
Friday    → Write: "When NOT to use Strategy" + answer: "How is Strategy different from State?"
```

---

## 💻 Language Strategy

> Pick your weapons before you start — don't switch mid-battle.

| Domain | Language | Why |
|--------|----------|-----|
| **LLD / Design Patterns** | **Java** (preferred) or Kotlin | Industry standard in interviews; strong OOP, interfaces, generics |
| **HLD / System Design** | Language-agnostic | Focus on architecture, trade-offs, not syntax |
| **Scripting / Tooling** | Python | Quick prototyping, data scripts |
| **Diagrams** | PlantUML / Draw.io | Version-controllable, clean UML |

**Setup References:**
- 🌐 [Download JDK 17+ (Adoptium)](https://adoptium.net)
- 🌐 [IntelliJ IDEA Community](https://www.jetbrains.com/idea/download/)
- 🌐 [PlantUML Online Editor](https://www.plantuml.com/plantuml/uml/)
- 🌐 [Draw.io (diagrams.net)](https://app.diagrams.net)

---

## 🧾 LLD Deliverables (For Every Problem)

> For *every* LLD problem you solve, produce all of these:

### Mandatory
- [ ] **Class Diagram (UML)** — entities, relationships, interfaces (use PlantUML)
- [ ] **Working Code** — compilable, runnable, follows SOLID
- [ ] **Design Decisions doc** — 1 paragraph: "Why did I use X pattern here?"

### Strongly Recommended
- [ ] **Sequence Diagram** — show 1 key use-case end-to-end
- [ ] **Edge Cases List** — at least 3 edge cases considered
- [ ] **Unit Tests** — at least 1 test per class/interface

### Example Deliverable Structure (Parking Lot)
```
parking-lot/
├── diagrams/
│   ├── class_diagram.puml
│   └── sequence_booking.puml
├── src/
│   ├── ParkingLot.java
│   ├── ParkingSpot.java
│   ├── Vehicle.java
│   ├── Ticket.java
│   └── PaymentStrategy.java
├── tests/
│   └── ParkingLotTest.java
└── DESIGN.md
```

---

## ⚠️ HLD Golden Rule: Always Follow This Order

> **Skipping requirements or estimation is the #1 interview killer. Full stop.**

```
Step 1: Requirements (5 min minimum)
  → Functional:     What does the system DO?
  → Non-functional: Scale, latency, availability, consistency needs?
  → Out of scope:   What are we NOT building today?

Step 2: Capacity Estimation (5 min minimum)
  → Daily Active Users (DAU)?
  → Read/write ratio?
  → QPS (queries per second)?
  → Storage per day/month/year?

Only THEN → draw your architecture.
```

**Back-of-envelope cheat sheet:**
```
1M users/day   → ~12 req/sec average, ~120 req/sec peak (10x)
1KB per record → 1GB for 1M records
1 image (1MB)  → 1TB for 1M images
Disk read → ~1ms | Network roundtrip → ~100ms | RAM → ~100ns
```

---

## ❌ Common Mistakes (What NOT To Do)

### Design Patterns — Mistakes
- ❌ **Memorizing syntax without understanding use-case** — if you can't say "I'd use this when...", you don't know it
- ❌ **Forcing patterns** — Singleton because you heard it, not because it fits
- ❌ **Over-engineering** — 3 patterns in 1 class = design smell
- ❌ **Ignoring simpler solutions** — a plain function beats a Strategy when there's only 1 algorithm
- ❌ **Skipping tests** — a pattern without a test is just theory

### LLD — Mistakes
- ❌ **God classes** — one class doing 10 things (violates SRP)
- ❌ **Ignoring edge cases** — what if the parking lot is full? payment fails?
- ❌ **Concrete dependencies** — code to interfaces, not implementations
- ❌ **No extensibility thinking** — "what if we add a new vehicle type tomorrow?"
- ❌ **Jumping to code before diagram** — class diagram first, always

### HLD — Mistakes
- ❌ **Jumping to microservices too early** — start monolith, split with evidence
- ❌ **No estimation** — "it scales" is not an answer
- ❌ **No trade-off discussion** — every choice has a cost; name it
- ❌ **Ignoring failure modes** — what when DB is down? service crashes?
- ❌ **Over-caching** — caching solves read problems, not write problems

---

## 🚀 Capstone Projects (Combine Everything)

> Do 1 per phase completion. These bridge LLD + HLD + Patterns.

### Capstone 1: Ride Booking System (After Phase 2)

| Layer | What to Build |
|-------|--------------|
| **LLD** | `Driver`, `Rider`, `Trip`, `TripState` (FSM), `PaymentStrategy` |
| **Patterns** | Strategy (pricing), Observer (notifications), State (trip FSM), Factory (vehicle types) |
| **HLD Sketch** | Matching service, WebSocket tracking, Kafka for events, Redis for locations |

### Capstone 2: Real-Time Chat System (After Phase 3)

| Layer | What to Build |
|-------|--------------|
| **LLD** | `User`, `Message`, `ChatRoom`, `GroupChat`, `NotificationObserver` |
| **Patterns** | Observer, Decorator (message types), Composite (groups), Mediator |
| **HLD** | WebSocket servers, Kafka, Cassandra, Redis presence, CDN |

### Capstone 3: Mini Netflix (After Phase 4)

| Layer | What to Build |
|-------|--------------|
| **LLD** | `Content`, `Subscription` (State), `RecommendationStrategy`, `StreamSession` |
| **Patterns** | Strategy (recommendations), Template Method (pipeline), Observer (billing) |
| **HLD** | Video ingestion, adaptive streaming, CDN, A/B testing framework |

---

## Phase 1 — Design Patterns (Months 1–3)

### 🎯 Goal
Understand the 23 classic GoF patterns and know *when* and *why* to use them — not just *how*.

---

### Week 1–2: Mindset & Fundamentals

- [ ] Read **"Head First Design Patterns"** — Chapters 1–3
- [ ] Understand SOLID principles deeply
- [ ] Composition vs inheritance
- [ ] UML basics: class diagrams, sequence diagrams

**📚 References — Fundamentals & SOLID:**

| Resource | Type | Link |
|----------|------|------|
| SOLID Principles Explained | Article | https://www.digitalocean.com/community/conceptual-articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design |
| SOLID in Java (Baeldung) | Article | https://www.baeldung.com/solid-principles |
| SOLID Principles — Uncle Bob | YouTube | https://www.youtube.com/watch?v=zHiWqnTWsn4 |
| SOLID in 8 Min | YouTube | https://www.youtube.com/watch?v=9oIXy-XDenU |
| UML Class Diagram Tutorial | Article | https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/ |
| UML Diagrams Full Guide | YouTube | https://www.youtube.com/watch?v=WnMQ8HlmeXc |
| PlantUML Docs | Docs | https://plantuml.com/class-diagram |
| Head First Design Patterns | Book | O'Reilly / Amazon |

**Exercise:** Refactor a messy class — apply SRP and OCP.

---

### Week 3–5: Creational Patterns

These control *how objects are created*.

| Pattern | When to Use | Real Example |
|---------|------------|--------------|
| **Singleton** | Single shared instance | DB connection pool, Logger |
| **Factory Method** | Subclass decides which object to create | Notification (SMS/Email/Push) |
| **Abstract Factory** | Family of related objects | UI toolkit (Windows vs Mac) |
| **Builder** | Complex object step-by-step | SQL Query builder, HTTP Request |
| **Prototype** | Clone instead of new | Game object spawning |

**📚 References — Creational Patterns:**

| Pattern | Article | YouTube |
|---------|---------|---------|
| **Singleton** | https://refactoring.guru/design-patterns/singleton | https://www.youtube.com/watch?v=hUE_j6q0LTQ |
| **Factory Method** | https://refactoring.guru/design-patterns/factory-method | https://www.youtube.com/watch?v=EcFVTgRHJLM |
| **Abstract Factory** | https://refactoring.guru/design-patterns/abstract-factory | https://www.youtube.com/watch?v=v-GiuMmsXj4 |
| **Builder** | https://refactoring.guru/design-patterns/builder | https://www.youtube.com/watch?v=MaY_MDdWkQw |
| **Prototype** | https://refactoring.guru/design-patterns/prototype | https://www.youtube.com/watch?v=DcFhITC9v0E |
| All Creational (Source Making) | https://sourcemaking.com/design_patterns/creational_patterns | https://www.youtube.com/watch?v=vNHpsC5ng_E |

**Exercise:** Build a `NotificationService` using Factory Method.

---

### Week 6–8: Structural Patterns

These control *how objects are composed*.

| Pattern | When to Use | Real Example |
|---------|------------|--------------|
| **Adapter** | Make incompatible interfaces work | Legacy API wrapper |
| **Decorator** | Add behavior dynamically | Java I/O streams, middleware |
| **Facade** | Simplify a complex subsystem | Startup orchestrator |
| **Proxy** | Control access to an object | Auth proxy, lazy loading |
| **Composite** | Tree structures | File system, UI tree |
| **Bridge** | Decouple abstraction from impl | Device + Remote |
| **Flyweight** | Share common state | Game particles |

**📚 References — Structural Patterns:**

| Pattern | Article | YouTube |
|---------|---------|---------|
| **Adapter** | https://refactoring.guru/design-patterns/adapter | https://www.youtube.com/watch?v=2PKqtcf18VM |
| **Decorator** | https://refactoring.guru/design-patterns/decorator | https://www.youtube.com/watch?v=GCraGHx6gso |
| **Facade** | https://refactoring.guru/design-patterns/facade | https://www.youtube.com/watch?v=K4FkHVO5iac |
| **Proxy** | https://refactoring.guru/design-patterns/proxy | https://www.youtube.com/watch?v=NwaabigVqmk |
| **Composite** | https://refactoring.guru/design-patterns/composite | https://www.youtube.com/watch?v=EWDmWbJ4wRA |
| **Bridge** | https://refactoring.guru/design-patterns/bridge | https://www.youtube.com/watch?v=88kAIisOiYs |
| **Flyweight** | https://refactoring.guru/design-patterns/flyweight | https://www.youtube.com/watch?v=0vV-R2926ss |

**Exercise:** Build a `FileSystem` using Composite. Add a `LoggingProxy` on top.

---

### Week 9–11: Behavioral Patterns

These control *how objects communicate*.

| Pattern | When to Use | Real Example |
|---------|------------|--------------|
| **Observer** | Event-driven updates | Event bus, pub/sub |
| **Strategy** | Swap algorithms at runtime | Payment methods |
| **Command** | Encapsulate requests | Undo/redo, job queue |
| **State** | Behavior based on state | Order FSM |
| **Template Method** | Skeleton with customizable steps | Data parsers |
| **Iterator** | Traverse collections uniformly | Custom iterators |
| **Chain of Responsibility** | Pass request along handlers | Middleware pipeline |
| **Mediator** | Centralize communication | Chat room |
| **Memento** | Capture & restore state | Text editor undo |
| **Visitor** | Add ops without modifying classes | AST traversal |
| **Interpreter** | Grammar for a language | SQL parser |

**📚 References — Behavioral Patterns:**

| Pattern | Article | YouTube |
|---------|---------|---------|
| **Observer** | https://refactoring.guru/design-patterns/observer | https://www.youtube.com/watch?v=_BpmfnqjgzQ |
| **Strategy** | https://refactoring.guru/design-patterns/strategy | https://www.youtube.com/watch?v=v9ejT8IXVYc |
| **Command** | https://refactoring.guru/design-patterns/command | https://www.youtube.com/watch?v=9qA5kw8dcSU |
| **State** | https://refactoring.guru/design-patterns/state | https://www.youtube.com/watch?v=abX4xzaAsoc |
| **Template Method** | https://refactoring.guru/design-patterns/template-method | https://www.youtube.com/watch?v=7ocpwK9uesw |
| **Iterator** | https://refactoring.guru/design-patterns/iterator | https://www.youtube.com/watch?v=VKIzUuMiRBA |
| **Chain of Responsibility** | https://refactoring.guru/design-patterns/chain-of-responsibility | https://www.youtube.com/watch?v=FafNcoBvVQo |
| **Mediator** | https://refactoring.guru/design-patterns/mediator | https://www.youtube.com/watch?v=35D5cBosD4c |
| **Memento** | https://refactoring.guru/design-patterns/memento | https://www.youtube.com/watch?v=jOnxYT8Iaoo |
| **Visitor** | https://refactoring.guru/design-patterns/visitor | https://www.youtube.com/watch?v=pL4mOUDi54o |

**Exercise:** Build Order Management FSM (State). Add undo using Command + Memento.

---

### Week 12: Review & Consolidation

- [ ] Re-read your code from weeks 3–11 — refactor what feels off
- [ ] Pick 1 open-source project (Spring/Django/Rails) — identify 5 patterns
- [ ] Write a 1-page note for each pattern family

**📚 Phase 1 Master Resources:**

| Resource | Type | Link |
|----------|------|------|
| Refactoring Guru | Website | https://refactoring.guru/design-patterns |
| Source Making | Website | https://sourcemaking.com/design_patterns |
| Java Design Patterns (Iluwatar) | GitHub | https://github.com/iluwatar/java-design-patterns |
| Design Patterns in Java (Playlist) | YouTube | https://www.youtube.com/playlist?list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc |
| Derek Banas – All 23 Patterns | YouTube | https://www.youtube.com/watch?v=vNHpsC5ng_E |
| Christopher Okhravi – Patterns | YouTube | https://www.youtube.com/@ChristopherOkhravi |
| Concept && Coding – LLD Playlist | YouTube | https://www.youtube.com/playlist?list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW |

---

## Phase 2 — Low-Level Design (LLD) (Months 3–5)

### 🎯 Goal
Design classes, interfaces, and modules that are clean, extensible, and testable.

---

### Core Skills to Build

- [ ] Class diagram design from requirements
- [ ] Identifying entities, relationships, responsibilities
- [ ] Writing clean interfaces and abstract classes
- [ ] Applying patterns naturally (not forcefully)
- [ ] Thinking about extensibility

**📚 References — LLD Foundations:**

| Resource | Type | Link |
|----------|------|------|
| Awesome LLD (GitHub) | GitHub | https://github.com/ashishps1/awesome-low-level-design |
| Low Level Design Primer | GitHub | https://github.com/prasadgujar/low-level-design-primer |
| Clean Code | Book | Robert C. Martin |
| OOP Concepts in Java | Article | https://www.baeldung.com/java-oop |
| LLD Playlist – Concept && Coding | YouTube | https://www.youtube.com/playlist?list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW |

---

### Month 3: Foundations — Easy Problems

#### 🅿️ Parking Lot

| Resource | Link |
|----------|------|
| Design Video (Concept && Coding) | https://www.youtube.com/watch?v=tVRyb4HaHgw |
| Solution Walkthrough | https://www.youtube.com/watch?v=DSGsa0pu8-k |
| GitHub Solution (Java) | https://github.com/ashishps1/awesome-low-level-design/tree/main/solutions/java/src/parkinglot |

#### 📚 Library Management System

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=TLJJzGlUOTs |
| GitHub Solution | https://github.com/ashishps1/awesome-low-level-design/tree/main/solutions/java/src/library |

#### 🏧 ATM Machine

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=KHcVSRj_TaM |
| State Machine in Java (Baeldung) | https://www.baeldung.com/java-state-design-pattern |

---

### Month 4: Intermediate LLD

#### 🍔 Food Delivery App (Swiggy/Uber Eats)

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=YE-lFlW1wHo |
| GitHub Solution | https://github.com/ashishps1/awesome-low-level-design/tree/main/solutions/java/src/fooddeliveryservice |

#### 🛗 Elevator System

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=siqiJAJWUVg |
| Scheduling Algorithms (SCAN/LOOK) | https://www.geeksforgeeks.org/disk-scheduling-algorithms/ |

#### 🏨 Hotel Booking System

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=RCYzPkD5b3g |

#### ♟️ Chess Game

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=nTFkS9SdZU0 |
| GitHub Solution | https://github.com/ashishps1/awesome-low-level-design/tree/main/solutions/java/src/chessgame |

#### 🐦 Twitter / Social Feed

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=wYk0MImc9Mk |

#### ⚡ LRU Cache

| Resource | Link |
|----------|------|
| Concept + Code Video | https://www.youtube.com/watch?v=7ABFKPK2hD4 |
| LeetCode Problem | https://leetcode.com/problems/lru-cache/ |

---

### Month 5: Advanced LLD + Code Quality

#### 🚗 Ride-Sharing App (Uber/Lyft)

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=lsKU38RKQSo |
| GitHub Solution | https://github.com/ashishps1/awesome-low-level-design/tree/main/solutions/java/src/ridesharing |

#### 🔔 Notification System

| Resource | Link |
|----------|------|
| Design Video | https://www.youtube.com/watch?v=bBTZ-CMqiNU |

#### 🚦 Rate Limiter (LLD)

| Resource | Link |
|----------|------|
| Token Bucket Explained | https://www.youtube.com/watch?v=mhUQe4BKZXs |
| Cloudflare Blog (Rate Limiting) | https://blog.cloudflare.com/counting-things-a-lot-of-different-things/ |
| Algorithms Overview (Baeldung) | https://www.baeldung.com/guava-rate-limiter |

**Code Quality References:**

| Resource | Type | Link |
|----------|------|------|
| JUnit 5 Official Docs | Docs | https://junit.org/junit5/docs/current/user-guide/ |
| Dependency Injection in Java | Article | https://www.baeldung.com/inversion-control-and-dependency-injection-in-spring |
| Mockito for Unit Testing | Article | https://www.baeldung.com/mockito-series |
| SOLID Review | YouTube | https://www.youtube.com/watch?v=pTB30aXS77U |
| LeetCode OOD Section | Practice | https://leetcode.com/discuss/interview-question/object-oriented-design |

---

## Phase 3 — High-Level Design (HLD) (Months 5–7)

### 🎯 Goal
Think at scale. Design systems that handle millions of users, stay available, and recover from failures.

---

### Month 5–6: Building Blocks (Must Know Cold)

#### 🌐 Networking & APIs

| Concept | Read | Watch |
|---------|------|-------|
| REST vs GraphQL vs gRPC | https://www.redhat.com/en/topics/api/grpc-vs-rest | https://www.youtube.com/watch?v=gnchfOojMk4 |
| WebSockets vs SSE vs Polling | https://ably.com/blog/websockets-vs-long-polling | https://www.youtube.com/watch?v=2Nt-ZrNP22A |
| API Gateway | https://www.nginx.com/learn/api-gateway/ | https://www.youtube.com/watch?v=vHQqQBYJtnQ |
| HTTP/2 vs HTTP/3 | https://www.cloudflare.com/learning/performance/http2-vs-http1.1/ | https://www.youtube.com/watch?v=a-sBfyiXysI |

#### 🗄️ Data Layer

| Concept | Read | Watch |
|---------|------|-------|
| SQL vs NoSQL | https://www.mongodb.com/nosql-explained/nosql-vs-sql | https://www.youtube.com/watch?v=t8U3Os-QCug |
| CAP Theorem | https://www.ibm.com/topics/cap-theorem | https://www.youtube.com/watch?v=BHqjEjzAicA |
| ACID vs BASE | https://www.baeldung.com/cs/acid-vs-base-database-transactions | https://www.youtube.com/watch?v=pomxJOFVcQs |
| DB Indexing (B-tree, LSM) | https://use-the-index-luke.com | https://www.youtube.com/watch?v=fsG1XaZEa78 |
| Database Sharding | https://www.digitalocean.com/community/tutorials/understanding-database-sharding | https://www.youtube.com/watch?v=5faMjKuB9bc |
| DB Replication | https://www.postgresql.org/docs/current/high-availability.html | https://www.youtube.com/watch?v=nFnzKLoqbXw |
| Redis Deep Dive | https://redis.io/docs/ | https://www.youtube.com/watch?v=G1rOthIU-uo |
| Cassandra Explained | https://cassandra.apache.org/doc/latest/ | https://www.youtube.com/watch?v=J-cSy5MeMOA |
| Elasticsearch Intro | https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html | https://www.youtube.com/watch?v=ZP0NmfyfsoM |

#### ⚡ Caching

| Concept | Read | Watch |
|---------|------|-------|
| Caching Strategies | https://codeahoy.com/2017/08/11/caching-strategies-and-how-to-choose-the-right-one/ | https://www.youtube.com/watch?v=ccemOqDrc2I |
| Redis Caching Patterns | https://redis.io/docs/manual/client-side-caching/ | https://www.youtube.com/watch?v=a4yX7RUgTxI |
| CDN Explained | https://www.cloudflare.com/learning/cdn/what-is-a-cdn/ | https://www.youtube.com/watch?v=Bsq5cKkS33I |
| Cache Invalidation | https://martinfowler.com/bliki/TwoHardThings.html | https://www.youtube.com/watch?v=U3RkDLtS7uY |

#### 📨 Messaging & Async

| Concept | Read | Watch |
|---------|------|-------|
| Kafka vs RabbitMQ | https://www.confluent.io/blog/kafka-vs-rabbitmq/ | https://www.youtube.com/watch?v=sjDnqrnnlNs |
| Kafka Architecture | https://kafka.apache.org/documentation/ | https://www.youtube.com/watch?v=Ch5VhJzaoaI |
| Kafka Full Course | https://developer.confluent.io/learn-kafka/ | https://www.youtube.com/watch?v=R873BlNVUB4 |
| Message Delivery Guarantees | https://www.cloudamqp.com/blog/part1-rabbitmq-best-practice.html | https://www.youtube.com/watch?v=QmpBOCvY8mY |
| Dead Letter Queues | https://aws.amazon.com/what-is/dead-letter-queue/ | https://www.youtube.com/watch?v=nBEkj7O3R9Q |

#### 🏗️ Infrastructure

| Concept | Read | Watch |
|---------|------|-------|
| Load Balancing | https://www.nginx.com/resources/glossary/load-balancing/ | https://www.youtube.com/watch?v=sCR3SAVdyCc |
| Consistent Hashing | https://www.toptal.com/big-data/consistent-hashing | https://www.youtube.com/watch?v=UF9Iqmg94tk |
| Docker Quickstart | https://docs.docker.com/get-started/ | https://www.youtube.com/watch?v=pg19Z8LL06w |
| Kubernetes Basics | https://kubernetes.io/docs/tutorials/kubernetes-basics/ | https://www.youtube.com/watch?v=s_o8dwzRlu4 |
| Service Discovery | https://www.consul.io/docs/intro | https://www.youtube.com/watch?v=FpBjClKJDMc |

#### 🔭 Observability

| Concept | Read | Watch |
|---------|------|-------|
| Prometheus + Grafana | https://prometheus.io/docs/introduction/overview/ | https://www.youtube.com/watch?v=h4Sl21AKiDg |
| ELK Stack | https://www.elastic.co/what-is/elk-stack | https://www.youtube.com/watch?v=ZP0NmfyfsoM |
| Distributed Tracing | https://opentelemetry.io/docs/concepts/observability-primer/ | https://www.youtube.com/watch?v=idDu_jXqf4E |
| The Three Pillars of Observability | https://www.oreilly.com/library/view/distributed-systems-observability/9781492033431/ch04.html | https://www.youtube.com/watch?v=frngMXOi2ys |

---

### Month 6–7: HLD Practice Problems

**Framework for every HLD problem:**
```
1. Clarify requirements (functional + non-functional)
2. Capacity estimation (QPS, storage, bandwidth)
3. High-level diagram
4. Deep-dive on critical components
5. Address: scalability, availability, consistency, latency
6. Identify failure modes and mitigations
```

**📚 References per HLD Problem:**

| System | ByteByteGo | Gaurav Sen | Written Guide |
|--------|-----------|------------|---------------|
| **URL Shortener** | https://www.youtube.com/watch?v=fMZMm_0ZhK4 | https://www.youtube.com/watch?v=JQDHz72OA3c | https://systemdesign.one/url-shortening-system-design/ |
| **Instagram** | https://www.youtube.com/watch?v=VvZf_lZAZyA | https://www.youtube.com/watch?v=QmX2NPkJTKg | https://www.educative.io/courses/grokking-the-system-design-interview/m2yDVZnQ8lG |
| **Twitter Timeline** | https://www.youtube.com/watch?v=wYk0MImc9Mk | https://www.youtube.com/watch?v=KmAyPMe0QP4 | https://systemdesign.one/twitter-timeline-system-design/ |
| **WhatsApp / Chat** | https://www.youtube.com/watch?v=vvhC64hQZMk | https://www.youtube.com/watch?v=vvhC64hQZMk | https://systemdesign.one/whatsapp-system-design/ |
| **YouTube** | https://www.youtube.com/watch?v=mp-OSK6jm1c | https://www.youtube.com/watch?v=jPKTo1iGQiE | https://systemdesign.one/youtube-system-design/ |
| **Uber / Lyft** | https://www.youtube.com/watch?v=lsKU38RKQSo | https://www.youtube.com/watch?v=umWABit-wbk | https://systemdesign.one/uber-system-design/ |
| **Google Drive** | https://www.youtube.com/watch?v=U0xTu6E2CT8 | — | https://systemdesign.one/google-drive-system-design/ |
| **Netflix** | https://www.youtube.com/watch?v=psQzyFfsUGU | https://www.youtube.com/watch?v=lYoSd2WCJTo | https://systemdesign.one/netflix-system-design/ |
| **Web Crawler** | https://www.youtube.com/watch?v=BKZxZwUgL3Y | — | https://systemdesign.one/web-crawler-system-design/ |
| **Rate Limiter (HLD)** | https://www.youtube.com/watch?v=mhUQe4BKZXs | — | https://systemdesign.one/rate-limiter-system-design/ |
| **Distributed Cache** | https://www.youtube.com/watch?v=iuqZvajTOyA | https://www.youtube.com/watch?v=DUbEgNw-F9c | https://systemdesign.one/distributed-cache-system-design/ |
| **Notification System** | https://www.youtube.com/watch?v=bBTZ-CMqiNU | — | https://systemdesign.one/notification-system-design/ |
| **Search Autocomplete** | https://www.youtube.com/watch?v=us0qySiUsGU | — | https://systemdesign.one/typeahead-suggestion-system-design/ |

**Phase 3 Master Resources:**

| Resource | Type | Link |
|----------|------|------|
| Designing Data-Intensive Applications | Book ⭐ | https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/ |
| System Design Interview Vol 1 & 2 | Book ⭐ | https://www.amazon.com/System-Design-Interview-insiders-Second/dp/B08CMF2CQF |
| System Design Primer | GitHub | https://github.com/donnemartin/system-design-primer |
| Awesome System Design Resources | GitHub | https://github.com/ashishps1/awesome-system-design-resources |
| ByteByteGo Channel | YouTube | https://www.youtube.com/@ByteByteGo |
| Gaurav Sen Channel | YouTube | https://www.youtube.com/@gkcs |
| Tech Dummies – Narendra L | YouTube | https://www.youtube.com/@TechDummiesNarendraL |
| systemdesign.one | Website | https://systemdesign.one |
| High Scalability | Website | http://highscalability.com |
| Grokking System Design (Educative) | Course | https://www.educative.io/courses/grokking-the-system-design-interview |

---

## Phase 4 — System Design Deep Dives (Months 7–10)

### 🎯 Goal
Go beyond surface-level designs. Understand distributed systems theory and production realities.

---

### Month 7–8: Distributed Systems Theory

| Concept | Read | Watch |
|---------|------|-------|
| Consistency Models | https://jepsen.io/consistency | https://www.youtube.com/watch?v=gluIh8zd26I |
| Raft Consensus Algorithm | https://raft.github.io | https://www.youtube.com/watch?v=vYp4LYbnnW8 |
| Raft Visualization | https://thesecretlivesofdata.com/raft/ | — |
| Paxos (Lamport Paper) | https://lamport.azurewebsites.net/pubs/paxos-simple.pdf | https://www.youtube.com/watch?v=SRsK-ZXTeZ0 |
| Vector Clocks | https://www.allthingsdistributed.com/2008/12/eventually_consistent.html | https://www.youtube.com/watch?v=jD4ECsieFbE |
| Saga Pattern | https://microservices.io/patterns/data/saga.html | https://www.youtube.com/watch?v=txlSrGVCK18 |
| Two-Phase Commit (2PC) | https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html | https://www.youtube.com/watch?v=aDp99WDIM_4 |
| Circuit Breaker (Martin Fowler) | https://martinfowler.com/bliki/CircuitBreaker.html | https://www.youtube.com/watch?v=ADHcBxEXvFA |
| Idempotency (Stripe Blog) | https://stripe.com/blog/idempotency | https://www.youtube.com/watch?v=voUVLPFY5f4 |
| Backpressure | https://mechanical-sympathy.blogspot.com/2012/05/apply-back-pressure-when-overloaded.html | https://www.youtube.com/watch?v=m64SWl9bfvk |

---

### Month 8–9: Microservices Architecture

| Concept | Read | Watch |
|---------|------|-------|
| Microservices vs Monolith | https://martinfowler.com/articles/microservices.html | https://www.youtube.com/watch?v=rv4LlmLmVWk |
| Domain-Driven Design (DDD) | https://martinfowler.com/bliki/DomainDrivenDesign.html | https://www.youtube.com/watch?v=pMuiVlnGqjk |
| Event Sourcing | https://martinfowler.com/eaaDev/EventSourcing.html | https://www.youtube.com/watch?v=rolfJR9ERxo |
| CQRS | https://martinfowler.com/bliki/CQRS.html | https://www.youtube.com/watch?v=dK4Yb6-LxAk |
| Outbox Pattern | https://microservices.io/patterns/data/transactional-outbox.html | https://www.youtube.com/watch?v=u8fOnxAxKHk |
| Service Mesh (Istio) | https://istio.io/latest/docs/concepts/what-is-istio/ | https://www.youtube.com/watch?v=16fgzklcF7Y |
| API Versioning Strategies | https://www.baeldung.com/rest-versioning | https://www.youtube.com/watch?v=dqFHLABxhj4 |
| Contract Testing (Pact) | https://docs.pact.io | https://www.youtube.com/watch?v=-6x6XjDkbuA |

---

### Month 9–10: Real Architecture Case Studies

| Company | Blog | Must-Read Article | Watch |
|---------|------|-------------------|-------|
| **Netflix** | https://netflixtechblog.com | https://netflixtechblog.com/chaos-engineering-upgraded-878d341f15fa | https://www.youtube.com/watch?v=psQzyFfsUGU |
| **Uber** | https://www.uber.com/en-US/blog/engineering/ | https://www.uber.com/en-US/blog/microservice-architecture/ | https://www.youtube.com/watch?v=umWABit-wbk |
| **LinkedIn** | https://engineering.linkedin.com/blog | https://engineering.linkedin.com/blog/2019/apache-kafka-trillion-messages | https://www.youtube.com/watch?v=pJr3bzUTF7s |
| **Discord** | https://discord.com/blog | https://discord.com/blog/how-discord-stores-billions-of-messages | https://www.youtube.com/watch?v=O3PwuzCvAjI |
| **Dropbox** | https://dropbox.tech | https://dropbox.tech/infrastructure/magic-pocket-infrastructure | https://www.youtube.com/watch?v=PE4gwstWhmc |
| **Facebook** | https://engineering.fb.com | https://engineering.fb.com/2013/06/25/core-data/tao-the-power-of-the-graph/ | https://www.youtube.com/watch?v=9-hjBGxuiEs |
| **Twitter** | https://blog.twitter.com/engineering | https://blog.twitter.com/engineering/en_us/topics/infrastructure/2017/the-infrastructure-behind-twitter-scale | https://www.youtube.com/watch?v=wYk0MImc9Mk |
| **Airbnb** | https://medium.com/airbnb-engineering | https://medium.com/airbnb-engineering/smartstack-service-discovery-in-the-cloud-4b8a080de619 | https://www.youtube.com/watch?v=Yx7YCeGsiAA |

**Phase 4 Master Resources:**

| Resource | Type | Link |
|----------|------|------|
| DDIA — Martin Kleppmann | Book ⭐ | https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/ |
| Release It! — Michael Nygard | Book | https://pragprog.com/titles/mnee2/release-it-second-edition/ |
| Software Architecture: The Hard Parts | Book | https://www.oreilly.com/library/view/software-architecture-the/9781492086888/ |
| Building Microservices — Sam Newman | Book | https://www.oreilly.com/library/view/building-microservices-2nd/9781492034018/ |
| Martin Fowler Blog | Website | https://martinfowler.com |
| microservices.io patterns | Website | https://microservices.io/patterns |
| MIT 6.824 Distributed Systems | Free Course | https://pdos.csail.mit.edu/6.824/schedule.html |
| MIT 6.824 Lecture Videos | YouTube | https://www.youtube.com/playlist?list=PLrw6a1wE39_tb2fErI4-WkMbsvGQk9_UB |
| Jepsen — Distributed Systems Analysis | Website | https://jepsen.io |

---

## Phase 5 — Mastery & Interview Prep (Months 10–12)

### 🎯 Goal
Synthesize everything. Be able to whiteboard any system confidently in 45 minutes.

---

### Interview Prep Strategy

**For LLD Interviews (45–60 min):**
```
0:00 – 5:00   Clarify requirements, ask edge cases
5:00 – 10:00  Identify core entities and relationships
10:00 – 25:00 Design class diagram, interfaces, key methods
25:00 – 35:00 Apply patterns, explain trade-offs
35:00 – 45:00 Walk through a use case end-to-end
45:00 – 60:00 Handle follow-ups: extensibility, edge cases, testing
```

**For HLD Interviews (45–60 min):**
```
0:00 – 5:00   Gather functional + non-functional requirements
5:00 – 10:00  Capacity estimation (back-of-envelope)
10:00 – 20:00 High-level architecture diagram
20:00 – 35:00 Deep-dive on 2–3 critical components
35:00 – 45:00 Discuss trade-offs, failure modes, bottlenecks
45:00 – 60:00 Scaling strategies, future extensions
```

**📚 Interview Prep Resources:**

| Resource | Type | Link |
|----------|------|------|
| System Design Interview — Alex Xu | Book ⭐ | https://www.amazon.com/System-Design-Interview-insiders-Second/dp/B08CMF2CQF |
| Grokking System Design Interview | Course | https://www.educative.io/courses/grokking-the-system-design-interview |
| Grokking OOD Interview | Course | https://www.educative.io/courses/grokking-the-object-oriented-design-interview |
| Exponent — Mock Interviews | Website | https://www.tryexponent.com |
| InterviewBit — System Design | Website | https://www.interviewbit.com/system-design-interview-questions/ |
| NeetCode — System Design | YouTube | https://www.youtube.com/@NeetCodeIO |
| Awesome System Design Resources | GitHub | https://github.com/ashishps1/awesome-system-design-resources |
| System Design Fight Club | GitHub | https://github.com/systemdesign42/system-design |

---

### Monthly Habit (Sustain Forever)

| Habit | Frequency |
|-------|-----------|
| Read 1 engineering blog post | Weekly |
| Design 1 system from scratch (timed) | Weekly |
| Code 1 design pattern with tests | Bi-weekly |
| Do 1 mock interview (LLD or HLD) | Monthly |
| Read 1 chapter of DDIA | Weekly |

---

### 📚 All-in-One Master Reference

#### YouTube Channels

| Channel | Best For | Link |
|---------|----------|------|
| ByteByteGo | HLD, System Design | https://www.youtube.com/@ByteByteGo |
| Gaurav Sen | Distributed Systems, HLD | https://www.youtube.com/@gkcs |
| Tech Dummies – Narendra L | HLD walkthroughs | https://www.youtube.com/@TechDummiesNarendraL |
| Concept && Coding | LLD, Patterns (Java) | https://www.youtube.com/@ConceptandCoding |
| NeetCode | LLD + System Design | https://www.youtube.com/@NeetCodeIO |
| Derek Banas | All 23 Design Patterns | https://www.youtube.com/@derekbanas |
| Christopher Okhravi | OOP, Patterns (deep) | https://www.youtube.com/@ChristopherOkhravi |
| Arpit Bhayani | DB internals, distributed | https://www.youtube.com/@AsliEngineering |

#### Key Websites

| Website | Best For | Link |
|---------|----------|------|
| Refactoring Guru | Design Patterns | https://refactoring.guru/design-patterns |
| Source Making | Patterns + Anti-patterns | https://sourcemaking.com/design_patterns |
| System Design Primer | HLD (free, comprehensive) | https://github.com/donnemartin/system-design-primer |
| Awesome LLD | LLD problems + solutions | https://github.com/ashishps1/awesome-low-level-design |
| systemdesign.one | HLD articles | https://systemdesign.one |
| Martin Fowler Blog | Architecture thinking | https://martinfowler.com |
| microservices.io | Microservice patterns | https://microservices.io/patterns |
| High Scalability | Real production stories | http://highscalability.com |
| Jepsen | Distributed systems reality | https://jepsen.io |
| use-the-index-luke.com | DB indexing deep dive | https://use-the-index-luke.com |

#### Books (Priority Order)

| # | Book | Author | Link |
|---|------|--------|------|
| 1 ⭐ | Designing Data-Intensive Applications | Kleppmann | https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/ |
| 2 ⭐ | System Design Interview Vol 1 & 2 | Alex Xu | https://www.amazon.com/System-Design-Interview-insiders-Second/dp/B08CMF2CQF |
| 3 | Head First Design Patterns | Freeman & Robson | https://www.oreilly.com/library/view/head-first-design/0596007124/ |
| 4 | Clean Code | Robert C. Martin | https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882 |
| 5 | Clean Architecture | Robert C. Martin | https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164 |
| 6 | Building Microservices | Sam Newman | https://www.oreilly.com/library/view/building-microservices-2nd/9781492034018/ |
| 7 | Domain-Driven Design | Eric Evans | https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215 |
| 8 | Release It! | Michael Nygard | https://pragprog.com/titles/mnee2/release-it-second-edition/ |
| 9 | Software Architecture: The Hard Parts | Ford et al. | https://www.oreilly.com/library/view/software-architecture-the/9781492086888/ |

#### Free Courses

| Course | Link |
|--------|------|
| MIT 6.824 Distributed Systems | https://pdos.csail.mit.edu/6.824/schedule.html |
| CS75 Scalability (Harvard) | https://www.youtube.com/watch?v=-W9F__D3oY4 |
| Java Design Patterns (Iluwatar GitHub) | https://github.com/iluwatar/java-design-patterns |
| Confluent Kafka Learning | https://developer.confluent.io/learn-kafka/ |

---

## 📊 Progress Tracker

### Phase 1: Design Patterns
- [ ] SOLID Principles mastered
- [ ] Creational Patterns (5/5)
- [ ] Structural Patterns (7/7)
- [ ] Behavioral Patterns (11/11)
- [ ] Identified 5 patterns in real open-source codebase

### Phase 2: LLD
- [ ] Parking Lot
- [ ] Library System
- [ ] ATM
- [ ] Food Delivery App
- [ ] Elevator System
- [ ] Hotel Booking
- [ ] Chess Game
- [ ] Twitter Feed
- [ ] LRU Cache
- [ ] Ride-sharing App
- [ ] Rate Limiter

### Phase 3: HLD
- [ ] Building Blocks mastered (APIs, DB, Cache, Kafka, LB)
- [ ] URL Shortener
- [ ] Instagram
- [ ] Twitter Timeline
- [ ] WhatsApp
- [ ] YouTube
- [ ] Uber
- [ ] Google Drive
- [ ] Netflix
- [ ] Web Crawler
- [ ] Rate Limiter (distributed)
- [ ] Notification System
- [ ] Search Autocomplete

### Phase 4: Deep Dives
- [ ] Distributed systems theory (Raft, Sagas, 2PC, Circuit Breaker)
- [ ] Microservices, DDD, CQRS, Event Sourcing
- [ ] 5+ real architecture case studies (company blogs)

### Phase 5: Interview Prep
- [ ] 10+ timed LLD sessions
- [ ] 10+ timed HLD sessions
- [ ] 5+ mock interviews done

### Capstone Projects
- [ ] Capstone 1: Ride Booking System
- [ ] Capstone 2: Real-Time Chat System
- [ ] Capstone 3: Mini Netflix

### Execution System
- [ ] 5-day loop running consistently
- [ ] All LLD problems: diagram + code + DESIGN.md
- [ ] All HLD problems: requirements + estimation first
- [ ] Weekly habit streak: 4+ weeks unbroken

---

> 💡 **Pro Tip from 6+ Years:** Don't just *study* patterns — *hunt* for them in production code. Every time you see elegant code you didn't write, ask "What pattern is this?" That recognition muscle is what separates senior engineers.
>
> 🔥 **Execution beats knowledge. A dev who builds 10 mediocre systems knows more than one who read 10 books.** Ship the capstones. The discomfort of building is where the learning actually lives.

---

*Last Updated: April 2026*
