---
rfc: "0002"
title: "Casing"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0002: Casing

## Abstract

This document defines the casing conventions required for all artifact names within an MGP substrate. Casing governs character form only; naming grammar, ontology, domain boundaries, and prohibited patterns are defined in RFC‑0001, RFC‑0009, and RFC‑0008.  
Conventional filenames exempt from casing rules are defined in RFC‑0003.

---

## 1. Scope

This RFC specifies:

- the required casing style for all artifacts
- the allowed character set
- numeric token rules
- hyphen rules
- file extension rules
- prohibited casing forms
- the relationship between casing and naming semantics

This RFC does **not** define naming grammar (see RFC‑0001), domain boundaries (see RFC‑0009), or prohibited naming patterns (see RFC‑0008).

---

## 2. Casing Requirements

All artifact names inside the substrate MUST use **kebab‑case**:

- lowercase letters (`a–z`)
- hyphens (`-`) separating tokens
- optional numeric tokens (see Section 3.2)
- no uppercase characters
- no underscores
- no spaces

Examples:

- `security-agent.md`
- `planning.md`
- `openai-tool.md`
- `agent-2.md`

Casing MUST NOT encode semantics, hierarchy, priority, or intent.

---

## 3. Character Set Rules

### 3.1 Allowed Characters

Artifact names MAY contain:

- lowercase letters (`a–z`)
- digits (`0–9`)
- hyphens (`-`)
- a single file extension (see Section 3.3)

No other characters are permitted.

### 3.2 Numeric Tokens

Numeric tokens MAY appear in artifact names **only** when:

- they do not encode versioning (prohibited by RFC‑0008)
- they do not alter grammatical category
- they follow kebab‑case rules

Examples:

- `agent-2.md` → valid
- `workflow-step-3.md` → valid
- `v2-agent.md` → invalid (version encoding; see RFC‑0008)

### 3.3 File Extensions

Artifact names MUST:

- use a single extension
- use lowercase extensions
- use extensions appropriate to the artifact type

Examples:

- `.md`
- `.json`
- `.yaml`

CFNs (RFC‑0003) MAY violate this rule.

---

## 4. Hyphen Rules

Hyphens MUST:

- separate tokens
- not appear consecutively (`--`)
- not appear at the start or end of a name
- not encode hierarchy or semantics

Examples:

- `security-agent.md` → valid
- `--agent.md` → invalid
- `agent--2.md` → invalid
- `agent-.md` → invalid

---

## 5. Prohibited Casing Forms

The following forms MUST NOT appear anywhere in artifact names:

- `snake_case`
- `camelCase`
- `PascalCase`
- `MixedCase`
- uppercase words (`AGENT`, `TOOL`)
- space‑separated forms (`security agent.md`)
- names containing non‑ASCII punctuation
- names containing leading/trailing hyphens

These forms introduce ambiguity and violate deterministic parsing requirements.

---

## 6. Interaction With Other RFCs

- Naming grammar and ontology are defined in **RFC‑0001**.
- Domain boundaries and placement rules are defined in **RFC‑0009**.
- Runtime artifacts follow the same casing rules (RFC‑0010).
- Prohibited naming patterns are defined in **RFC‑0008**.
- Conventional filenames exempt from casing rules are defined in **RFC‑0003**.

Casing MUST be interpreted in conjunction with these documents.

---

## 7. Security Considerations

This RFC introduces no security considerations.

---

## 8. References

- RFC‑0000: Index and Glossary
- RFC‑0001: Naming and Ontology
- RFC‑0003: Conventional Filenames
- RFC‑0008: Prohibitions
- RFC‑0009: Domain Boundaries
- RFC‑0010: Runtime Artifacts

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Normative.**  
**Last Updated:** 2026‑03‑27
