```markdown
# <Problem Title> — YYYY-MM-DD

> Follow Question-Driven Design (QDD): start with a problem prompt, then use the Question Bank to ask and answer.

---

## 0) Discovery — Questions → Answers

### Goals & Scope
- Q: What problem are we solving? What is success in one sentence?
- Q: Who are the main users and what’s their core journey?
- Q: What’s explicitly out of scope for V1?
- A:

### Constraints
- Q: What’s the expected scale (users, QPS, data size)?
- Q: Do we need strong or eventual consistency?
- Q: What’s the latency target (p95) for reads/writes?
- Q: What’s the availability goal (e.g., 99.9%)?
- A:

### Workload & Traffic
- Q: What’s the read:write ratio?
- Q: Do we expect bursts of traffic? How big?
- Q: Any hot keys or skew?
- A:

### Data
- Q: What are the main entities and relationships?
- Q: What’s the size per record? Retention?
- Q: What are the most common query patterns?
- A:

### Risks & Unknowns
- Q: What could fail first?
- Q: How do we degrade gracefully?
- Q: What will we intentionally defer for V1?
- A:

---

## 1) Requirements
- Functional:
- Non-functional:

## 2) APIs & Data Model
- Endpoints (basic request/response):
- Entities & indexes:

## 3) High-Level Design
- Components & responsibilities:
- Sequence of main flows:
- Diagram (Mermaid or image):

## 4) Scale, Bottlenecks & Failures
- Assumptions:
- Bottlenecks:
- Failure scenarios:

## 5) Trade-offs & Alternatives
- Why this design?
- What we rejected and why:
- Pros/Cons:

## 6) Observability & Security
- Metrics, logs, traces:
- Error handling, retries:
- Auth/authz, sensitive data handling:

## 7) Open Questions & Next Steps
- Unknowns to validate:
- Follow-ups:
- [ ] Next action 1
- [ ] Next action 2
