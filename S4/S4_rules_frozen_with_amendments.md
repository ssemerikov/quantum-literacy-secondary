# Supplementary S4, Part B — Domain-derivation rules as frozen, with their dated amendments

Published copy of the project file `crosswalk_rules.md`; SHA-256 of the original: `a9e221fddce3d5143be447f1ab6861c63a496fc1567d7e15e75bca364303d071`. 5 redactions, marked ⟦…⟧, replace internal file names, internal role names, or references to a separate manuscript, and local times are given in UTC; nothing else is changed. R-merge has two clauses: (1) the objectives cannot be distinguished; (2) a cluster has school-level support only at the level of awareness of platforms or devices.

---

# Domain-derivation rules (W2) — FROZEN before any coding

Frozen: 2026-10-24 (time and SHA-256 ⟦recorded in the project log⟧). Any later change must be a dated amendment at the end of this file. Never edit silently.

## Sources (six; the extraction must quote each item verbatim with a locator)
- **S1:** CFQT content map. Greinert et al. 2023 (Front. Quantum Sci. Technol. 2:1225733) and CFQT v3.0, Greinert & Müller 2025 (doi 10.2759/8917117). Workforce-oriented.
- **S2:** "Key Concepts for Future QIS Learners" (NSF/NQCO, 2020). Grey literature; verify the official page and record the URL.
- **S3:** Krijtenburg-Lewerissa et al. 2019 (IJSE 41(3):349–366). Delphi study of key topics for secondary school.
- **S4:** Merzel et al. 2024 (EPJ QT 11:27). Core of secondary-level quantum education, multi-stakeholder.
- **S5:** Bitzenbauer et al. 2025 (PRPER 21:020157). Expert Delphi on quantum (technology) topics for school.
- **S6:** Stadermann et al. 2019 (PRPER 15:010130). Topics in the secondary curricula of 15 countries.

School-level sources: S2 (K-12 learners), S3, S4, S5, S6. S1 is NOT school-level.

## Procedure
1. **Extraction.** List every topic, concept, competence or content item each source names, verbatim, with a locator (table, page, section) → `crosswalk_extraction.csv` (`source_id, item_id, item_verbatim, source_group, locator`).
2. **Open coding.** Give each item a short content code in the source's own terms. Do NOT use the CFQT domain labels or the R1 domain labels as coding bins.
3. **Second coder.** An author codes all items, or at least 40% of them chosen at random (seed recorded), independently and without seeing the first codes. Report percentage agreement and resolve disagreements by discussion. Until this is done, the domain set is provisional.
4. **Clustering.** Group content codes into candidate domains by shared subject matter.
5. **Apply rules R-retain, R-merge, R-split and R-crosscut, in that order.**
6. **Comparison.** Only after step 5, compare the resulting domains with the CFQT content map, with the nine domains of the R1 manuscript, and with the eight domains of the related published framework (⟦Semerikov et al. (2026)⟧). Record agreements and differences.
7. **Residuals.** Report items that fit no retained domain (e.g., nature of science, history or philosophy of quantum physics), with counts.

## Rules
- **R-retain.** A candidate domain is retained if it is supported by items from ≥3 of the 6 sources, of which ≥2 are school-level sources (S2–S6). The CFQT alone cannot create a domain.
- **R-merge.** Two candidate domains are merged if their items within secondary reach (CFQT A1 Awareness / A2 Literacy) cannot be distinguished as learning objectives, OR if one of them has school-level support only at the level of "awareness of platforms/devices".
- **R-split.** A candidate domain is split if its items differ by ≥1 phase in prerequisites (per placement rule P1) AND ≥2 sources treat the parts as separate categories.
- **R-crosscut.** A cluster of practices (programming, simulation, experimentation, collaboration) becomes a domain only if ≥2 sources list it as a separate category. Otherwise it becomes a cross-cutting practice layer noted in every domain.

## Expected outcome (a hypothesis recorded in advance, NOT a target)
Eight domains, with "QC hardware & sensors" merged into enabling technologies/platforms and sensors going to sensing. If the rules give a different result, report that result.

## Amendments

### Amendment 1 — 2026-10-25 ⟦(authors' decision)⟧
- Procedure step 3 originally specified that "an author" codes all items, or at least 40% of them chosen at random, independently. At the authors' decision, the second coding is instead done by a second large language model from a different developer than the first coder (NVIDIA Nemotron 3 Ultra, accessed through Ollama's cloud service, model tag `nemotron-3-ultra:cloud`). It runs independently, in two stages (blind open coding; then assignment of its own codes to the candidate clusters or "none"), and has no access to the first coder's codes, clusters or decisions.
- The sample rule is unchanged: at least 40% of items chosen at random per source with a recorded seed (20261025), plus the pivotal items, unmarked.
- Percentage agreement and Cohen's kappa are reported. Disagreements are listed for adjudication by the authors; until they adjudicate, the domain set stays provisional.
- The effect of the second coder on every retention result is reported (R-retain recomputed under both readings with the second coder's cluster substituted for every sampled item).
- This is an inter-model check, not a human verification of the coding.

### Amendment 2 — 2026-10-26 (authors' request). Decided and logged in the project log at ⟦07:00 UTC⟧, before the adjudication ran, together with the reporting plan. Written here at ⟦09:50 UTC⟧, after the run.
- Amendment 1 said that disagreements would be adjudicated by the authors. At the authors' request, they are instead adjudicated by a language model: Claude Opus 5.5 (Anthropic, `claude-opus-5-5`), run as a fresh subagent at the highest reasoning-effort setting. **It is the same model as coder 1**, so a preference for coder 1's assignments is expected. The number of decisions siding with each coder is reported.
- **Blinding:**
  - the A/B order is randomised per row (seed 20261026);
  - the coders' own code labels are removed;
  - the adjudicator works in a folder holding only the packet, the cluster definitions and the six source texts;
  - the key linking options to coders is held outside the evidence folder during the run;
  - the adjudicator is told not to infer coder identity or consequences.
- The decisions decide only cluster membership. The four rules are then re-applied mechanically under both readings, and with S4 and S5 counted as one source. Every change in a retention result is reported.
- **The authors check every decision before submission.** The number they change is reported. Until the check is done, the manuscript marks it as pending.
