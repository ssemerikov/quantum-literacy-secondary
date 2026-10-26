# Adjudicating coding disagreements (instructions for the model adjudicator)

**Task.** Two coders assigned topic items, taken verbatim from six published sources, to a fixed set of clusters. For the item in `PACKET_FOR_MODEL.csv` they chose different clusters. Decide it.

**Files you may use. Work only inside this folder (`adjudication_rerun_S6018/`).**
- `PACKET_FOR_MODEL.csv`: one row. `option_A` and `option_B` are the two coders' clusters, in random order.
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

**Saving (required, because the session may stop at any time).**
- After deciding each row, rewrite the whole of `DECISIONS_MODEL.csv`. It has the packet's columns plus `confidence`. Write it atomically: write `DECISIONS_MODEL.csv.tmp`, then rename it, for example with `python3 -I`.
- Then append one line to `progress.log`: UTC time, row number, decision.
- If `DECISIONS_MODEL.csv` already exists when you start, keep its decided rows and continue with the rest.
- Never modify `PACKET_FOR_MODEL.csv`.

**When the row is decided**, write `SUMMARY.md` with the decision, the confidence, and, if neither option fits well, a one-line explanation.
