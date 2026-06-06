<!-- # PROMPTS.md — my key prompts log

Keep the handful of prompts that actually moved the build. Not every message — the ones that
mattered: the system/sub-agent prompts, the ones you iterated on, the "this finally worked"
moment. This shows how you direct an AI, which is graded (challenge brief section 08).

Format per entry:
- **Prompt** (paste it)
- **For:** what you were trying to do
- **Revised?** did you have to change it, and why

---

## Example (replace with your own)

- **Prompt:** "Extend seo/detector.py to detect redirect chains: build a map of {Address ->
  Redirect URL} for all 3xx rows, then a chain exists when a Redirect URL is itself a key in
  that map. Add a redirect_chain issue (High). Run python seo/detector.py and show counts."
- **For:** adding the redirect-chain detector
- **Revised?** Yes — first version flagged single redirects as chains; added the "target is
  also a redirecting URL" condition.

---

## My prompts

### Prompt 1

* **Prompt:** "Read seo/detector.py. List every detector that already exists and every detector that is still missing compared to the SEO rulebook. Do not modify any files."
* **For:** Understanding current detector coverage before making changes.
* **Revised?** No. It correctly identified the missing detectors.

### Prompt 2

* **Prompt:** "Implement ONLY these detectors in seo/detector.py: title_too_short, missing_meta_description, duplicate_meta_description, and meta_description_too_long. Follow the existing detector pattern. Do not modify unrelated files."
* **For:** Expanding rulebook coverage for title and meta description issues.
* **Revised?** Yes. The meta description length threshold was later adjusted after verifying the rulebook.

### Prompt 3

* **Prompt:** "Read ..\rulebook.md. Verify whether the current severities for missing_h1 and duplicate_h1 match the rulebook. Do not modify code. Only report mismatches."
* **For:** Ensuring detector severities matched the official rulebook.
* **Revised?** No. It correctly identified severity mismatches.

### Prompt 4

* **Prompt:** "Implement ONLY these detectors in seo/detector.py: thin_content, non_indexable_but_linked, and slow_page. Use the exact thresholds and severities from the rulebook."
* **For:** Completing content-quality detector coverage.
* **Revised?** No. The implementation matched the rulebook requirements.

### Prompt 5

* **Prompt:** "Read rulebook.md and seo/detector.py. Create a table showing every detector required by the rulebook, whether it is implemented, severity, and code location."
* **For:** Final verification of detector coverage.
* **Revised?** No. This confirmed full rulebook implementation.

### Prompt 6

* **Prompt:** "Read report.schema.json and outputs/report.json. Verify schema compliance and identify any missing required fields."
* **For:** Ensuring report.json matched the required schema.
* **Revised?** Yes. After identifying missing run_meta information, the report generation logic was updated and revalidated.
 -->







# PROMPTS.md — my key prompts log

## Prompt 1

**Prompt:**
"Read seo/detector.py. List every detector that already exists and every detector that is still missing compared to the SEO rulebook. Do not modify any files."

**For:**
Understanding current detector coverage before making changes.

**Revised?**
No. It correctly identified the missing detectors.

---

## Prompt 2

**Prompt:**
"Implement ONLY these detectors in seo/detector.py: title_too_short, missing_meta_description, duplicate_meta_description, and meta_description_too_long. Follow the existing detector pattern. Do not modify unrelated files."

**For:**
Expanding rulebook coverage for title and meta description issues.

**Revised?**
Yes. The meta description length threshold was later adjusted after verifying the rulebook.

---

## Prompt 3

**Prompt:**
"Read ..\rulebook.md. Verify whether the current severities for missing_h1 and duplicate_h1 match the rulebook. Do not modify code. Only report mismatches."

**For:**
Ensuring detector severities matched the official rulebook.

**Revised?**
No. It correctly identified severity mismatches.

---

## Prompt 4

**Prompt:**
"Implement ONLY these detectors in seo/detector.py: thin_content, non_indexable_but_linked, and slow_page. Use the exact thresholds and severities from the rulebook."

**For:**
Completing content-quality detector coverage.

**Revised?**
No. The implementation matched the rulebook requirements.

---

## Prompt 5

**Prompt:**
"Implement ONLY redirect_chain detection. Follow the existing detector pattern and the rulebook definition of a redirect chain."

**For:**
Completing technical SEO coverage.

**Revised?**
Yes. Redirect chains were only flagged when the redirect target was itself another redirect.

---

## Prompt 6

**Prompt:**
"Read rulebook.md and seo/detector.py. Create a table showing every detector required by the rulebook, whether it is implemented, severity, and code location."

**For:**
Final verification of detector coverage.

**Revised?**
No. This confirmed full rulebook implementation.

---

## Prompt 7

**Prompt:**
"Read report.schema.json and outputs/report.json. Verify schema compliance and identify any missing required fields."

**For:**
Ensuring report.json matched the required schema.

**Revised?**
Yes. This identified the missing run_meta section and led to updates in report generation.

---

## Prompt 8

**Prompt:**
"Read report.schema.json, outputs/report.json, run.py, and mcp/server.py. Determine where report.json is generated and update the report generation logic so that the schema is satisfied."

**For:**
Fixing report schema compliance.

**Revised?**
No. This resulted in adding run_meta, model_calls, and duration information to the generated report.

---

## Prompt 9

**Prompt:**
"Compare rulebook.md against the current detector implementation and report any remaining gaps without modifying code."

**For:**
Final readiness check before submission.

**Revised?**
No. This confirmed that all required detectors had been implemented and validated.


