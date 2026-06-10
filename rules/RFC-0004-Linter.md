---
rfc: "0004"
title: "Linter"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0004: Linter

## Abstract

This document defines the normative requirements for any implementation that validates MGP substrate compliance.  
A compliant linter MUST enforce naming grammar (RFC‑0001), casing (RFC‑0002), conventional filename handling (RFC‑0003), substrate structure (RFC‑0005), domain boundaries (RFC‑0009), runtime artifact rules (RFC‑0010), and prohibited patterns (RFC‑0008).  
This RFC specifies enforcement behavior, traversal requirements, error schemas, version negotiation, and completeness criteria.

---

## 1. Scope

This RFC defines:

- the responsibilities of a compliant linter
- substrate traversal requirements
- error classification and error schema
- namespace and domain boundary handling
- CFN handling
- runtime artifact handling
- version negotiation
- completeness criteria

This RFC does **not** redefine naming grammar, casing, CFNs, substrate structure, or prohibitions.  
Those are defined in RFC‑0001, RFC‑0002, RFC‑0003, RFC‑0005, RFC‑0008, RFC‑0009, and RFC‑0010.

---

## 2. Linter Responsibilities

A compliant linter MUST validate all of the following:

### 2.1 Naming Grammar (RFC‑0001)

- plural noun domains
- singular noun files
- base verb files
- gerund files
- head noun rule
- modifier rules
- numeric token rules
- namespace domain interpretation

### 2.2 Casing (RFC‑0002)

- enforcement of kebab‑case
- rejection of snake_case, camelCase, PascalCase, MixedCase, uppercase forms
- enforcement of hyphen rules
- enforcement of allowed character set

### 2.3 Conventional Filenames (RFC‑0003)

- CFNs MUST match the registry exactly
- CFNs MUST be treated as opaque
- undeclared CFNs MUST be flagged
- CFNs MUST NOT be morphologically analyzed
- CFN placement MUST follow RFC‑0003 and RFC‑0005

### 2.4 Substrate Structure (RFC‑0005)

- only the ten canonical top‑level domains
- presence of `mgp.md`
- no additional root‑level files except CFNs
- no hidden or system files at substrate root
- correct identification of namespace domains
- enforcement of substrate purity

### 2.5 Domain Boundaries (RFC‑0009)

- correct placement of artifacts
- correct interpretation of domain semantics
- detection of cross‑domain leakage
- detection of ambiguous or conflicting placements

### 2.6 Runtime Artifacts (RFC‑0010)

- runtime artifacts MUST appear only in allowed runtime directories
- runtime artifacts MUST NOT be linted for naming grammar
- runtime artifacts MUST NOT appear in canonical domains
- runtime artifacts MUST NOT be committed to version control

### 2.7 Prohibited Patterns (RFC‑0008)

- emotional or subjective descriptors
- infinitives
- ambiguous or intent‑encoding forms
- reserved or disallowed terms
- version‑encoded names

---

## 3. Substrate Traversal Requirements

A compliant linter MUST:

- traverse the entire substrate recursively
- validate every artifact name except runtime artifacts (RFC‑0010)
- validate domain grammar at every level
- validate namespace domains
- validate CFNs
- detect disallowed files
- detect missing required domains
- detect unknown top‑level domains
- detect extension depth violations (RFC‑0006)

Traversal MUST be deterministic.

---

## 4. Error Classification

A compliant linter MUST classify violations using the following stable error codes:

| Code        | Meaning                    |
| ----------- | -------------------------- |
| **MGP‑001** | Invalid grammar category   |
| **MGP‑002** | Invalid casing             |
| **MGP‑003** | Invalid domain grammar     |
| **MGP‑004** | Undeclared CFN             |
| **MGP‑005** | Reserved word violation    |
| **MGP‑006** | Prohibited pattern         |
| **MGP‑007** | Invalid namespace domain   |
| **MGP‑008** | Substrate purity violation |
| **MGP‑009** | Unknown top‑level domain   |
| **MGP‑010** | Runtime artifact violation |
| **MGP‑011** | Domain boundary violation  |
| **MGP‑012** | Extension depth violation  |

Error messages MUST reference the violated RFC section.

---

## 5. Error Schema

A compliant linter MUST output errors using the following canonical schema:

```json
{
  "code": "MGP-XXX",
  "path": "string (relative path to artifact)",
  "message": "string (human-readable explanation)",
  "rfc": "RFC-XXXX Section Y.Z",
  "suggestion": "string (optional auto-fix guidance)"
}
```

Requirements:

- `code` MUST be one of the codes in Section 4
- `path` MUST be relative to the substrate root
- `message` MUST be actionable
- `rfc` MUST reference the violated rule
- `suggestion` MAY be omitted

---

## 6. Auto‑Fix Guidelines

A compliant linter MAY provide auto‑correction suggestions.

Auto‑fixes MUST:

- never change semantics
- never rename CFNs
- never move artifacts across domains
- never modify runtime artifacts
- never introduce new violations

Auto‑fixes MAY:

- correct casing
- correct hyphen usage
- correct pluralization when unambiguous
- remove prohibited modifiers
- suggest domain relocation (but MUST NOT perform it automatically)

---

## 7. Version Negotiation

A compliant linter MUST:

- declare the MGP version it supports
- detect version mismatches between `mgp.md` and the RFC suite
- warn when the substrate references outdated RFC versions
- refuse to validate substrates referencing future RFC versions

Versioning rules are defined in RFC‑0007.

---

## 8. Completeness Requirements

A linter implementation is considered **complete** if it:

- enforces all normative requirements from RFC‑0001, RFC‑0002, RFC‑0003, RFC‑0005, RFC‑0006, RFC‑0008, RFC‑0009, RFC‑0010
- correctly identifies namespace domains
- correctly handles CFNs
- validates domain grammar
- validates file grammar
- validates casing
- validates substrate purity
- validates runtime artifact placement
- provides actionable error messages
- supports CI integration
- implements the canonical error schema

Partial implementations MUST NOT be considered compliant.

---

## 9. Principles

- **Determinism**: identical substrates MUST produce identical results across implementations.
- **Minimal Exceptions**: only CFNs, namespace domains, and runtime artifacts are exceptions, and all are strictly defined.
- **Clarity**: violations MUST be unambiguous and actionable.
- **Morphosemantic Precedence**: grammar determines meaning.
- **Purity**: substrate structure MUST remain clean and predictable.

---

## 10. Examples

### 10.1 Valid

- `agents/`
- `tools/openai/` (namespace domain)
- `security-agent.md`
- `logging.md`
- `README.md` (CFN)
- `logs/runtime/session-1234.json` (runtime artifact)

### 10.2 Invalid

- `smart-agent.md` (emotional adjective)
- `to-run.md` (infinitive)
- `openai-tools/` (namespace MUST be singular)
- `policies.md` (files MUST be singular nouns)
- `config/` (reserved word)
- `random/` (unknown top‑level domain)
- `logs/tmp/` (invalid runtime directory)

---

## 11. Security Considerations

This RFC introduces no security considerations.

---

## 12. References

- RFC‑0000: Index and Glossary
- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
- RFC‑0003: Conventional Filenames
- RFC‑0005: Substrate Root
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
