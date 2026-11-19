# subjective_life

Analysis code and paper.

## Layout

    src/subjective_life/   pytask tasks and reusable code
    notebooks/             exploration
    data/raw/              original data, read-only, not in git
    data/processed/        script outputs, not in git
    paper/                 LaTeX paper — a separate repo synced with Overleaf
    paper/figures/         figures written by the pipeline
    paper/tables/          tables written by the pipeline
    literature/            downloaded PDFs, not in git

## Setup

Requires [uv](https://docs.astral.sh/uv/) and git:

    brew install uv git

Clone and build the environment:

    git clone <github-url> && cd subjective_life
    uv sync

`uv sync` recreates the exact environment from `uv.lock` — same Python
version, same package versions.

Clone the paper (needs access to the Overleaf project):

    git clone https://git.overleaf.com/6afeb3d68cc3e1ca212d98db paper

Username at the prompt is `git`; the password is your personal Overleaf
git token (Account Settings -> Git integration). Tokens are per-account,
not shared.

## VS Code

    Cmd+Shift+P -> Python: Select Interpreter -> ./.venv/bin/python

Install the recommended extensions when prompted.

## Running

    uv run pytask

Figures go to `paper/figures/`, tables to `paper/tables/`. The paper
compiles on Overleaf, so a local TeX installation is optional.

## Working on the paper

`paper/` is a separate git repo pointing at Overleaf. Pull before you
start and push when you stop:

    cd paper && git pull
    ...
    git add -A && git commit -m "..." && git push

Avoid Overleaf's track changes while pushing from git — pushes can
displace tracked changes and comments.
