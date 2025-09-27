# Question Bank

The focus is on **asking the right questions first** to clarify requirements and guide design decisions, without diving into highly advanced distributed systems concepts.  
Over time, this list can grow with more advanced questions contributed by you or the community.

---

## 1) Goals & Scope
- What problem are we solving in one sentence?
- Who are the main users? What is their core journey?
- What features are **must-have** vs. **nice-to-have**?
- What is explicitly **out of scope** for V1?

## 2) Requirements & Constraints
- What are the functional requirements (what it should do)?
- What are the non-functional requirements (performance, availability, scalability)?
- What is the expected **scale** (number of users, requests per second, data size)?
- Do we need strong consistency or is eventual consistency okay?

## 3) APIs & Data
- What APIs/endpoints do we need? (basic CRUD, read-heavy, write-heavy?)
- What does the data model look like (entities, fields, relationships)?
- How will users query or access the data most often?
- Are there size limits on objects/records?

## 4) Architecture & Components
- What are the main building blocks (API service, database, cache, queue)?
- What external dependencies do we need (cloud services, libraries, APIs)?
- Do we need a cache? If yes, what should we cache?
- Should some parts be synchronous (real-time) vs. asynchronous (background jobs)?

## 5) Scale & Bottlenecks
- Where might the system break first (database, cache, network)?
- How do we handle sudden spikes in traffic?
- What is the read-to-write ratio? Does it impact the design?
- Do we need sharding/partitioning now or later?

## 6) Reliability & Failures
- What happens if a component fails (database down, cache evicted, service crash)?
- How can we degrade gracefully (read-only mode, retries, fallbacks)?
- Do we need replication or backups?
- How will we monitor errors and performance?

## 7) Security & Privacy
- Do we need authentication and authorization? (who can do what)
- What kind of data is sensitive (PII, passwords)?
- Should data be encrypted in transit and at rest?
- Are there rate limits or abuse-prevention measures needed?

## 8) Observability & Operations
- What should we log? (errors, requests, performance metrics)
- What alerts do we need? (high error rate, latency spikes, downtime)
- How will we know the system is healthy?
- How do we roll out changes safely (staging, canary, feature flags)?

## 9) Evolution & Next Steps
- What’s the MVP (minimum viable product)?
- What features can be added later as we scale?
- If we had to cut scope in half, what would remain?
- What is the most uncertain part we should validate with real usage?
