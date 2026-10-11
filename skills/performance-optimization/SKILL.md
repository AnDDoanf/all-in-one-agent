---
name: performance-optimization
description: Analyze performance bottlenecks, query latencies, memory leaks, and render overhead to improve throughput and efficiency.
---

# Performance Optimization

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when diagnosing slow endpoints, excessive database queries (N+1 issues), large bundle sizes, or high memory/CPU usage.

## Workflow

1. **Resolve Repository**: Check target repository in `insight/registry.json`.
2. **Read Performance Insight**:
   - Check `insight/<repo>/architecture/performance.md` for known latency benchmarks or caching patterns.
3. **Profile & Measure**:
   - Quantify baseline performance (e.g. execution time, DB query count, bundle weight).
   - Identify hotspot algorithms (O(N^2) or nested loops), unindexed DB queries, or unnecessary re-renders.
4. **Implement Optimization**:
   - Add database indexes or batch queries (`DataLoader`, `JOIN` instead of N+1).
   - Introduce caching where appropriate (Redis, in-memory LRU, HTTP Cache-Control).
   - Optimize bundle splitting or lazy loading for frontend apps.
5. **Verify Improvement**:
   - Re-measure metric against baseline. Ensure correctness tests still pass.
6. **Synchronize Insight**:
   - Record the optimization strategy and benchmark metrics in `insight/<repo>/architecture/performance.md`.
7. **Report**: Summarize measured performance before vs after.

## Constraints

- Avoid premature optimization without empirical baseline measurements.
- Maintain code readability unless micro-optimization is explicitly warranted.
