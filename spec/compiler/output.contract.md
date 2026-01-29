# RNC Compiler Output Contract v1.0

This document defines the immutable output requirements of the RNC Compiler.

The compiler output constitutes an executable RNC Package.
Any output that violates this contract is considered non-RNC-compliant.

---

## 1. RNC Package Definition

An RNC Package MUST consist of exactly the following artifacts:

1. Schema.json
2. Rules.json
3. ErrorCatalog.json
4. TruthSources.json
5. PolicyVersion

All five artifacts are mandatory.
Partial packages are invalid.

---

## 2. General Output Constraints

All output artifacts MUST be:

- machine-readable
- deterministic given identical inputs
- traceable to source documents
- free from natural-language explanation
- free from discretionary interpretation

No artifact may include:
- commentary
- rationale
- human judgement
- inferred intent

---

## 3. Schema.json

Schema.json MUST:

- Conform to rnc.schema.meta.json
- Define all input fields explicitly
- Specify required vs optional fields
- Declare data types and constraints
- Disallow undeclared fields

Each field MUST include provenance:
- source document identifier
- source path or section
- excerpt hash

---

## 4. Rules.json

Rules.json MUST:

- Conform to rules.meta.json
- Contain only declarative rules
- Use explicit conditions and assertions
- Avoid natural-language logic
- Reference fields defined in Schema.json

Each rule MUST:
- Have a stable rule_id
- Map to exactly one error_id
- Include provenance to source text

Rules MUST NOT:
- Contain soft validation
- Emit warnings
- Encode exceptions

---

## 5. ErrorCatalog.json

ErrorCatalog.json MUST:

- Define all error IDs referenced by Rules.json
- Map each error ID to exactly one corrective command
- Use imperative form only
- Avoid explanation or justification

Error messages MUST NOT contain:
- reasons
- apologies
- conditional phrasing
- policy references
- human tone

Errors are executable correction tasks.

---

## 6. TruthSources.json

TruthSources.json MUST:

- Declare all external or internal truth references used by rules
- Identify the authority for each source
- Specify source type (registry, database, ledger, API, etc.)
- Disallow runtime substitution or override

If no truth sources are required, an explicit empty TruthSources.json
MUST still be emitted.

---

## 7. PolicyVersion

PolicyVersion MUST:

- Uniquely identify the policy state used for compilation
- Be immutable once published
- Change whenever source documents or rules change

PolicyVersion MAY be a string, hash, or semantic version,
but MUST be stable and comparable.

---

## 8. Provenance Requirement (Global)

Every artifact in the RNC Package MUST preserve provenance.

At minimum, provenance MUST allow:
- tracing each field, rule, and error to source text
- identifying the originating document
- locating the exact source segment

If provenance cannot be preserved, the compiler MUST emit design questions
instead of producing unverifiable output.

---

## 9. Immutability and Responsibility

Once emitted, an RNC Package:

- MUST NOT be modified at runtime
- MUST NOT be overridden by human judgement
- MUST NOT accept exceptions outside rule updates

Responsibility boundaries are fixed:
- Organization owns policy definition
- User owns input correctness
- Compiler owns faithful transformation only

---

## 10. One-Line Definition

RNC Compiler output is a complete, traceable, and executable contract package,
not an explanation of policy.
