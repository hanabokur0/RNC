# RNC — Responsibility Normalization Contract  
**Responsibility Normalization Contract Protocol (v1.0)**

RNC is a contract and application protocol that removes human judgment from decision-making  
and returns responsibility to where it structurally belongs: **the input**.

It transforms contracts from  
> *“people deciding whether something is acceptable”*  
into  
> *“systems accepting input only when it fully matches rules.”*

---

## Why RNC Exists

Modern organizations are overloaded with invisible responsibilities:

- Interpreting vague rules  
- Making discretionary exceptions  
- Explaining rejection reasons  
- Taking blame for user mistakes  

RNC eliminates these problems **by design**, not by training.

---

## Core Principles

- **Instant decision** (True / False only)
- **Zero human discretion**
- **No interpretation, no negotiation**
- **Clear responsibility split**
  - Organization → rules & schema
  - User → input correctness
- **No “checking”, no “pending”, no “manual review”**

---

## What RNC Achieves

| Before | After (RNC) |
|------|-------------|
Manual review | Automatic validation |
“Just this once” | Rule update or nothing |
Human explanation | Error ID only |
Implicit responsibility | Explicit responsibility |
Emotional complaints | Specification questions |

---

## Scope

### In Scope
- Contracts
- Applications
- Registrations
- Any process that depends on user input

### Out of Scope
- Internal HR evaluations
- Internal approvals
- Performance reviews  
*(Use a different protocol)*

---

## RNC Workflow

### Step 0 — Target Selection
Choose processes that involve **user-provided input**.

---

### Step 1 — Raw Input Injection
Feed the following **as-is** into the RNC Compiler:

- Manuals
- Terms of Service
- Application guidelines
- FAQs
- Past rejection reasons (if available)

⚠️ **No summarizing, no editing, no cleanup.**  
Human preprocessing mixes responsibility.

---

### Step 2 — Structural Extraction (Automatic)

The compiler extracts:

- Input fields
- Required / optional flags
- Data types (number, date, string, enum)
- Prohibited conditions
- Conditional branches (If / Then)
- Truth sources / references

**Outputs**
- `Schema.json`
- `Rules.json`

---

### Step 3 — Ambiguity Detection (RII-based)

The system flags ambiguous phrases such as:

- “in principle”
- “appropriate”
- “as deemed necessary”
- “case by case”
- “at our discretion”

**Output**
- `DesignQuestions.md`

👉 Humans do **not** judge cases here  
👉 Humans only **define rules**

---

### Step 4 — Error Definition

The system generates:

- Error IDs
- Violated rules
- User-facing correction commands (imperative form)

**Output**
- `ErrorCatalog.json`

---

### Step 5 — RNC Package Completion

RNC is complete when all are present:

- `Schema.json`
- `Rules.json`
- `ErrorCatalog.json`
- `TruthSources.json`
- `PolicyVersion`

---

## Runtime Protocol

### Input Acceptance
- Input is rejected until it fully matches
- No provisional acceptance
- No “we’ll check later”

---

### Decision Output (C3)

Only this format is allowed:

```json
{
  "result": true | false,
  "error_ids": ["E-102", "E-341"]
}
