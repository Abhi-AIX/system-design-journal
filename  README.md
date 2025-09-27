# System Design Journal — Question-Driven Design (QDD)

A lightweight journal for practicing system design where **questions lead the design**.  
Start with a problem, ask relentlessly, surface unknowns early, and make trade-offs explicit.

---

### 📂 Structure

```text
.
|-- README.md                        (overview, usage, mini-templates, contrib)
|-- designs/                         (design entries)
|-- images/                          (diagrams)
|-- templates/                       (templates)
|   |-- DESIGN_TEMPLATE.md           (design template)
|   `-- GENERAL_QUESTION_TEMPLATE.md (general question template)
|   `-- QUESTION_BANK_TEMPLATE.md    (question bank)
`-- general-questions/               (one file per question)
    |-- networking-and-dns/
    |-- caching-and-cdns/
    |-- databases-and-storage/
    |-- data-modeling-and-schema/
    |-- consistency-and-cap-theorem/
    |-- messaging-and-queues/
    |-- microservices-and-service-mesh/
    |-- scalability-and-performance/
    |-- reliability-availability-and-dr/
    |-- security-and-auth/
    `-- miscellaneous/
```

---

### 🚀 Purpose

- Turn vague prompts into concrete requirements by **asking the right questions first**.  
- Capture reasoning, assumptions, and trade-offs you can revisit and improve.  
- Keep it beginner → intermediate friendly; go deeper as you grow.

---

### 🛠 How to Use (design problems)

1. **Pick a problem prompt**  
   Examples: “Design a URL shortener”, “Design a chat service”, “Design a rate limiter”.

2. **Copy the Design Template**  
   From `templates/DESIGN_TEMPLATE.md` → into `designs/`:
   ```
   designs/2025-09-30-url-shortener.md
   ```

3. **Use the Question Bank**  
   Open `templates/QUESTION_BANK.md` and pick only the questions that fit your prompt.

4. **Complete your design**  
   Fill the template sections (requirements, APIs, HLD, trade-offs).  
   Put diagrams in `images/` and reference them from your design file.

---

### 🧩 Mini QDD Template (for quick starts)

```markdown
# <Problem Title> — YYYY-MM-DD

## 0) Discovery Questions
## 1) Requirements
## 2) APIs & Data
## 3) High-Level Design
## 4) Scale / Bottlenecks / Failures
## 5) Trade-offs & Alternatives
## 6) Observability & Ops
## 7) Open Questions & Next Steps
```

---

### ❓ General Questions (quick guide)

Use this for short, standalone questions that come up during practice.

- **One question = one file** in the best-fit folder under `general-questions/`.  
- **Filename format:** `YYYY-MM-DD-question-slug.md`  
  e.g., `2025-09-30-does-each-microservice-need-a-load-balancer.md`

**Minimal template (no YAML needed now):**
```markdown
# <The Question> — YYYY-MM-DD

**Difficulty:** beginner | beginner-intermediate | intermediate  
**Summary:** One line explaining why this question matters.

## Initial Thoughts
...

## When it might be true
...

## When it might not be needed
...

## Trade-offs / Considerations
...

## Related
...
```

---

### 🖼️ Diagrams (optional)

- Inline Mermaid is supported on GitHub, or store PNG/SVG in `images/` and link them.  
- Add diagrams only when they clarify a flow or trade-off.

---

### ✅ Why QDD Works

- Forces **clarity** by surfacing assumptions early.  
- Shows **reasoning**, not just answers (great for interviews).  
- Makes **trade-offs defensible** and easy to revisit.

---

### 💚 Use & Contribute

You’re welcome to **use** this material and **contribute** new designs or questions.
If this repo helps you, a ⭐️ or a PR is always appreciated!
<details>
<summary><strong>How to open a PR</strong></summary>

1) Fork this repo and create a branch.  
2) Add your file:
   - **Designs:** `designs/YYYY-MM-DD-problem-title.md` (use `templates/DESIGN_TEMPLATE.md`)
   - **General questions:** `general-questions/<topic>/YYYY-MM-DD-question-slug.md`  
3) Keep it short and beginner-friendly.  
4) Open a PR with a clear title (e.g., `Add: URL shortener design`).

</details>

### 📜 License


  Content (README, designs, templates, general-questions, images) is shared under **CC BY 4.0** — please attribute: *Abhinav Bellamkonda, System Design Journal — QDD (2025)*. See [LICENSE-docs](./LICENSE-docs).
