---
rfc: "0009"
title: "Domain Boundaries"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0009: Domain Boundaries

## Abstract

This document defines the semantic boundaries between the ten canonical substrate domains. It provides deterministic placement rules, disambiguation logic, namespace constraints, and domain decision trees to prevent drift caused by overlapping semantics.  
Naming grammar is defined in RFC‑0001; casing is defined in RFC‑0002; substrate structure is defined in RFC‑0005; runtime artifact rules are defined in RFC‑0010.

---

## 1. Scope

This RFC defines:

- the semantic purpose of each canonical domain
- rules for resolving ambiguous artifact placement
- domain decision trees
- namespace boundary rules
- extension boundary rules
- constraints on cross‑domain relationships

This RFC does **not** define naming grammar (RFC‑0001), casing (RFC‑0002), CFNs (RFC‑0003), substrate structure (RFC‑0005), or extension behavior (RFC‑0006).

---

## 2. Domain Semantics

Each canonical domain has a single, non‑overlapping semantic purpose.  
The canonical domain list is defined in RFC‑0005:

| Domain          | Purpose                                                     |
| --------------- | ----------------------------------------------------------- |
| `agents/`       | Autonomous actors and their definitions                     |
| `tools/`        | Reusable, atomic callable capabilities                      |
| `prompts/`      | Prompt templates and components                             |
| `memories/`     | Persistent or transient state used by agents                |
| `workflows/`    | Multi‑step orchestrations                                   |
| `skills/`       | Composite capabilities built from tools, prompts, workflows |
| `guardrails/`   | Constraints, safety rules, enforcement logic                |
| `instructions/` | Procedural guides and operational instructions              |
| `logs/`         | Execution traces and historical records                     |
| `evaluations/`  | Benchmarks, tests, and performance assessments              |

Domains MUST be interpreted **semantically**, not grammatically.

---

## 3. Domain Decision Rules

### 3.1 Tools vs Skills

**Rule:**  
A _tool_ is atomic.  
A _skill_ is composite.

- If the artifact wraps or chains multiple tools → `skills/`
- If the artifact exposes a single callable capability → `tools/`

### 3.2 Memories vs Logs

**Rule:**  
A _memory_ is used by agents.  
A _log_ is produced by agents.

- If the artifact is read during execution → `memories/`
- If the artifact is written during execution → `logs/`

### 3.3 Guardrails vs Instructions

**Rule:**  
Guardrails constrain behavior.  
Instructions guide behavior.

- If the artifact restricts or validates → `guardrails/`
- If the artifact describes how to perform a task → `instructions/`

### 3.4 Workflows vs Instructions

**Rule:**  
Workflows orchestrate.  
Instructions describe.

- If the artifact coordinates multiple steps or agents → `workflows/`
- If the artifact documents a procedure → `instructions/`

### 3.5 Evaluations vs Logs

**Rule:**  
Evaluations measure performance.  
Logs record execution.

- If the artifact is a benchmark, test, or scoring mechanism → `evaluations/`
- If the artifact is a trace or record → `logs/`

---

## 4. Domain Decision Tree

### 4.1 High‑Level Decision Tree

```
Is the artifact a collection? → plural noun → domain directory
Else:
  Does it define an autonomous actor? → agents/
  Does it define a callable capability? → tools/
  Does it combine multiple capabilities? → skills/
  Does it orchestrate multi-step processes? → workflows/
  Does it constrain or validate? → guardrails/
  Does it instruct or guide? → instructions/
  Does it store state used by agents? → memories/
  Does it record execution history? → logs/
  Does it measure performance? → evaluations/
  Else → prohibited (RFC‑0008)
```

---

## 5. Namespace Boundary Rules

Namespace domains (RFC‑0001, RFC‑0006) MUST:

- be singular proper nouns
- not encode versioning, environment, or intent
- not chain multiple namespaces
- not redefine domain semantics
- not contain runtime artifacts (RFC‑0010)

Example (valid):

```
tools/openai/embeddings/
```

Example (invalid):

```
tools/openai/google/anthropic/   ← namespace chain
```

---

## 6. Extension Boundary Rules

Extensions (RFC‑0006) MUST:

- inherit the semantics of their parent domain
- not redefine or override domain semantics
- not exceed the extension depth limit
- not introduce shadow ontologies
- not introduce new semantic categories

Example (invalid):

```
tools/vendor/product/feature/subfeature/   ← depth > 3
```

---

## 7. Runtime Boundary Rules

Runtime artifacts (RFC‑0010):

- MUST appear only under `logs/runtime/` or `memories/runtime/`
- MUST NOT appear in canonical domains
- MUST NOT influence domain placement
- MUST NOT be linted for naming grammar

Example (invalid):

```
tools/runtime/   ← runtime directory in wrong domain
```

---

## 8. Cross‑Domain Prohibitions

Artifacts MUST NOT:

- encode multiple domain semantics
- appear in more than one domain
- be placed based on convenience or implementation detail
- redefine domain semantics through extensions (RFC‑0006)
- use modifiers to force domain reinterpretation
- use numeric tokens to imply domain semantics
- use namespace directories to bypass domain rules

---

## 9. Examples

### 9.1 Valid

- `skills/retrieval/`
- `tools/openai/embeddings/`
- `memories/session/`
- `logs/runtime/`
- `guardrails/runtime/`

### 9.2 Invalid

- `tools/retrieval/` (composite → skills/)
- `skills/openai/` (namespace misuse)
- `memories/logs/` (mixed semantics)
- `instructions/guardrails/` (cross‑domain nesting)
- `tools/runtime/` (runtime in wrong domain)
- `tools/openai/google/` (namespace chain)

---

## 10. Security Considerations

This RFC introduces no security considerations.

---

## 11. References

- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
- RFC‑0005: Substrate Root
- RFC‑0006: Extensions
- RFC‑0007: Versioning
- RFC‑0008: Prohibitions
- RFC‑0010: Runtime Artifacts

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Normative.**  
**Last Updated:** 2026‑03‑27
