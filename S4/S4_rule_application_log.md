# Supplementary S4, Part C — Rule-application log (clustering, R-retain, R-merge clauses 1 and 2, R-split, R-crosscut, addenda)

Published copy of the project file `crosswalk_decisions.md`; SHA-256 of the original: `b9a39cdfa7ebfb7fb55926f1bb258b5cb8a9ec45d2926f2d073a0a031e442378`. 3 redactions, marked ⟦…⟧, replace internal file names, internal role names, or references to a separate manuscript, and local times are given in UTC; nothing else is changed. 

---

# Crosswalk decision log (W2 / T5) — PROVISIONAL pending the second coder

Written 2026-10-25 (UTC) by the `crosswalk` agent (Claude, model ID `claude-opus-5-5`). Rules: `evidence/crosswalk_rules.md`, sha256 `ffe9bd716970122d7e83d5e0086c33a5392612833059f939c80c6adb88d47fea`, verified unchanged before coding and again before this log was written. Protocol (written before coding): `supplementary/S4_crosswalk_protocol.md`. Data: `crosswalk_extraction.csv` (339 items), `crosswalk_coding.csv` (232 codes), `crosswalk_clusters.csv` (13 candidate clusters). Scripts: `tools/crosswalk/01_extract.py` … `05_outputs.py`.

**Read Addendum B (end of file) first:** an extraction gap (Merzel et al. Tables 8a–8i) was found after the first rule application; the item set grew from 339 to 400, and the counts and the K09 result below are superseded where Addendum B differs.

Every result below is **provisional** until an author has second-coded the packet (due Thu 29 Oct 2026) and agreement has been computed.

## 0. Results that contradict the pre-registered hypothesis (read first)

The rules file recorded a hypothesis of eight domains, with "QC hardware & sensors" merged into enabling technologies/platforms and sensors moved to sensing. The rules give a different result:

