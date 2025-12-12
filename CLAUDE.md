# Page-Spec YAML Project

This project uses a structured YAML format to specify UI pages, layouts, and user flows. The specs are designed to be maintained by AI and validated against JSON schemas.

## Commands

- `pnpm run lint` - Validate all specs against schemas
- `pnpm run docs` - Serve interactive spec browser at localhost:3000

## File Structure

```
page-specs/
├── pages/*.ui.yaml      # Page specifications
├── flows/*.flow.yaml    # User flow specifications
├── layouts/*.layout.yaml # Layout templates
└── schemas/*.schema.json # JSON schemas (do not edit)
```

## Creating/Editing Specs

Always include the schema reference at the top of each file:

```yaml
# yaml-language-server: $schema=../schemas/ui-spec.schema.json
```

### Pages (`*.ui.yaml`)

Required fields: `page`, `route`

Key patterns:
- Use `{variable}` for data bindings (e.g., `{product.name}`)
- Use `source` + `repeat` for lists (e.g., `source: cart.items`, `repeat: item`)
- Use `condition` for conditional rendering (e.g., `condition: "{user.isAdmin}"`)
- Use `onClick` for actions, `action` for navigation

### Flows (`*.flow.yaml`)

Required fields: `flow`, `goal`, `steps`

Flows document multi-page user journeys. Each step references a page route.

## Naming Conventions

- Pages: `kebab-case.ui.yaml` (e.g., `product-detail.ui.yaml`)
- Flows: `NN.NN-description.flow.yaml` (e.g., `02.00-browse-and-purchase.flow.yaml`)

## Validation

Run `pnpm run lint` after changes. Fix any schema violations before committing.
