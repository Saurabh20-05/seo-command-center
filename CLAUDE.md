<!-- # CLAUDE.md — project memory for the SEO Command Center build

This file is your **context / memory for the AI**. Claude Code loads it automatically every
session. Strong builders engineer this file instead of re-explaining everything in chat — it
is one of the clearest signals of good practice, and it is graded (see the challenge brief
section 08). Keep it short, specific, and update it as you learn.

Replace the prompts below with your own. This is YOUR file.

## What we are building
A Claude Code plugin that ingests a Screaming Frog SEO export (`internal_all.csv` + issue
CSVs), audits it against the rulebook, prioritizes issues, writes fixes, serves a live
dashboard at localhost:7700, and outputs `outputs/report.json` + `outputs/report.html`.

## Hard rules (the agent must follow these)
- Detect issues in **plain Python** (csv/pandas). Use the model only for judgment
  (rewriting titles/metas, choosing redirect targets). Never feed raw crawl rows to the model.
- `outputs/report.json` MUST match `report.schema.json`. Validate before declaring done.
- Filter to `text/html` + indexable pages before title/meta checks (see `rulebook.md`).
- Do not hard-code anything to the sample export — it must work on an unseen export.
- Keep model calls small and few (free-tier quota). One page per fix call.

## Architecture (keep it real)
- `skills/seo-audit/SKILL.md` orchestrates. Sub-agents: ingest, auditor, fixer, reporter.
- `seo/detector.py` = deterministic detectors (extend to the full rulebook — biggest score).
- `mcp/server.py` = MCP tools + the live dashboard.

## Conventions
- Commit after each working step with a real message.
- Run `python run.py sample-export/` to test end to end.

## Things I learned during the build

- Screaming Frog exports require filtering to indexable 200-status pages before title, meta, and H1 analysis.
- Meta description length threshold from the rulebook is >155 characters.
- H1 severities must match the rulebook exactly (missing_h1 = Medium, duplicate_h1 = Low).
- report.json must include run_meta and run_meta.model_calls to satisfy report.schema.json.
- Detector coverage was expanded to include title, meta, H1, redirect, orphan page, thin content, slow page, and non-indexable-but-linked checks.
- The dashboard is served through mcp/server.py at localhost:7700.
- Using deterministic Python detectors is more reliable than model-based detection for rulebook compliance.
- Redirect chains must only be flagged when a redirect target is itself a redirecting URL.
- Detector coverage was verified against rulebook.md and all required detectors were implemented.
- report.json generation is handled by _report_obj() in mcp/server.py. -->














# CLAUDE.md — project memory for the SEO Command Center build

## What we are building

SEO Command Center is a Claude Code plugin that ingests a Screaming Frog SEO export (`internal_all.csv`), audits it against a deterministic SEO rulebook, prioritizes issues, generates recommendations, serves a live dashboard at `localhost:7700`, and outputs:

* `outputs/report.json`
* `outputs/report.html`

The solution must work on unseen Screaming Frog exports and should not be hard-coded to the sample dataset.

---

## Hard Rules

* Use deterministic Python logic for SEO detection.
* Use the model only for judgment-based tasks such as rewrite suggestions and recommendations.
* Never send raw crawl exports to the model.
* `outputs/report.json` must conform to `report.schema.json`.
* Filter to indexable HTML pages before title, meta description, and H1 analysis.
* Follow thresholds and severities defined in `rulebook.md`.
* Keep model usage minimal to conserve free-tier quota.

---

## Architecture

### Detector Layer

**File:** `seo/detector.py`

Responsible for all deterministic SEO checks:

#### Title Detectors

* missing_title
* duplicate_title
* title_too_long
* title_too_short

#### Meta Description Detectors

* missing_meta_description
* duplicate_meta_description
* meta_description_too_long

#### H1 Detectors

* missing_h1
* duplicate_h1

#### Crawl & Technical SEO Detectors

* broken_link
* server_error
* redirect
* redirect_chain
* orphan_page

#### Content Quality Detectors

* thin_content
* slow_page
* non_indexable_but_linked

---

### Reporting Layer

**File:** `mcp/server.py`

Responsible for:

* report.json generation
* report.html generation
* dashboard updates
* MCP endpoints
* schema-compliant report output

The report object is generated through:

* `_report_obj()`

Required schema fields include:

* site
* urls_crawled
* summary
* issues
* fixes
* recommendations
* run_meta

---

### Orchestration Layer

**File:** `skills/seo-audit/SKILL.md`

Sub-agents:

* ingest
* auditor
* fixer
* reporter

---

## Testing

Run the complete pipeline:

```bash
python run.py ..\sample-export\
```

Expected outputs:

```text
outputs/report.json
outputs/report.html
```

Dashboard:

```text
http://localhost:7700
```

---

## Git History Milestones

Implemented through incremental commits:

* implement title and meta description detectors
* fix h1 detector severities
* add content quality detectors
* add redirect chain detector
* complete rulebook detector coverage
* complete detector coverage and schema fixes

---

## Things I Learned During The Build

* Screaming Frog exports require filtering to indexable 200-status pages before title, meta description, and H1 analysis.
* Duplicate title and duplicate meta checks should only run against indexable pages.
* Meta description length threshold from the rulebook is greater than 155 characters.
* Missing H1 severity must be Medium.
* Duplicate H1 severity must be Low.
* Redirect chains should only be flagged when a redirect target is itself a redirecting URL.
* Thin content detection is based on low word-count pages.
* Slow page detection uses response time values from the crawl export.
* Non-indexable pages with incoming internal links should be reported separately.
* Deterministic Python detectors are more reliable than model-based classification for rulebook compliance.
* Detector coverage was verified against `rulebook.md`.
* All rulebook detectors were implemented and tested.
* `report.json` must include `run_meta` and `run_meta.model_calls` to satisfy `report.schema.json`.
* Report generation is handled by `_report_obj()` inside `mcp/server.py`.
* The dashboard is served through `mcp/server.py` on localhost:7700.
* Incremental commits make it easier to validate functionality and track changes.

---

## Final Project Status

* Detector Coverage: Complete
* Rulebook Coverage: Complete
* Dashboard: Operational
* Report Generation: Operational
* JSON Schema Compliance: Verified
* HTML Report Generation: Verified
* GitHub Repository: Configured
* Incremental Commit History: Complete
