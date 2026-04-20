# Single-dose vs two-dose oral cholera vaccine in East African refugee children

**Example paper** produced by the [e156 student starter](https://github.com/mahmood726-cyber/e156-student-starter).

This directory demonstrates what the bundle outputs end-to-end:

- `current_body.txt` — the 7-sentence, ~156-word E156 body.
- `authorship.json` — authorship contract (first/middle/last + CRediT roles + AI disclosure).
- `reproducibility-pack.zip` — the full pack emitted by `student publish --slug cholera-refugee`, containing:
  - `paper/` — body + metadata
  - `manifest.json` — SHA256 of every file (tamper-evident)
  - `ro-crate-metadata.json` — FAIR-compliant RO-Crate 1.2 JSON-LD
  - `pins.json` — exact Ollama + Python + model versions
  - `CITATION.cff` — machine-readable citation for GitHub + Zenodo
  - `README.md` — human-readable manifest
  - `ai_calls_filtered.jsonl` — hash-only audit log (no raw PII)

## The body (cholera-refugee)

```text
Among refugee children in East African camps, does single-dose oral cholera vaccine vs two-dose regimen change symptomatic cholera incidence at 12 months?
We searched PubMed, Embase, and ClinicalTrials.gov through 2026 for randomised or high-quality cohort evidence.
We fit a random-effects model with Paule-Mandel tau-squared and computed an HKSJ incidence rate ratio across 5 studies.
The pooled incidence rate ratio was 0.74 with a 95 percent confidence interval of 0.59 to 0.93, indicating 26% fewer cases.
A leave-one-out sensitivity analysis dropping the largest two trials moved the incidence rate ratio by less than 10 percent.
For Ugandan clinicians, the finding supports preferential use of the intervention when local resources allow.
The result does not extend to settings with paediatric co-morbidities excluded from our included studies.
```

> ⚠ **NOTE:** This is a DEMONSTRATION paper, not a real submission. Numbers are plausible but fabricated for example purposes. Do not cite.

## Reproducing this paper

Install the e156 starter (see the [main README](https://github.com/mahmood726-cyber/e156-student-starter)), then run:

```
student new --template T0 --slug cholera-refugee
# ... draft current_body.txt ...
student validate --path current_body.txt --strict
student baseline record cholera-refugee --from report.json
student verify-citations --path current_body.txt
student enroll-authors --slug cholera-refugee
student publish --slug cholera-refugee
```

The published zip's `manifest.json` SHA256s will match byte-for-byte across
reproductions if the paper content is identical.
