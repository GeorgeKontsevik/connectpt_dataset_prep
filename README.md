# connectpt_dataset_prep

---

[![OSA-improved](https://img.shields.io/badge/improved%20by-OSA-yellow)](https://github.com/aimclub/OSA)

---

## Table of Contents

- [Overview](#overview)
- [Core Features](#core-features)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Architecture](#architecture)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Citation](#citation)

---

## Overview

`connectpt_dataset_prep` provides dataset-preparation helpers for ConnectPT experiments, with a focus on assembling and checking real-morph training data for researchers and developers working on dataset generation and evaluation. It is a small Python 3.11+ utility centered on a command-line interface that can build, analyze, and compare dataset outputs, and it also includes support for collecting top-up inputs across cities. If you are new to the project, start with the Getting Started section for runnable examples and the expected workflow.

---

## Core Features

- Builds a ConnectPT real-morph training dataset from a selected set of candidate cities, giving researchers a repeatable way to assemble experiment inputs.
- Validates city inputs by checking required spatial layers and graph availability, helping catch incomplete or unusable datasets before training.
- Supports optional dataset processing during build, making it easier to produce the prepared artifacts expected by downstream ConnectPT workflows.
- Analyzes the generated dataset and compares real versus synthetic demand, providing quick feedback on dataset quality and experiment alignment.
- Collects top-up data for additional cities through an external spatial pipeline, enabling expansion of the dataset when more coverage is needed.

---

## Installation

**Prerequisites:** requires Python >=3.11

Install connectpt_dataset_prep using one of the following methods:

**Build from source:**

1. Clone the connectpt_dataset_prep repository:
```sh
git clone https://github.com/GeorgeKontsevik/connectpt_dataset_prep
```

2. Navigate to the project directory:
```sh
cd connectpt_dataset_prep
```

3. Install the project dependencies:

```sh
pip install -r requirements.txt
```

---

## Getting Started

Prerequisites:
- Python 3.11 or newer.
- A local checkout of this repository.
- Use the installed CLI entry point `connectpt-dataset-prep` or run the module from the package source.

1. Install the project in your environment from the repository root.
```bash
   uv pip install -e .
```

2. Verify the CLI is available.
```bash
   connectpt-dataset-prep --help
```

3. Run the default dataset build.
```bash
   connectpt-dataset-prep build-current
```

4. If you want the full local workflow, run the build, analysis, and comparison steps through the CLI.
```bash
   connectpt-dataset-prep run-all
```

5. Review the generated dataset under the default path defined in `connectpt_dataset_prep.city_sets.DEFAULT_DATASET_DIR`, or pass a different dataset directory if your workflow requires it.

---

## Architecture

The project is a small, CLI-driven utility for preparing ConnectPT datasets and running the related evaluation steps. It centers on a few workflows: building a real morph dataset, analyzing the generated dataset, comparing real and synthetic demand, and collecting top-up city inputs.

- The main CLI assembles command-line arguments and orchestrates external scripts for dataset build, analysis, and comparison.
- A combined `run-all` flow runs build, analysis, and comparison in sequence for a single dataset directory.
- The CLI also supports a top-up collection workflow that iterates over a configured set of city places, prepares per-city input and output directories, and invokes the joint collection pipeline in collect-only mode.
- Shared city selections and default dataset locations are defined centrally so the workflows operate on consistent inputs.
- Before running downstream steps, the CLI validates candidate city data by checking for required spatial layers and a usable graph, and it reports whether a city is suitable for training.
- The package is distributed as a Python entrypoint and is designed to run with the repository as the working root, with environment setup handled by the CLI when it launches subprocesses.

---

## Documentation

A detailed connectpt_dataset_prep description is available [here](https://github.com/GeorgeKontsevik/connectpt_dataset_prep/tree/main/docs).

---

## Contributing

- **[Report Issues](https://github.com/GeorgeKontsevik/connectpt_dataset_prep/issues)**: Submit bugs found or log feature requests for the project.

- **[Submit Pull Requests](https://github.com/GeorgeKontsevik/connectpt_dataset_prep/tree/main/CONTRIBUTING.md)**: To learn more about making a contribution to connectpt_dataset_prep.

---

## Citation

If you use this software, please cite it as below.

### APA format:

    GeorgeKontsevik (2026). connectpt_dataset_prep repository [Computer software]. https://github.com/GeorgeKontsevik/connectpt_dataset_prep

### BibTeX format:

    @misc{connectpt_dataset_prep,

        author = {GeorgeKontsevik},

        title = {connectpt_dataset_prep repository},

        year = {2026},

        publisher = {github.com},

        journal = {github.com repository},

        howpublished = {\url{https://github.com/GeorgeKontsevik/connectpt_dataset_prep}},

        url = {https://github.com/GeorgeKontsevik/connectpt_dataset_prep}

    }

---