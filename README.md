# Quantum literacy in secondary education: search, derivation and placement materials

This repository holds the materials behind the manuscript *Integrating quantum literacy into secondary education frameworks:
A position paper* (submitted to *Social Sciences & Humanities Open*). The manuscript refers to them as Supplementary S1–S6.
No data from human participants were collected.

## Contents

Each folder holds the machine-readable files (Markdown, CSV, TSV, LaTeX) and readable copies (PDF, Excel). In an Excel
workbook, each CSV or TSV file of the folder is one sheet, named after the file without its `S<n>_` prefix.

| Folder | Part | Readable copy | Machine-readable files |
|---|---|---|---|
| [`S1/`](S1/) | Search log and screening protocol | `S1_search_and_screening.pdf` | `S1_search_and_screening_protocol.md` |
| [`S2/`](S2/) | Screening decisions, one row per record | `S2_screening_decisions.xlsx` | `S2_screening_decisions.csv` |
| [`S3/`](S3/) | Full-text eligibility and extraction for the empirical inclusions | `S3_evidence_matrix.xlsx` | `S3_evidence_matrix.csv` |
| [`S4/`](S4/) | Derivation of the competency domains | `S4_domain_derivation.pdf`, `S4_domain_derivation_data.xlsx` | `S4_adjudication_run_records.md`, `S4_coverage_check.csv`, `S4_crosswalk_adjudication.csv`, `S4_crosswalk_clusters.csv`, `S4_crosswalk_coding.csv`, `S4_crosswalk_disagreements.csv`, `S4_crosswalk_extraction.csv`, `S4_crosswalk_protocol.md`, `S4_crosswalk_second_coding_llm.csv`, `S4_rule_application_log.md`, `S4_rules_frozen_with_amendments.md` |
| [`S5/`](S5/) | Placement rules, evidence grading, matrix and sensitivity analysis | `S5_placement.pdf`, `S5_placement_data.xlsx` | `S5_outcome_level.csv`, `S5_placement_entry.csv`, `S5_placement_grid.tex`, `S5_placement_grid_first.tex`, `S5_placement_grid_frozen.tex`, `S5_placement_log.md`, `S5_placement_matrix.csv`, `S5_placement_protocol.md`, `S5_placement_samples.csv`, `S5_placement_sensitivity.csv`, `S5_placement_units.csv` |
| [`S6/`](S6/) | Citation and bibliography checks | `S6_citation_and_bibliography_checks.pdf`, `S6_citation_and_bibliography_data.xlsx` | `S6_bibliography_audit.tsv`, `S6_citation_and_bibliography_checks.md`, `S6_citation_check_previous_text.tsv`, `S6_citation_check_revised_text.tsv` |
| [`records/`](records/) | Working records that the protocols name by path (raw search responses, screening batches, second-coder responses, adjudication inputs and outputs); see `records/README.md` | | |

**What each file contains.**

| File | Content |
|---|---|
| S1_search_and_screening_protocol.md | Part A: search log (databases, exact query strings, run times, hit counts). Part B: screening protocol, criteria, model instructions, precedents, verification result. |
| S2_screening_decisions.csv | One row per record (4141 rows): first-pass decision and criterion, extracted characteristics, verification sample flag, verifier decision, final decision. |
| S3_evidence_matrix.csv | Full-text eligibility and extraction for the empirical inclusions (111 rows), with page locators. The last column, `placement_evidence`, states for each row whether it counts as evidence from teaching studies for the placements and, if not, why. |
| S4_crosswalk_protocol.md, S4_*.csv | Domain derivation: rules, amendments, addenda (second coder, adjudication, post hoc coverage check), extracted items, codes, clusters, disagreements, adjudications, and the coverage-check items. |
| S5_placement_protocol.md, S5_*.csv, S5_*.tex | Placement rules, amendments (including the A4 correction), operational decisions, sensitivity scenarios, the full matrix, and three grids. |
| S4_rules_frozen_with_amendments.md, S4_rule_application_log.md | The domain-derivation rules as frozen (both R-merge clauses), their dated amendments, and the log of every rule application (redacted copies; hashes of the originals stated). |
| S5_placement_log.md | Time-stamped log of the placement run, showing when the operational decisions were fixed (redacted copy). |
| S4_adjudication_run_records.md | Prompt, run record and summary of the model adjudication of the coding disagreements, and the pre-registration and result of the neutral re-run of item S6-018. |
| S5_placement_samples.csv, S5_outcome_level.csv | The samples behind the grades (full references in S5_placement_protocol.md, Section 4) and, for each evidence record, whether its outcomes are reported per topic or only as aggregate scores. |
| S6_*.md, S6_*.tsv | Bibliography audit (field by field, every previous entry) and the logs of both citation checks, one row per citation instance, with the source read and the verdict. |

## Formats

- CSV files are UTF-8, comma-separated, with a header row; TSV files are UTF-8 and tab-separated.
- Markdown files are the protocols and logs; the PDF in the same folder renders the same text.
- `S5/*.tex` are the three placement grids as LaTeX table source; their count macros are defined in the manuscript. The
  rendered grids are at the end of `S5/S5_placement.pdf`.
- Timestamps are in UTC.
- `SHA256SUMS` lists a checksum for every file (`sha256sum -c SHA256SUMS`).

## Notes

Anonymisation: one record of the search is withheld from S2 and S3 for anonymous review, so S2 has one row fewer than the 4142 unique records reported in the manuscript; the screening precedent concerning it is redacted in S1. The withheld record was not used as evidence. The verifier is identified as A1. Timestamps are in UTC.
Most working files that the protocols name by path and that are not part of this upload, among them the raw search responses, the screening batch files and the second coder's raw responses, are deposited under the same paths in the folder `records/` of the open repository given in the Data availability statement; its `records/README.md` maps every path named here to its location, including the files published in this upload under an S-name. The analysis scripts are available from the authors on request.

## Licence

The authors' own files in this repository (protocols, logs, coding, decisions, matrices, and their PDF and Excel copies) are
released under the Creative Commons Attribution 4.0 International licence (CC BY 4.0); see `LICENSE`. Third-party material keeps the
terms of its source: the bibliographic records and abstracts in `records/` and in the screening files were retrieved from OpenAlex
and ERIC, and quoted items from published sources remain the property of their rights holders.

## Citation

Citation details for the article will be added here when it is published.
