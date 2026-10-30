# Boat videos - the pipeline

The flow in one line: check the footage and facts, plan the edit, render and verify it, then write the posts.

| Step | Job | Check |
|---|---|---|
| [01_intake](stages/01_intake/CONTEXT.md) | review footage, list facts and questions | Ernie confirms the facts |
| [02_edit-plan](stages/02_edit-plan/CONTEXT.md) | start/end points, edits, cards, fixes | Ernie approves the plan |
| [03_render](stages/03_render/CONTEXT.md) | render, audio, captions, export, verify | verification writes `check.md` |
| [04_publish](stages/04_publish/CONTEXT.md) | Facebook post, YouTube package, thumbnail | Ernie approves the copy |

Factory (every boat): [`_shared/`](_shared/) - [brand](_shared/brand.md), [house rules](_shared/house-rules.md), [edit recipe](_shared/edit-recipe.md), [publish rules](_shared/publish-rules.md), [locations](_shared/locations.md).
Product (each boat): `boats/<slug>/`, plus the video files in the Desktop project folder.

## Status

Each boat's `CONTEXT.md` carries one `status:` line. The lifecycle:

`intake` -> `intake-confirmed` -> `plan-approved` -> `rendered` -> `video-approved` -> `package-approved` -> `published`

Ernie's go-ahead moves a boat past `intake`, `rendered` (he watched it) and the package. If he sends a video back, his feedback goes into the house rules and the boat returns to `02_edit-plan`.

## Two deliberate breaks from the ICM defaults

- **Outputs live in the boat's folder, not in `stages/*/output/`.** Several boats are often in progress at once, so each step writes `boats/<slug>/NN_*.md`, and the stage folders hold only contracts.
- **Video files live outside the repo.** Raw and Final videos are hundreds of MB and stay in the Desktop project folder ([locations](_shared/locations.md)). The repo keeps the small files: facts, plans, captions, copy, check results.

## Not in this repo yet

The render scripts (`final_pipeline.sh`, card, caption and check scripts) are in `_Brand\toons_video_scripts.tgz` on the Desktop. Copy them into `_tools/video/` the next time the Desktop folder is connected.
