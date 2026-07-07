# connectpt_dataset_prep

Builds and audits real-morphology ConnectPT training samples.

## Scheme

```mermaid
flowchart LR
    A[Inputs] --> B[Run: cli.py]
    B --> C[Checked outputs]
    C --> D[Paper / thesis use]
```

## Main Result

![Main result](docs/readme_result.svg)

## Run

Entrypoint: `cli.py`

Human:

```bash
PYTHONPATH=$PWD python -m connectpt_dataset_prep.cli status
```

Agent:

Run status/analyze after rebuild and inspect manifest plus analysis PNGs.

## Publication

No standalone publication yet.

## Next Steps / Heuristics

Heuristic: skip cities without valid gravity OD instead of silently falling back.
