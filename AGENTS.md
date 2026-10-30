# Toons HQ

Ernie Smith's private working repo for Toons USA (Toons Eufaula): where agents and people find how recurring work gets done. Built with ICM (folder structure as agent architecture).

## Where things live

| Folder | What it holds |
|---|---|
| `boat-videos/` | boat walkthrough videos, from the raw phone video to the published Facebook + YouTube posts |
| `_tools/` | checks run from the repo root: `links.py` (every link and input path resolves), `index.py` (rebuilds `_index.md` files) |

## Route by task

| If | Go to |
|---|---|
| editing or publishing a boat video | [boat-videos/AGENTS.md](boat-videos/AGENTS.md) |
| checking the repo after a change | run `python -I _tools/links.py` from the repo root |

## Not built yet

Planned, in order: company map (org, stores, approvals, data sources); portal map (`erniesmith-ui/toons-usa-employee-portal`); partner and vendor records (Excel, Xpress, Boatzon, Nine Marina). No folders exist for them until they are built.

## Rules for every agent here

- Big media never goes in git. Raw and finished videos stay in the Desktop project folder; this repo holds plans, facts, copy and check results.
- Facts come from Ernie or the source files. If a fact is not on file, ask; never fill it in.
- Nothing moves past a step until that step's check passes.
