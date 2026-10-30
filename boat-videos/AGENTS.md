# Boat videos

Turns a salesperson's raw walkthrough phone video into a finished, on-brand Toons video plus its Facebook post and YouTube package. One boat = one record folder in `boats/`.

## Where things live

| Folder | What it holds |
|---|---|
| `stages/` | the four steps, in order; each `CONTEXT.md` is that step's contract |
| `boats/` | one folder per boat: its status line and every step's output ([index](boats/_index.md)) |
| `_shared/` | the factory: brand facts, house rules, edit recipe, publish rules, file locations |
| `_templates/boat/` | copy this folder to start a new boat |

## Route by what just happened

| If | Go to | Stop at |
|---|---|---|
| a new raw video arrived | copy `_templates/boat/` to `boats/<year>-<make>-<model>/`, then [01_intake](stages/01_intake/CONTEXT.md) | Ernie confirms the facts |
| the boat's status is `intake-confirmed` | [02_edit-plan](stages/02_edit-plan/CONTEXT.md) | Ernie approves the plan |
| status is `plan-approved` | [03_render](stages/03_render/CONTEXT.md) | `check.md` says pass |
| status is `video-approved` | [04_publish](stages/04_publish/CONTEXT.md) | Ernie approves the copy |
| asked for status | [boats/_index.md](boats/_index.md) (rebuild first: `python -I _tools/index.py boat-videos/boats`) | report what it says |
| Ernie gives new feedback | add it to [house rules](_shared/house-rules.md) | the rule is written down |

## The one rule

Play the footage the way it was shot, and nothing moves to the next step until the last one's check passes.
