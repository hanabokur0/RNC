# RNC Error Contract v1.0

This document defines the immutable error semantics of the
Responsibility Normalization Contract (RNC).

In RNC, errors are not explanations.
Errors are executable correction commands.

---

## 1. Error Definition

An error represents a precise violation of a declared rule.

Errors do NOT express:
- intent
- interpretation
- evaluation
- discretion

Errors exist solely to return responsibility to user input.

---

## 2. Error Identity

Each error MUST:

- Have a unique and stable error ID (E-xxx)
- Correspond to exactly one rule violation
- Be machine-readable
- Be reusable across executions and versions

Error IDs, once published, MUST NOT be reassigned.

---

## 3. Error Message Semantics

### 3.1 Allowed Content

Error messages MAY contain only:

- Field identifier(s)
- Required corrective action
- Constraint reference

Messages MUST be written in imperative form.

Examples:
- "Provide a valid value for field X"
- "Select one of the allowed values for Y"
- "Remove prohibited value Z"

---

### 3.2 Forbidden Content

Error messages MUST NOT contain:

- Explanations
- Reasons
- Apologies
- Contextual language
- Judgement
- Suggestions
- Conditional expressions

The following are strictly prohibited:
- "because"
- "please"
- "we cannot"
- "in this case"
- "our policy"
- "at our discretion"

---

## 4. Error as Correction Task

An error is treated as a correction task, not a rejection.

System behavior on error:

- Return error ID(s)
- Await user modification
- Re-evaluate input after resubmission

No human intervention is allowed at any stage.

---

## 5. Error Lifecycle

- Errors are generated during validation
- Errors disappear immediately when corrected
- Errors are not persisted as user faults
- Errors carry no historical or reputational meaning

---

## 6. Responsibility Boundary

- The system owns rule definition
- The user owns input correctness
- Errors explicitly return responsibility to the user

After error emission, the system retains no responsibility.

---

## 7. Immutability Clause

Error semantics MUST NOT be modified at runtime.

Any exception handling MUST be implemented as a rule update,
never as an override, bypass, or manual decision.

---

## 8. One-Line Definition

An RNC error is a command describing how to change input,
not why the input failed.
