# Entwined Path Degree-Theoretic Reasoning — ULDR

A public dataset-interpretation toolkit for lattice walks, replay streams, and geometric visualizations inspired by **Wen's Book of Changes**.

This repository exposes enough tooling to inspect and render existing datasets without publishing the private state-generation engine or the exact darkTetra succession.

## What is included

- Readers for direction-string, coordinate `.walk`, CSV, JSON, and NDJSON datasets
- Pareto-layer ranking by resonance and numerical response
- King Wen sequence labels for 64-state replay records
- Conversion to a neutral geometry/event schema
- Blender import script for paths and event markers
- Small sanitized example datasets

## What is intentionally not included

- The full state engine
- Exact darkTetra succession or transition rules
- Private candidacy/ejection heuristics
- Proprietary generation constants and reconstruction logic
- Personal paths, executables, build artifacts, or raw research dumps

The public boundary is:

```text
existing dataset -> normalized event stream -> metrics / ranking -> Blender geometry
```

not:

```text
private state engine -> proprietary succession -> generated walk
```

## Quick start

Requires Python 3.10+ and no third-party packages.

```bash
python python/wen_changes.py inspect datasets/sample_replay.ndjson
python python/wen_changes.py pareto datasets/sample_replay.ndjson -o exports/sample_pareto.ndjson
python python/wen_changes.py normalize datasets/sample_walk.walk -o exports/sample_geometry.ndjson
```

To create a Blender-ready bundle:

```bash
python python/wen_changes.py blender-bundle \
  datasets/sample_walk.walk \
  --events datasets/sample_replay.ndjson \
  -o exports/blender_bundle.json
```

Then open Blender's **Scripting** workspace, load `blender/import_wen_dataset.py`, set `DATASET_PATH`, and run the script.

## Dataset formats

See [`docs/DATASETS.md`](docs/DATASETS.md) and [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md).

## Terminology

The historical inspiration is described here as **Wen's Book of Changes** or the **King Wen sequence**. This project is an experimental graph-theoretic and geometric interpretation, not an authoritative edition, translation, or oracle.

## Author

**Tim Megna** is a Data Science graduate student at Tufts University. His graduate work has included faculty-guided exploration of dimensionality-reduction methods such as UMAP alongside continuing research in lattice walks, computational geometry, graph-theoretic analysis, and simulation. EPDT and Changes-Sieve reflect his original computational and conceptual influence.

Tufts University and its faculty are not represented as endorsing this independent research repository.

## Repository status

Research software. Schemas may evolve, but the public tools are deliberately kept separate from the private generative engine.