1. **Societal context is not retained.** Only the CFQT (S1, domain 8 "Valorisation") supplies items about market, business, impact, ethics or public communication. None of the five school-level content lists does. Under R-retain the CFQT cannot create a domain alone, so these 4 items are residual. (The item units were fixed before coding as content lists; the sources' rationale or introduction text, e.g., the NSF introduction on "commerce, governance, privacy, employment, and education", was not eligible. Widening the scope now would be outcome-driven, so it was not done.)
2. **Nature, history and philosophy of quantum physics is retained as a domain** (S3, S4, S5, S6; also under the endorsement reading), although the rules file lists "nature of science, history or philosophy" as an example of a residual.
3. **Atoms, light and matter** and **Quantum information and qubits** come out as domains of their own; R1's "Physical foundations" is divided.
4. **Qubit hardware platforms** do not form a domain and do not merge anywhere: they fail R-retain and are reported as residuals (§6), not absorbed.
5. **Communication and sensing are fragile:** they are retained only under the literal reading of "support" (§2).

Primary outcome: **nine domains plus a cross-cutting practice layer**, with 17 residual items. Endorsement reading: seven domains.

## 1. Candidate clusters (step 3)

Items per source, literal reading (endorsement reading in brackets). S1 = CFQT (workforce); S2–S6 school-level.

| ID | Candidate cluster | codes | S1 | S2 | S3 | S4 | S5 | S6 | items |
|---|---|---|---|---|---|---|---|---|---|
| K01 | Quantum principles and phenomena | 48 | 1 (1) | 10 (10) | 22 (11) | 27 (24) | 33 (7) | 6 (6) | 99 (59) |
| K02 | Mathematical representations | 24 | 1 (1) | 4 (4) | 6 (3) | 8 (8) | 12 (1) | 3 (3) | 34 (20) |
| K03 | Atoms, light and matter | 46 | 4 (4) | 0 | 24 (15) | 7 (7) | 27 (1) | 6 (6) | 68 (33) |
| K04 | Particle and nuclear physics | 4 | 0 | 0 | 3 (1) | 0 | 1 (0) | 0 | 4 (1) |
| K05 | Quantum information and qubits | 10 | 0 | 9 (9) | 1 (1) | 2 (2) | 1 (0) | 0 | 13 (12) |
| K06 | Quantum computing and simulation | 11 | 5 (5) | 4 (4) | 1 (1) | 2 (1) | 1 (0) | 0 | 13 (11) |
| K07 | Quantum communication and cryptography | 12 | 6 (6) | 3 (3) | 4 (0) | 1 (0) | 4 (0) | 0 | 18 (9) |
| K08 | Quantum sensing and metrology | 17 | 7 (7) | 5 (5) | 2 (0) | 0 | 6 (0) | 0 | 20 (12) |
| K09 | Qubit hardware platforms | 9 | 8 (8) | 1 (1) | 0 | 0 | 0 | 0 | 9 (9) |
| K10 | Quantum devices and enabling technologies | 28 | 4 (4) | 0 | 17 (4) | 0 | 12 (0) | 1 (1) | 34 (9) |
| K11 | Valorisation and societal impact | 4 | 4 (4) | 0 | 0 | 0 | 0 | 0 | 4 (4) |
| K12 | Nature, history and philosophy of QP | 15 | 0 | 0 | 4 (1) | 2 (2) | 6 (1) | 7 (7) | 19 (11) |
| K13 | Practices (programming, experimentation, building) | 4 | 2 (2) | 0 | 0 | 0 | 2 (0) | 0 | 4 (2) |

Boundary placements made at clustering, with the rule used: an item goes to sensing when the source links it to precision measurement or timing (GPS: S2-004 "depends on the extreme precision of atomic clocks"; S3-074 by the same code); medical and laboratory instruments whose working principle the item names but not a measurement-precision claim go to devices (MRI, NMR, CT, PET, STM, SEM, AFM). Sensor devices named as sensors (S1 6.2–6.4; S5 "Superconducting sensors", "Spin-qubit based sensors", "Atom interferometers") go to sensing; physical systems named as qubits or qubit control go to K09. Neither boundary changes any pass/fail result (checked by `04_pivotal.py`), except the K09 sensitivity in §5.

## 2. R-retain (≥ 3 of 6 sources, ≥ 2 school-level; the CFQT alone cannot create a domain)

**Which reading do the frozen rules specify?** The rule says a domain "is supported by items from ≥3 of the 6 sources". It counts sources whose *items* support the domain and says nothing about the sources' own ratings or inclusion thresholds. The literal reading (an extracted item coded into the domain counts) is the reading closest to the text, and it was pre-registered as primary in protocol §2 before any item was coded. The rule is nevertheless **ambiguous**: "support" is undefined, and the extraction includes topics that a source rated and rejected (S5 Tables IV–V: no Physical-Foundations or Quantum-Technologies topic met both inclusion criteria, and all have Cns < 0.75 and inclusion below 75 %; the authors write that advanced QT topics "were widely deemed unsuitable for the secondary school"). The primary result below uses the literal reading; the endorsement outcome is reported beside it. **Flag for the authors:** if they prefer the endorsement reading, it must be added as a dated amendment to `crosswalk_rules.md`, and the domain count becomes seven.

| Cluster | Literal: sources (school) | Result | Endorsed: sources (school) | Result |
|---|---|---|---|---|
| K01 | 6 (5) | retain | 6 (5) | retain |
| K02 | 6 (5) | retain | 6 (5) | retain |
| K03 | 5 (4) | retain | 5 (4) | retain |
| K04 | 2 (2) | **fail** | 1 (1) | fail |
| K05 | 4 (4) | retain | 3 (3) | retain |
| K06 | 5 (4) | retain | 4 (3) | retain |
| K07 | 5 (4) | retain | 2 (1): S1, S2 | **fail → fragile** |
| K08 | 4 (3) | retain | 2 (1): S1, S2 | **fail → fragile** |
| K09 | 2 (1): S1, S2 | **fail** | 2 (1) | fail |
| K10 | 4 (3) | retain | 3 (2): S1, S3, S6 | retain |
| K11 | 1 (0): S1 only | **fail** | 1 (0) | fail |
| K12 | 4 (4) | retain | 4 (4) | retain |
| K13 | 2 (1) | (practices: decided by R-crosscut) | 1 (0) | — |

K07 and K08 fall to S1 and S2 under the endorsement reading because every S3, S4 and S5 item in them is below that source's own cut-off (S3: atomic clock 6/12, GPS 5/12, quantum cryptography 7/12, teleportation 6/12, BB84 3/12; S4: quantum cryptography offered as a sparse illustration; S5: all Table V topics < 75 % inclusion, e.g., BB84 34 %, atom interferometers 29 %, Definition of SI units 51 %). This matches Bitzenbauer et al.'s own conclusion. The manuscript must not describe communication or sensing as consensus domains.

## 3. R-merge (applied to retained clusters)

Clause 1 test: write the A1/A2 objective each cluster implies (CFQT A1 "Reproduce basic quantum concepts & terminology"; A2 "describing and relating quantum concepts, including elements of mathematical formalism", as quoted by S5 §VII.B) and ask whether the two can be told apart. Clause 2 test: is a cluster's school-level support only "awareness of platforms/devices"?

| Pair | Objective implied by cluster A (items) | Objective implied by cluster B (items) | Decision |
|---|---|---|---|
| K01–K02 | describe and relate phenomena: superposition, interference, measurement outcomes, uncertainty (S4-001 "Superposition"; S6-005 "Wave-particle duality or complementarity") | represent states and compute outcome probabilities: "Quantum states are represented by directions or vectors in an abstract space" (S2-006); "Calculation of detection probability, Born rule" (S6-017); Dirac notation, matrices (S5-003/004) | distinguishable (representation vs phenomenon; S4 and S6 class them separately; S5 treats the mathematical level as a separate instructional level) → **no merge** |
| K01–K03 | as above | explain spectra, emission and material properties from quantised levels and bands (S6-003 "Discrete energy levels (line spectra)"; S3-036 "Spectral lines"; S5-077 "Band structure") | distinguishable (principle vs its application to atoms and solids) → **no merge** |
| K01–K05 (most contestable) | "Spin-1/2 particle (two level system)" (S5-010); "Two-level system" (S4-029): describe measurement outcomes of a two-state system | "Unlike a classical bit, each qubit can represent information in a superposition" (S2-015); "a set of n qubits can exist in a superposition of all of these states" (S2-016); "The quantum bit, or qubit, is the fundamental unit of quantum information" (S2-014) | the information objectives (bit–qubit contrast, encoding, 2^n scaling) occur in no K01 item → **no merge**. Alternative recorded and not adopted: Merzel et al. §5.3.2/§6.2 note that "Qubit" and "Two level systems" were offered both as key concepts and as illustrations ("indeterminacy"), and the CFQT lists "Two-state systems (e.g. spin-1/2, polarisation), qubits" together in 1.1. If the second coder clusters "qubit" with "two-level system", K05 fails R-retain (pivotal, §5). |
| K05–K06 | qubit as unit of information (above) | "will solve certain complex computational problems more efficiently … no speed advantage for many other types of computations" (S2-028); "Quantum gates (esp. H. Z. X. CX)" (S5-089); error correction (S2-029) | distinguishable → **no merge** (Semerikov et al. (2026) place "Qubit concept" inside Quantum computing; the crosswalk does not) |
| K06–K07–K08 | computing (above) | communication: eavesdropper detection (S2-032), teleportation (S2-031); sensing: "detect and measure physical properties with the highest precision allowed by quantum mechanics" (S2-033) | distinguishable; S2 itself presents them as three areas → **no merge** |
| K03–K10 | energy levels, bands, materials (above) | explain how devices work and name the technologies QT require: "Technical applications (e.g., scanning electron microscope SEM, semiconductors, LED, laser)" (S6-007); "Solar cells", "Lasers", "LEDs" (S3) | distinguishable (device function vs underlying physics; S3 and S6 separate applications from concepts) → **no merge** |
| K08–K10 | precision measurement, quantum vs classical sensors, SI units (S2-036; S5-098) | device function (above) | distinguishable → **no merge** |
| K01–K12 | principles (above) | discuss interpretations, history, models, tentativeness (S6-010 "Philosophical consequences or interpretations"; S6-019–023) | distinguishable → **no merge** |

Clause 2: K07 has conceptual school items (S2-032 eavesdropper detection; S3-083 "Bennet–Brassard protocol"; S5-092 "Comparison to current cryptography technologies"); K08 has conceptual school items (S2-033, S2-034, S2-036; S5-098 "Quantum sensors versus classical sensors"); K10 has curriculum learning outcomes (S6-007, present in 13 of 15 countries). None has school-level support only at the level of awareness of platforms/devices → **no merge under clause 2**. K09, the cluster for which clause 2 was written, never reaches R-merge because it fails R-retain.

## 4. R-split (both conditions needed: ≥ 1 phase difference in prerequisites per P1 AND ≥ 2 sources separate the parts)

P1 evidence available now: Stadermann et al. 2019 (QP mostly in final-year advanced courses, ages 17–19; only Bavaria teaches it in a compulsory course at 15–16; entanglement in 2 of 15 countries' documents; discrete energy levels in 15 of 15; no materials or band-structure item); Lehka 2021 Appendix Г as summarised in the project's internal notes (not re-read for this log): Ukrainian standard grade 10 quantum optics/photoeffect, grade 11 Bohr model, lasers, de Broglie; uncertainty and tunnelling only at profile level; probability and complex numbers only in grade-10 advanced mathematics; no matrices. `evidence/evidence_matrix.csv` (T2) does not yet exist, so **every "not established" below is provisional pending T2/T6.**

| Candidate split | ≥ 2 sources separate the parts? | ≥ 1 phase prerequisite difference (P1)? | Decision |
|---|---|---|---|
| K01: entanglement/non-locality vs other principles | yes: S3 Table 5 "nonlocality"; S4 categories "Entanglement", "Non-locality"; S5 Table I "Entanglement and nonlocality" (CFQT-structured) | not established: entanglement's prerequisites (superposition, probabilistic measurement, correlation) are the same probability-based prerequisites as the rest of K01; the curricula differ in *presence* (2/15 vs 15/15) but P1 concerns prerequisites | **no split** (provisional) |
| K03: atoms vs materials/solid state | yes: S3 Table 5 "atoms" vs "materials"; S5 Table I "Atoms and atomic physics" vs "Solid state physics" / "Material science and nanostructures" (CFQT-structured) | not established: atomic levels are core curriculum (15/15, ages 17–19; Ukrainian grade 11); no P1 source reports where band structure sits | **no split** (provisional) |
| K10: first-generation devices vs QT enabling technologies | no: only S5 separates them (Tables IV vs V, CFQT-structured); S1 has no first-generation-device category; S3 groups all devices as "applications"; S6 has one item | — | **no split** |
| K12: history vs philosophy/interpretation vs NOS | yes: S6 (Table III philosophical theme vs Table I NOS/history aspects); S3 (a "history" category) | no: NOS aspects appear in ≥ 12 of 15 countries' curricula in all QP courses; no curricular prerequisite separates them | **no split** |

## 5. R-crosscut and pivotal items

K13 contains "Computers and software" (S1-011), "Quantum programming tools …" (S1-022), "Measuring h" (S5-037) and "Microelectronics (Arduino. Raspberry)" (S5-103). Sources that list practices as a separate category: S1 (proficiency area II "QT hardware (HW) & software (SW) engineering"). S6 lists "Methodology (e.g., experiments and hypothesis)" inside its table of *nature-of-science* aspects; it was coded as understanding methodology (Table I example: "relation between experiment and theory", "thought experiments") and clustered in K12, so S6 is not counted as listing practices. One source < 2 → **practices become a cross-cutting practice layer noted in every domain**, not a domain. (If N1 were coded as a practice, S6 would arguably make two sources, and R-crosscut would yield a practice domain; this item is in the purposive add-on, §8.)

Pivotal items (recoding one would flip a result; from `04_pivotal.py`):

| Result | Reading | Pivotal item(s) |
|---|---|---|
| K05 retained | both | code "qubit" (S2-014, S4-015, S4-040, S5-054); endorsed also S3-059 "Quantum information" |
| K06 retained | endorsed | S3-063 "Quantum computers" (8/12, exactly at cut-off) or S4-016 "Quantum computing" (jointly) |
| K10 retained | endorsed | S6-007 "Technical applications" |
| K12 retained | endorsed | code "Schrödinger's cat" (S3-046, S5-033) |
| K09 fails | literal | S2-024 (NSF 6b); S5-100 "Entangled photon sources", S5-093, S5-094 (one S5 item coded as a platform would give K09 three sources) |
| practice layer | — | S6-018 "Methodology (e.g., experiments and hypothesis)" |

## 6. Resulting domains (primary = literal reading), definitions and support

| Domain | Definition (one sentence) | Items (endorsed) | Sources literal / endorsed |
|---|---|---|---|
| D1 Quantum principles and phenomena | Superposition, interference, measurement and probability, uncertainty and complementarity, wave–particle duality, quantisation, spin, entanglement and decoherence, with the experiments that display them. | 99 (59) | 6 / 6 |
| D2 Mathematical representations | State vectors, wave functions, amplitudes and the Born rule, operators and model systems such as the potential well. | 34 (20) | 6 / 6 |
| D3 Atoms, light and matter | Quantum accounts of atomic structure and spectra, light–matter interaction, and the properties of solids and materials. | 68 (33) | 5 / 5 |
| D4 Quantum information and qubits | The qubit as a unit of information in a two-state system, its contrast with the bit, multi-qubit states, and what quantum information science is. | 13 (12) | 4 / 3 |
| D5 Quantum computing and simulation | What quantum computers and simulators do, gates and algorithms, speed-up and its limits, error correction. | 13 (11) | 5 / 4 |
| D6 Quantum communication and cryptography *(fragile)* | Quantum cryptography and key distribution, teleportation, random-number generation and networks. | 18 (9) | 5 / **2 (fails)** |
| D7 Quantum sensing and metrology *(fragile)* | Precision measurement with quantum states: sensors, atomic clocks and timing, quantum limits, SI units. | 20 (12) | 4 / **2 (fails)** |
| D8 Quantum devices and enabling technologies | Devices that work because of quantum physics (lasers, LEDs, solar cells, detectors, microscopes, medical scanners) and the techniques used to build quantum technologies. | 34 (9) | 4 / 3 |
| D9 Nature, history and philosophy of quantum physics | Historical development, interpretations, the role of models and other nature-of-science aspects of quantum physics. | 19 (11) | 4 / 4 |
| Practice layer (cross-cutting) | Programming, simulation, experimentation and building, noted in every domain. | 4 (2) | — |

## 7. Comparison (done only after §§2–5)

**CFQT content map (8 domains).** D1 ≈ CFQT 1.1; D2 ≈ 1.2; D3 ≈ domain 2 (2.1–2.4); D4 has no CFQT domain (the CFQT places qubits in 1.1 and information theory in 1.2); D5 ≈ domain 5 (5.3 programming tools → practice layer); D6 ≈ domain 7; D7 ≈ domain 6; D8 ≈ domain 3 (3.1–3.4; 3.5 → practice layer) plus first-generation devices that the CFQT does not list; **CFQT 4 "Quantum hardware" → no domain (residual)**; **CFQT 8 "Valorisation" → no domain (residual)**; D9 has no CFQT counterpart.

**R1 manuscript (9 domains).** Physical foundations → D1 + D3 (and D4 for qubits). Mathematical foundations → D2. Supporting technologies → D8 (widened to first-generation devices). **QC hardware & sensors → not retained:** sensors → D7; qubit platforms → residual. Quantum computing → D5 (qubit concept moved to D4). Quantum sensing → D7 (fragile). Quantum communication → D6 (fragile). Practical skills → cross-cutting layer. **Societal context → not retained (residual).** New: D3 as a separate domain, D4, D9.

**Semerikov et al. (2026) (8 domains, Table 3, p. 7).** Physical foundations (superposition, entanglement, measurement, wave–particle duality) → D1 (its content is CFQT 1.1, not CFQT domain 2, so the same label means different things in the two frameworks); Mathematical foundations → D2; Quantum computing (incl. "Qubit concept") → D5 + D4; Quantum sensing → D7; Quantum communication → D6; Supporting technologies (cryogenics, photonics, control systems, infrastructure) → D8; **Applications and impact (industry applications, societal benefits, ethics, careers) → no domain**; Practical skills → practice layer. Semerikov et al. (2026) have no atoms/matter domain, no information domain and no nature-of-science domain; like the crosswalk, they have no separate hardware domain.

**Why (or whether) hardware/sensors and sensing are separate — answer to R1.2a.** They should not be separate, and in the derivation they are not. (a) Sensor devices code to sensing by subject matter: the CFQT's sensor subdomains (6.2–6.4) and S5's "Superconducting sensors", "Spin-qubit based sensors" and "Atom interferometers" all sit in D7. (b) Qubit hardware platforms (CFQT 4.1–4.8) form a candidate cluster that fails R-retain: apart from the CFQT, only one NSF fundamental (6b, "Some types of qubits are inherently isolated, whereas others require carefully-engineered materials …") addresses them, and no school-level Delphi or curriculum source names a qubit platform. So no "hardware" domain survives, and the R1 split had no support beyond the CFQT's workforce structure (CFQT v3.0 itself keeps "4 Quantum hardware" and "6 Quantum sensors and imaging systems" apart). Observation only: the R1 label "QC hardware & sensors" closely mirrors S5's round-1 category "Hardware for quantum computers and sensors" (9 mentions), which S5's authors assigned "using the CFQT". An internal planning note states that the split was inherited from the CFQT v1.0 content map; this was not verified against the Zenodo record. ⟦The manuscript⟧ may present qubit platforms as awareness-level context inside D8, but must say that this placement is an authors' decision and **not derived from the crosswalk**.

## 8. Residuals, second coding, limitations

**Residuals (items in failed clusters; fit test = the §5 clustering criterion, so none is re-homed): 17 of 339 items (5.0 %).**
- K09 Qubit hardware platforms: 9 (S1 4.1–4.8: 8; S2 6b: 1).
- K04 Particle and nuclear physics: 4 (S3 "Subatomic particles", "Standard model", "Radioactive decay"; S5 "Pair production").
- K11 Valorisation and societal impact: 4 (S1 8.1–8.4).
- Under the endorsement reading, K07 (18 items) and K08 (20 items) would also be residual (55 items in all).

**Second coder.** Packet `crosswalk_second_coding_packet.csv`: a random 40 % stratified by source (seed 20261025) plus an unmarked purposive add-on of the pivotal items in §5 that the random draw missed. Agreement on the random sample and on the pivotal items is reported separately (instructions in `SECOND_CODER_INSTRUCTIONS.md`).

**What a reviewer could criticise.**
1. One model did extraction, coding and clustering, and had seen the source structures; the second coder is the only check.
2. Clustering granularity is a judgement. Coarser clusters would merge D1/D3 (as Semerikov et al. (2026) and R1 did); finer ones would create more residuals.
3. "Support" is undefined in the frozen rules; two domains depend on the reading.
4. Several retentions rest on one or two items (§5).
5. Source independence is limited. S4 reports the first round of the same QCI Delphi study whose three rounds S5 reports (S5 §IV.B: "previously reported by Merzel et al."). S4 respondents were shown the CFQT, S5 structured its categories with the CFQT, and S5's authors include the CFQT authors (Greinert, Müller) and the first authors of S3, S4 and S6. Treating S4 and S5 as one source changes no R-retain result under either reading (checked by hand from §2), but it makes K12 (endorsed) depend on S3's "Schrödinger's cat".
6. S2 is a non-consensus workshop document, and S1 is workforce-oriented.
7. Item units differ in grain: one CFQT subdomain is counted like one S3 topic. Counts are therefore read as source presence, not weight.
8. S4 illustrations come only from the article text; the image tables 7a–9b (104 illustrations) were not extracted.
9. The P1 judgements in R-split rest on two curriculum sources and are provisional.
10. English-language sources only.


## Addendum B — 2026-10-25 (UTC): extraction gap found after the first rule application

**What happened.** After §§1–8 were written, the authors' review noted that Merzel et al.'s image tables had not been extracted. The publisher PDF could not be retrieved (anti-bot challenge), so the PDF pages could not be rendered; instead the publisher's online table pages and full-size table images were retrieved (online tables 7–27). Tables 7a–7h list KC categories per prominent illustration (no new illustrations); Tables 9a–9b are consensus tables (HTML); **Tables 8a–8i list the illustrations offered for the nine most prominent KC categories.** All nine images were read and transcribed (118 cells; Merzel et al.'s Table 6 gives 127 per-category distinct illustrations for these categories: 8a 20 vs 21, 8c 14 vs 20, 8e 11 vs 12, 8f 12 vs 13; the images show complete tables, so the difference is recorded as an inconsistency in the source, not filled in). Illustrations for the other ten KC categories are not tabulated by the source. PDF page numbers are not available; locators give table, online table number, row and column.

**Extraction.** 61 distinct illustrations not already extracted were added as S4-050 to S4-110 (variants of existing items were mapped to them, e.g., "BB84" and "Ekert 91" to S4-049; "Spin states" to S4-042). Their verbatim check is against our own transcription only (`image_transcription`), not an independent match. By Merzel et al.'s own cut-off (at least 6 mentions and at least 4 KC categories), **none of the 61 is endorsed.** Items: 400 (S4: 110).

**Coding and clustering.** Codes were assigned under protocol §4 (22 new codes; 254 in all). "Bernstein 1967" (S4-099) cannot be coded from its wording and forms an unclassifiable cluster K14 that cannot be retained. Two judgements decide a result and are flagged: S4-097 "Coherent control" and S4-098 "NV-center" were coded as qubit control / qubit platform (K09). Both were offered once, by physicists, for KC "Qubit". "NV-center" names neither a qubit nor a sensor, and the CFQT lists NV centres under both 4.2 and 6.2, so the source's KC context was used to resolve it; the alternatives are K01 (two-state dynamics) and K08 (sensor).

**R-retain, 400 items** (sources literal / endorsed; items literal (endorsed)):

| Cluster | Items | Literal | Endorsed | Change from §2 |
|---|---|---|---|---|
| K01 principles | 130 (59) | 6 retain | 6 retain | S4 27→58 items |
| K02 mathematical representations | 44 (20) | 6 retain | 6 retain | S4 8→18 |
| K03 atoms, light and matter | 75 (33) | 5 retain | 5 retain | S4 7→14 |
| K04 particle/nuclear | 4 (1) | 2 fail | 1 fail | none |
| K05 quantum information and qubits | 13 (12) | 4 retain | 3 retain | none |
| K06 quantum computing | 16 (11) | 5 retain | 4 retain | S4 2→5 (Hadamard gate, Quantum circuit, Bernstein-Vazirani alg.) |
| K07 communication | 19 (9) | 5 retain | **2 fail** | S4 +Teleportation; **dispute not resolved** |
| K08 sensing | 20 (12) | 4 retain | **2 fail** | none: no sensing illustration in 8a–8i |
| K09 qubit hardware platforms | 11 (9) | **3 retain** (S1, S2, S4) | 2 fail | **changed: was 2 fail** |
| K10 devices and enabling technologies | 34 (9) | 4 retain | 3 retain | none |
| K11 valorisation/societal | 4 (4) | 1 fail | 1 fail | none |
| K12 nature/history/philosophy | 24 (11) | 4 retain | 4 retain | S4 2→7 |
| K13 practices | 5 (2) | 3 (R-crosscut) | 1 | S4 +Quantum games |
| K14 unclassifiable | 1 (0) | 1 fail | 0 fail | new |

**The reading dispute for D6/D7 does not disappear.** The new communication illustrations (Teleportation, offered by two groups; BB84 and Ekert 91, each by one) and the absence of any sensing illustration leave both domains at two sources under the endorsement reading. (⟦The authors have⟧ since confirmed the literal reading as primary and the endorsement reading as the sensitivity check.)

**K09 — two branches; no separate hardware domain in either.**
- **Branch A (literal reading, current coding):** K09 passes R-retain on S1 (8 subdomains), S2 (6b) and S4 (S4-097, S4-098). Its school-level support is one NSF fundamental and two single-mention illustrations, i.e. awareness of platforms only, so **R-merge clause 2 applies**. Partner criterion (stated before choosing, the same test as clause 1): the retained domain whose A1/A2 objective the school-level platform items serve. NSF Key Concept 4 defines the qubit as "encoded in a physical system, such as polarization states of light, energy states of an atom, or spin states of an electron"; NSF 6b concerns "types of qubits"; S4 offered both illustrations for the KC "Qubit". → **merged into D4 (Quantum information and qubits), which then includes awareness of physical qubit platforms.** Alternative considered and not adopted: D8 (devices and enabling technologies), which would rest on a subject-matter resemblance ("hardware is a kind of device"), not on how the school-level sources use the items.
- **Branch B (endorsement reading, or either S4-097/S4-098 recoded):** K09 fails R-retain (S1, S2) and its 11 items are residual.
- Wording consequence for the manuscript and the response letter: "the hardware domain fails R-retain" is true only in Branch B; under the primary reading it is an R-merge (clause 2) outcome. Sensor devices go to D7 by subject matter in both branches.

**Pivotal items (400-item set).** Literal: K05 on the code "qubit" (S2-014, S4-015, S4-040, S5-054); K09 on S2-024, S4-097, S4-098 (each). Endorsed: K05 on S3-059 and "qubit"; K10 on S6-007; K12 on "Schrödinger's cat" (S3-046, S5-033); K06 on S3-063 or S4-016 jointly. Practice layer: S6-018. S5-093/094/100 are no longer pivotal.

**Independence check repeated.** Treating S4 and S5 as one source changes no R-retain result under either reading (K09 literal: S1, S2, S4/S5 = 3).

**Resulting domains (primary, Branch A):** D1 130 items; D2 44; D3 75; D4 24 (13 + 11 merged platform items); D5 16; D6 19 (fragile); D7 20 (fragile); D8 34; D9 24; practice layer 5. **Residuals: 9 of 400** (K04 4, K11 4, K14 1). Endorsement reading: 7 domains; residuals 59 of 400 (K04 4, K11 4, K14 1, K07 19, K08 20, K09 11).

**Comparison with the R1 domains and the CFQT v3.0 content map (claim check).** The R1-round response draft states that "the R1 domains were taken over, with one addition, from the CFQT content map". Read against the R1 domain definitions (R1 manuscript, Table 2 and §4.2) and CFQT v3.0 (the version the R1 manuscript cites as v3), the correspondence is:

| CFQT v3.0 domain | R1 domain(s) |
|---|---|
| 1 Concepts and foundations | **two** R1 domains: "Physical foundations" (superposition, interference, entanglement, measurement = CFQT 1.1) and "Mathematical foundations" (= CFQT 1.2) |
| 2 Physical foundations of quantum technologies (atomic, optics, solid state, many-body) | **none** — R1 reuses the label "Physical foundations" for CFQT 1.1 content |
| 3 Enabling technologies and techniques | Supporting technologies |
| 4 Quantum hardware | "QC hardware & sensors" (which also adds sensor principles that the CFQT keeps in domain 6) |
| 5 Quantum computing and simulation | Quantum computing |
| 6 Quantum sensors and imaging systems | Quantum sensing (and partly "QC hardware & sensors") |
| 7 Quantum communication and networks | Quantum communication |
| 8 Valorisation (8.3 impact and responsibility incl. ethics; 8.4 education and communication) | partly Societal context, although R1 says this row "supplies the societal dimension absent from the CFQT" |
| — | Practical skills (no CFQT content domain; CFQT 3.5/5.3 subdomains and proficiency area II) |

The claim is therefore **approximate at best**: one CFQT domain is split into two R1 domains, one CFQT domain has no R1 counterpart despite the shared label, sensors appear in two R1 domains, Practical skills has no CFQT domain, and Societal context overlaps CFQT domain 8 although R1 calls it absent from the CFQT. ⟦The manuscript⟧ should not repeat "with one addition".

**Origin of the R1 label "QC hardware & sensors" (checked 2026-10-25, UTC).** Lehka (2021, p. 28) renders the CFQT v1.0 (2021) structure as seven knowledge fields and one practical-skills section: Concepts of quantum physics; Physical foundations of quantum technologies; Supporting technologies; **Hardware for quantum computers and sensors**; Quantum computing and simulation; Quantum sensors and metrology; Quantum communication; Practical skills and key competences. Lehka's own competency model (p. 54) has eight groups: physical foundations; mathematical foundations of quantum informatics; enabling technologies; hardware for quantum computers and sensors; quantum computing and simulation; quantum sensors and metrology; quantum communication; practical skills and general competences. Bitzenbauer et al. (2025, Table I) use the same category "Hardware for quantum computers and sensors", assigned with the CFQT. **The R1 nine domains equal Lehka's eight groups plus Societal context.** So "taken over, with one addition" holds approximately against CFQT v1.0 as rendered by Lehka (2021), with v1.0's concepts/physical-foundations pair re-cut into physical vs mathematical foundations, but not against CFQT v3.0, the version the R1 manuscript cites, where the domain is "Quantum hardware" and sensors sit only in "Quantum sensors and imaging systems". CFQT v1.0 itself (Zenodo) was not opened; the rendering is Lehka's (in Ukrainian; translation by the agent).

## Addendum C — 2026-10-25 (UTC): inter-model second coding (Amendment 1)

Second coder: NVIDIA Nemotron 3 Ultra (`nemotron-3-ultra:cloud`, via Ollama 0.30.6), two stages, blind to the first coder's codes; prompts, settings and raw records in `supplementary/S4_crosswalk_protocol.md` Addendum C and `evidence/second_coder_llm/`. **This is an inter-model check, not a human verification.**

- Agreement on cluster assignment: random sample 138/162 = 85.2 % (Cohen's kappa 0.826); pivotal items 11/14 = 78.6 % (kappa 0.731); all 170 packet items 84.7 % (kappa 0.822).
- 26 disagreements, listed in `evidence/crosswalk_disagreements.csv` for the authors (empty `author_decision` column). The most frequent were mathematical representations → principles (6) and atoms, light and matter → principles (5).
- **R-retain sensitivity:** with the second model's cluster substituted for all 170 sampled items, **no retention result changes under either reading.** Source sets change only for D7 and D8 (+S4, literal), the practice layer (+S6) and D9 (endorsed: loses S3 and is then supported by S4, S5 and S6, still three sources).
- **K09 (qubit platforms), Branch A** survives (S1, S2, S4) but then rests on one single-mention illustration, "NV-center", because the second model placed "Coherent control" (S4-097) with devices.
- **R-crosscut caveat (needs adjudication):** the second model placed S6-018 "Methodology (e.g., experiments and hypothesis)" with practices. If the authors adopt that, a second source arguably lists practices as a separate category and R-crosscut would turn the practice layer into a domain (ten domains on the literal reading).
- The second model was internally inconsistent on "Schrödinger's cat" (same label, two clusters).

- **Conditions on the agreement figures.** The stage-2 cluster definitions were written by the first coder (from the labels and the rules file only), and the clusters are the first coder's candidate clusters, so the figures measure agreement on assignment to that cluster set, not an independent clustering. The disagreements concentrate on the D1/D2/D3 boundaries, which supports the granularity limitation (§8, item 2) and changes no result.
- **Combined sensitivity (S4 and S5 counted as one source):** literal reading — no change with either coder, except that the practices cluster would fail R-retain (no consequence: practices are a layer by R-crosscut); endorsement reading with the second model's clusters — **D9 (nature, history and philosophy) would fail** (sources S4/S5, S6). The primary result is unaffected; add this to the limitations.

Until the authors have adjudicated the disagreements, the domain set stays provisional.
