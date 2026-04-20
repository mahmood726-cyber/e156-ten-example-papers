# Nurse-led task-shifting vs physician-only hypertension care in rural Uganda

**Example paper** produced by the [e156 student starter](https://github.com/mahmood726-cyber/e156-student-starter).

This directory demonstrates what the bundle outputs end-to-end:

- `current_body.txt` — the 7-sentence, ~156-word E156 body.
- `authorship.json` — authorship contract (first/middle/last + CRediT roles + AI disclosure).
- `reproducibility-pack.zip` — the full pack emitted by `student publish --slug htn-rural-uga`, containing:
  - `paper/` — body + metadata
  - `manifest.json` — SHA256 of every file (tamper-evident)
  - `ro-crate-metadata.json` — FAIR-compliant RO-Crate 1.2 JSON-LD
  - `pins.json` — exact Ollama + Python + model versions
  - `CITATION.cff` — machine-readable citation for GitHub + Zenodo
  - `README.md` — human-readable manifest
  - `ai_calls_filtered.jsonl` — hash-only audit log (no raw PII)

## The body (htn-rural-uga)

```text
Among adults with uncontrolled hypertension attending rural Ugandan clinics, does nurse-led task-shifting vs physician-only care change systolic BP at 6 months?
We searched PubMed, Embase, and ClinicalTrials.gov through 2026 for randomised or high-quality cohort evidence.
We fit a random-effects model with Paule-Mandel tau-squared and computed an HKSJ mean difference across 10 studies.
The pooled mean difference was -4.3 with a 95 percent confidence interval of -6.1 to -2.5, indicating systolic BP fell by about 4 mmHg.
A leave-one-out sensitivity analysis dropping the largest two trials moved the mean difference by less than 10 percent.
For Ugandan clinicians, the finding supports preferential use of the intervention when local resources allow.
The result does not extend to settings with paediatric co-morbidities excluded from our included studies.
```

> ⚠ **NOTE:** This is a DEMONSTRATION paper, not a real submission. Numbers are plausible but fabricated for example purposes. Do not cite.

## Reproducing this paper

Install the e156 starter (see the [main README](https://github.com/mahmood726-cyber/e156-student-starter)), then run:

```
student new --template T0 --slug htn-rural-uga
# ... draft current_body.txt ...
student validate --path current_body.txt --strict
student baseline record htn-rural-uga --from report.json
student verify-citations --path current_body.txt
student enroll-authors --slug htn-rural-uga
student publish --slug htn-rural-uga
```

The published zip's `manifest.json` SHA256s will match byte-for-byte across
reproductions if the paper content is identical.
