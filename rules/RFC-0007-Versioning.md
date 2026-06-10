---
rfc: "0007"
title: "Versioning"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0007: Versioning

## Abstract

This document defines the versioning model for the Morpho‑Semantic Governance Protocol (MGP), its RFC suite, and the substrate declaration (`mgp.md`).  
All version identifiers MUST follow Semantic Versioning.  
This RFC additionally defines migration guidelines, compatibility rules, and the deprecation process for RFCs.  
Domain boundary implications are defined in RFC‑0009.  
Runtime artifact implications are defined in RFC‑0010.

---

## 1. Scope

This RFC defines:

- the versioning scheme for MGP and all RFCs
- the meaning of major, minor, and patch increments
- changelog requirements
- update obligations for agents and tooling
- migration guidelines
- compatibility matrix rules
- RFC deprecation process

This RFC does **not** define naming grammar, casing, substrate structure, or extension behavior.

---

## 2. Versioning Model

MGP and all RFCs MUST use **Semantic Versioning** in the form:

```
MAJOR.MINOR.PATCH
```

### 2.1 Major Version (X.0.0)

A major version increment MUST occur when:

- naming grammar changes (RFC‑0001)
- casing rules change (RFC‑0002)
- substrate structure changes (RFC‑0005)
- extension semantics change (RFC‑0006)
- domain boundary rules change in a breaking manner (RFC‑0009)
- runtime artifact rules change in a breaking manner (RFC‑0010)
- prohibited patterns change in a breaking manner (RFC‑0008)

Major increments indicate breaking changes.

### 2.2 Minor Version (X.Y.0)

A minor version increment MUST occur when:

- new capabilities are added
- clarifications are introduced
- non‑breaking normative requirements are added
- new examples or guidance are added

Minor increments MUST NOT break existing substrates.

### 2.3 Patch Version (X.Y.Z)

A patch version increment MUST occur when:

- editorial corrections are made
- formatting or typographical fixes occur
- non‑normative clarifications are added
- references are updated

Patch increments MUST NOT change normative behavior.

---

## 3. Changelog Requirements

All RFCs and the substrate declaration (`mgp.md`) MUST include a **Changelog** section.

Changelog entries MUST:

- appear in reverse chronological order
- include a date and version identifier
- describe the change precisely and concisely
- not duplicate content from other RFCs

Example format:

```
## Changelog
- 2026‑03‑27 (v1.0.0): Initial version.
```

---

## 4. Update Requirements

Agents and tooling MUST:

- reference the latest version of each RFC
- validate substrate compliance according to the latest normative versions
- treat outdated RFC versions as superseded
- warn when encountering deprecated RFCs
- refuse to validate substrates referencing future RFC versions

Linter behavior for version mismatches is defined in RFC‑0004.

---

## 5. Migration Guidelines

When a new version of MGP or an RFC is released:

### 5.1 Backward Compatibility

- Minor and patch updates MUST be backward‑compatible.
- Major updates MAY break compatibility.

### 5.2 Migration Steps

Implementations SHOULD:

1. Read the changelog for breaking changes.
2. Update substrate artifacts to comply with new rules.
3. Update `mgp.md` to reference the new version.
4. Re‑run the linter (RFC‑0004).

### 5.3 Migration Tools

Migration MAY be assisted by:

- linter auto‑fix suggestions (RFC‑0004)
- substrate‑level migration scripts (implementation‑specific)

### 5.4 Migration Windows

Organizations MAY define migration windows, but MUST NOT modify the protocol’s version semantics.

---

## 6. Compatibility Matrix

A compatibility matrix MUST be maintained in `mgp.md` or project documentation.

The matrix MUST specify:

- supported MGP versions
- supported RFC versions
- minimum linter version
- compatibility notes for orchestrators and agents

Example (illustrative):

| Component    | Supported Versions |
| ------------ | ------------------ |
| MGP          | 1.1.x              |
| RFC‑0001     | ≥1.1.0             |
| Linter       | ≥1.1.0             |
| Orchestrator | ≥1.0.0             |

---

## 7. RFC Deprecation Process

An RFC MAY be deprecated when:

- it is superseded by a new RFC
- its content is merged into another RFC
- its domain is removed or restructured

### 7.1 Deprecation Steps

1. The RFC is marked **Deprecated** in its metadata.
2. A new version of RFC‑0000 MUST reference the deprecation.
3. A replacement RFC MUST be listed, if applicable.
4. Tooling MUST warn when deprecated RFCs are referenced.

### 7.2 Removal

Deprecated RFCs MUST remain available in `rfcs/archive/`.

---

## 8. Security Considerations

This RFC introduces no security considerations.

---

## 9. References

- RFC‑0000: Index and Glossary
- RFC‑0004: Linter
- RFC‑0005: Substrate Root
- RFC‑0008: Prohibitions
- RFC‑0009: Domain Boundaries
- RFC‑0010: Runtime Artifacts

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Normative.**  
**Last Updated:** 2026‑03‑27
