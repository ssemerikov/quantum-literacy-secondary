# Supplementary S4 — Domain-derivation (crosswalk) protocol and coding instructions

Written: 2026-10-25 (UTC), before any item was coded. Coder 1: Claude (Anthropic), model ID `claude-opus-5-5`, working as the `crosswalk` agent (task T5). Coder 2: as first planned, one author independently (see §7); changed by Amendment 1 to the rules (see Addendum C).

Frozen rules: `evidence/crosswalk_rules.md` (sha256 ffe9bd716970122d7e83d5e0086c33a5392612833059f939c80c6adb88d47fea, frozen 2026-10-24, verified unchanged on 2026-10-24/25 before this protocol was written). This protocol does not change the rules. It records (a) the extraction scope, (b) how two undefined terms in the rules are operationalised, (c) the exact coding instructions. Any point below that a reader judges to go beyond an operationalisation should be treated as a candidate dated amendment to the rules file (flagged to the main session).

## 1. Sources and cached texts

| ID | Source | Group | Text used | Item unit |
|---|---|---|---|---|
| S1 | CFQT v3.0 content map (Greinert & Müller 2025, doi 10.2759/8917117); structure as in Greinert et al. 2023 | workforce | a local text extraction of the published CFQT v3.0 PDF, pp. 5–13 | the 42 subdomains (p. 5); topics of pp. 6–13 kept in `extra` |
| S2 | NSF/NQCO (2020) Key Concepts for Future QIS Learners | school (K-12) | a local text extraction of the published NSF PDF, pp. 2–5 | 9 Key Concepts + 27 supporting fundamentals (1a–9c). Introduction/background text excluded. The report states it "is not a consensus document". |
| S3 | Krijtenburg-Lewerissa et al. (2019), IJSE 41(3) | school | a local text copy of the published article; Table 6 column assignment checked against the publisher PDF (layout-preserving text extraction of p. 358) | 84 topics of Table 6 (round 2, N = 12); round-3 mean rank (Table 7) in `extra` |
| S4 | Merzel et al. (2024), EPJ QT 11:27 | school | the publisher's open-access online article (HTML text, Tables 2 and 5 as HTML, Tables 6 and 8a–8i as images), retrieved 2026-10-25 | 36 exemplary key concepts of Table 2 (with their category) + 13 illustrations named in the text (§5.3.2, §6.1, §6.3, §6.4) |
| S5 | Bitzenbauer et al. (2025), PRPER 21:020157 | school | the CC-BY publisher PDF (institutional repository copy) | 105 topics of Tables III–V (round 3, N = 68) with Cns(X) and Include (%) |
| S6 | Stadermann et al. (2019), PRPER 15:010130 | school | a local text copy of the published article | 17 curriculum items Q1–Q17 (Table VI, countries of 15, documents of 23) + 6 NOS/history aspects N1–N6 (Table I; frequencies from §IV.D.1) |

Not extracted at first (limitation, remedied in Addendum B): S4 Tables 7a–7h, 8a–8i, 9a–9b (images); S3 Table 4 (a subset of Table 6, flagged in `extra`); S5 Table I categories are recorded as a category structure (§3), not as items.

Verbatim rule: items are copied exactly, including source typos (e.g., CFQT "communitcation", S5 "0,76", "Technolgies"); parsed values go into `extra`. An automated check (`tools/crosswalk/01_extract.py`) confirms that each verbatim string occurs in the cached source text (whitespace- and hyphenation-normalised).

## 2. Operationalising "supported by items from" (R-retain) — two readings, both reported

The frozen rules do not define *support*. Both readings below are fixed now, before coding, and R-retain is applied under both. A domain whose retention differs between the readings is reported as **fragile**.

