---
rfc: "0000"
title: "Index and Glossary"
version: "1.0.0"
status: "Informational"
introduced: "MGP v1.0.0"
last_updated: "2026-03-27"
author: "MGP Working Group"
---

# RFC‑0000: Index and Glossary

## Abstract

This document provides the canonical index and glossary for the Morpho‑Semantic Governance Protocol (MGP). It defines core terminology and lists all RFCs in the specification series. All normative requirements are defined in the referenced RFCs.  
The substrate declaration (`mgp.md`) MUST reference these RFCs directly and MUST NOT duplicate their content.

---

## 1. RFC Index

| RFC  | Title                  | Status        | Description                                |
| ---- | ---------------------- | ------------- | ------------------------------------------ |
| 0000 | Index and Glossary     | Informational | Terminology and RFC directory              |
| 0001 | Naming and Ontology    | Normative     | Naming grammar and substrate ontology      |
| 0002 | Casing                 | Normative     | Casing conventions                         |
| 0003 | Conventional Filenames | Normative     | Reserved and conventional filenames        |
| 0004 | Linter                 | Normative     | Linter behavior and enforcement criteria   |
| 0005 | Substrate Root         | Normative     | Root declaration and structural invariants |
| 0006 | Extensions             | Normative     | Substrate extension mechanisms             |
| 0007 | Versioning             | Normative     | Versioning model and update requirements   |
| 0008 | Prohibitions           | Normative     | Forbidden naming patterns and structures   |
| 0009 | Domain Boundaries      | Normative     | Domain semantics and placement rules       |
| 0010 | Runtime Artifacts      | Normative     | Rules for runtime‑generated artifacts      |

Archived RFCs are stored in `rfcs/archive/`.

---

## 2. Reading Order

The specification is designed to be read in the following order:

1. **RFC‑0000** — index and glossary
2. **RFC‑0001** — naming and ontology
3. **RFC‑0002** — casing
4. **RFC‑0003** — conventional filenames
5. **RFC‑0004** — linter
6. **RFC‑0005** — substrate root
7. **RFC‑0006** — extensions
8. **RFC‑0007** — versioning
9. **RFC‑0008** — prohibitions
10. **RFC‑0009** — domain boundaries
11. **RFC‑0010** — runtime artifacts

Implementations MUST reference the latest version of each RFC.

---

## 3. Cross‑Reference Matrix

This matrix shows which RFCs reference which others.  
Rows = referencing RFC.  
Columns = referenced RFC.

| RFC ↓ \ RFC → | 0000 | 0001 | 0002 | 0003 | 0004 | 0005 | 0006 | 0007 | 0008 | 0009 | 0010 |
| ------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **0000**      | —    | X    | X    | X    | X    | X    | X    | X    | X    | X    | X    |
| **0001**      | X    | —    | X    | X    | X    | X    | X    | —    | X    | X    | —    |
| **0002**      | X    | X    | —    | X    | X    | —    | —    | —    | X    | —    | —    |
| **0003**      | X    | X    | X    | —    | X    | X    | —    | —    | X    | —    | —    |
| **0004**      | X    | X    | X    | X    | —    | X    | X    | X    | X    | X    | X    |
| **0005**      | X    | X    | X    | X    | X    | —    | X    | —    | X    | X    | X    |
| **0006**      | X    | X    | X    | —    | X    | X    | —    | —    | X    | X    | —    |
| **0007**      | X    | —    | —    | —    | X    | X    | —    | —    | —    | —    | —    |
| **0008**      | X    | X    | X    | X    | X    | X    | X    | —    | —    | X    | X    |
| **0009**      | X    | X    | —    | —    | X    | X    | X    | —    | X    | —    | X    |
| **0010**      | X    | X    | X    | —    | X    | X    | —    | —    | X    | X    | —    |

---

## 4. Glossary

**Agent**  
A system that reads, writes, or interprets substrate artifacts.

**Artifact**  
Any file or domain within the substrate. See RFC‑0001.

**Casing**  
The allowed character patterns for identifiers. See RFC‑0002.

**Changelog**  
A version‑tracked record of modifications to the protocol or RFC suite. Required for all version increments. See RFC‑0007.

**Conventional Filename (CFN)**  
A filename exempt from standard naming morphology due to ecosystem or tooling requirements. See RFC‑0003.

**Domain**  
One of the ten canonical top‑level domains that define the substrate ontology. See RFC‑0001.

**Domain Boundary**  
The semantic rules determining which domain an artifact belongs to. See RFC‑0009.

**Extension**  
An optional, non‑core substrate capability defined in RFC‑0006.

**Linter**  
The enforcement component that validates substrate compliance. See RFC‑0004.

**Loanword**  
A synonym for CFN. See RFC‑0003.

**Modifier**  
A prefix that refines meaning without altering the underlying ontology category. See RFC‑0001.

**Morphology**  
The grammatical structure of artifact names. See RFC‑0001.

**Namespace Directory**  
A directory named after an external system, vendor, or model family. Namespace directories act as scoping labels and are exempt from plural‑noun directory rules. See RFC‑0005.

**Ontology**  
The semantic structure of the substrate, defined by the ten canonical domains. See RFC‑0001.

**Orchestrator**  
A coordinating system that loads and executes substrate artifacts.

**Prohibition**  
A forbidden naming pattern or structure. See RFC‑0008.

**Runtime Artifact**  
A temporary or ephemeral file generated during execution. See RFC‑0010.

**Substrate**  
The complete filesystem governed by MGP, including all domains and artifacts. See RFC‑0005.

**Substrate Purity**  
The requirement that the substrate root contain only the canonical domains, `mgp.md`, and CFNs. See RFC‑0005.

**Substrate Root**  
The top‑level directory containing the substrate declaration and canonical ontology. See RFC‑0005.

**Taxonomy**  
The classification system used by MGP to categorize naming, ontology, casing, and substrate concepts.

**Versioning**  
The protocol governing updates to MGP and its RFC suite. See RFC‑0007.

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial version.

---

**This RFC is Informational.**  
**Last Updated:** 2026‑03‑27
