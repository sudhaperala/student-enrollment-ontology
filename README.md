# Student Enrollment Ontology — COM759 CW2

OWL 2 DL ontology for formal document validation in student enrollment,
built in Protégé 5.6.9 with SWRL rules executed via HermiT 1.4.3 and Drools SWRLAPI.

## File

| File | Description |
|------|-------------|
| `StudentEnrollment_v6.owl` | Main ontology — OWL 2 DL / RDF-XML format |

## Key statistics

- **70+ OWL classes** across 6 branches (Document, Person, Institution, FileType, AppStatus, Address)
- **18 object properties** including `nameMatchesFather`, `nameMismatchFather`, `hasDocument`, `hasChild`
- **57 data properties**
- **9 SWRL rules** — POA-1, POR-1, POR-2, FILE, INTL-1, INTL-3, HE-1 (pass + fail variants)
- **8 test individuals** (TC-001 to TC-008): 4 PASS, 4 FAIL

## Reasoning

| Reasoner | Purpose |
|----------|---------|
| HermiT 1.4.3 | OWL 2 DL structural reasoning — consistency + classification |
| Drools SWRLAPI | SWRL rule execution — infers `applicationStatus` data property values |

> **Note:** Set Reasoner → None before running Drools; run HermiT separately for class inference.

## Notable design decisions

- `swrlb:equal` causes a `PlainLiteral` error in Drools — replaced with `nameMatchesFather` / `nameMismatchFather` **object properties**
- `PDFDocument` and `EXEDocument` use **class membership** (not string matching) for file-type validation
- `AcceptedFileType` ⊥ `RejectedFileType` declared disjoint
- 93 redundant `subClassOf` declarations removed after HermiT hierarchy verification

## How to open

1. Install [Protégé 5.6.9](https://protege.stanford.edu/)
2. File → Open → `StudentEnrollment_v6.owl`
3. For SWRL rules: install SWRLTab plugin via Plugins menu

## Author

Pavani Koduri · Ulster University · COM759 · 2026
