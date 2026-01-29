# RNC Compiler Ambiguity Contract v1.0

This document defines how the RNC Compiler must handle ambiguity.

Ambiguity MUST NOT be resolved by interpretation.
Ambiguity MUST be externalized as design questions.

---

## 1. Definition of Ambiguity

An ambiguous expression is any policy language that cannot be compiled
into a deterministic rule without human interpretation.

Examples include, but are not limited to:

- "appropriate"
- "reasonable"
- "in principle"
- "as needed"
- "case by case"
- "at our discretion"
- "exceptional circumstances"
- "special cases"

The list is non-exhaustive.

---

## 2. Prohibited Compiler Behavior

When ambiguity is detected, the compiler MUST NOT:

- infer intended meaning
- apply common-sense assumptions
- consult external context
- select an interpretation
- soften or harden constraints
- rewrite ambiguous language

Any such behavior constitutes a violation of RNC.

---

## 3. Mandatory Compiler Behavior

When ambiguity is detected, the compiler MUST:

- identify the ambiguous phrase
- record its exact source location
- preserve the original text verbatim
- emit a design question
- continue compilation without resolving ambiguity

---

## 4. Design Questions

A design question is a structured request for policy clarification.

Design questions MUST:

- reference the ambiguous source text
- specify what decision is required
- avoid proposing answers
- avoid suggesting interpretations
- avoid framing as errors or failures

Design questions are NOT part of runtime execution.
They are policy-authoring artifacts.

---

## 5. Output Requirements

Design questions MUST be emitted as a separate artifact
(e.g. `DesignQuestions.md` or `DesignQuestions.json`).

The presence of unresolved design questions MUST NOT:

- block compilation
- be silently ignored
- be auto-resolved

---

## 6. Responsibility Boundary

- The compiler identifies ambiguity
- The organization resolves ambiguity by updating policy
- The compiler never absorbs responsibility for meaning

Ambiguity resolution is a policy decision, not a compilation task.

---

## 7. Immutability Clause

Ambiguity handling rules are immutable.

Any attempt to auto-resolve ambiguity MUST be treated
as a protocol violation.

---

## 8. One-Line Definition

In RNC, ambiguity is not resolved — it is surfaced.
