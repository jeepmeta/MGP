# Orchestrator Integration Guide

This guide describes how orchestrators interact with an MGP‑compliant substrate.  
It focuses on runtime behavior, loading semantics, and operational expectations.  
This document is **non‑normative** and MUST NOT override any RFC.

---

## 1. Substrate Root

An orchestrator MUST be pointed at the substrate root — the directory containing:

- `mgp.md`
- the ten canonical domains (RFC‑0005)

At minimum, orchestrators typically consume:

- `agents/`
- `tools/`
- `skills/`
- `workflows/`
- `guardrails/`
- `prompts/`
- `instructions/`
- `memories/` (schemas only)

The orchestrator MUST NOT modify the substrate structure.

---

## 2. What the Orchestrator Loads

The orchestrator interprets the substrate as a **structured capability graph**.

It loads:

- **Agents** — autonomous actors
- **Tools** — atomic capabilities
- **Skills** — composite capabilities
- **Workflows** — orchestrated sequences
- **Guardrails** — constraints and safety rules
- **Instructions** — procedural guidance
- **Prompts** — prompt templates and components
- **Memory Schemas** — definitions for agent‑usable state

Runtime artifacts (RFC‑0010) MUST NOT be loaded as capabilities.

---

## 3. Agent Loading

Agents are singular‑noun files under `agents/`.

The orchestrator SHOULD:

- parse agent metadata
- bind tools, skills, and prompts
- apply guardrails
- load memory schemas relevant to the agent

Agents MUST NOT be inferred from other domains.

---

## 4. Tool Loading

Tools live under `tools/`, optionally inside namespace domains (RFC‑0006).

The orchestrator SHOULD:

- load tool definitions
- expose them to agents and workflows
- validate that tools are atomic (RFC‑0009)
- respect namespace boundaries

Tools MUST NOT be treated as skills.

---

## 5. Workflow Execution

Workflows define multi‑step orchestrations.

The orchestrator SHOULD:

- load workflow definitions
- resolve agent and tool references
- execute steps deterministically
- apply guardrails at each step
- write runtime outputs to `logs/runtime/` (RFC‑0010)

Workflows MUST NOT redefine domain semantics.

---

## 6. Guardrail Enforcement

Guardrails constrain behavior globally or per‑agent.

The orchestrator SHOULD:

- load guardrail definitions
- apply constraints before tool execution
- enforce safety during workflows
- respect guardrail precedence rules (if defined by implementation)

Guardrails MUST NOT be treated as instructions.

---

## 7. Memory Integration

The orchestrator reads:

- memory schemas (`memories/`)
- memory instances (runtime only)
- embeddings or profiles (if defined by implementation)

The orchestrator SHOULD:

- maintain continuity and context
- store ephemeral state under `memories/runtime/` (RFC‑0010)

Memory artifacts MUST NOT be treated as logs.

---

## 8. Logging and Evaluation

The orchestrator writes:

- execution logs → `logs/runtime/`
- evaluation outputs → `evaluations/`

Runtime logs MUST NOT be committed to version control (RFC‑0010).  
Evaluations MUST NOT be placed in `logs/`.

---

## 9. Extending Behavior

To extend orchestrator behavior, developers MAY:

- add new workflows
- add new skills
- add new tools
- add new guardrails
- add new instructions
- add new prompts

All extensions MUST follow RFC‑0006 and respect domain boundaries (RFC‑0009).  
New top‑level domains are prohibited (RFC‑0005).

---

## 10. Summary

The orchestrator treats the substrate as:

- a **capability graph**
- a **behavioral contract**
- a **safety envelope**
- a **knowledge base**

MGP ensures the substrate is predictable, machine‑interpretable, and semantically unambiguous.
