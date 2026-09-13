# Project Governance

This document defines the collaboration rules and authority boundaries for the three roles in the GEE_kesh project.

---

## Roles and Responsibilities

### Project Manager

**Authority:**
- Defines project goals and objectives
- Sets priorities and scope
- Makes product decisions
- Final acceptance of deliverables
- Approves commits and pushes to the repository

**Responsibilities:**
- Defines what to build
- Manages scope and prevents scope creep
- Accepts or rejects completed work
- Provides explicit approval for commits and pushes

---

### Architect

**Authority:**
- Defines system architecture
- Defines contracts and interfaces
- Breaks project into blocks/phases
- Conducts architecture reviews
- Detects and approves architectural changes
- Prevents scope creep at architectural level

**Responsibilities:**
- Decides how the system should be designed
- Defines contracts between components
- Reviews and approves technical designs
- Ensures architectural integrity

---

### Coding Agent

**Authority:**
- Implements approved designs
- Writes tests for implemented features
- Fixes bugs within approved scope
- Creates technical documentation for implementation
- Presents diffs for review
- Reports test results

**Responsibilities:**
- Implements the approved design
- Does NOT decide what to build
- Does NOT decide how to design the system
- Only implements what has been explicitly approved

---

## Explicit Authority Statement

> **Manager decides what to build.**
> **Architect decides how it should be designed.**
> **Coding Agent implements the approved design.**

---

## Decision Making Flow

1. **Project Manager** defines requirements and scope
2. **Architect** designs the solution and defines contracts
3. **Project Manager** approves the architecture
4. **Coding Agent** implements per approved design
5. **Architect** reviews implementation against contracts
6. **Project Manager** accepts or requests changes
7. **Project Manager** explicitly approves commit and push

---

## Commit and Push Rules

> **DO NOT COMMIT until explicit approval from the Project Manager.**

> **DO NOT PUSH until explicit approval from the Project Manager.**

Even if the Coding Agent believes changes are complete and correct, they are NOT authorized to commit or push without explicit Project Manager approval.

---

## Scope Control

- Any change to scope requires Project Manager approval
- Any architectural change requires Architect review and Project Manager approval
- Coding Agent must not implement features outside approved scope
- Coding Agent must not refactor without explicit request