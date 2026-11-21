# SigLIP2 LoRA Image Ordering

An unofficial participant solution for the
[SNU AI Challenge 2026](https://snuaichallenge.github.io/). The task is to
restore the temporal order of four shuffled image frames from a natural-language
storyline.

This repository contains only the author's training and inference notebook.
Competition data, test answers, submissions, fine-tuned weights, and pretrained
model files are deliberately excluded.

## Method

- Google SigLIP2 Base Patch16 224 backbone
- LoRA fine-tuning
- 24-way permutation classification
- Auxiliary pairwise ordering loss
- Single model; no ensemble
- No external API during training or inference

## Files

- `siglip2_ordering_step_by_step.ipynb`: numbered training and inference notebook
- `requirements.txt`: pinned Python dependencies
- `THIRD_PARTY_NOTICES.md`: model and competition attribution

## Data layout

Obtain the competition data through the official channel and keep it outside
version control. Point `SNU_DATA_DIR` at the data directory, or place the files
under the local `data/` directory:

```text
data/
├── train.csv
├── test.csv
├── sample_submission.csv
├── train/<Id>/<images>
└── test/<Id>/<images>
```

Example:

```bash
export SNU_DATA_DIR=/absolute/path/to/competition-data
jupyter lab siglip2_ordering_step_by_step.ipynb
```

The notebook can download `google/siglip2-base-patch16-224` at the pinned
revision. The downloaded files remain under `pretrained/` and are ignored by
Git.

## Reproducibility and scope

- Python dependencies are pinned in `requirements.txt`.
- Input paths are relative by default and can be overridden with
  `SNU_DATA_DIR`.
- The repository does not include competition data or model weights.
- This is an independent participant project and is not an official Seoul
  National University repository or endorsement.

Review the current [challenge rules](https://snuaichallenge.github.io/rules/)
before reproducing or extending the experiment.

## License

The original code and notebook in this repository are licensed under the MIT
License. Competition data and third-party models retain their own terms; the
MIT License does not grant rights to those materials.
