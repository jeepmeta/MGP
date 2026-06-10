---
rfc: "0005"
title: "Substrate Root"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0005: Substrate Root

## Abstract

This document defines the canonical structure of the MGP substrate root. It specifies the ten required top‑level domains, the placement of the substrate declaration, and the constraints governing root‑level purity.  
Naming grammar, casing, and prohibited patterns are defined in RFC‑0001, RFC‑0002, and RFC‑0008.  
Domain boundaries are defined in RFC‑0009.  
Runtime artifact rules are defined in RFC‑0010.

---

## 1. Scope

This RFC defines:

- the required top‑level domain structure
- the placement and role of the substrate declaration (`mgp.md`)
- root‑level purity constraints
- the rule prohibiting additional top‑level domains
- multi‑substrate composition rules
- symbolic link rules

This RFC does **not** define naming grammar (RFC‑0001), casing (RFC‑0002), CFNs (RFC‑0003), or extension behavior (RFC‑0006).

---

## 2. Substrate Root Structure

An MGP substrate consists of **exactly ten** canonical top‑level domains. These domains define the substrate ontology and MUST appear at the root level.

| Domain          | Purpose                                                        |
| --------------- | -------------------------------------------------------------- |
| `agents/`       | Autonomous actors and their definitions                        |
| `tools/`        | Reusable, callable capabilities                                |
| `prompts/`      | Prompt templates and prompt components                         |
| `memories/`     | Persistent or transient state used by agents                   |
| `workflows/`    | Multi‑step orchestrations                                      |
| `skills/`       | Composite capabilities built from tools, prompts, or workflows |
| `guardrails/`   | Constraints, safety rules, and enforcement logic               |
| `instructions/` | Procedural guides and operational instructions                 |
| `logs/`         | Execution traces and historical records                        |
| `evaluations/`  | Benchmarks, tests, and performance assessments                 |

These domains MUST:

- be plural nouns
- be lowercase
- use kebab‑case (RFC‑0002)
- represent semantic domains (RFC‑0001)
- follow domain boundary rules (RFC‑0009)

No additional top‑level domains are permitted.

---

## 3. Substrate Declaration

The substrate root MUST contain a single file:

- `mgp.md` — the substrate declaration

`mgp.md` MUST:

- appear at the substrate root
- define the substrate’s version and metadata
- reference (but not duplicate) the CFN registry (RFC‑0003)
- reference the RFC suite rather than restating grammar or ontology
- not define naming grammar or ontology (see RFC‑0001)

No other non‑CFN files are permitted at the root.

---

## 4. Root‑Level Purity

The substrate root MUST contain **only**:

- the ten canonical domains
- the substrate declaration (`mgp.md`)
- CFNs explicitly permitted by RFC‑0003

The following MUST NOT appear at the substrate root:

- hidden files (e.g., `.DS_Store`)
- system files
- additional domains
- arbitrary configuration files
- namespace domains
- runtime artifacts (RFC‑0010)
- symbolic links (see Section 6)

Violations MUST be flagged by the linter (RFC‑0004).

---

## 5. No New Top‑Level Rule

No new top‑level domains MAY be added to the substrate.

Future concepts MUST:

- be placed as subdomains under one of the ten canonical domains, or
- be introduced through the extension mechanism defined in RFC‑0006

Extensions MUST NOT modify the top‑level ontology.

---

## 6. Symbolic Link Rules

Symbolic links introduce ambiguity and MUST NOT appear anywhere in the substrate.

A compliant substrate MUST:

- NOT contain symbolic links at the root
- NOT contain symbolic links inside any canonical domain
- NOT contain symbolic links pointing outside the substrate

If symbolic links are required for execution environments, they MUST be created dynamically and MUST NOT be committed to the substrate.

---

## 7. Multi‑Substrate Composition

Multi‑substrate systems (e.g., swarm‑of‑swarms architectures) MUST follow these rules:

### 7.1 No Nested Substrates

A substrate MUST NOT contain another substrate root.  
Specifically:

- no nested `mgp.md`
- no nested copies of the ten canonical domains

### 7.2 Federation, Not Embedding

Multiple substrates MAY coexist **side‑by‑side**, but MUST NOT be nested.

Example (valid):

```
substrate-a/
substrate-b/
```

Example (invalid):

```
substrate-a/
  agents/
  tools/
  substrate-b/   ← nested substrate (invalid)
```

### 7.3 Orchestrator Responsibility

Orchestrators MAY load multiple substrates but MUST treat each as an independent root.

---

## 8. Interaction With Other RFCs

- Naming grammar: **RFC‑0001**
- Casing: **RFC‑0002**
- Conventional filenames: **RFC‑0003**
- Linter enforcement: **RFC‑0004**
- Extensions: **RFC‑0006**
- Versioning: **RFC‑0007**
- Prohibitions: **RFC‑0008**
- Domain boundaries: **RFC‑0009**
- Runtime artifacts: **RFC‑0010**

This RFC defines structure only; all naming and casing requirements are external.

---

## 9. Security Considerations

This RFC introduces no security considerations.

---

## 10. References

- RFC‑0000: Index and Glossary
- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
- RFC‑0003: Conventional Filenames
- RFC‑0004: Linter
- RFC‑0006: Extensions
- RFC‑0007: Versioning
- RFC‑0008: Prohibitions
- RFC‑0009: Domain Boundaries
- RFC‑0010: Runtime Artifacts

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Normative.**  
**Last Updated:** 2026‑03‑27
