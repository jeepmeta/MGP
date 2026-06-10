---
rfc: "0010"
title: "Runtime Artifacts"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0010: Runtime Artifacts

## Abstract

This document defines the rules governing runtime‑generated artifacts within an MGP substrate.  
It specifies allowed runtime domains, naming grammar, cleanup requirements, namespace restrictions, extension restrictions, and linter exemptions.  
Naming grammar is defined in RFC‑0001; casing is defined in RFC‑0002; substrate structure is defined in RFC‑0005; domain boundaries are defined in RFC‑0009.

---

## 1. Scope

This RFC defines:

- allowed runtime domains
- allowed runtime file types
- naming rules for runtime artifacts
- cleanup and lifecycle requirements
- linter exemptions for ephemeral files
- namespace and extension restrictions for runtime artifacts

This RFC does **not** define naming grammar (RFC‑0001) or domain boundaries (RFC‑0009).

---

## 2. Allowed Runtime Domains

Runtime artifacts MUST be placed under exactly one of the following:

- `logs/runtime/`
- `memories/runtime/` (for ephemeral state)

No other runtime domains are permitted.

Runtime directories MUST:

- follow extension rules (RFC‑0006)
- not exceed extension depth limits
- not appear under namespace domains

Example (valid):

```
logs/runtime/
```

Example (invalid):

```
tools/runtime/        ← wrong domain
tools/openai/runtime/ ← runtime under namespace
```

---

## 3. Runtime Artifact Types

Allowed runtime artifacts include:

- temporary logs
- ephemeral state files
- intermediate workflow outputs
- agent‑generated scratch files

Runtime artifacts MUST NOT:

- redefine substrate structure
- introduce new domain types
- persist beyond their intended lifecycle
- appear in canonical domains
- appear in namespace domains
- appear in extension paths unrelated to logs or memories

---

## 4. Naming Rules

Runtime artifacts MUST follow:

- naming grammar (RFC‑0001)
- casing rules (RFC‑0002)
- prohibited pattern rules (RFC‑0008)

Runtime artifacts MAY include:

- numeric tokens
- timestamps
- UUIDs
- temporary extensions (e.g., `.tmp`)

Examples:

- `session-20260327-184200.md`
- `workflow-step-3.json`
- `agent-output-uuid-1234.tmp`

### 4.1 Prohibited Runtime Names

Runtime artifacts MUST NOT:

- encode versioning (`v1`, `v2`)
- use infinitives (`to-run.md`)
- use emotional or subjective modifiers (`smart-output.md`)
- use namespace‑like prefixes (`openai-log.md`)

---

## 5. Cleanup Requirements

Runtime artifacts MUST:

- be deleted when no longer needed
- not persist across substrate versions (RFC‑0007)
- not be committed to version control
- not be used as durable state

### 5.1 Linter Behavior

Linter implementations (RFC‑0004) MUST:

- ignore runtime artifacts during naming grammar validation
- validate that runtime artifacts appear **only** in allowed runtime domains
- warn (but not error) when runtime artifacts accumulate excessively
- error when runtime artifacts appear outside allowed domains

---

## 6. Namespace and Extension Restrictions

### 6.1 Namespace Restrictions

Runtime artifacts MUST NOT appear under namespace domains.

Invalid:

```
tools/openai/runtime/
```

### 6.2 Extension Restrictions

Runtime artifacts MUST NOT:

- appear under extension paths except `logs/runtime/` or `memories/runtime/`
- exceed extension depth limits (RFC‑0006)
- introduce new extension categories

---

## 7. Examples

### 7.1 Valid

- `logs/runtime/agent-output-1.md`
- `memories/runtime/session-uuid-1234.json`
- `logs/runtime/workflow-step-3.tmp`

### 7.2 Invalid

- `logs/tmp/` (invalid domain)
- `agents/runtime/` (invalid domain)
- `logs/runtime/v1/` (version encoding)
- `logs/runtime/to-run.md` (infinitive; RFC‑0008)
- `tools/runtime/` (runtime in wrong domain)
- `tools/openai/runtime/` (runtime under namespace)

---

## 8. Security Considerations

Runtime artifacts may contain sensitive data.  
Implementations SHOULD ensure secure deletion.

---

## 9. References

- RFC‑0001: Naming and Ontology
- RFC‑0002: Casing
- RFC‑0003: Conventional Filenames
- RFC‑0004: Linter
- RFC‑0005: Substrate Root
- RFC‑0006: Extensions
- RFC‑0007: Versioning
- RFC‑0008: Prohibitions
- RFC‑0009: Domain Boundaries

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Normative.**  
**Last Updated:** 2026‑03‑27
