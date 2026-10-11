---
name: api-development
description: Design, implement, and document REST, GraphQL, or RPC API endpoints, serializers, middleware, and request validation contracts.
---

# API Development

## Required First Step

Read `../shared/insight-protocol.md` and follow it throughout this task.

## Purpose & When to Use

Use this skill when adding or updating HTTP endpoints, route handlers, middleware, request validation schemas (Zod, Joi, Pydantic), and response contracts.

## Workflow

1. **Resolve Repository**: Look up target repository in `insight/registry.json`.
2. **Read API Insight**:
   - Check `insight/<repo>/api/contracts.md` for existing routing conventions, auth headers, and response formats.
3. **Check Routing & Middleware**:
   - Identify how authentication, authorization, and rate limiting are applied to routes.
4. **Define Contract**:
   - Define schema validation for parameters, query string, and request payload.
   - Define status codes (200, 201, 400, 401, 403, 404, 500) and error envelope format.
5. **Implement Handler**:
   - Write controller / route handler using repository services and repositories.
6. **Add Integration Tests**:
   - Create route tests testing happy paths and validation failures.
7. **Synchronize Insight**:
   - Document new endpoints or updated payload schemas in `insight/<repo>/api/contracts.md`.
8. **Report**: Summarize new endpoints, schemas, and test results.

## Constraints

- Never expose unvalidated input to internal domain services.
- Adhere to the established error envelope format across the repository.
