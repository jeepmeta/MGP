---
rfc: "0006"
title: "Extensions"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0006: Extensions

## Abstract

This document defines the sanctioned mechanism for extending an MGP substrate without modifying the top‑level ontology.  
Extensions MUST preserve substrate purity (RFC‑0005) and comply with naming grammar (RFC‑0001), casing (RFC‑0002), domain boundaries (RFC‑0009), runtime artifact rules (RFC‑0010), and prohibited pattern rules (RFC‑0008).  
This RFC defines extension types, placement rules, depth limits, and inheritance constraints.

---

## 1. Scope

This RFC defines:

- the extension mechanism
- allowed extension domain types
- constraints on extension placement
- extension depth limits
- namespace extension constraints
- extension inheritance rules
- prohibited extension behaviors

This RFC does **not** define naming grammar, casing, CFNs, or linter behavior.  
Those are defined in RFC‑0001, RFC‑0002, RFC‑0003, and RFC‑0004.

---

## 2. Extension Mechanism

### 2.1 No New Top‑Level Domains (EXT‑01)

An MGP substrate MUST contain exactly the ten canonical top‑level domains defined in RFC‑0005.

Extensions MUST be implemented **only** as subdomains under one of the canonical domains.

### 2.2 Grammar Alignment (EXT‑02)

Extensions MUST align with the grammatical category of their parent domain:

- Under plural‑noun domains → subdomains MUST be valid extension types (Section 3)
- Under namespace domains → extensions MUST follow naming grammar (RFC‑0001)
- Under capability domains → extensions MUST refine or specialize the capability

Extensions MUST NOT alter the grammatical interpretation of their parent domain.

### 2.3 Extension Depth Limit (EXT‑03)

To prevent shadow ontologies, extension depth is limited:

- Maximum depth under any canonical domain: **3 levels**
- Namespace directories do **not** count toward depth
- Runtime directories (RFC‑0010) do **not** count toward depth

Example (valid):

```
tools/openai/embeddings/
```

Example (invalid):

```
tools/vendor/product/feature/subfeature/
```

### 2.4 Extension Inheritance (EXT‑04)

Extensions MUST inherit the semantics of their parent domain.

Extensions MUST NOT:

- redefine the parent domain’s semantic category
- introduce new semantic categories
- create parallel ontologies
- override domain boundaries (RFC‑0009)

### 2.5 Namespace Extension Constraints (EXT‑05)

Namespace extensions MUST:

- be singular proper nouns
- not encode versioning, environment, or intent
- not proliferate without semantic justification
- not exceed one namespace level per extension path

Example (valid):

```
tools/openai/embeddings/
```

Example (invalid):

```
tools/openai/google/anthropic/   ← namespace chain (invalid)
```

---

## 3. Allowed Extension Types (EXT‑06)

Extensions MAY take the following forms:

| Type                 | Form        | Purpose                                    |
| -------------------- | ----------- | ------------------------------------------ |
| Category Domain      | plural noun | Groups related artifacts                   |
| Capability Domain    | base verb   | Defines a capability or operation          |
| Instructional Domain | gerund      | Defines a process or procedural refinement |
| Namespace Domain     | proper noun | Scopes external systems or vendors         |

No other domain types are permitted.

---

## 4. Prohibited Extensions (EXT‑07)

Extensions MUST NOT:

- introduce new top‑level domains
- introduce new domain types
- violate naming grammar (RFC‑0001)
- violate casing (RFC‑0002)
- violate domain boundaries (RFC‑0009)
- violate runtime artifact rules (RFC‑0010)
- introduce prohibited or reserved terms (RFC‑0008)
- encode versioning, intent, or metadata in domain names
- redefine or override ontology semantics
- exceed the extension depth limit (EXT‑03)

---

## 5. Examples

### 5.1 Valid Extensions

- `guardrails/runtime/`
- `skills/retrieval/`
- `workflows/adaptation/`
- `evaluations/self-critique/`
- `tools/openai/embeddings/`

### 5.2 Invalid Extensions

- `runtime/` (new top‑level domain)
- `skills/v1/` (versioning encoded in name)
- `agents/to-run/` (infinitive; see RFC‑0008)
- `tools/openai-tools/` (invalid namespace form)
- `tools/vendor/product/feature/subfeature/` (depth > 3)
- `tools/openai/google/` (namespace chain)

---

## 6. Security Considerations

This RFC introduces no security considerations.

---

## 7. References

- RFC‑0000: Index and Glossary
- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
- RFC‑0003: Conventional Filenames
- RFC‑0004: Linter
- RFC‑0005: Substrate Root
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
