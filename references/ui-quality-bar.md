# UI Quality Bar

Use this reference for any user-facing interface. UI planning must be domain-specific and complete enough that implementation does not drift into generic template work.

## UI Planning Checklist

- Audience: who uses it and how skilled, hurried, or risk-sensitive they are.
- Primary job: the one task the first screen must help complete.
- Information hierarchy: what must be visible first, second, and only on demand.
- Visual direction: restrained SaaS, dense operations tool, editorial, playful, premium, technical, etc.
- Layout system: navigation, content regions, toolbars, forms, tables, panels, modals.
- Interaction model: create, edit, approve, retry, undo, export, filter, compare, inspect.
- States: loading, empty, first-use, populated, error, disabled, permission denied, offline, success.
- Responsive behavior: desktop, tablet, mobile, overflow, long labels, dense data.
- Accessibility: keyboard, focus, contrast, labels, semantic controls, motion sensitivity.
- Design-system fit: existing components, typography, spacing, icon style, color constraints.

## UI Document Template

```markdown
# UI Design Plan

## Product Tone
<Domain-specific visual direction and rationale.>

## Screen Inventory
| Screen | User goal | Primary action | Secondary actions |
| --- | --- | --- | --- |

## Information Hierarchy
- First priority:
- Second priority:
- Hidden until needed:

## Component Plan
| Component | Purpose | Data needed | States |
| --- | --- | --- | --- |

## Interaction States
- Loading:
- Empty:
- Error:
- Permission denied:
- Success:

## Responsive Rules
- Desktop:
- Mobile:
- Overflow/long text:

## Quality Risks
- Generic-template risk:
- Visual clutter risk:
- Accessibility risk:
```

## Strict UI Pushback

Reject UI plans that:

- Start with decorative hero sections for operational tools.
- Use generic cards everywhere without information hierarchy.
- Hide the product's main object or workflow behind marketing copy.
- Ignore empty/error/loading/permission states.
- Use color, gradients, or decoration without domain reason.
- Depend on text instructions instead of clear controls.
- Cannot fit long labels, real data, or mobile constraints.

## Practical Aesthetic Defaults

For SaaS, CRM, internal tools, analytics, ecommerce tooling, and operational workflows:

- Prefer dense but organized layouts.
- Use restrained color and clear status semantics.
- Put frequent actions near the data they affect.
- Favor tables, split panes, filters, tabs, toolbars, and inspectors over decorative cards.
- Make scanning, comparison, and repeated action efficient.

For consumer, portfolio, game, campaign, or brand-led work:

- Define a stronger visual concept.
- Use real imagery, generated bitmap imagery, or product-specific visual assets when helpful.
- Keep the primary object visible in the first viewport.
