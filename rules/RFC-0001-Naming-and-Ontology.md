---
rfc: "0001"
title: "Naming and Ontology"
version: "1.0.0"
status: "Normative"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0001: Naming and Ontology

## Abstract

This document defines the naming grammar and ontology structure required for all artifacts within an MGP substrate. It specifies the allowed grammatical categories, modifier behavior, namespace constraints, and ontology semantics.  
Casing conventions, prohibited forms, and conventional filenames are defined in RFC‑0002, RFC‑0008, and RFC‑0003 respectively.  
Domain boundaries and placement rules are defined in RFC‑0009. Runtime artifact rules are defined in RFC‑0010.

---

## 1. Scope

This RFC defines:

- the grammatical categories permitted in artifact names
- the rules governing modifiers
- the ontology structure for substrate domains
- the interpretation of head nouns
- the constraints on namespace domains
- the interaction between naming grammar and domain boundaries

This RFC does **not** define:

- casing requirements (see RFC‑0002)
- prohibited naming patterns (see RFC‑0008)
- conventional filenames (see RFC‑0003)
- substrate root requirements (see RFC‑0005)
- domain boundary rules (see RFC‑0009)
- runtime artifact rules (see RFC‑0010)

---

## 2. Ontology

An MGP substrate consists of **ten canonical domains**, each represented by a top‑level domain. These domains constitute the substrate ontology.

Domains MUST:

- be plural nouns
- represent collections of artifacts
- be interpreted semantically, not grammatically
- follow the domain boundary rules defined in RFC‑0009

Artifacts MUST be placed in the domain corresponding to their semantic role.

---

## 3. Naming Grammar

Artifact names MUST conform to one of the following grammatical categories:

| Category      | Form                                | Usage                                      |
| ------------- | ----------------------------------- | ------------------------------------------ |
| Plural Noun   | plural noun                         | Domains representing collections           |
| Singular Noun | singular noun (+ optional modifier) | Files representing single conceptual units |
| Base Verb     | base verb (+ optional modifier)     | Executable or process‑oriented artifacts   |
| Gerund        | verb + “‑ing” (+ optional modifier) | Instructional or guardrail artifacts       |

Grammar determines artifact type.  
Casing and allowed characters are defined in RFC‑0002.

### 3.1 Numeric Tokens

Numeric tokens MAY appear in artifact names **only** when:

- they do not encode versioning (prohibited by RFC‑0008)
- they do not alter grammatical category
- they follow casing rules in RFC‑0002

Examples:

- `agent-2.md` → valid
- `v2-agent.md` → invalid (version encoding; see RFC‑0008)

---

## 4. Modifiers

Modifiers refine meaning without altering the underlying grammatical category.

### 4.1 Allowed Modifiers

Modifiers MUST be one of:

- **descriptive adjectives** (non‑emotional, non‑subjective)
- **proper nouns** (vendors, model families, organizations)

### 4.2 Prohibited Modifier Classes

Modifiers MUST NOT:

- encode emotion or subjectivity (e.g., `smart-`, `friendly-`)
- encode modality or intent (e.g., `maybe-`, `should-`)
- encode time or state (e.g., `future-`, `current-`)
- encode versioning (e.g., `v1-`, `latest-`)

See RFC‑0008 for full prohibitions.

### 4.3 Semantic Neutrality Requirement

Modifiers MUST NOT:

- redefine the artifact’s domain
- introduce new semantic categories
- override the head noun rule

### 4.4 Placement

Modifiers MUST:

- appear as prefixes
- preserve the head noun’s category
- not determine plurality

### 4.5 Examples

Correct:

- `security-agent.md` → adjective + singular noun
- `openai-tool.md` → proper noun + singular noun

Incorrect:

- `smart-agent.md` → emotional adjective
- `maybe-process.md` → ambiguous intent
- `future-plan.md` → temporal adjective
- `v1-agent.md` → version encoding

---

## 5. Head Noun Rule

The **final word** in an artifact name determines its grammatical category.

Examples:

- `security-agent.md` → singular noun
- `security-agents/` → plural noun

Modifiers MUST NOT override this rule.

---

## 6. Namespace Domains

Namespace domains provide scoping for external systems, vendors, or model families.

Namespace domains MUST:

- be singular proper nouns
- not replace or redefine ontology domains
- not alter naming grammar for contained artifacts
- not encode versioning, environment, or intent
- not exceed a depth of **one level** under any canonical domain
- not proliferate without semantic justification

Example:

```
tools/openai/gpt-tool.md
```

The file MUST still follow standard naming grammar.

Namespace domain placement rules are defined in RFC‑0005.  
Domain boundary interactions are defined in RFC‑0009.

---

## 7. Prohibited Forms

This RFC defines only the **category‑level prohibitions**.  
Specific prohibited patterns are defined in RFC‑0008.

The following forms MUST NOT appear:

- infinitives (e.g., `to-run.md`)
- emotional or subjective descriptors (e.g., `friendly-agent.md`)
- ambiguous or intent‑encoding forms (e.g., `maybe-process.md`)
- temporal adjectives (e.g., `future-plan.md`)
- version‑encoded forms (e.g., `v1-agent.md`)

---

## 8. Examples

### 8.1 Correct

- `agents/`
- `tools/`
- `security-agent.md`
- `openai-tool.md`
- `planning.md`
- `logging.md`
- `agent-2.md`

### 8.2 Incorrect

- `smart-agent.md`
- `to-run.md`
- `maybe-process.md`
- `openai-tools/` (namespace MUST be singular)
- `policies.md` (files MUST be singular nouns)
- `v1-agent.md` (version encoding)

---

## 9. Security Considerations

This RFC introduces no security considerations.

---

## 10. References

- RFC‑0000: Index and Glossary
- RFC‑0002: Casing
- RFC‑0003: Conventional Filenames
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
