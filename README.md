# High Level Design (HLD) Interview Prep

Study material for High Level Design / System Design interviews for Software Engineer roles.

Content targets both mid-level (SDE II) and senior (SDE III / Staff) bars — senior-only material is marked with **[Senior]**. Companion repo for class-level design: [lld-interview-prep](https://github.com/asimnit/lld-interview-prep).

## What is an HLD round?

A 45–60 minute interview where you design a large-scale system ("design a URL shortener", "design WhatsApp") out of services, databases, caches and queues, usually on a whiteboard, with little or no code. You are evaluated on:

| Signal | What the interviewer looks for |
| --- | --- |
| Requirement clarification | Functional vs. non-functional requirements, scope, what's out |
| Estimation | Rough traffic, storage and bandwidth numbers that drive the design |
| API & data model | Clear interfaces and a schema that fits the access patterns |
| High-level architecture | Sensible components and data flow, end to end |
| Deep dives | Going deep on the hard part: scaling, consistency, hot spots |
| Trade-offs | Naming alternatives and justifying choices (SQL vs. NoSQL, push vs. pull) |
| Reliability & operations | **[Senior]** failure modes, multi-region, monitoring, cost |

## How HLD differs from LLD

| | LLD | HLD |
| --- | --- | --- |
| Unit of design | Classes, interfaces, patterns | Services, databases, caches, queues |
| Output | Class diagram + working code | Architecture diagram + data flow |
| Key concerns | Extensibility, SOLID, patterns | Scale, availability, consistency, latency |
| Typical prompt | "Design a parking lot" | "Design Uber" |

## How to use this repo

1. Skim the topic catalog below and pick a track from [Study Schedules](#study-schedules).
2. Work through phases in order — fundamentals before building blocks, building blocks before case studies.
3. For every case study: attempt it on paper first (45 min timer), *then* read the write-up.
4. Tick the checkboxes below as you go.

---

## Topic Catalog

Tick boxes as topics are completed. Each topic gets its own write-up with: concept notes, diagrams, trade-offs, common pitfalls, and interview questions.

### Phase 1 — Fundamentals

| # | Topic | Key points | Done |
| --- | --- | --- | --- |
| 1.1 | [Life of a request](phase-1-fundamentals/1.1-life-of-a-request.md) | DNS → load balancer → app server → cache → database | [ ] |
| 1.2 | Networking basics | TCP vs. UDP, HTTP/1.1 vs. 2 vs. 3, TLS | [ ] |
| 1.3 | DNS | resolution, TTLs, DNS-based load balancing | [ ] |
| 1.4 | Back-of-the-envelope estimation | latency numbers, QPS, storage, bandwidth | [ ] |
| 1.5 | Availability & reliability | nines, SLA/SLO/SLI, single points of failure | [ ] |
| 1.6 | Scalability | vertical vs. horizontal, stateless services | [ ] |

**Interview questions:** What happens when you type a URL into a browser? How many servers do you need for 10k QPS? What does 99.99% availability allow per month?

### Phase 2 — Building Blocks

| # | Topic | Key points | Done |
| --- | --- | --- | --- |
| 2.1 | Load balancers | L4 vs. L7, round robin, least connections, health checks | [ ] |
| 2.2 | Caching | cache-aside, write-through, write-back, eviction, invalidation | [ ] |
| 2.3 | CDN | push vs. pull, edge caching, static vs. dynamic content | [ ] |
| 2.4 | Reverse proxy & API gateway | routing, auth, rate limiting at the edge | [ ] |
| 2.5 | Message queues & pub/sub | Kafka vs. RabbitMQ vs. SQS, delivery guarantees | [ ] |
| 2.6 | Object/blob storage | S3-style storage, metadata vs. content | [ ] |
| 2.7 | Search | inverted index, Elasticsearch basics | [ ] |
| 2.8 | Rate limiting | token bucket, sliding window, distributed counters | [ ] |
| 2.9 | Unique ID generation | UUID, Snowflake, ticket servers | [ ] |
| 2.10 | Consistent hashing | virtual nodes, rebalancing | [ ] |

**Interview questions:** Cache-aside vs. write-through — when would you pick each? How do you invalidate a cache? At-least-once vs. exactly-once delivery?

### Phase 3 — Data & Storage

| # | Topic | Key points | Done |
| --- | --- | --- | --- |
| 3.1 | SQL vs. NoSQL | relational, key-value, document, wide-column, graph | [ ] |
| 3.2 | Data modeling for scale | access patterns, denormalization | [ ] |
| 3.3 | Indexes | B-tree vs. LSM tree, secondary indexes | [ ] |
| 3.4 | Replication | leader-follower, multi-leader, leaderless, replication lag | [ ] |
| 3.5 | Partitioning / sharding | range vs. hash, hot keys, resharding | [ ] |
| 3.6 | Transactions & isolation | ACID, isolation levels, anomalies | [ ] |
| 3.7 | Consistency models | strong, eventual, read-your-writes | [ ] |
| 3.8 | CAP & PACELC | what the trade-off really means in practice | [ ] |
| 3.9 | **[Senior]** Consensus | Raft/Paxos, leader election, quorums | [ ] |
| 3.10 | **[Senior]** Distributed transactions | 2PC, Saga, transactional outbox | [ ] |

**Interview questions:** How would you shard a users table? What happens to reads during replication lag? Why is CAP often misunderstood?

### Phase 4 — Communication & APIs

| # | Topic | Key points | Done |
| --- | --- | --- | --- |
| 4.1 | REST vs. gRPC vs. GraphQL | when each fits | [ ] |
| 4.2 | API design | pagination, idempotency keys, versioning | [ ] |
| 4.3 | Real-time communication | polling, long polling, WebSockets, SSE | [ ] |
| 4.4 | Sync vs. async & event-driven design | events, choreography vs. orchestration | [ ] |
| 4.5 | Monolith vs. microservices | service boundaries, service discovery | [ ] |
| 4.6 | **[Senior]** Resilience patterns | timeouts, retries with backoff, circuit breakers, back-pressure | [ ] |

**Interview questions:** How do you make a payment API safe to retry? WebSockets vs. SSE for a live scoreboard? When would you *not* split into microservices?

### Phase 5 — Reliability, Operations & Security

| # | Topic | Key points | Done |
| --- | --- | --- | --- |
| 5.1 | Fault tolerance | redundancy, failover, graceful degradation | [ ] |
| 5.2 | Observability | metrics, logs, traces, alerting | [ ] |
| 5.3 | Authentication & authorization | sessions, JWT, OAuth2 | [ ] |
| 5.4 | Security basics | encryption in transit/at rest, secrets, abuse prevention | [ ] |
| 5.5 | **[Senior]** Multi-region & disaster recovery | active-active vs. active-passive, RPO/RTO | [ ] |
| 5.6 | **[Senior]** Batch vs. stream processing | MapReduce, Spark, Flink, lambda/kappa | [ ] |
| 5.7 | **[Senior]** Cost & trade-off discussions | build vs. buy, cost of scale | [ ] |

### Phase 6 — Case Studies

A "how to approach HLD case studies" guide (requirements → estimation → API → data model → architecture → deep dive → bottlenecks, plus time management) will open this phase.

Attempt each in 45 min before reading the solution.

**Tier 1 — Warm-up**

| # | Problem | Core concepts | Done |
| --- | --- | --- | --- |
| 6.1 | URL Shortener | ID generation, read-heavy caching, redirects | [ ] |
| 6.2 | Pastebin | object storage, expiry, metadata DB | [ ] |
| 6.3 | Distributed Rate Limiter | token bucket, shared counters, Redis | [ ] |
| 6.4 | Notification System | queues, fan-out, retries, user preferences | [ ] |
| 6.5 | Web Crawler | URL frontier, politeness, deduplication | [ ] |

**Tier 2 — Standard**

| # | Problem | Core concepts | Done |
| --- | --- | --- | --- |
| 6.6 | News Feed (Twitter/Facebook) | fan-out on write vs. read, celebrity problem | [ ] |
| 6.7 | Chat (WhatsApp) | WebSockets, message ordering, delivery receipts, presence | [ ] |
| 6.8 | Photo Sharing (Instagram) | blob storage, CDN, feed generation | [ ] |
| 6.9 | Video Streaming (YouTube/Netflix) | transcoding pipeline, adaptive bitrate, CDN | [ ] |
| 6.10 | File Sync (Dropbox/Google Drive) | chunking, deduplication, sync conflicts | [ ] |
| 6.11 | Search Autocomplete | trie, top-K, offline aggregation | [ ] |
| 6.12 | Ride Hailing (Uber) | geospatial indexing, matching, location updates | [ ] |
| 6.13 | Ticket Booking (BookMyShow) | seat holds, consistency, high contention | [ ] |
| 6.14 | E-commerce Flash Sale | inventory contention, queues, oversell prevention | [ ] |

**Tier 3 — [Senior] Advanced**

| # | Problem | Core concepts | Done |
| --- | --- | --- | --- |
| 6.15 | Distributed Message Queue (Kafka) | partitions, replication, consumer groups, offsets | [ ] |
| 6.16 | Distributed Key-Value Store / Cache | consistent hashing, quorums, gossip | [ ] |
| 6.17 | Collaborative Editing (Google Docs) | OT vs. CRDT, real-time sync | [ ] |
| 6.18 | Payment System | idempotency, ledger, reconciliation, exactly-once effects | [ ] |
| 6.19 | Ad Click Aggregator / Top-K | stream processing, windowing, approximate counting | [ ] |
| 6.20 | Proximity Service (Yelp) | geohash, quadtree, read scaling | [ ] |
| 6.21 | Distributed Job Scheduler | leader election, at-least-once execution | [ ] |
| 6.22 | Real-time Leaderboard | sorted sets, sharded ranking | [ ] |

---

## Study Schedules

### 4-Week Standard Track (~1.5 hrs/day)

| Week | Focus | Deliverable |
| --- | --- | --- |
| 1 | Phase 1 + Phase 2 | Estimation cheat sheet; one-page notes per building block |
| 2 | Phase 3 + Phase 4 | Trade-off table: databases, replication, sharding, API styles |
| 3 | Phase 5 + case-study approach guide + Tier 1 | 5 warm-up designs on paper |
| 4 | Phase 6 Tier 2 | 6–8 standard designs, timed |

### 2-Week Crash Track (~2.5 hrs/day)

| Days | Focus |
| --- | --- |
| 1–2 | Phase 1 (estimation, scalability) + case-study approach guide |
| 3–5 | High-yield blocks: load balancers, caching, CDN, queues, sharding, replication, consistent hashing |
| 6–9 | Case studies 6.1, 6.4, 6.6, 6.7, 6.12, 6.13 |
| 10–12 | Case studies 6.9, 6.10, 6.11 + Phase 3.7–3.8 (consistency, CAP) |
| 13–14 | Mock interviews, review weak spots |

### 6-Week Senior Track

Weeks 1–4 as Standard, plus:

| Week | Focus |
| --- | --- |
| 5 | Senior topics (3.9, 3.10, 4.6, 5.5–5.7) + Tier 3 case studies 6.15–6.18 |
| 6 | Tier 3 case studies 6.19–6.22 + trade-off drills, failure-scenario deep dives |

---

## Master Question Bank

Cross-cutting questions asked after most HLD problems:

1. What are the read/write ratios and how did they shape your design?
2. Where is the single point of failure, and how do you remove it?
3. What happens when traffic grows 10x? 100x?
4. Which data needs strong consistency, and where is eventual consistency fine?
5. How do you handle a hot key or a celebrity user?
6. What happens if this component goes down mid-request?
7. How would you monitor this system and know it's healthy? **[Senior]**
8. How would you run this across multiple regions? **[Senior]**

---

## Progress Summary

| Phase | Topics | Done |
| --- | --- | --- |
| 1. Fundamentals | 6 | 0 |
| 2. Building Blocks | 10 | 0 |
| 3. Data & Storage | 10 | 0 |
| 4. Communication & APIs | 6 | 0 |
| 5. Reliability, Operations & Security | 7 | 0 |
| 6. Case Studies | 22 | 0 |
| **Total** | **61** | **0** |
