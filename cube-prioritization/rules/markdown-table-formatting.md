# Claude Code Rule: Markdown Table Formatting

## Rule Name
`markdown-table-formatting`

## Rule Description
All markdown tables must be well-formatted and human-readable. Tables are a primary interface for data presentation in Claude Code agents, and poor formatting degrades usability, increases errors, and makes the output unprofessional.

## Applicability
This rule applies to all Claude Code agents that output markdown tables, including:
- Data enrichment agents (adding analysis columns)
- Reporting agents (summarizing results)
- Planning agents (organizing backlog or roadmap)
- Any agent transforming structured data into markdown output

## Requirements

### 1. Column Alignment & Width

**Requirement:** All columns must be consistently aligned and have sufficient width for readability.

**Standards:**
- Text columns (ID, Title, Description): Left-aligned
- Numeric columns (Effort, Value, ROI Ratio): Right-aligned or center-aligned
- Category columns (Type, Status, Version): Center-aligned
- Each column must have minimum width appropriate to its content

**Example — Good:**
```markdown
| ID       | Title                          | Description                    | Story Points | ROI Ratio |
|----------|--------------------------------|--------------------------------|-------------:|----------:|
| FEAT-001 | User Authentication            | Implement OAuth2 login flow    |           13 |     230.8 |
| FEAT-002 | Email Notifications            | Send alerts on task updates    |            5 |     240.0 |
```

**Example — Poor:**
```markdown
| ID | Title | Description | Story Points | ROI Ratio |
|---|---|---|---|---|
| FEAT-001 | User Authentication | Implement OAuth2 login flow | 13 | 230.8 |
| FEAT-002 | Email Notifications | Send alerts on task updates | 5 | 240.0 |
```

**Why:** Column headers and separator rows must align with data. Wide columns prevent line wrapping and improve scannability.
