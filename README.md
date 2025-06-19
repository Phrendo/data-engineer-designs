# Backend Engineering Recipes

Note: this is my design, and preferrences. There is no snowflake, azure or google cloud and rarely even aws.  These are primarily local stack based solutions.

## Preferred Services, Methodologies, & Frameworks
- [Preferrences](docs/preferred_services_frameworks.md)

## Core Designs

### 1. High-Throughput Event Pipeline
[Design Document](docs/high-throughput-event-pipeline.md) | [ADR 0001](docs/adr-0001-event-ingest-pipeline.md)

A horizontally scalable pipeline handling millions of events/sec with Apache Kafka, real-time processing, and multi-tier storage.

### 2. Multi-Tenant Billing System
[Design Document](docs/multi-tenant-billing-system.md) | [ADR 0002](docs/adr-0002-multi-tenant-billing.md)

A comprehensive billing system supporting subscription, usage-based, and freemium monetization models with eventual consistency.

### 3. Rewards Calculation Engine
[Design Document](docs/rewards-calculation-engine.md) | [ADR 0003](docs/adr-0003-rewards-calculation-engine.md)

A high-performance rewards engine processing 10 million transactions through Redis write-through cache to PostgreSQL.

### 4. Real-Time Notification System
[Design Document](docs/real-time-notification-system.md) | [ADR 0004](docs/adr-0004-real-time-notification.md)

A scalable notification delivery system handling 5 million push notifications with GraphQL subscriptions and message queuing.

### 5. Feature Flag Service
[Design Document](docs/feature-flag-service.md) | [ADR 0005](docs/adr-0005-feature-flag-service.md)

A feature flag service supporting A/B testing for 20 million users with sub-100ms latency requirements.

### 6. Distributed Rate Limiting
[Design Document](docs/distributed-rate-limiting.md) | [ADR 0006](docs/adr-0006-distributed-rate-limiting.md)

A distributed rate limiting system protecting APIs from 1 million requests per second across multiple regions.

### 7. Data Consistency Layer
[Design Document](docs/data-consistency-layer.md) | [ADR 0007](docs/adr-0007-data-consistency-layer.md)

A data consistency layer for order processing across payment, inventory, and shipping microservices.

### 8. Analytics Pipeline
[Design Document](docs/analytics-pipeline.md) | [ADR 0008](docs/adr-0008-analytics-pipeline.md)

A horizontally scalable analytics pipeline aggregating user behavior data from 100+ million events daily.

### 9. Circuit Breaker Pattern
[Design Document](docs/circuit-breaker-pattern.md) | [ADR 0009](docs/adr-0009-circuit-breaker-pattern.md)

A circuit breaker pattern implementation for a service mesh handling cascading failures across 50+ microservices.

### 10. Multi-Region CDN
[Design Document](docs/multi-region-cdn.md) | [ADR 0010](docs/adr-0010-multi-region-cdn.md)

A multi-region content delivery system with cache invalidation strategies for a global user base of 10 million.

## Architectural Decision Records

- [ADR 0001: Event Ingestion Pipeline](docs/adr-0001-event-ingest-pipeline.md)
- [ADR 0002: Multi-Tenant Billing System](docs/adr-0002-multi-tenant-billing.md)
- [ADR 0003: Rewards Calculation Engine](docs/adr-0003-rewards-calculation-engine.md)
- [ADR 0004: Real-Time Notification System](docs/adr-0004-real-time-notification.md)
- [ADR 0005: Feature Flag Service](docs/adr-0005-feature-flag-service.md)
- [ADR 0006: Distributed Rate Limiting](docs/adr-0006-distributed-rate-limiting.md)
- [ADR 0007: Data Consistency Layer](docs/adr-0007-data-consistency-layer.md)
- [ADR 0008: Analytics Pipeline](docs/adr-0008-analytics-pipeline.md)
- [ADR 0009: Circuit Breaker Pattern](docs/adr-0009-circuit-breaker-pattern.md)
- [ADR 0010: Multi-Region CDN](docs/adr-0010-multi-region-cdn.md)