---
name: database-migration
description: Design, write, and verify relational or document database migrations, schemas, indices, and rollback scripts.
---

# Database Migration

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when modifying database schemas, creating tables, adding columns, updating indices, or altering constraints.

## Workflow

1. **Resolve Repository**: Check target repository in `insight/registry.json`.
2. **Read Database Insight**:
   - Check `insight/<repo>/database/schema.md` for existing tables, ERDs, and ORM in use (Prisma, TypeORM, Drizzle, Alembic, etc.).
3. **Draft Migration**:
   - Write migration script adhering to zero-downtime guidelines (expand and contract pattern).
   - Ensure backwards compatibility if old app versions run during deployment.
   - Always provide an idempotent `down` / rollback step where supported.
4. **Update ORM / Schema Files**:
   - Update schema definition files (`schema.prisma`, models, entities).
5. **Test Migration**:
   - Run migration on local/test database.
   - Test rollback migration.
6. **Synchronize Insight**:
   - Update `insight/<repo>/database/schema.md` with new entities, columns, and foreign keys.
7. **Report**: Summarize schema changes and migration files generated.

## Constraints

- Never perform destructive column drops without a phased deprecation strategy.
- Avoid long-running exclusive locks on large production tables.
