# Image Assets

This directory stores small, reusable visual assets for the BAES-Updates repository.

## Usage principles

- Prefer lightweight SVG for icons and simple diagrams.
- Keep visuals explanatory rather than decorative.
- Use descriptive, lowercase filenames with hyphens.
- Provide meaningful alternative text whenever an image is embedded in a document.
- Do not use an image as the sole carrier of essential information.
- Check that a visual remains legible at the size used in a page.
- Use repository-relative paths when embedding assets in Markdown.
- Treat illustrations as explanations, not evidence of validation, funding, partnerships, or outcomes.

## Existing conceptual illustrations

- `human-authority.svg` — illustrates the distinction between human authority and bounded AI execution.
- `evaluation-process.svg` — a compact overview of an evaluation cycle.
- `baes-layers.svg` — a high-level view of the BAES layer structure.

These are conceptual illustrations, not evidence that BAES has been independently validated.

## BAES thematic SVG library

The following 12 lightweight, native-vector icons share a consistent palette and visual style.

| File | Theme | Recommended use |
|---|---|---|
| `01-institutions-organizations.svg` | Institutions & Organizations | Institutional context and stakeholders |
| `02-artificial-intelligence.svg` | Artificial Intelligence | AI capabilities and AI-assisted engineering |
| `03-universities-research.svg` | Universities & Research | Research summaries and academic collaboration |
| `04-progress-development.svg` | Progress & Development | Milestones and documented progress |
| `05-thinking-ideas.svg` | Thinking & Ideas | Reasoning, concepts, and exploration |
| `06-management-coordination.svg` | Management & Coordination | Roles, coordination, and process ownership |
| `07-decision-making.svg` | Decision Making | Decisions and authorization points |
| `08-governance-compliance.svg` | Governance & Compliance | Governance, traceability, and accountability |
| `09-collaboration-partnerships.svg` | Collaboration & Partnerships | Invitations and pathways for collaboration |
| `10-evaluation-evidence.svg` | Evaluation & Evidence | Evaluation methods, evidence, and results |
| `11-sustainable-impact.svg` | Sustainable Impact | Responsible and long-term development |
| `12-human-at-the-center.svg` | Human at the Center | Human intent, authority, and override |

### Example: embedding an icon

From a Markdown file in the repository root:

```markdown
![Governance and compliance](assets/images/08-governance-compliance.svg)
```

From a Markdown file in a subdirectory, adjust the relative path as needed (for example, `../assets/images/08-governance-compliance.svg`).

### Visual conventions

- **Format:** native SVG vector artwork; no embedded raster images.
- **ViewBox:** `0 0 100 100`; scalable without pixelation.
- **Palette:** navy and blue for structure, teal/green for responsible action, orange for selective emphasis.
- **Style:** simple, consistent geometry intended for README pages and research briefs.
- **Accessibility:** each icon contains a title and short description.
- **Naming:** numbered prefixes keep the set in a predictable order.

### BAES-specific usage guidance

- Use **Evaluation & Evidence** for methods or documented evidence; do not imply a successful result unless results are actually recorded.
- Use **Collaboration & Partnerships** to indicate a possible collaboration pathway, not to imply that a partnership already exists.
- Use **Progress & Development** only alongside an accurate description of real progress.
- Use **Human at the Center** for material about human intent, authority, authorization, and override.
- Keep new illustrations consistent with the palette, 100×100 viewBox, accessible title/description, and filename convention.

These images support navigation and comprehension. They do not replace technical definitions, evaluation evidence, or the relevant BAES documents.

---

[← Back to BAES-Updates Home](https://github.com/babak-rasti-meymandi/BAES-Updates/)