- **Primary (literal) reading.** A source supports a candidate domain if at least one item extracted from that source is coded into it. An item is extracted when the source names it as candidate content for learners at that level (S1: workforce content map; S2–S6: secondary/K-12).
- **Sensitivity (endorsement) reading.** Only items that meet the source's *own* inclusion criterion count:
  - S1: all 42 subdomains (S1 cannot create a domain alone in any case).
  - S2: all 36 items (a curated list without ratings).
  - S3: topics selected by ≥ 8 of 12 experts in round 2 (the authors' cut-off for round 3; 37 topics).
  - S4: all 36 exemplary key concepts (nominated by respondents); illustrations only if among the 8 prominent ones (≥ 6 mentions, the authors' cut-off).
  - S5: the 10 topics of Table II that met both inclusion criteria (Cns ≥ 0.75 and ≤ 25 % "not needed").
  - S6: all 17 Q-items (the authors' list criterion: mentioned in more than one curriculum document) and all six NOS aspects (present in curricula); core-curriculum status (Q3–Q9) is recorded in `extra`.

"School-level support" in R-merge and the "≥ 2 school-level sources" condition of R-retain use the same reading as the count they belong to.

## 3. Each source's own category structure (verbatim, recorded before coding)

Used only for R-split ("≥ 2 sources treat the parts as separate categories") and R-crosscut ("≥ 2 sources list it as a separate category"). Never used as coding bins.

- **S1 (CFQT, p. 5):** blocks "Quantum background" (domains 1–2), "Core device technologies" (3–4), "QT systems and applications" (5–8). Domains: 1 "Concepts and foundations"; 2 "Physical foundations of quantum technologies"; 3 "Enabling technologies and techniques"; 4 "Quantum hardware"; 5 "Quantum computing and simulation"; 6 "Quantum sensors and imaging systems"; 7 "Quantum communication and networks"; 8 "Valorisation". Proficiency areas (p. 3): "(I) Quantum concepts, incl. mathematical formalism & physics; (II) QT hardware (HW) & software (SW) engineering …; (III) QT applications & strategies … as well as impact, ethics and education".
- **S2 (NSF, p. 1):** "The first Key Concept defines the field as a whole. Concepts 2-6 introduce ideas that are necessary for building an understanding of quantum information science and its applications. Concepts 7-9 provide short explanations of critical areas of study within QIS: quantum computing, quantum communication and quantum sensing."
- **S3 (Krijtenburg-Lewerissa, p. 356–357, Table 5):** round-1 categories "wave–particle duality, wave functions, atoms, subatomic particles, materials, nonlocality and history"; rounds 2–3 grouping (Tables 6–7): "concepts, examples and applications".
- **S4 (Merzel, Table 5):** four classes "Fundamental concepts", "Phenomena and applications", "Mathematical representations", "Philosophical aspects"; 19 KC categories (Table 2); and the distinction between key concepts and illustrations. *CFQT dependence:* respondents were shown the CFQT "as a means to achieve some degree of uniformity" (§4.2), though not obliged to use it.
- **S5 (Bitzenbauer, Table I and Tables III–V):** three fields "Concepts of QP", "Physical Foundations of Quantum Technologies", "Quantum Technologies 2.0"; 23 round-1 categories, including, under Quantum Technologies 2.0, "Quantum computing", "Quantum sensors and metrology", "Quantum communication", "Enabling technologies", "Hardware for quantum computers and sensors". *CFQT dependence:* the categories were assigned "by the authors, using the CFQT", and the experts were shown three CFQT domains. These category boundaries therefore echo the CFQT and are not independent evidence for a separation that the CFQT also makes.
- **S6 (Stadermann, Table III):** five themes "Fundamental QP principles", "Phenomena and applications", "Atomic theory", "Wave function or other mathematical representations", "Philosophical aspects of QP"; separately, Table I "Aspects of nature of science and history of science in quantum physics" (N1–N6); and core curriculum (Q3–Q9) vs extensions.

## 4. Coding instructions (coder 1, applied exactly as written)

1. Unit: one row of `crosswalk_extraction.csv`. Read `item_verbatim`; for S1 also read the listed topics in `extra` because the subdomain title alone is too terse. Do not read the CFQT domain/field of S5 items or the class of S4 items in `extra` before choosing the code.
2. Assign **one** short content code (2–6 words) that names what the item is *about* (the phenomenon, object, representation, device, practice or issue), using the source's wording. Normalise only spelling and grammatical form so that the same thing gets the same code across sources (e.g., "Tunnelling", "Tunneling", "Quantum tunnelling" → `tunnelling`). Use constant comparison: before creating a new code, check whether an existing code names the same thing.
3. Prohibited bins: do not use the CFQT domain labels (§3, S1) or the R1 manuscript's nine domain labels (Physical foundations; Mathematical foundations; Supporting technologies; QC hardware & sensors; Quantum computing; Quantum sensing; Quantum communication; Practical skills; Societal context) as codes for items whose own wording does not use those words. A source's own term remains a legitimate code when the item itself uses it (e.g., NSF concept 9 "Quantum sensing uses …" → `quantum sensing`).
4. First-revolution devices (lasers, LEDs, transistors, solar cells, chips, STM, MRI, CCD, flash memory, etc.) keep their own device codes; they are not folded into qubit-platform or "hardware" codes.
5. Experiments named as items (double slit, Stern–Gerlach, Mach–Zehnder, photoelectric effect) are coded by the experiment, not by the principle they are used to illustrate.
6. An item that names several things gets the code of its head concept (the first-named or defining one); the note records what else it contains. Multi-topic CFQT subdomains are coded at subdomain level.
7. Write a ≤ 20-word note when the code required a judgement (ambiguous wording, multi-topic item, a code chosen over an alternative).
8. Disclosure: coder 1 also performed the extraction and had therefore seen every source's tables and category structure before coding; instruction 1 limits, but cannot remove, that exposure. This is why an independent second coder is required (§7).
9. Coder 1 codes all items. Codes are written to `evidence/crosswalk_coding.csv` with `coder = claude-opus-5-5`.

## 5. Clustering instructions

Group content codes (not items) into candidate domains by **shared subject matter**: codes go together when they are about the same kind of thing (e.g., the same family of phenomena, the same family of devices, the same representational apparatus, the same kind of societal issue). Source category placement is not used. Each code goes to exactly one candidate cluster; codes that fit no cluster with others stay as singletons and become residuals unless retained. The cluster label is written after the members are fixed. Output: `evidence/crosswalk_clusters.csv` with item counts per source under both readings.

## 6. Rule application

R-retain → R-merge → R-split → R-crosscut, in that order, each decision logged with reasons and source counts in `evidence/crosswalk_decisions.md`. Prerequisite judgements for R-split use placement rule P1 (`evidence/placement_rules.md`). Only after all four rules are applied is the result compared with the CFQT content map, the R1 nine domains and Semerikov et al. (2026).

## 7. Second coder (independent) and agreement

- Sample: ≥ 40 % of items, stratified by source (ceil(0.4 × n) per source), drawn with Python `random.seed(20261025)`; `random.sample` on each source's item list in item-ID order; sources processed S1…S6.
- Packet `evidence/crosswalk_second_coding_packet.csv` shows only `item_id, source, item_verbatim, locator` and blank `second_code`, `coder`; `extra` is withheld (it contains CFQT fields/classes that would cue the coder).
- Stage 1: the author writes open codes blind (without opening `crosswalk_coding.csv`, `crosswalk_clusters.csv` or `crosswalk_decisions.md`). Stage 2: after returning stage 1, the same author assigns each of their own codes to one cluster from the cluster list, or "none". Claude does not map the author's codes.
- Agreement: percentage of sampled items assigned to the same cluster by both coders, and Cohen's κ over clusters (incl. "none"). Disagreements are resolved by discussion and logged. Until then the domain set is **provisional**.

## Addendum A — 2026-10-25 (added after clustering and rule application, before any second coding)

These points were not in §§5–7 as written before coding. They are recorded here so that the supplementary trace matches what was done.

1. **Residual fit test.** Items in a candidate cluster that fails R-retain are counted as residual unless they would have been clustered with a retained domain's codes under the §5 criterion. Applied this way, no item of a failed cluster was moved into a retained domain.
2. **Purposive add-on to the second-coder packet.** In addition to the stratified random 40 % (138 of 339 items; seed 20261025; method unchanged from §7), the packet contains the "pivotal" items, i.e. those whose recoding would flip an R-retain or R-crosscut result (listed in `evidence/crosswalk_decisions.md` §5). Ten of the 15 were already in the random draw, so five were added. The combined list was shuffled with the same random generator and the added items are not marked. Agreement is reported separately for the random sample and for the 15 pivotal items. The sampling record is in `evidence/crosswalk_second_coding_sample.json`.
3. **Stage 2 uses all 13 candidate clusters plus "none"**, described by subject matter only (`evidence/crosswalk_second_coding_stage2.md`), not the retained domains. Agreement therefore measures coding and clustering, not the rule outcomes.
4. **Packet locators for S4** give "Table 2, row n" instead of the source's category name, so that the source category does not cue the coder. Extraction content is unchanged.

## Addendum B — 2026-10-25 (UTC): Merzel et al. Tables 8a–8i added after the first rule application

The first application (339 items) omitted Merzel et al.'s image tables. They were retrieved from the publisher's online article (the PDF was not obtainable), read and transcribed, and 61 distinct illustrations not already extracted were added as S4-050 to S4-110 (400 items in all). These items were coded under §4 without change to the instructions. Their verbatim check is against our own transcription of the images only. Endorsement for them follows §2 (Merzel et al.'s own cut-off of at least 6 mentions and at least 4 KC categories; none qualifies). One item whose content cannot be determined from its wording ("Bernstein 1967") is placed in an unclassifiable cluster that cannot be retained. When R-merge clause 2 applies, the merge partner is the retained domain whose A1/A2 objective the school-level items serve (the clause-1 test); this criterion was written down before the partner was named. The second-coder sample was redrawn from the 400-item set with the same seed and method (162 random items, 40.5 %, plus 8 pivotal items not drawn; 170 in all). Results are in `evidence/crosswalk_decisions.md`, Addendum B.

## Addendum C — 2026-10-25 (UTC): inter-model second coding (Amendment 1)

This is an **inter-model check, not a human verification** of the coding. Amendment 1 to the frozen rules (dated 2026-10-25, authors' decision) replaced the author second coder with a second large language model from a different developer.

**Model and access.** NVIDIA Nemotron 3 Ultra, Ollama model tag `nemotron-3-ultra:cloud`, called through a local Ollama daemon (version 0.30.6) that forwards to Ollama's cloud service (`/api/chat`). Model record from `/api/show` (retrieved 2026-10-25T15:24:29Z): parameter size 550000000000, context length 262144, capabilities completion, thinking, tools. The model's default reasoning ("thinking") was left on; the API returns it in a separate field, which is kept in each response file.

**Settings.** temperature 0; seed 20261025; stream false; batches of 20 items (last batch smaller) in packet order; output constrained by a JSON schema and validated (every input item exactly once; stage-2 values restricted to K01–K13 or "none"); at most two retries per batch. Run from 2026-10-25T15:24:29Z to 2026-10-25T15:47:23Z. Retries: none.

**Input.** The 170 packet items (162 random, 40.5 %, plus 8 pivotal items not drawn; unmarked). For each item the model received only its ID, source ID, a one-line source type, the verbatim item text, the locator and, for S1, the topics listed under the subdomain. In stage 1 it also received the list of its own labels from earlier batches. Nothing derived from the first coder (codes, cluster memberships, decisions) was sent. No email address or personal data was sent (the script refuses any request containing "@").

**Stage 1 system prompt (verbatim):**

```text
You are coding items for a research synthesis on quantum physics and quantum technology education. Each item is a topic, concept, competence or content item quoted verbatim from one of six published sources: a European competence framework for the quantum-technology workforce (S1); a US list of key concepts for future learners of quantum information science (S2); an expert Delphi study on key topics for secondary-school quantum mechanics (S3); a multi-stakeholder study of key concepts and illustrations for secondary-school quantum physics (S4); an expert Delphi study on secondary-school quantum physics (S5); and an analysis of secondary-school quantum-physics curricula in 15 countries (S6).

Task (open coding). For each item, write a short label (2-6 words) that names what the item is ABOUT: the phenomenon, object, representation, device, practice or issue. Rules:
1. Use the source's own words where you can. Examples of the kind of label meant (not taken from the items): "Compton scattering", "photon counting statistics", "history of the photon concept".
2. Give the same label to the same thing across sources (for example "Tunnelling", "Tunneling" and "Quantum tunnelling" all get one label). Before inventing a new label, check whether one you have already used fits; your labels from earlier batches are listed in the request.
3. Do not sort items into ready-made categories. In particular, do not use any of the following as a label unless the item itself uses those words: Concepts and foundations; Physical foundations of quantum technologies; Enabling technologies and techniques; Quantum hardware; Quantum computing and simulation; Quantum sensors and imaging systems; Quantum communication and networks; Valorisation; Physical foundations; Mathematical foundations; Supporting technologies; QC hardware & sensors; Quantum computing; Quantum sensing; Quantum communication; Practical skills; Societal context. (An item that says, for example, "Quantum sensing uses ..." may be labelled "quantum sensing".)
4. Name devices as devices (for example "lasers", "solar cells", "MRI"). Name an experiment by the experiment (for example "Stern-Gerlach experiment"), not by the principle it shows.
5. If an item names several things, label its main (first-named or defining) idea. For items from S1, the topics the framework lists under that subdomain are given as context; use them to understand the item.
6. If the content of an item cannot be determined from its wording, use the label "unclear".

Return only JSON of the form {"items": [{"item_id": "...", "code": "..."}]}, with exactly one entry for every input item and no other text.
```

**Stage 2 system prompt (verbatim; {CLUSTERS} was replaced by the 13 definitions below, one per line as "ID label: definition"):**

```text
You are coding items for a research synthesis on quantum physics and quantum technology education. In an earlier stage you gave each item a short label describing what it is about. Now assign each item to exactly one of the candidate clusters listed below, or to "none" if no cluster fits. Decide from the item text and your own label. Choose the cluster whose subject matter the item shares; do not try to guess what any other coder did.

Candidate clusters:
{CLUSTERS}

Return only JSON of the form {"items": [{"item_id": "...", "cluster": "K01"}]}, where cluster is one of K01, K02, K03, K04, K05, K06, K07, K08, K09, K10, K11, K12, K13 or none, with exactly one entry for every input item and no other text.
```

**Neutral cluster definitions sent in stage 2** (written from the cluster labels and the rules file, not from the first coder's member codes):

- K01 Quantum principles and phenomena: Fundamental principles of quantum physics and the phenomena and experiments in which they show themselves.
- K02 Mathematical representations: Mathematical descriptions and formalisms used to represent quantum states, their change over time and the outcomes of measurements.
- K03 Atoms, light and matter: Quantum physics of atoms, of light and its interaction with matter, and of the structure and properties of matter and materials.
- K04 Particle and nuclear physics: Subatomic particles, atomic nuclei and the processes they undergo.
- K05 Quantum information and qubits: Information represented and processed in quantum systems, with the qubit as its basic unit.
- K06 Quantum computing and simulation: Computation and simulation performed with quantum systems, including quantum computers, their operations, algorithms and applications.
- K07 Quantum communication and cryptography: Transmission and protection of information using quantum systems, and cryptography in a quantum context.
- K08 Quantum sensing and metrology: Measurement, sensing and timekeeping that exploit quantum systems, and the standards of measurement.
- K09 Qubit hardware platforms: The physical systems and engineering used to realise, control and scale qubits.
- K10 Quantum devices and enabling technologies: Devices whose operation relies on quantum physics, and the technologies and techniques used to build and run quantum technologies.
- K11 Valorisation and societal impact: Economic, business, societal and ethical aspects of quantum technologies and their communication to the public.
- K12 Nature, history and philosophy of quantum physics: How quantum physics developed, how it is interpreted, and what it shows about the nature of science.
- K13 Practices: Activities that learners carry out, such as programming, simulation, experimentation and building.

**Records.** `evidence/second_coder_llm/`: `batch_001`–`batch_018` request and response JSON (stage 1 = batches 1–9; stage 2 = the rest), `manifest.json` (item IDs, sha256 of every request and response, UTC times, attempts), `model_info.json`, `run_log.txt`. Output: `evidence/crosswalk_second_coding_llm.csv`.

| Batch | Stage | Items | Request sha256 (first 16) | Response sha256 (first 16) |
|---|---|---|---|---|
| 001 | 1 | 20 | 8e162f16960a639c | 438eb2a8d4f380a6 |
| 002 | 1 | 20 | 138e1bdbc3eece2f | 7eeba6d822a8fbf1 |
| 003 | 1 | 20 | 3ac5f5c8d7bb372b | ca75d4b2975ff29d |
| 004 | 1 | 20 | 9acb778ecb788ea5 | 38e1fa3ca46419f8 |
| 005 | 1 | 20 | 3b1183af04bb70c2 | cf9ba769e9b2baf5 |
| 006 | 1 | 20 | da18eedfd281f744 | 432b9ebb906e4858 |
| 007 | 1 | 20 | 9967588edee31a76 | 7a2ea5208ca330da |
| 008 | 1 | 20 | 00f72aa432203fa8 | aea602a577871ebb |
| 009 | 1 | 10 | c059a6b1471482da | 41f1b530a8d846ed |
| 010 | 2 | 20 | 38f978875fa6b908 | 33cf6377b664fdc9 |
| 011 | 2 | 20 | c10778866998514d | 8ef0eef27be7432a |
| 012 | 2 | 20 | 3a0d973f7c29f94d | 97066004ee91c936 |
| 013 | 2 | 20 | b925b0b5afcac51e | 6fb572c823cce7a9 |
| 014 | 2 | 20 | ef817315551745b6 | 8d45a886e6fda42e |
| 015 | 2 | 20 | a7cae4e0b465d77a | d7cda8fde838ce9f |
| 016 | 2 | 20 | 78e3e6840b853715 | a019f39851e3444e |
| 017 | 2 | 20 | 70e78f5401231d6a | 12141d09c0e4edbb |
| 018 | 2 | 10 | 12fb396e45311da4 | eaa0e3383edd29f6 |

**Agreement on cluster assignment** (first coder's cluster for the item vs the second model's stage-2 cluster; the first coder's unclassifiable cluster is compared as "none"):

| Set | n | Agreement | Cohen's kappa |
|---|---|---|---|
| Random sample | 162 | 138/162 = 85.2 % | 0.826 |
| Pivotal items | 14 | 11/14 = 78.6 % | 0.731 |
| All packet items | 170 | 144/170 = 84.7 % | 0.822 |

Disagreements: 26, listed in `evidence/crosswalk_disagreements.csv` for adjudication by the authors (empty `author_decision` column). Full figures, per-cluster counts and the confusion summary: `evidence/crosswalk_agreement_llm.json`.

**Retention sensitivity** (R-retain recomputed with the second model's cluster substituted for every sampled item):

- literal reading: no retention result changes.
- endorsed reading: no retention result changes.

**Disagreements on pivotal items:** S3-046 "Schrödinger’s cat" (first coder K12, second model K01); S4-097 "Coherent control" (first coder K09, second model K10); S6-018 "Methodology (e.g., experiments and hypothesis)" (first coder K12, second model K13).

**Consequences beyond R-retain.** (1) Qubit hardware platforms (K09) stay at three sources on the literal reading with the second model's clusters, but then rest on a single single-mention illustration ("NV-center"), because the second model placed "Coherent control" with devices and enabling technologies. (2) The second model placed Stadermann et al.'s nature-of-science aspect "Methodology (e.g., experiments and hypothesis)" with practices. If the authors adopt that coding, a second source arguably lists practices as a separate category, and R-crosscut would make practices a domain rather than a cross-cutting layer. This is the one disagreement with a possible rule consequence; it is flagged for adjudication. (3) The second model gave both Delphi items "Schrödinger's cat" the same stage-1 label but assigned them to different clusters (principles; nature, history and philosophy), an inconsistency within the second coder.

**Conditions on the agreement figures.** The stage-2 cluster definitions were written by the first coder (from the cluster labels and the rules file only), and the clusters themselves are the first coder's candidate clusters; the agreement is therefore agreement on assignment to the first coder's cluster set, not an independent clustering. The disagreements concentrate on the boundaries between principles, mathematical representations and atoms/light/matter (mathematical representations → principles 6; atoms, light and matter → principles 5), which bears on the clustering granularity and changes no result.

**Combined sensitivity** (Merzel et al. and Bitzenbauer et al. counted as one source, because they report the same Delphi study): literal/coder1: K13 retain → fail; literal/coder2_substituted: no change; endorsed/coder1: no change; endorsed/coder2_substituted: K12 retain → fail. Under the primary (literal) reading nothing changes except the practices cluster, which is a cross-cutting layer by R-crosscut in any case; under the endorsement reading with the second model's clusters, the nature, history and philosophy domain would fail.

Until the authors have adjudicated the disagreements, the domain set remains provisional.

## Addendum D — 2026-10-26: adjudication of the coder disagreements by a language model

**Who decided, and why a model.** The authors asked that the disagreements be adjudicated by Claude Opus 5.5 (Anthropic, model `claude-opus-5-5`) and that they check every decision afterwards. The adjudicator ran as a fresh Claude Code subagent at the highest reasoning-effort setting, with no access to the context of the session that coordinated the revision. **It is the same model as coder 1**, so a preference for coder 1's assignments is to be expected. That is why the share of decisions siding with each coder is reported below. The reporting plan was recorded before any decision was seen.

**Blinding.**
- Options A and B appear in the same random order as in the authors' packet (seed 20261026).
- The coders' own code labels were removed from the options, because their wording could reveal which coder gave them.
- The adjudicator worked in a separate folder that held only the packet, the cluster definitions and the six source texts. The key linking options to coders was held outside the project's evidence folder during the run.
- It was told not to infer which coder gave which option, or what a decision would change.

**Prompt (verbatim; local path replaced):**

```text
You are the adjudicator for a coding exercise in an academic study. Your working folder is:
<working folder>/

Read INSTRUCTIONS_FOR_MODEL.md in that folder first and follow it exactly. In short:
- decide all 26 rows of PACKET_FOR_MODEL.csv, using only cluster_definitions.md and the source texts in sources/;
- write DECISIONS_MODEL.csv atomically after every row and append to progress.log;
- finish with SUMMARY.md.

Rules:
- Work only inside this folder. Do not open, list or search any file or directory outside it, and do not use the web.
- Do not try to infer which coder gave which option, or what a decision would change.
- Quote paths in shell commands, because they contain spaces, '&' and parentheses. Use python3 -I for any script.
- Take the time each row needs. Read each item in its source context before deciding.

When done, reply with:
- the number of rows decided;
- the counts of each decision type;
- the path of DECISIONS_MODEL.csv.

Do not include anything else.
```

The run stopped at the account's usage limit after the adjudicator had read every item but before it saved any decision. It was resumed in the same context with a message asking it to write its decisions row by row as instructed, under unchanged rules. The full run record, with that message verbatim, is published as S4_adjudication_run_records.md.

The adjudicator also had an advisor tool, which Claude Code provides. The tool forwards the subagent's own transcript to a stronger Anthropic reviewer model and returns advice. The transcript shows three advisor calls. The advice is redacted in the transcript and is not recorded. Because the advisor sees only that transcript, it had no information from outside the adjudication folder; it may, however, have influenced some decisions.

**Instructions file given to the adjudicator (verbatim):**

````markdown
# Adjudicating coding disagreements (instructions for the model adjudicator)

**Task.** Two coders assigned topic items, taken verbatim from six published sources, to a fixed set of clusters. For the 26 items in `PACKET_FOR_MODEL.csv` they chose different clusters. Decide each item.

**Files you may use. Work only inside this folder (`adjudication_run/`).**
- `PACKET_FOR_MODEL.csv`: one row per item, in random order. `option_A` and `option_B` are the two coders' clusters. Which coder gave which option varies at random from row to row.
- `cluster_definitions.md`: the definitions. These are the only basis for a decision.
- `sources/`: the six source texts (S1 to S6, named by file) and `all_extracted_items.csv`. That file lists every item extracted from the six sources, with its locator, so you can see the table, column or list in which an item appears and its neighbouring items.

**Do not open, list or search anything outside this folder.** That covers the parent directory and its siblings (evidence/, tools/, agents/, source/, backup/, drafts/, supplementary/, and the state and plan files), and also the web. Do not try to work out which coder gave which option, whether an item matters for any later result, or what any decision would change. None of that is a basis for a decision.

**How to decide each row.**
1. Read the item where it appears in its source. Use the `locator` column, the source text, and the neighbouring items in `all_extracted_items.csv`.
2. Ask which cluster definition the item's subject matter fits best, as it would be taught or discussed at secondary level.
3. In `decision`, write one of:
   - `A`
   - `B`
   - `other: K##`, if a different cluster fits better than both options;
   - `none`, if no cluster fits.
4. In `reason_one_line`, give one line of at most 30 words that refers to the definition. For example: "about how measurement changes the state, so K01 not K02".
5. In `confidence`, write `high`, `medium` or `low`.

**One item may look ambiguous:** a "Methodology (e.g., experiments and hypothesis)" entry from a curriculum comparison's nature-of-science table. Decide it like any other row. The question is whether the entry is about a student practice (doing experiments) or about knowledge of how science works (the nature of scientific methods). Use the source's own table context.

**Saving (required, because the session may stop at any time).**
- After deciding each row, rewrite the whole of `DECISIONS_MODEL.csv`. It has the packet's columns plus `confidence`. Write it atomically: write `DECISIONS_MODEL.csv.tmp`, then rename it, for example with `python3 -I`.
- Then append one line to `progress.log`: UTC time, row number, decision.
- If `DECISIONS_MODEL.csv` already exists when you start, keep its decided rows and continue with the rest.
- Never modify `PACKET_FOR_MODEL.csv`.

**When all 26 rows are decided**, write `SUMMARY.md`. It should give:
- the number of each decision type (A, B, other, none);
- the rows with `low` confidence;
- any row where neither option fits well, with a one-line explanation.
````

**Decisions (unblinded).**

| Item | Source | Item text | Coder 1 | Coder 2 | Final | Sided with | Confidence | Reason (adjudicator) | Authors' check |
|---|---|---|---|---|---|---|---|---|---|
| S1-011 | S1 | Computers and software | K13 | K10 | K10 | coder 2 | high | CFQT places it under Enabling technologies and techniques: IT infrastructure and control software used to run QT, matching K10, not a learner activity (K13). | agree |
| S2-016 | S2 | At a particular moment in time, a set of n classical bits can exist in only one of 2n poss | K05 | K01 | K05 | coder 1 | high | Compares n classical bits with n qubits for storing and processing information; matches K05's information represented and processed with qubits, not a general K01 principle. | agree |
| S3-026 | S3 | Stationary states | K02 | K01 | K02 | coder 1 | low | A stationary state is defined by how a quantum state changes over time (energy eigenstate, time-independent solution), matching K02's 'change over time'; K01 reading also plausible. | agree |
| S3-029 | S3 | Development of atomic models | K03 | K12 | K12 | coder 2 | medium | 'Development' of atomic models is the historical sequence of models, showing how quantum physics developed and models' tentativeness: K12; atomic content itself appears as separate items. | agree |
| S3-030 | S3 | Free vs. localised particle | K02 | K01 | K01 | coder 2 | low | Conceptual contrast between delocalised free and confined particles (quantisation, uncertainty); a fundamental principle (K01) rather than a mathematical formalism (K02). | agree |
| S3-041 | S3 | Magnetism | K03 | K01 | K03 | coder 1 | medium | An everyday example explained by electron spin; magnetism is a property of matter and materials (K03) rather than a fundamental principle or experiment (K01). | agree |
| S3-046 | S3 | Schrödinger’s cat | K12 | K01 | K12 | coder 1 | low | Thought experiment on macroscopic superposition and the measurement problem; chiefly a vehicle for discussing interpretation, so K12 rather than an experiment showing principles (K01). | agree |
| S3-050 | S3 | Heat radiation | K03 | K01 | K03 | coder 1 | low | Heat (thermal) radiation is light emitted by matter because of its temperature; quantum physics of light and its interaction with matter (K03) fits better than general principles (K01). | agree |
| S3-081 | S3 | Single molecule microscopy | K10 | K08 | K08 | coder 2 | low | An application that images individual molecules: a measurement and imaging technique exploiting quantum systems (K08), more specific than a generic quantum device (K10). | agree |
| S4-023 | S4 | Pauli Exclusion principle | K03 | K01 | K03 | coder 1 | medium | Source clusters it under Atomic models (with orbitals, band structure); taught to explain electron shells and periodic table, so K03 over the general-principle reading (K01). | agree |
| S4-044 | S4 | Double-well | K02 | K01 | K01 | coder 2 | low | Offered as an illustration of Superposition, Quantum measurement, Heisenberg principle and Statistical nature; a system where these K01 principles show themselves, not a formalism (K02). | agree |
| S4-050 | S4 | Light interference | K01 | K03 | K01 | coder 1 | high | Offered as an illustration of Superposition; interference is a phenomenon where the superposition principle shows itself (K01), not quantum physics of light-matter interaction (K03). | agree |
| S4-062 | S4 | Space and velocity measurement | K01 | K08 | K01 | coder 1 | high | Illustration for the Quantum measurement key concept: measuring a particle's position and velocity is about the measurement principle (K01), not sensing technology (K08). | agree |
| S4-066 | S4 | Malus’ law with a single photon | K01 | K03 | K01 | coder 1 | high | Offered for Quantum measurement and Statistical nature; single-photon transmission probability shows probabilistic measurement, an experiment where K01 principles show themselves, not K03 light-matter physics. | agree |
| S4-069 | S4 | Analogy of standing waves and a particle in a box | K02 | K01 | K01 | coder 2 | low | Offered as an illustration of Quantization (Table 8c); the standing-wave analogy conveys the quantisation principle conceptually (K01) rather than a mathematical formalism for states (K02). | agree |
| S4-090 | S4 | Bloch sphere | K02 | K05 | K02 | coder 1 | high | Listed under Mathematical foundations; the Bloch sphere is a representation of a two-level quantum state, so K02 representations, not K05 information processing. | agree |
| S4-097 | S4 | Coherent control | K09 | K10 | K09 | coder 1 | medium | Offered for the Qubit key concept; coherent control means manipulating qubit states with pulses, matching K09 'control qubits' more specifically than K10's general enabling technologies. | agree |
| S5-032 | S5 | Photoelectric effect | K03 | K01 | K01 | coder 2 | medium | Listed among double slit, Mach-Zehnder and matter-wave interference experiments; demonstrates light quanta, an experiment where K01 principles (wave-particle duality) show themselves, over K03. | agree |
| S5-041 | S5 | Electrons | K03 | K04 | K03 | coder 1 | low | Listed beside spin, Franck-Hertz experiment and atomic models in the quantisation sequence; electrons as constituents of atoms fit K03 better than particle physics (K04). | agree |
| S5-048 | S5 | Quantum harmonic oscillator | K02 | K01 | K02 | coder 1 | low | A model system whose quantised states follow from the Schrödinger equation; a mathematical description of quantum states (K02) rather than a principle or experiment (K01). | agree |
| S5-067 | S5 | Spectroscopy | K03 | K08 | K03 | coder 1 | high | Source lists spectroscopy under atoms and atomic physics (Physical Foundations); it concerns light-matter interaction in atoms, K03, not quantum-enhanced measurement (K08). | agree |
| S5-085 | S5 | Topological effects | K03 | K01 | K03 | coder 1 | high | Physical Foundations, materials/nanostructures group (CFQT solid-state topic); topological effects are properties of materials, so K03, not a fundamental principle (K01). | agree |
| S5-086 | S5 | Surface tension | K03 | none | none | coder 2 | low | Surface tension is taught classically at secondary level (intermolecular cohesion); no quantum content, so K03's 'quantum physics of... properties of matter' does not fit; no cluster fits. | agree |
| S5-101 | S5 | Photon fibres | K10 | K07 | K10 | coder 1 | medium | Listed with photon sources, single-photon detectors and vacuum technology; a component technology used to build and run QT (K10), not communication itself (K07). | agree |
| S6-011 | S6 | One-dimensional model or potential well | K02 | K01 | K02 | coder 1 | high | Source groups Q11 with wave function and mathematical representations (graphical Schrödinger-equation solutions, wave-function diagrams), so K02, not a fundamental principle (K01). | agree |
| S6-018 | S6 | Methodology (e.g., experiments and hypothesis) | K12 | K13 | K12 | coder 1 | high | Source lists N1 among nature-of-science aspects (relation between experiment and theory, thought experiments in QP's development); knowledge of how science works, so K12 not K13. | agree |

**Results.**
- Of 26 decisions, 18 chose coder 1's cluster and 8 chose coder 2's. 0 chose another cluster, and 0 chose no cluster where neither coder had.
- 10 decisions were marked low-confidence.
- 8 items changed cluster relative to coder 1.
- Retention results that changed (R-retain under both readings, and with S4 and S5 counted as one source): 0.
- S6-018, "Methodology (e.g., experiments and hypothesis)", was assigned to K12. Sources listing practices as a separate category: S1. So practices remain a cross-cutting layer (R-crosscut).
- Some subjects that appear in several sources are assigned differently by source: the photoelectric effect (S3 → K03, S5 → K01), the double well (S4 → K01, S5 → K02), and standing waves and a particle in a box (S4 → K01, S5 and S6 → K02). The adjudicator decided by each source's own context, for example the key concept under which S4 offers an illustration. These splits fall on the D1–D3 boundaries noted above and change no retention result.
- **Authors' check:** done. The authors checked all 26 decisions and changed none of them; the last column records their verdict.
- **Neutral re-run of S6-018.** The instructions above single this item out as possibly ambiguous and name its two readings. After a model-run review of the revised manuscript noted this, a fresh run of the same model at the same effort setting decided S6-018 alone, with the same definitions and source texts and with the same instructions except that the paragraph naming the item was removed; the option order was re-randomised (seed 20261027). Decision: K12 Nature, history and philosophy of quantum physics, confidence high; reason: "NOS aspect on scientific method (experiment-theory relation, thought experiments in QP's development): K12 'what it shows about the nature of science', not K13 'activities that learners carry out'." This agrees with the original decision, so practices remain a cross-cutting layer.
- Files: `evidence/crosswalk_adjudication.csv` (one row per item) and `evidence/crosswalk_adjudication.json` (summary).

## Addendum E — 2026-10-26: post hoc coverage check of further framework, curriculum, and consensus works

**Status.** Post hoc. The check was run after the domains, the adjudication (Addendum D), and a review of the revised manuscript had been completed, and it does not change the domains. It asks whether the six sources of Section 1, which were chosen before the structured search was complete, missed content that other framework, curriculum, or consensus works list.

**Works.** The 13 records that the structured search included as framework, curriculum, or consensus works (Supplementary S2, role F; criteria I1, I2, I4, I5) and that are not crosswalk sources: R0001, R0004, R0006, R0007, R0011, R0024, R0033, R0037, R0042, R0102, R0186, R0353, R4135. The four crosswalk sources found by the search and the related framework of Semerikov et al. (2026), with which the manuscript compares the result, are excluded. R0042 reports the same study as crosswalk source S6, and R4135 the same study as R0006; both are counted as separate works.

**Reporting fixed before any extraction.** (1) For each work: what was read, the number of content items, and the count per domain D1–D9, practice layer, societal dimension, or none. (2) Every item mapped to none is listed verbatim. (3) A topic outside the nine domains is flagged as a candidate the derivation did not see if it appears in at least 3 of the 13 works, at least 2 of them school-level, mirroring R-retain. The flag is reported; the domains are not changed by this check.

**Coding.** One item per topic, concept, example, or learning standard as the work lists it; rationale, motivation, attitude, and method statements are not content. Items were assigned to the cluster definitions used in the adjudication (Addendum D), calibrated on their member codes, and mapped to domains as in S4_crosswalk_clusters.csv (K01 D1, K02 D2, K03 D3, K05 and K09 D4, K06 D5, K07 D6, K08 D7, K10 D8, K12 D9, K13 practice layer). Citizen-facing societal, ethical, or economic content counts for the societal dimension; K04, K11, K14, and content in no cluster count as none. Curriculum documents, school textbooks, and teachers count as school-level; R0186 covers university and high-school textbooks and is counted as school-level. Extraction and coding were done by a language model (Claude, Anthropic), the model that coded the six sources. A script confirmed that every item occurs verbatim in the saved text of its work. The authors did not re-check the coding item by item.

**What was read.** Each work was sought in an openly available copy with plain requests. One full text was read (R0024, publisher PDF); the other twelve were coded from their abstracts, because no open copy existed or the host refused automated requests or was unreachable. No request was retried against a host that refused it, and no full text was downloaded by hand. An abstract names fewer topics than a full text, so the counts are lower bounds and the check has low sensitivity to topics outside the domains.

**Counts per work.**

| Work | School-level | Read | Items | D1 | D2 | D3 | D4 | D5 | D6 | D7 | D8 | D9 | practice | societal | none |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R0001 | yes | abstract | 5 | 3 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 2 | 0 | 0 | 0 |
| R0004 | yes | abstract | 3 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
| R0006 | no | abstract | 9 | 4 | 1 | 3 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| R0007 | no | abstract | 2 | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| R0011 | yes | abstract | 3 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| R0024 | yes | full text | 45 | 9 | 2 | 12 | 0 | 0 | 1 | 0 | 8 | 11 | 2 | 0 | 0 |
| R0033 | no | abstract | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| R0037 | yes | abstract | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| R0042 | yes | abstract | 7 | 4 | 0 | 2 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| R0102 | yes | abstract | 2 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| R0186 | yes (mixed) | abstract | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| R0353 | yes | abstract | 7 | 6 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| R4135 | no | abstract | 2 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| **Total** | | | 87 | 30 | 4 | 20 | 0 | 0 | 1 | 0 | 9 | 20 | 2 | 0 | 1 |

**Items mapped to none (verbatim).**

- R0004 (abstract): "general relativity" — relativity: non-quantum topic in the Norwegian curriculum; outside all quantum clusters

**Result.**
- 86 of the 87 items fall within the nine domains or the practice layer (84 in the domains, 2 in the practice layer). Topic "relativity": 1 work(s).
- Pre-registered flag: did not fire.
- No item fell to D4, D5, or D7 (quantum information, computing, sensing), and none to the societal dimension. The works read concern quantum physics in the curriculum and its teaching; the three technology domains rest on the six sources (manuscript, Section 4.2), and the societal dimension is a design choice, not a result of the derivation.
- Teleportation (R0024) is a member code of the communication cluster (K07) in the crosswalk and is counted under D6 here; the placement grid (manuscript, Table 4) treats it under D4, as a use of entanglement as a resource.
- Rationale statements that mention society were not extracted as content, among them R0006 "informing and educating society about quantum technologies" and R0037 "the growing relevance of quantum technologies and the need to address quantum misinformation".
- File: `S4_coverage_check.csv` (one row per item: work, what was read, verbatim item, locator, cluster, domain, reason).
