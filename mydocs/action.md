# ADR Integration Guide

A step-by-step instruction set for embedding Architectural Decision Records (ADRs) into your **backend-engineering-designs** repo.

---

## 1. Create a Design for Each Core Items in `README.md`

* Create a detailed design document for each core design listed in your `README.md`.
* Store these in `docs/` and reference them via links from the `README.md`.

---

## 2. Create a Mermaid Flowchart for Each Design

* Embed a focused flowchart (≤10 nodes) illustrating the key components and data flow.
* Place the Mermaid code inline in each design markdown (e.g., `docs/high-throughput-ingest.md`).
* Base the design on the example_mermaid.mmd file - colors and animated arrows.

---

## 3. Number Your ADRs

Map each core design to a unique ADR ID. Example:

| ADR ID | Core Design                                                                                                     |
| :----: | :-------------------------------------------------------------------------------------------------------------- |
|  0001  | Horizontally scalable pipeline handling millions of events/sec                                                  |
|  0002  | Multi-tenant billing system supporting subscription, usage-based, and freemium models with eventual consistency |
|  0003  | Rewards calculation engine processing 10M transactions through Redis write-through cache to PostgreSQL          |
|   …    | …                                                                                                               |
|  0010  | Circuit breaker pattern implementation for a service mesh handling cascading failures across 50+ microservices  |

---

## 4. Create ADR Files for Each Design

For each of the ten core designs:

1. **Copy** the template:

   ```bash
   cp docs/adr_template.md docs/adr-000X-<short-slug>.md
````

2. **Fill out** the sections:

   * **Context:** Why this design is needed.
   * **Decision:** Your chosen architecture.
   * **Consequences:** Pros and cons.
   * **Alternatives Considered:** Other options and why you rejected them.
   * **Next Steps:** Implementation & validation plan.
3. **Link back** from the corresponding design document. At the bottom of `docs/<design>.md`:

   ```markdown
   ---
   **Related ADR:** [ADR 000X: Short Title](docs/adr-000X-short-slug.md)
   ```

---

## 5. Update the README

Under an **Architectural Decision Records** section, list all ADRs:

```markdown
### Architectural Decision Records
- [ADR 0001: Event Ingestion Pipeline](docs/adr-0001-event-ingest-pipeline.md)
- [ADR 0002: Multi-Tenant Billing System](docs/adr-0002-multi-tenant-billing.md)
- …
- [ADR 0010: Service-Mesh Circuit Breaker](docs/adr-0010-service-mesh-circuit-breaker.md)
```

---

## 6. Iterate and Evolve

* **Update** an ADR’s `Status` (e.g., to `accepted`) as you gather real-world feedback.
* **Revise** `Consequences` and `Next Steps` over time.
* **Deprecate** and supersede ADRs if new technologies or patterns arise, linking to new ADRs as needed.
