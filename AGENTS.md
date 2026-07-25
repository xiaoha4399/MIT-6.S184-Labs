# AGENTS.md

## Cursor Cloud specific instructions

This repo is a single self-contained Jupyter notebook lab for MIT 6.S184
(`lab_one.ipynb`), which simulates ODEs/SDEs (Brownian motion, OU process,
Langevin dynamics) with PyTorch and produces plots plus an optional animation.
There is no server, build step, or lint config.

### Environment
- Python deps live in a virtualenv at `.venv` (created by the startup update
  script from `requirements.txt`). Activate with `source .venv/bin/activate` or
  call binaries directly, e.g. `.venv/bin/python`, `.venv/bin/jupyter`.
- PyTorch is installed as the CPU-only build (`torch==...+cpu`) via the extra
  index URL pinned in `requirements.txt`. The notebook auto-selects CPU when
  CUDA is unavailable, so no GPU is required.
- `ffmpeg` (system package) is required only by the optional animation cells
  (`celluloid`); it is preinstalled in the base image.

### Running / testing the notebook
- The notebook's saved kernelspec is named `myenv`, which does not exist here.
  When executing headlessly you MUST override the kernel, e.g.:
  `.venv/bin/jupyter nbconvert --to notebook --execute --output /tmp/out.ipynb --ExecutePreprocessor.kernel_name=python3 lab_one.ipynb`
- To develop interactively: `.venv/bin/jupyter lab` (or `notebook`).
- There are no automated tests or linters. "Running the app" means executing the
  notebook end-to-end; success = all cells run without error and the optional
  cell writes `dynamics_animation.mp4` (a generated file; do not commit it).
