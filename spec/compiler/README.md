# RNC Compiler Specification

This directory defines the compilation boundary of RNC.

The compiler converts raw organizational documents into an RNC Package
without human interpretation.

---

## Compiler Mission

Given raw documents (manuals/terms/guidelines/FAQs),
produce an executable RNC Package:

- Schema.json
- Rules.json
- ErrorCatalog.json
- TruthSources.json
- PolicyVersion

---

## Non-Negotiable Constraints

- No summarization of source documents
- No human preprocessing
- No discretionary rewriting
- No exception injection
- No "helpful" natural-language explanations

Any ambiguity found in sources must be emitted as design questions,
not resolved by interpretation.

---

## Output Philosophy

Outputs must be machine-readable, stable, and traceable.

Every emitted field/rule/error MUST include provenance:
where it came from in the source documents.

---

## Responsibility Split

- Organization defines policy by updating source documents and rules.
- Users are responsible for providing valid input.
- The compiler is responsible only for faithful structural extraction.

The compiler must never absorb responsibility by interpreting vague text.
