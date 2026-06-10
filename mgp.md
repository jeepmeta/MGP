# Morpho‑Semantic Governance Protocol (MGP) Substrate Declaration

This document declares that this repository is an **MGP‑compliant substrate**.  
All structure, naming, casing, runtime behavior, and governance rules are defined exclusively by the MGP RFC suite.  
This file is **declarative only** and MUST NOT restate normative requirements.

---

## 1. Substrate Identity

- **Protocol:** Morpho‑Semantic Governance Protocol (MGP)
- **Substrate Version:** 1.0.0
- **RFC Suite Version:** 1.0.0
- **Governance Model:** RFC‑driven, SemVer‑aligned (RFC‑0007)

This substrate adheres to the canonical ontology and structural invariants defined in the MGP specification.

---

## 2. Canonical Structure

This substrate contains **exactly the ten canonical top‑level domains** defined in RFC‑0005.  
All artifacts within these domains MUST comply with:

- naming grammar (RFC‑0001)
- casing rules (RFC‑0002)
- CFN rules (RFC‑0003)
- linter enforcement (RFC‑0004)
- extension rules (RFC‑0006)
- versioning rules (RFC‑0007)
- prohibitions (RFC‑0008)
- domain boundaries (RFC‑0009)
- runtime artifact rules (RFC‑0010)

No additional top‑level domains are permitted.

---

## 3. RFC Suite

This substrate is governed by the following RFCs:

| RFC  | Title                  | Status        |
| ---- | ---------------------- | ------------- |
| 0000 | Index and Glossary     | Informational |
| 0001 | Naming and Ontology    | Normative     |
| 0002 | Casing                 | Normative     |
| 0003 | Conventional Filenames | Normative     |
| 0004 | Linter                 | Normative     |
| 0005 | Substrate Root         | Normative     |
| 0006 | Extensions             | Normative     |
| 0007 | Versioning             | Normative     |
| 0008 | Prohibitions           | Normative     |
| 0009 | Domain Boundaries      | Normative     |
| 0010 | Runtime Artifacts      | Normative     |

All normative behavior is defined in these documents.  
This declaration MUST NOT override or reinterpret any RFC.

---

## 4. Compliance Requirements

A substrate is considered compliant when:

- its structure matches RFC‑0005
- all artifacts conform to RFC‑0001, RFC‑0002, and RFC‑0008
- CFNs appear only as defined in RFC‑0003
- extensions follow RFC‑0006
- runtime artifacts follow RFC‑0010
- versioning follows RFC‑0007
- domain placement follows RFC‑0009
- the linter (RFC‑0004) reports no violations

Compliance MUST be validated through a complete linter implementation.

---

## 5. Substrate Purity

The substrate root MUST contain only:

- the ten canonical domains
- this declaration (`mgp.md`)
- CFNs permitted by RFC‑0003

No other files or directories are allowed at the root.

---

## 6. Change Management

All changes to this substrate MUST:

- follow the versioning rules in RFC‑0007
- be recorded in the Changelog below
- be validated by a compliant linter (RFC‑0004)

---

## Changelog

- **2026‑03‑27 (v1.0.0):** Initial substrate declaration.
