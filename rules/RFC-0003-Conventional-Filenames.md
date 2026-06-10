---
rfc: "0003"
title: "Conventional Filenames"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0003: Conventional Filenames

## Abstract

This document defines the Conventional Filename (CFN) class and provides the authoritative registry of filenames exempt from MGP naming and casing requirements. CFNs exist solely to preserve ecosystem compatibility.  
All non‑CFN artifacts MUST follow RFC‑0001 and RFC‑0002.  
CFN placement and substrate purity rules are defined in RFC‑0005.  
Domain boundary interactions are defined in RFC‑0009.  
Runtime artifact rules are defined in RFC‑0010.

---

## 1. Scope

This RFC specifies:

- the definition of a Conventional Filename (CFN)
- the authoritative CFN Registry
- the conditions under which CFNs may appear
- the placement rules for CFNs
- the process for adding new CFNs
- conflict‑resolution rules

This RFC does **not** define naming grammar (RFC‑0001), casing conventions (RFC‑0002), or substrate structure (RFC‑0005).

---

## 2. Definition

A **Conventional Filename (CFN)** is a filename that:

1. violates one or more MGP naming or casing requirements, and
2. is preserved for compatibility with established ecosystem conventions, and
3. appears exactly as listed in the CFN Registry.

CFNs MUST be treated as opaque tokens.  
They MUST NOT be morphologically interpreted, renamed, or reformatted.

---

## 3. CFN Requirements

CFNs:

- MUST appear exactly as written in the registry
- MUST NOT be renamed, altered, or reformatted
- MUST NOT be used as general‑purpose filenames
- MUST NOT appear inside substrate domains unless explicitly permitted by RFC‑0005
- MUST NOT override naming grammar for any non‑CFN artifact
- MUST NOT be used to bypass prohibited patterns (RFC‑0008)

CFNs are exceptions, not alternatives.

---

## 4. CFN Registry (Authoritative List)

The following filenames are recognized as CFNs:

| Filename         | Purpose                       |
| ---------------- | ----------------------------- |
| `README.md`      | Repository overview           |
| `LICENSE`        | Licensing information         |
| `CHANGELOG.md`   | Version history               |
| `.gitignore`     | Git ignore rules              |
| `.gitattributes` | Git attribute rules           |
| `.gitkeep`       | Placeholder for empty domains |

No other filenames are considered CFNs.

---

## 5. CFN Placement Rules

### 5.1 Root Placement

CFNs MAY appear at the substrate root **only** when:

- they are included in the registry, and
- their presence does not violate substrate purity (RFC‑0005).

Examples of valid root CFNs:

- `README.md`
- `LICENSE`

### 5.2 Subdirectory Placement

CFNs MAY appear inside subdirectories **only** when:

- the CFN is ecosystem‑required for that directory’s function, and
- the placement does not conflict with domain semantics (RFC‑0009), and
- the CFN is not used to bypass naming grammar.

Examples:

- `.gitkeep` MAY appear inside any empty domain.
- `.gitignore` MAY appear inside any directory.

### 5.3 Prohibited Placement

CFNs MUST NOT:

- appear inside namespace directories unless ecosystem‑required
- appear inside runtime directories (RFC‑0010)
- appear inside directories where they would conflict with domain semantics

---

## 6. Adding New CFNs

A filename MAY be added to the CFN Registry only if **all** of the following conditions are met:

### 6.1 Eligibility Criteria

1. The filename is required for ecosystem or tooling compatibility.
2. The filename is widely recognized across multiple systems or runtimes.
3. The filename cannot be renamed without breaking compatibility.
4. The filename does not introduce ambiguity or violate substrate purity.

### 6.2 Approval Process

1. A proposal is submitted to the MGP Working Group.
2. The Working Group evaluates the filename against the eligibility criteria.
3. If approved, this RFC is updated with:
   - a new version entry
   - the new CFN added to the registry
4. The update MUST be versioned according to RFC‑0007.

### 6.3 Conflict Resolution

If a proposed CFN conflicts with:

- naming grammar (RFC‑0001)
- casing rules (RFC‑0002)
- domain boundaries (RFC‑0009)
- substrate purity (RFC‑0005)

…the CFN MUST NOT be added.

---

## 7. Principles

- CFNs are **exceptions**, not alternatives.
- The registry MUST remain minimal and stable.
- MorphoSemantic rules (RFC‑0001) apply to all non‑CFN artifacts.
- Casing rules (RFC‑0002) do not apply to CFNs.
- Substrate purity (RFC‑0005) MUST be preserved.

---

## 8. Security Considerations

This RFC introduces no security considerations.

---

## 9. References

- RFC‑0000: Index and Glossary
- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
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
