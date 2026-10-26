# Working records

Files that the protocols of Supplementary S1, S4 and S5 name by path, under the same paths. JSON responses are gzip-compressed (`.json.gz`). Timestamps inside the files are as recorded.

**Redactions.** Record R3873, a preprint of the manuscript under review, is withheld from these files as it is from S2 and S3: `screening/abstracts.jsonl`: 1 line(s) or record(s) removed; `screening/batches/batch_023.tsv`: 1 line(s) or record(s) removed; `screening/manual_queue.csv`: 1 line(s) or record(s) removed; `screening/record_provenance.csv`: 1 line(s) or record(s) removed; `screening/records_dedup.csv`: 1 line(s) or record(s) removed; `screening/verify_packet.csv`: 1 line(s) or record(s) removed; `search/raw/openalex_C1_2026-10-24_p1.json`: 1 line(s) or record(s) removed. The SHA-256 that S1 states for the query whose response held it therefore matches the response as retrieved, not the redacted copy here; every other raw response is byte-identical to the retrieved file before compression. In the run files, local paths are replaced by `[working folder]/`.

**Not included.** The source texts given to the adjudicator (publishers' copyright; the sources are cited in S4), the calls made to discover open full texts, and the analysis scripts (available from the authors on request).

**Where each named path is.**

| Path named in the protocols | Where it is |
|---|---|
| `evidence/adjudication/ADJUDICATION_PACKET.csv` | `records/evidence/adjudication/ADJUDICATION_PACKET.csv` |
| `evidence/crosswalk_adjudication.csv` | published in the supplement as S4_crosswalk_adjudication.csv |
| `evidence/crosswalk_adjudication.json` | `records/evidence/crosswalk_adjudication.json` |
| `evidence/crosswalk_agreement_llm.json` | `records/evidence/crosswalk_agreement_llm.json` |
| `evidence/crosswalk_clusters.csv` | published in the supplement as S4_crosswalk_clusters.csv |
| `evidence/crosswalk_coding.csv` | published in the supplement as S4_crosswalk_coding.csv |
| `evidence/crosswalk_decisions.md` | published in the supplement as S4_rule_application_log.md (redacted copy) |
| `evidence/crosswalk_disagreements.csv` | published in the supplement as S4_crosswalk_disagreements.csv |
| `evidence/crosswalk_rules.md` | published in the supplement as S4_rules_frozen_with_amendments.md (redacted copy) |
| `evidence/crosswalk_second_coding_llm.csv` | published in the supplement as S4_crosswalk_second_coding_llm.csv |
| `evidence/crosswalk_second_coding_packet.csv` | `records/evidence/crosswalk_second_coding_packet.csv` |
| `evidence/crosswalk_second_coding_sample.json` | `records/evidence/crosswalk_second_coding_sample.json` |
| `evidence/crosswalk_second_coding_stage2.md` | `records/evidence/crosswalk_second_coding_stage2.md` |
| `evidence/evidence_matrix.csv` | published in the supplement as S3_evidence_matrix.csv |
| `evidence/placement_rules.md` | published in the supplement as S5_placement_protocol.md, Sections 1-2 |
| `evidence/second_coder_llm/` | `records/evidence/second_coder_llm/` |
| `screening/VERIFY_INSTRUCTIONS.md` | not deposited; available from the authors on request |
| `screening/abstracts.jsonl` | `records/screening/abstracts.jsonl` (gzip) |
| `screening/batches/` | `records/screening/batches/` |
| `screening/batches/batch_NNN.tsv` | `records/screening/batches/` |
| `screening/corrections.tsv` | `records/screening/corrections.tsv` |
| `screening/dedup_flags.csv` | `records/screening/dedup_flags.csv` |
| `screening/manual_queue.csv` | `records/screening/manual_queue.csv` |
| `screening/prefilter_counts.json` | `records/screening/prefilter_counts.json` |
| `screening/records_dedup.csv` | `records/screening/records_dedup.csv` |
| `screening/screening.csv` | published in the supplement as S2_screening_decisions.csv |
| `screening/screening_counts.json` | `records/screening/screening_counts.json` |
| `screening/verify_packet.csv` | `records/screening/verify_packet.csv` |
| `screening/verify_sample.json` | `records/screening/verify_sample.json` |
| `search/counts.json` | `records/search/counts.json` |
| `search/raw/calls.jsonl` | `records/search/raw/calls.jsonl` (gzip) |
| `search/raw/openalex_SB_manifest.json` | `records/search/raw/openalex_SB_manifest.json` (gzip) |
| `search/search_log.md` | published in the supplement as S1, Part A |
| `search/snowball_prefilter.csv` | `records/search/snowball_prefilter.csv` |
| `supplementary/S4_crosswalk_protocol.md` | published in the supplement as S4_crosswalk_protocol.md |
| `tools/crosswalk/01_extract.py` | analysis script, available from the authors on request |
| `tools/screen/apply_corrections.py` | analysis script, available from the authors on request |
| `tools/screen/screen.py` | analysis script, available from the authors on request |
