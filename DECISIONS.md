<!-- # DECISIONS.md — decision & learnings log

A short running note of the real choices you made: what you tried, what failed and why, what
you changed. This is your engineering judgement on the record — it is what separates a builder
from a button-presser, and it is graded (challenge brief section 08).

Append a 1–2 line entry whenever you make a real decision or hit/fix a wall. Add a timestamp.

Format:
`[HH:MM] <decision or problem> → <what you did and why>`

---

## Example (replace with your own)
- `[10:20]` Chose plain-csv parsing over pandas → fewer deps, fast enough for 5k rows, model
  quota saved for the fixer.
- `[11:05]` Title detector over-counted duplicates → realized non-indexable pages were
  included; added an indexable+200 filter (per rulebook).
- `[12:40]` Dashboard wasn't updating live → MCP tool wasn't emitting the SSE event; added
  `_emit("issue", row)` in extract.

---

## My log

* `[12:30]` Reviewed detector coverage against rulebook.md → Identified missing title, meta description, H1, content quality, and redirect chain detectors before implementing new logic.

* `[12:45]` Added title and meta description detectors → Implemented title_too_short, missing_meta_description, duplicate_meta_description, and meta_description_too_long using the existing detector pattern to keep output consistent.

* `[12:55]` Corrected meta description threshold → Updated meta_description_too_long from >160 to >155 after verifying the official rulebook.

* `[13:05]` Verified H1 detector severities → Changed missing_h1 from High to Medium and duplicate_h1 from High to Low to match rulebook requirements.

* `[13:20]` Implemented content quality detectors → Added thin_content, non_indexable_but_linked, and slow_page using deterministic CSV analysis rather than model-based detection.

* `[13:30]` Completed detector coverage verification → Compared seo/detector.py against rulebook.md and confirmed all required detectors were implemented.

* `[13:45]` Investigated report schema validation failure → Found report.json was missing run_meta information required by report.schema.json.

* `[13:55]` Fixed report schema compliance → Updated _report_obj() in mcp/server.py to include run_meta, model_calls, and duration information.

* `[14:05]` Chose deterministic rule evaluation over AI classification → Improved reproducibility, reduced cloud usage, and ensured consistent rulebook compliance. -->







# DECISIONS.md — decision & learnings log

## My log

* `[12:30]` Reviewed detector coverage against `rulebook.md` → Audited the existing implementation before making changes to avoid duplicate work and identify missing detectors.

* `[12:45]` Added title and meta description detectors → Implemented `title_too_short`, `missing_meta_description`, `duplicate_meta_description`, and `meta_description_too_long` using the existing detector pattern to maintain consistent output formatting.

* `[12:55]` Corrected meta description threshold → Initial implementation used `>160` characters; updated to `>155` after validating against the official rulebook.

* `[13:05]` Verified H1 severities against the rulebook → Changed `missing_h1` from **High → Medium** and `duplicate_h1` from **High → Low** to ensure compliance.

* `[13:20]` Implemented content quality detectors → Added `thin_content`, `non_indexable_but_linked`, and `slow_page` using deterministic analysis of Screaming Frog export data instead of model-based classification.

* `[13:30]` Verified detector coverage → Compared `seo/detector.py` against `rulebook.md` and confirmed all required detectors were implemented.

* `[13:40]` Added redirect chain detection → Implemented chain detection based on redirect target relationships rather than flagging all redirects.

* `[13:45]` Investigated report schema validation issues → Discovered that `report.json` was missing the required `run_meta` object defined in `report.schema.json`.

* `[13:55]` Fixed report schema compliance → Updated `_report_obj()` in `mcp/server.py` to include `run_meta`, `model_calls`, and duration information.

* `[14:05]` Chose deterministic rule evaluation over AI classification → Improved reproducibility, reduced cloud usage, and ensured consistent rulebook compliance across datasets.

* `[14:15]` Validated generated outputs → Re-ran the audit pipeline and verified generation of both `outputs/report.json` and `outputs/report.html`.

* `[14:20]` Improved project documentation → Updated `CLAUDE.md`, `PROMPTS.md`, and `DECISIONS.md` to reflect actual implementation work, findings, and engineering decisions.
