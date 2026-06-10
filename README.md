# Morpho‑Semantic Governance Protocol (MGP)

MGP is a filesystem‑level governance protocol for agent substrates.  
It defines a deterministic morpho‑Semantic grammar that orchestrators, agents, and tools can rely on for structure, clarity, and long‑term maintainability.

MGP is intentionally minimal:

- one declaration file
- one canonical ontology
- one naming grammar
- one linter  
  Everything else is defined normatively in the RFC suite.

---

## Why MGP Exists

Agent ecosystems drift.  
Naming collapses.  
Directories sprawl.  
Workflows become ungovernable.  
Every team invents its own structure, and every orchestrator must guess.

MGP eliminates ambiguity by defining a **universal substrate grammar**:

- deterministic directory ontology
- strict naming rules
- enforced placement rules
- substrate declaration
- linter‑verified invariants

This gives every swarm — large or small — a predictable, governed foundation.

---

## Quickstart

This is the entire process for creating a valid MGP substrate.  
All normative rules live in the RFCs; this guide simply points to them.

## 1. Declare the Substrate Root

Create a file named:

```tree
mgp.md
```

This marks the directory as an MGP substrate.

**See:**

- RFC‑0001 — Substrate Declaration

---

## 2. Create the Canonical Ontology

MGP requires ten top‑level directories.  
Their definitions, purpose, and constraints are fully specified in the RFC suite.

**See:**

- RFC‑0005 — Substrate Structure
- RFC‑0002 — Naming & Ontology Rules

---

## 3. Add Any Valid Artifact

Example:

```tree
agents/classifier-agent.md
```

Follow the naming grammar:

- singular nouns for files
- plural nouns for directories
- kebab‑case everywhere

**See:**

- RFC‑0002 — Naming & Ontology Rules

---

## 4. Install & Run the Linter

### Install

If using npm:

```tree
npm install -g mgp-lint
```

Or add it to your project:

```tree
npm install --save-dev mgp-lint
```

### Run

From the substrate root:

```tree
mgp-lint .
```

The linter enforces:

- ontology correctness
- naming grammar
- file placement rules
- substrate declaration
- structural invariants

**See:**

- RFC‑0004 — Linter Behavior & Enforcement

---

## 5. Load the Substrate in Your Orchestrator

```js
const substrate = loadSubstrate("./");
```

A compliant orchestrator will automatically load all governed domains.

**See:**

- RFC‑0003 — Orchestrator Integration

---

## Development Philosophy

MGP is designed to be:

- **minimal** — no duplication, no examples in the spec repo
- **deterministic** — every artifact has one correct home
- **governed** — the linter enforces the protocol
- **scalable** — works for tiny swarms and massive ecosystems
- **future‑proof** — RFC‑driven evolution, not ad‑hoc changes

This repo intentionally contains **no examples** and **no swarm code**.  
Real‑world validation happens on external swarms before any adoption guidance is published.

---

## Next Steps

To understand the protocol fully, read:

RFC‑0000 — Index and Glossary
RFC‑0001 — Naming and Ontology
RFC‑0002 — Casing
RFC‑0003 — Conventional Filenames
RFC‑0004 — Linter
RFC‑0005 — Substrate Root
RFC‑0006 — Extensions
RFC‑0007 — Versioning
RFC‑0008 — Prohibitions

Once validated on a real swarm, MGP becomes a powerful governance layer for any agent ecosystem.
