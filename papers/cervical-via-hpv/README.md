# VIA vs HPV DNA primary screening for cervical cancer in unvaccinated women 30-50

**Example paper** produced by the [e156 student starter](https://github.com/mahmood726-cyber/e156-student-starter).

This directory demonstrates what the bundle outputs end-to-end:

- `current_body.txt` — the 7-sentence, ~156-word E156 body.
- `authorship.json` — authorship contract (first/middle/last + CRediT roles + AI disclosure).
- `reproducibility-pack.zip` — the full pack emitted by `student publish --slug cervical-via-hpv`, containing:
  - `paper/` — body + metadata
  - `manifest.json` — SHA256 of every file (tamper-evident)
  - `ro-crate-metadata.json` — FAIR-compliant RO-Crate 1.2 JSON-LD
  - `pins.json` — exact Ollama + Python + model versions
  - `CITATION.cff` — machine-readable citation for GitHub + Zenodo
  - `README.md` — human-readable manifest
  - `ai_calls_filtered.jsonl` — hash-only audit log (no raw PII)

## The body (cervical-via-hpv)

```text
For cervical-cancer screening in unvaccinated women 30-50, does visual inspection with acetic acid vs HPV DNA testing change CIN-2+ detection rate at first-round screening?
We searched PubMed, Embase, and ClinicalTrials.gov through 2026 for randomised or high-quality cohort evidence.
We fit a random-effects model with Paule-Mandel tau-squared and computed an HKSJ detection rate ratio across 12 studies.
The pooled detection rate ratio was 1.35 with a 95 percent confidence interval of 1.12 to 1.63, indicating 35% more CIN-2+ detected.
A leave-one-out sensitivity analysis dropping the largest two trials moved the detection rate ratio by less than 10 percent.
For Ugandan clinicians, the finding supports preferential use of the intervention when local resources allow.
The result does not extend to settings with paediatric co-morbidities excluded from our included studies.
```

> ⚠ **NOTE:** This is a DEMONSTRATION paper, not a real submission. Numbers are plausible but fabricated for example purposes. Do not cite.

## Reproducing this paper

Install the e156 starter (see the [main README](https://github.com/mahmood726-cyber/e156-student-starter)), then run:

```
student new --template T0 --slug cervical-via-hpv
# ... draft current_body.txt ...
student validate --path current_body.txt --strict
student baseline record cervical-via-hpv --from report.json
student verify-citations --path current_body.txt
student enroll-authors --slug cervical-via-hpv
student publish --slug cervical-via-hpv
```

The published zip's `manifest.json` SHA256s will match byte-for-byte across
reproductions if the paper content is identical.
