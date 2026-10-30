# 02_edit-plan - plan the edit before rendering anything

One job: write down exactly how the video will start, end and look, so Ernie can correct it before hours of rendering.

## Inputs
- Working (this boat): `../../boats/{slug}/01_intake.md`
- Working (this boat): `../../boats/{slug}/transcript.txt`
- Reference (every boat): `../../_shared/house-rules.md`
- Reference (every boat): `../../_shared/edit-recipe.md` (Plan and Cards sections)
- Reference (every boat): `../../_shared/brand.md`
- Example (optional): `../../boats/2024-hurricane-sundeck-191/02_edit-plan.md` (the approved plan)

Do NOT load: the publish rules, other boats' transcripts.

## Process
1. If the record's status isn't `intake-confirmed`, stop and say so.
2. Choose the start point (first clean sentence) and end point (the salesperson's sign-off), with raw timestamps.
3. List every edit. Each must sit at a shot change that already exists in the footage; name it. No cuts inside a continuous shot.
4. List asides kept, and any mistake and how it's fixed without a cut (card, end card) or "ask Ernie".
5. Build the card table: time, card, text, position. One card at a time, at least 0.4 s apart, on the line naming the feature. No price card.
6. Write the end card text and the expected final length (must be under 3:00).

## Outputs
- `02_edit-plan.md` -> `../../boats/{slug}/`

## Check
Ernie reads the plan and approves or corrects it. Record his answer in the plan, then set the record's status to `plan-approved`.
