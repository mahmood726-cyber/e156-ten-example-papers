# e156 ten example papers

Ten showcase E156 micro-papers produced end-to-end with the
[e156 student starter](https://github.com/mahmood726-cyber/e156-student-starter).

Each paper is a 7-sentence, ≤156-word body answering a clinically-relevant
question that a first-time Uganda medical student might tackle. The bodies
in this repository are **demonstrations**, not real findings — the numbers
are plausible but fabricated, and nothing here should be cited. The
reproducibility packs are real artifacts emitted by `student publish` and
they pass `student sentinel`, `student validate --strict`, and the
`manifest.json` SHA256 tamper-evident check.

## Why this exists

The main starter repo can tell you *what* the bundle does. This repo
shows *what the bundle actually ships* — byte-for-byte, the same files a
real student would hand to their supervisor.

## What each paper directory contains

| File | What it is |
|---|---|
| `current_body.txt` | the 7-sentence body |
| `authorship.json` | first/middle/last authors + CRediT roles + AI disclosure |
| `reproducibility-pack.zip` | the zip emitted by `student publish` |
| `README.md` | a human-readable summary + reproduction recipe |

The zip inside each paper directory was produced by running the real
`student publish` pipeline against the real extracted v0.2.2 bundle with
`%LOCALAPPDATA%` pointed at a fresh tmp dir — no touch to dev-machine
state. Each pack contains: `paper/`, `manifest.json`, `ro-crate-metadata.json`
(FAIR RO-Crate 1.2 JSON-LD), `pins.json`, `CITATION.cff`,
`ai_calls_filtered.jsonl` (hash-only audit), and — if populated — a
`baseline.json` + `bypass.log`.

## The ten papers

| Slug | Topic |
|---|---|
| `sickle-hu-ssa`       | Hydroxyurea for sickle-cell pain crises in Sub-Saharan African children |
| `malaria-rdt-u5`      | Malaria RDT accuracy in Ugandan under-5s vs microscopy |
| `art-pmtct-uga`       | Integrase-inhibitor vs efavirenz-based ART in rural Ugandan PMTCT |
| `cs-ssi-lmic`         | Pre-incision vs post-cord-clamp cefazolin for caesarean SSI |
| `tb-hiv-ipt`          | 6-month vs 36-month IPT in TB/HIV co-infected adults |
| `cholera-refugee`     | Single-dose vs two-dose oral cholera vaccine in East African refugees |
| `neonatal-sepsis-abx` | Ampicillin-gentamicin vs ampicillin-cefotaxime empirical therapy |
| `htn-rural-uga`       | Nurse-led task-shifting vs physician-only hypertension care |
| `cervical-via-hpv`    | VIA vs HPV DNA primary cervical-cancer screening |
| `tb-xpert-smear`      | Xpert MTB/RIF vs direct sputum microscopy for time-to-TB-treatment |

## Reproducing any paper from scratch

```bash
# Install the starter (see https://github.com/mahmood726-cyber/e156-student-starter)
# Then, per paper:
student new --template T0 --slug <slug>
# ... fill in current_body.txt ...
student validate --path current_body.txt --strict
student baseline record <slug> --value pooled_estimate=X --value ci_lower=Y --value ci_upper=Z --value k=N
student verify-citations --path current_body.txt
student enroll-authors --slug <slug>
student publish --slug <slug>
```

If you want to verify a pack from this repo is tamper-free, extract the
zip and run:

```bash
python -c "import hashlib, json; m = json.load(open('manifest.json')); \
  print('OK' if all(hashlib.sha256(open(f,'rb').read()).hexdigest() == h \
    for f, h in m['files'].items() if f != 'manifest.json') else 'FAIL')"
```

## The full audit trail of how these were built

Produced by the scripted driver in the main starter's session history —
see commits `c4b7fb6` (publish) through `408ea78` (v0.2.3) in
[e156-student-starter](https://github.com/mahmood726-cyber/e156-student-starter).

The driver script that produced these ten in 22.6 seconds wall-clock:

1. Write 10 plausible bodies (pre-baked numbers per topic).
2. For each slug:
   - `student new --template T0 --slug <slug>`
   - Copy body into `workbook/<slug>/current_body.txt`
   - `student validate --strict`
   - `student baseline record` + `check`
   - `student drift snapshot`
   - `student sentinel --repo <slug>`
   - `student publish --slug <slug>` → zip here in `reproducibility-pack.zip`

10/10 passed every step. 22.6 s wall-clock total for the infrastructure path
(the AI-prose rewrite path takes ~170 s per paper with gemma2:2b, not
scripted here).

## License

CC0 for the demonstration content in this repo. The e156 starter itself
is MIT. The reproducibility packs contain quoted source-paper metadata
under the license terms of those papers (mostly CC-BY for the guideline
and rule sources cited in the packs).
