# RNC Compiler Input Contract v1.0

This document defines the immutable input requirements for the RNC Compiler.

The compiler must accept raw organizational documents as-is and must not
allow human preprocessing that mixes responsibility into interpretation.

---

## 1. Accepted Input Types

The compiler MUST accept the following as raw inputs:

- Operating manuals
- Terms of Service / contracts / policies
- Application requirements / eligibility guidelines
- FAQ and operational rules
- Historical rejection reasons (if available)
- Reference lists / registries (if provided as policy artifacts)

Inputs may be provided as:
- plain text
- markdown
- PDF (text-extractable)
- HTML
- DOCX

---

## 2. Prohibited Human Actions (Pre-Compilation)

Before compilation, the following are strictly prohibited:

- summarization
- rewriting
- cleanup / "making it clearer"
- merging multiple policy sources into one
- resolving contradictions by judgement
- inserting "common sense" assumptions
- adding exception clauses
- replacing ambiguous phrases with interpreted meaning

If any of the above occurs, the compiler output is considered invalid.

---

## 3. Required Provenance Availability

Source inputs MUST preserve traceability.

At minimum, each input document MUST have:

- document identifier (name or URI)
- stable path or location reference
- extractable segments (page/section/paragraph)
- immutable excerpt hash possibility (hashable chunk text)

If provenance cannot be established, the compiler MUST emit a design question
instead of guessing.

---

## 4. Ambiguity Handling

If ambiguous expressions are present (e.g. "appropriate", "as needed",
"case by case", "at our discretion"), the compiler MUST:

- flag the phrase
- emit a design question
- continue compilation without interpreting the phrase

The compiler MUST NOT infer intended meaning.

---

## 5. Conflict Handling

If source documents contain contradictions, the compiler MUST:

- emit a conflict report (as design questions)
- preserve both conflicting rules with provenance
- avoid selecting a "correct" interpretation

Resolution is a policy authoring task, not a compilation task.

---

## 6. Minimal Input Completeness

Compilation MUST be possible even with incomplete inputs.

If rules cannot be fully extracted due to missing policy artifacts,
the compiler MUST:

- emit design questions
- generate partial schema/rules where possible
- never fabricate missing requirements

---

## 7. One-Line Definition

RNC Compiler input is raw policy text with provenance, not a human-edited summary.
