---
rfc: "0008"
title: "Prohibitions"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0008: Prohibitions

## Abstract

This document defines the reserved words, prohibited grammatical forms, and disallowed naming patterns within an MGP substrate.  
These prohibitions ensure morphosemantic clarity, prevent ambiguity, and preserve the structural integrity required by the Morpho‑Semantic Governance Protocol (MGP).  
Allowed grammar categories are defined in RFC‑0001.  
Domain boundary implications are defined in RFC‑0009.  
Runtime artifact implications are defined in RFC‑0010.

---

## 1. Scope

This RFC defines:

- reserved words
- prohibited grammatical categories
- prohibited structural patterns
- namespace domain restrictions
- CFN‑related exceptions
- semantic‑emptiness rules
- character‑level prohibitions

This RFC does **not** define naming grammar (RFC‑0001), casing (RFC‑0002), CFNs (RFC‑0003), substrate structure (RFC‑0005), or extension behavior (RFC‑0006).

---

## 2. Reserved Words (PRO‑01)

The following words are **reserved** and MUST NOT appear in any artifact name (file or domain), except when part of a CFN (RFC‑0003):

- `config`, `configs`
- `setting`, `settings`
- `misc`
- `utils`, `helpers`
- `temp`, `tmp`
- `backup`, `final`
- `test`, `tests` (except under `evaluations/`)
- `old`, `new`, `latest`
- `default`, `defaults`

These words encode intent, ambiguity, or non‑semantic categorization and are therefore prohibited.

---

## 3. Prohibited Grammar Categories (PRO‑02)

The following grammatical forms MUST NOT appear in artifact names:

- **Infinitives**  
  Examples: `to-run`, `to-process`

- **Participles used as adjectives**  
  Examples: `processed-data`, `generated-output`

- **Emotional or subjective adjectives**  
  Examples: `smart-agent`, `friendly-tool`

- **Ambiguous modality terms**  
  Examples: `maybe-process`, `should-run`, `could-do`

- **Temporal adjectives**  
  Examples: `future-plan`, `current-state`, `final-version`

- **Ordinal or versioned forms**  
  Examples: `v1`, `v2`, `first`, `second`

These forms introduce ambiguity or encode intent rather than semantics.

---

## 4. Prohibited Structural Patterns (PRO‑03)

The following structural patterns MUST NOT appear:

### 4.1 Mixed Grammar Categories

A single name MUST NOT combine incompatible grammatical categories.  
Example: `run-tools/` (verb + plural noun)

### 4.2 Version‑Encoded Domains

Example: `v1/`, `v2/`

### 4.3 Environment‑Encoded Domains

Example: `prod/`, `dev/`, `staging/`

### 4.4 Workflow‑State Domains

Example: `in-progress/`, `done/`, `archived/`

### 4.5 Intent‑Encoding Names

Example: `should-process/`, `maybe-run/`

These patterns violate morphoSemantic determinism.

---

## 5. Interaction With CFNs (PRO‑04)

Reserved words and prohibited forms MAY appear inside a filename **only** if:

1. the filename is explicitly listed in the CFN Registry (RFC‑0003), and
2. the filename appears exactly as listed.

No other exceptions are permitted.

---

## 6. Namespace Domain Restrictions (PRO‑05)

Namespace domains (RFC‑0005) MUST:

- NOT use reserved words
- NOT use prohibited grammatical forms
- NOT encode versioning or environment
- NOT encode intent or workflow state
- NOT chain multiple namespaces (see RFC‑0006)
- be singular proper nouns

Invalid namespace examples:

- `config/`
- `openai-v1/`
- `smart/`
- `openai/google/` (namespace chain)

---

## 7. Semantic‑Emptiness Prohibitions (PRO‑06)

Artifact names MUST NOT be semantically empty.

The following are prohibited:

- **single‑letter names**  
  Examples: `a.md`, `x/`

- **numeric‑only names**  
  Examples: `123/`, `42.md`

- **hyphen‑only names**  
  Examples: `-`, `--`, `---.md`

- **nonsense tokens**  
  Examples: `misc2/`, `thing.md`, `stuff/`

Semantic emptiness violates ontology clarity (RFC‑0001) and domain boundaries (RFC‑0009).

---

## 8. Principles

- **Clarity**: names MUST be semantically meaningful and unambiguous.
- **Determinism**: prohibited forms prevent misinterpretation of intent as structure.
- **Minimal Exceptions**: only CFNs may violate naming rules, and only when explicitly declared.
- **Structural Purity**: reserved words prevent ad‑hoc or legacy naming patterns.
- **Ontology Integrity**: names MUST reinforce domain boundaries (RFC‑0009).

---

## 9. Examples

### 9.1 Valid

- `agents/`
- `tools/openai/`
- `skills/retrieval/`
- `guardrails/runtime/`
- `evaluations/self-critique/`

### 9.2 Invalid

- `config/` (reserved word)
- `to-run/` (infinitive)
- `smart-agent.md` (emotional adjective)
- `openai-v1/` (version encoding)
- `maybe-process.md` (ambiguous modality)
- `prod/` (environment encoding)
- `run-tools/` (mixed grammar categories)
- `x/` (single‑letter name)
- `123/` (numeric‑only name)
- `--/` (hyphen‑only name)

---

## 10. Security Considerations

This RFC introduces no security considerations.

---

## 11. References

- RFC‑0000: Index and Glossary
- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
- RFC‑0003: Conventional Filenames
- RFC‑0005: Substrate Root
- RFC‑0006: Extensions
- RFC‑0007: Versioning
- RFC‑0009: Domain Boundaries
- RFC‑0010: Runtime Artifacts

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Normative.**  
**Last Updated:** 2026‑03‑27
