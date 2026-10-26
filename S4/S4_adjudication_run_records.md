# Supplementary S4 — Run records of the model adjudication

## Adjudication of the 26 disagreements: prompt and run record


- **Requested by:** the corresponding author, in the session on 2026-10-26: "Use Opus 5.5 with Max efforts for adjudication". The authors will check every decision before submission.
- **Model:** Claude Opus 5.5 (`claude-opus-5-5`, Anthropic). It ran as a fresh Claude Code subagent with reasoning effort `max` and no access to the main model session's context.
- **Date:** 2026-10-26.
- **Relation to the coders:** coder 1 was the same model (`claude-opus-5-5`); coder 2 was Nemotron 3 Ultra (NVIDIA, via Ollama cloud).
- **Blinding measures:**
  - The A/B order is randomised per row (seed 20261026; the same order as the authors' packet).
  - The coders' own code labels are removed from the options, because their capitalisation and wording could identify the coder. The authors' packet (`evidence/adjudication/ADJUDICATION_PACKET.csv`) keeps them.
  - The unblinding key was moved out of the project's evidence folder for the duration of the run.
  - The adjudicator was told to read only this folder and not to infer coder identity or consequences.
- **Inputs:** `INSTRUCTIONS_FOR_MODEL.md`, `PACKET_FOR_MODEL.csv`, `cluster_definitions.md`, `sources/`.
- **Output:** `DECISIONS_MODEL.csv`, `progress.log`, `SUMMARY.md`.
- **Prompt given to the subagent:** see below, verbatim.

---
You are the adjudicator for a coding exercise in an academic study. Your working folder is:
<working folder>/adjudication_run/

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

---
**Interruption and resumption (2026-10-26).** The run stopped when the account's usage limit was reached. At that point the adjudicator had read every item but saved no decision. After the account holder logged in again, it was resumed in the same context with this message (verbatim):

> Resume the adjudication: the usage limit that stopped you has been cleared. Nothing has been saved to disk yet. Write your decisions now, following INSTRUCTIONS_FOR_MODEL.md: after each row, rewrite DECISIONS_MODEL.csv atomically and append a line to progress.log. If you consult the advisor on borderline rows, save the rows you are sure of first. Then write SUMMARY.md and reply in the format requested in your original prompt. All other rules are unchanged: work only inside adjudication_run/.

The adjudicator finished at 09:19 UTC, with all 26 rows decided. It could not create SUMMARY.md because subagents cannot write report files. The main model session saved that file verbatim from the adjudicator's final report.

The subagent also had access to an "advisor" tool. That tool sends the subagent's own transcript to a stronger reviewer model, so it adds no information from outside the adjudication folder. The subagent's transcript shows 3 advisor calls; the advice itself is redacted in the transcript and is not recorded.

## Adjudication of the 26 disagreements: the model's summary


(Written by the main model session from the adjudicator's final report, verbatim, because the subagent could not create report files; 2026-10-26.)

All 26 rows of `PACKET_FOR_MODEL.csv` are decided. The decisions are in `DECISIONS_MODEL.csv`, which has the packet's columns plus `confidence`.

## Decision counts

| Decision | Rows |
|---|---|
| A | 12 |
| B | 14 |
| other | 0 |
| none | 0 |

Row 1 is counted as A. Its option A is itself "none (no cluster fits)", so choosing A there means that no cluster fits.

Confidence levels: 10 high, 6 medium and 10 low.

## Low-confidence rows

| Row | Source | Item | Decision | Why confidence is low |
|---|---|---|---|---|
| 1 | S5 | Surface tension | A (none) | K03 is the matter and materials cluster, but surface tension has no quantum content as taught at secondary level. |
| 3 | S4 | Analogy of standing waves and a particle in a box | B (K01) | S4 offers it as an illustration of Quantization. The particle-in-a-box model can also be read as a representation of states (K02). |
| 4 | S5 | Electrons | B (K03) | A bare term. K04 ("subatomic particles") fits it literally; K03 rests on its neighbours in the sequence (spin, Franck-Hertz experiment, atomic models). |
| 11 | S3 | Heat radiation | B (K03) | Light emitted by matter (K03), but also the phenomenon in which energy quantisation first showed itself (K01). |
| 12 | S3 | Single molecule microscopy | B (K08) | A measurement and imaging technique (K08), but also readable as a device whose operation relies on quantum physics (K10). |
| 15 | S3 | Stationary states | B (K02) | Defined by how a state changes over time (K02), but taught at secondary level together with energy quantisation (K01). |
| 17 | S5 | Quantum harmonic oscillator | A (K02) | A model system (K02), but it also exemplifies quantised energy (K01). Its neighbours in the sequence are mixed. |
| 18 | S3 | Schrödinger's cat | A (K12) | Mainly a vehicle for discussing interpretation (K12), but S3 lists it in its Examples column beside experiments (K01). |
| 21 | S4 | Double-well | A (K01) | S4 offers it for four principle-type key concepts, but it is in itself a model potential described by wave functions (K02). |
| 25 | S3 | Free vs. localised particle | A (K01) | The source gives no description. It is a conceptual principle (K01), but could also be read as a wave-function description (K02). |

## Rows where neither option fits well

- **Row 1 (Surface tension):** K03 covers the *quantum* physics of matter, but surface tension is taught classically. "None" (option A) was chosen, although the item's place in S5's Physical Foundations list leaves K03 arguable.
- **Row 4 (Electrons):** The bare noun fits K04 literally (a subatomic particle) and K03 only through context (atoms). Electrons treated as quantum objects could also fall under K01.

## Rules applied for consistency

- **S4:** Where an item fits both options, S4's own grouping decides: the key-concept category in Table 2, or the key-concept tables (8a–8i) in which an illustration is offered. This covers rows 2, 3, 8, 14, 16, 20, 21 and 22.
- **S3:** Table 6 is sorted by the number of experts, so adjacent items share a vote count, not a theme. They were not used as evidence.
- **S5:** Tables III–V list topics "in sequence as given to the experts", so adjacent items were used as evidence (rows 4, 5, 9 and 17).
- **S6:** The source's own thematic grouping (Table III) and its nature-of-science framing (Table I) were used for rows 13 and 19.

## Neutral re-run of S6-018: pre-registration and result


- Decided by the authors on 2026-10-26 after a model-run review of the revised manuscript noted that the original instructions singled this item out.
- Item: S6-018, "Methodology (e.g., experiments and hypothesis)", Stadermann et al. 2019, Table I aspect N1.
- Original run (adjudication_run/, 2026-10-26): decision K12 (nature of science), confidence high. The original instructions contained a paragraph naming this item as possibly ambiguous and stating the two readings.
- This run: same model (Claude Opus 5.5, claude-opus-5-5), same effort setting (max), fresh agent; same cluster definitions and source texts; the instructions are the original ones with that paragraph removed and the counts changed from 26 items to one. Option order re-randomised (seed 20261027): option_A = K12, option_B = K13 (the original run had A = K13, B = K12).
- The agent is not shown the original decision and is told not to open anything outside this folder.
- Pre-registered reporting: both decisions are reported in §3.3 and S4. If this run decides K13 (practices), R-crosscut is re-applied mechanically and its result reported; whether practices then become a domain is put to the authors before any manuscript change. If it decides K12, the text states that the neutral re-run agreed.

## Result (added after the run)
- 2026-10-26T15:28:35Z: decision K12 (option A in this run's order), confidence high — the same cluster as the original run. Under the pre-registered reporting, the text states that the neutral re-run agreed; R-crosscut is unchanged (practices remain a layer).

## Neutral re-run of S6-018: summary


- Item: S6-018, "Methodology (e.g., experiments and hypothesis)".
- Decision: A = K12 Nature, history and philosophy of quantum physics. Confidence: high.
- Reason (from DECISIONS_MODEL.csv): "NOS aspect on scientific method (experiment-theory relation, thought experiments in QP's development): K12 'what it shows about the nature of science', not K13 'activities that learners carry out'."
- Run: 2026-10-26T15:28:35Z (progress.log). PACKET_FOR_MODEL.csv unchanged (md5 edceef90d5f158c2ccedc63eefbc3c29).
