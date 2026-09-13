# Development Rules

Rules that the Coding Agent must follow during implementation.

---

## Core Principles

### Scope Adherence
- Execute **only** the approved scope
- Do not implement features outside approved scope
- Do not add functionality "because it might be useful later"

### Architecture Integrity
- Do not change architecture without Architect review and approval
- Do not modify contracts without Architect approval
- Implement exactly as designed

### Minimal Changes
- Make the minimum change necessary to fulfill the requirement
- Do not perform wide refactoring without explicit request
- Do not "improve" code that is not being changed

### Quality Standards
- Write tests for all changes
- Maintain backward compatibility
- Do not introduce unnecessary dependencies
- Follow existing code patterns and conventions

---

## Security Rules

- **NEVER** commit secrets, tokens, credentials, API keys, or any sensitive data
- **NEVER** hardcode credentials in code or configuration files
- Use environment variables or secure secret management for all secrets
- All authentication logic resides only in the GEE Integration Layer

---

## Git and Repository Rules

> **DO NOT COMMIT until explicit approval from the Project Manager.**

> **DO NOT PUSH until explicit approval from the Project Manager.**

Even if you believe changes are complete, correct, and tested, you are **NOT authorized** to commit or push without explicit Project Manager approval.

### Additional Git Rules
- Do not commit directly to main/master branch without approval
- Write clear, concise commit messages following project conventions
- Stage only intended files; never commit secrets or generated files
- Do not amend or rewrite history without approval

---

## Implementation Workflow

1. **Receive approved design** from Architect
2. **Clarify ambiguities** before starting (ask questions)
3. **Implement** per approved design
4. **Write tests** for new functionality
5. **Run tests** and verify they pass
6. **Present diff** for review
7. **Wait for Project Manager approval** to commit
8. **Wait for Project Manager approval** to push

---

## Prohibited Actions

| Action | Status |
|--------|--------|
| Implement unapproved features | ❌ Forbidden |
| Change architecture without review | ❌ Forbidden |
| Refactor without request | ❌ Forbidden |
| Add dependencies without justification | ❌ Forbidden |
| Commit secrets/tokens | ❌ Forbidden |
| Commit without PM approval | ❌ Forbidden |
| Push without PM approval | ❌ Forbidden |
| Skip tests | ❌ Forbidden |
| Break backward compatibility | ❌ Forbidden |
| Assume project state not in repository | ❌ Forbidden |

---

## Documentation Requirements

- Update technical documentation for any API changes
- Document non-obvious implementation decisions
- Keep `DECISIONS/` log updated for architectural decisions
- All TODOs in code must reference a tracked issue or decision

---

## Testing Requirements

- Unit tests for all new functions/methods
- Integration tests for component boundaries
- All tests must pass before presenting for review
- Test coverage must not decrease

---

## Definition of Done

A task is considered done only when:
1. Implementation matches approved design
2. All tests pass
3. Documentation updated
4. Diff presented and reviewed
5. Project Manager explicitly approves commit
6. Project Manager explicitly approves push