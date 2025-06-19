# ADR 0003: Rewards Calculation Engine

**Date:** 2025-01-19  
**Status:** proposed

## Context

We need to architect a high-performance rewards calculation engine capable of processing 10 million transactions daily with real-time point calculations and balance updates. The system must support complex reward rules, maintain data consistency, and provide sub-50ms response times for reward calculations.

Key requirements:
- Process 10M transactions/day (115 TPS average, 1000 TPS peak)
- Sub-50ms p95 latency for reward calculations
- 99.99% calculation accuracy
- Support for complex multi-tier reward rules
- Real-time balance updates and point tracking
- Write-through caching for performance optimization

## Decision

We will implement a rewards calculation engine using Redis write-through cache pattern with PostgreSQL as the primary data store, leveraging Kafka for real-time transaction processing.

**Core Architecture:**
- **Redis Cluster** as write-through cache for hot data (user balances, recent transactions)
- **PostgreSQL** as primary transactional data store with read replicas
- **Kafka Streams** for real-time transaction ingestion and processing
- **Rules Engine** for configurable reward calculation logic
- **Connection pooling** and **prepared statements** for database optimization

**Key Design Patterns:**
- Write-through cache pattern for immediate consistency
- CQRS for separating calculation and query operations
- Event sourcing for transaction audit trail
- Circuit breaker for fault tolerance

## Consequences

**Positive outcomes:**
- Sub-millisecond cache lookups for frequently accessed data
- Immediate consistency between cache and database
- High throughput processing with parallel worker pools
- Flexible reward rules supporting complex business logic
- Strong audit trail for compliance and debugging
- Horizontal scalability through cache clustering

**Negative trade-offs:**
- Increased infrastructure complexity with cache management
- Higher memory costs for Redis cluster deployment
- Cache warming overhead during system startup
- Potential for cache invalidation complexity
- Additional monitoring requirements for cache health

## Alternatives Considered

**Option A: Database-only Solution**
- Rejected due to latency requirements (>50ms for complex calculations)
- Limited scalability for high-frequency balance lookups
- Increased database load affecting other operations

**Option B: Write-behind Cache Pattern**
- Rejected due to eventual consistency concerns
- Risk of data loss during cache failures
- Complex reconciliation logic required

**Option C: In-memory Database (Redis only)**
- Rejected due to durability requirements
- Higher risk of data loss without persistent storage
- Limited query capabilities for complex analytics

## Next Steps

1. **Infrastructure Setup** (Week 1-2)
   - Deploy Redis cluster with appropriate sharding
   - Set up PostgreSQL with read replicas
   - Configure Kafka for transaction streaming

2. **Core Engine Development** (Week 3-4)
   - Implement basic reward calculation logic
   - Develop cache management and warming strategies
   - Create transaction processing pipeline

3. **Rules Engine Implementation** (Week 5-6)
   - Build configurable rules engine
   - Implement multi-tier calculation logic
   - Add support for promotional campaigns

4. **Performance Optimization** (Week 7-8)
   - Load testing and performance tuning
   - Cache optimization and monitoring
   - Disaster recovery and failover testing
