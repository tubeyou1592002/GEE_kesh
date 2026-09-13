# AI Handoff

Project state transfer document for AI/Coding Agent.

---

## Project Goal

Build a cloud-based system for processing selected satellite imagery using Google Earth Engine (GEE) and returning results to the application. The system accepts processing requests, executes them on GEE asynchronously, monitors task progress, and delivers results back to users.

---

## Roles

| Role | Responsibility |
|------|----------------|
| **Project Manager** | Decides what to build; defines scope, priorities; final acceptance; approves commits/pushes |
| **Architect** | Decides how to design; defines architecture, contracts, interfaces; reviews implementation; prevents scope creep |
| **Coding Agent** | Implements approved design; writes tests; fixes bugs; documents implementation; presents diffs; reports test results |

> **Manager decides what to build.**
> **Architect decides how it should be designed.**
> **Coding Agent implements the approved design.**

---

## Current State

- Repository initialized
- **Phase:** Block 0 — Foundation & Documentation
- **Status:** Creating base documentation structure
- **Branch:** main (initial)
- **Commits:** None yet (awaiting Project Manager approval)

---

## Current Scope

**Only:** Create base project documentation:
- PROJECT_GOVERNANCE.md
- ARCHITECTURE.md
- ROADMAP.md
- DEVELOPMENT_RULES.md
- GEE_INTEGRATION.md
- PROCESSING_CONTRACTS.md
- AI_HANDOFF.md
- DECISIONS/ directory

---

## Out of Scope

The following are **explicitly out of scope** for the current phase and must not be implemented:

- GEE implementation (authentication, API calls, processing)
- Authentication implementation
- API implementation
- UI / Frontend
- Processing algorithms
- Database / persistence layer
- Deployment configuration
- Production infrastructure
- CI/CD pipelines
- Monitoring / observability
- Any code beyond documentation

---

## Next Step

After review and approval of all Block 0 documentation by Project Manager and Architect:

1. Architect defines detailed scope for **Block 1 — GEE Authentication / Connectivity**
2. Project Manager approves Block 1 scope
3. Coding Agent implements Block 1 per approved design

---

## Critical Rules

### Repository is Source of Truth
- Do not invent project state
- Do not assume files, commits, or branches exist unless verified
- All project state must be discoverable in the repository

### Do Not Assume
- Do not assume implementation details not in documentation
- Do not assume architectural decisions not explicitly documented
- Do not assume scope beyond what is explicitly approved

### Authority Boundaries
- Coding Agent **only** implements approved designs
- Coding Agent **never** decides what to build or how to design it
- Coding Agent **never** commits or pushes without explicit Project Manager approval

### Documentation First
- All work begins with documentation review
- Implementation follows approved contracts and architecture
- Changes to contracts/architecture require Architect approval

---

## Key References

- `docs/PROJECT_GOVERNANCE.md` — Role definitions and authority
- `docs/ARCHITECTURE.md` — System architecture and component boundaries
- `docs/ROADMAP.md` — Project phases and current focus
- `docs/DEVELOPMENT_RULES.md` — Coding Agent rules and constraints
- `docs/GEE_INTEGRATION.md` — GEE integration topics (all TBD)
- `docs/PROCESSING_CONTRACTS.md` — Component contracts (all Draft)
- `docs/DECISIONS/` — Architectural decision log (empty)

---

## Immediate Action Required

**None.** Awaiting Project Manager and Architect review of Block 0 documentation. No implementation work should begin until explicitly authorized.