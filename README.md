# candel-trgb

TRGB-calibrated H0 forward model for CANDEL. A probe package for
[CANDEL](https://github.com/candel-cosmo/CANDEL), part of the
[candel-cosmo](https://github.com/candel-cosmo) organisation. It imports the
core `candel` library; the core never imports it. See the
[CANDEL README](https://github.com/candel-cosmo/CANDEL#how-the-repositories-fit-together)
for how the repositories fit together.

## What it provides

Two-rung distance ladder from EDD Tip of the Red Giant Branch distances and
geometric anchors (`model.which_run = "EDD_TRGB"`), with mocks (`mock.py`,
`scripts/mock_TRGB.py`) and posterior predictive checks (`ppc.py`,
`scripts/ppc_TRGB.py`).

## Install

Clone this repository next to the CANDEL core and install both, core first:

```bash
git clone https://github.com/candel-cosmo/CANDEL.git
git clone https://github.com/candel-cosmo/candel-trgb.git
cd CANDEL
python -m venv venv_candel && source venv_candel/bin/activate
pip install -e .
pip install --no-deps -e ../candel-trgb
```

Data, results and the machine-local `local_config.toml` live in the CANDEL
checkout. Python code finds it through the installed `candel`
(`candel.util.CANDEL_ROOT`); shell scripts use `$CANDEL_ROOT`, defaulting to
`../CANDEL`.

## Layout

- `candel_trgb/` — the package
- `configs/` — run configurations
- `scripts/` — preprocessing, mocks and submission helpers
- `papers/` — scripts and notebooks behind each paper
- `tests/` — tests (`pytest`)

## Papers

- `papers/TRGBH0/` — $H_0$ from TRGB and geometric anchors alone, [arXiv:2609.29996](https://arxiv.org/abs/2609.29996)

## Run

```bash
python ../CANDEL/scripts/runs/main.py --config configs/config_EDD_TRGB.toml
```

Batch grids are defined in `candel_trgb/specs.py` and built with the core's
`scripts/runs/generate_tasks.py`.

## License

MIT; see `LICENSE`.
