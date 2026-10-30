# 03_render - render, verify and deliver the video

One job: turn the approved plan into the two final files and prove they match the plan.

## Inputs
- Working (this boat): `../../boats/{slug}/02_edit-plan.md`
- Working (this boat): the raw video, staged from `Toons Video Projects\<Boat>\Raw\`
- Reference (every boat): `../../_shared/edit-recipe.md` (Render, Cards, Audio, Captions, Export, Verify)
- Reference (every boat): `../../_shared/brand.md`
- Reference (every boat): `../../_shared/house-rules.md`
- Reference (every boat): `_Brand\` on Ernie's computer (logo, end card, fonts, denoise model, scripts)

Do NOT load: the publish rules, other boats' plans.

## Process
1. If the record's status isn't `plan-approved`, stop and say so.
2. Follow the plan exactly. If something in it can't be done without breaking a house rule, stop and ask; don't improvise a cut.
3. Render intermediates, cards, audio and captions, then the single final export, as the edit recipe says.
4. Run every Verify step.
5. Deliver both videos and the .srt in chat. Write the .srt, `UPLOAD_SETTINGS.txt` and anything under 30 MB into `<Boat>\Final\`; ask Ernie to save the videos there.

## Outputs
- `03_render-report.md` -> `../../boats/{slug}/` (files, durations, every edit and spike named, what was and wasn't verified)
- `captions.srt` -> `../../boats/{slug}/`
- `check.md` -> `../../boats/{slug}/`
- in `<Boat>\Final\`: `_FINAL.mp4`, `_YouTube_1440p.mp4`, `_captions.srt`, `UPLOAD_SETTINGS.txt`

## Check
The Verify steps write `check.md`: first line `pass` or `fail: <why>`. Pass requires: spikes only at planned edits and joins in the original recording, sharpness within ~5% of the source, every word intact on re-transcription, about -14 LUFS, under 3:00. On pass, set status `rendered`. Say plainly that you haven't watched it in full. Ernie watches it; his OK sets `video-approved`. His notes go into the house rules, and the boat goes back to 02.
