# Architecture Patterns Reference

Common architecture archetypes observed in modern multi-repository workspaces:

## 1. Clean / Hexagonal Architecture
- **Domain Layer**: Core models, entities, business invariants (no external dependencies).
- **Application Layer**: Use cases, command/query handlers, service orchestrators.
- **Infrastructure Layer**: Database repositories, API adapters, messaging clients.
- **Interface / Presentation**: REST routes, GraphQL resolvers, CLI handlers, React components.

## 2. Feature-Sliced Design (Frontend)
- `app/`: Routing, providers, global styles.
- `pages/` or `views/`: Composition of widgets.
- `widgets/`: Independent UI blocks combining entities/features.
- `features/`: User interaction flows (auth, checkout, cart).
- `entities/`: Domain models (user, product).
- `shared/`: Reusable UI kit, API client, utils.

## 3. Modular Monolith
- Distinct domain modules with clear public interfaces (`index.ts` / exports).
- Explicit prohibition of direct internal imports between modules without using public API.
