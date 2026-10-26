# Supplementary S6 — Bibliography audit and citation checks

## Files
- `S6_bibliography_audit.tsv`: the field-by-field comparison of the 42 entries of the previous bibliography with their registry records (resolver, title, every author, year, venue, volume, pages; action taken).
- `S6_citation_check_previous_text.tsv`: the first check, of the previous version of the text (139 rows; one row per claim and cited work, with the action proposed).
- `S6_citation_check_revised_text.tsv`: the second check, of the revised text: one row per citation instance and cited work (153 rows; a parenthesis citing *k* works gives *k* rows). Columns: `row_id` (cited work and a hash of the passage), `section`, `key`, `cite_cmd`, `context` (the passage as cited, with citations shown as [key]), `verdict`, `basis`, `note`, `checked_by`, `checked_at` (UTC).

## Verdicts in the revised text
S = the cited work supports the passage as worded; P = it supports it only in part (the note says what is missing); N = it does not support it.
Counts: P 1, S 152. Basis: abstract 23, fulltext 125, registry record 5 ("fulltext" includes preprints and author versions, named in the basis).

## Who checked
Every verdict was made by a language model, as stated in Section 3.1 of the manuscript: claude-opus-5-5 (checking run): 134, claude-opus-5-5 (main model session): 19. "Checking run" is a separate model run given the passage and the source; "main model session" is the model session that edited the manuscript. Where a passage was reworded after a P or N verdict, the new wording was checked again, and only the latest verdict is listed. The authors did not re-check the verdicts one by one; the log is published so that any of them can be checked.

## Not verifiable
One instance (the ISCED 2011 classification, cited for the names of its levels 2 and 3) is graded P because its text was not available to us.
