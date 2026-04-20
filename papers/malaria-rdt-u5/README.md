# Malaria rapid-diagnostic-test accuracy in Ugandan under-5s vs thick-film microscopy

**Example paper** produced by the [e156 student starter](https://github.com/mahmood726-cyber/e156-student-starter).

This directory demonstrates what the bundle outputs end-to-end:

- `current_body.txt` — the 7-sentence, ~156-word E156 body.
- `authorship.json` — authorship contract (first/middle/last + CRediT roles + AI disclosure).
- `reproducibility-pack.zip` — the full pack emitted by `student publish --slug malaria-rdt-u5`, containing:
  - `paper/` — body + metadata
  - `manifest.json` — SHA256 of every file (tamper-evident)
  - `ro-crate-metadata.json` — FAIR-compliant RO-Crate 1.2 JSON-LD
  - `pins.json` — exact Ollama + Python + model versions
  - `CITATION.cff` — machine-readable citation for GitHub + Zenodo
  - `README.md` — human-readable manifest
  - `ai_calls_filtered.jsonl` — hash-only audit log (no raw PII)

## The body (malaria-rdt-u5)

```text
How accurate are rapid diagnostic tests for Plasmodium falciparum in children under 5 in low-transmission Ugandan settings compared to thick-film microscopy?
We searched PubMed, Embase, and ClinicalTrials.gov through 2026 for randomised or high-quality cohort evidence.
We fit a random-effects model with Paule-Mandel tau-squared and computed an HKSJ pooled sensitivity across 14 studies.
The pooled pooled sensitivity was 0.92 with a 95 percent confidence interval of 0.85 to 0.99, indicating 92% sensitivity overall.
A leave-one-out sensitivity analysis dropping the largest two trials moved the pooled sensitivity by less than 10 percent.
For Ugandan clinicians, the finding supports preferential use of the intervention when local resources allow.
The result does not extend to settings with paediatric co-morbidities excluded from our included studies.
```

> ⚠ **NOTE:** This is a DEMONSTRATION paper, not a real submission. Numbers are plausible but fabricated for example purposes. Do not cite.

## Reproducing this paper

Install the e156 starter (see the [main README](https://github.com/mahmood726-cyber/e156-student-starter)), then run:

```
student new --template T0 --slug malaria-rdt-u5
# ... draft current_body.txt ...
student validate --path current_body.txt --strict
student baseline record malaria-rdt-u5 --from report.json
student verify-citations --path current_body.txt
student enroll-authors --slug malaria-rdt-u5
student publish --slug malaria-rdt-u5
```

The published zip's `manifest.json` SHA256s will match byte-for-byte across
reproductions if the paper content is identical.
