# COCA Framework Skill for Claude Code

A Claude Code skill that helps you build perfect specs using the COCA framework — a lightweight spec format that doubles as an AI prompt.

## Installation

```bash
/plugin marketplace add martellcode/cc-skill-coca
/plugin install coca@martellcode
```

## Usage

```bash
/coca                           # Start fresh, Claude will ask what to spec
/coca user authentication       # Jump straight into speccing a feature
```

The skill will guide you through each section of the COCA framework interactively, asking questions and refining until you have a complete, implementation-ready spec.

## The COCA Framework

COCA stands for **Context**, **Outcome**, **Constraints**, **Assertions**.

### C — Context
*Where are we starting from?*

- What exists today (current state)
- Who is the user (role, permissions, knowledge level)
- What system/codebase/stack is this part of
- Any relevant history

**Test:** Could a new engineer understand the landscape without follow-up questions?

### O — Outcome
*What does done look like?*

- The end state in concrete terms
- Who benefits and how
- What success feels like

**Test:** Could you demo this to a stakeholder and have them say "yes, that's what I wanted"?

**Trap:** Don't describe *how*—just describe *what*.

### C — Constraints
*What are the boundaries?*

- Tech stack requirements or limitations
- Timeline or budget
- Non-goals (what this is NOT)
- Security, compliance, performance requirements

**Test:** Does this prevent scope creep?

**Trap:** Don't over-constrain. Leave room for smart solutions.

### A — Assertions
*How do we know it works?*

- Specific "when I do X, I see Y" statements
- Happy path scenarios
- Edge cases and error states
- What should NOT happen

**Test:** Could QA write test cases from this? Could AI write tests from this?

## Example Output

```markdown
# PDF Export — COCA Spec

## Context
We have a React dashboard that displays real-time sales metrics. Users are sales
managers who check it daily. Currently there's no way to share the data with
executives who don't have login access.

## Outcome
Sales managers can generate a PDF report of their dashboard with one click and
email it to executives. Executives see the same data visualization without
needing to log in.

## Constraints
- Must work with existing React/Node stack
- PDF must generate in under 5 seconds
- NOT building a scheduled report feature (that's phase 2)
- Must respect existing user permissions—managers only see their region
- No new third-party services that require security review

## Assertions
- When I click "Export PDF" on my dashboard, a PDF downloads within 5 seconds
- The PDF matches the current dashboard view, including any filters I've applied
- When I'm a manager for West region, I only see West region data in the PDF
- When the dashboard has no data, I see "No data to export" instead of an empty PDF
- When PDF generation fails, I see an error message with a retry option
```

## Why COCA Works

1. **It's promptable** — Paste the spec into Claude and get usable code
2. **It's testable** — Assertions become acceptance criteria become tests
3. **It forces thinking** — You can't fill it out without understanding what you're building
4. **It's lightweight** — One page, not fifty. Takes 15-30 minutes, not days.

## License

MIT
