# Mermaid Adapter

Standardizes visualization schemas for architecture diagrams, ERDs, and sequence flows stored in `insight/<repo>/flows/` and `insight/<repo>/architecture/`.

## Conventions
- Always wrap labels with special characters in quotes.
- Use subgraphs for service and module boundaries.
- Adhere to the standard Markdown fence syntax:
  ````markdown
  ```mermaid
  flowchart TD
    A[Client] --> B[API Gateway]
  ```
  ````
