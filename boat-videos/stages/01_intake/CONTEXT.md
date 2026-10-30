# 01_intake - review the footage, list the facts

One job: understand what's in the raw video and what Ernie still needs to confirm, before any edit is planned.

## Inputs
- Working (this boat): the raw video in `Toons Video Projects\<Boat>\Raw\` on Ernie's computer, staged through the device link
- Working (this boat): `../../boats/{slug}/CONTEXT.md` (the record, copied from the template)
- Reference (every boat): `../../_shared/brand.md`
- Reference (every boat): `../../_shared/edit-recipe.md` (Review section)
- Reference (every boat): `../../_shared/locations.md`

Do NOT load: other boats' records, the publish rules, earlier videos' outputs.

## Process
1. If the raw video or the record is missing, stop and say which.
2. Run the Review steps in the edit recipe: probe, transcribe with word times, contact sheet, loudness, shot-change scan.
3. Write the facts list: every fact the salesperson says (with its timestamp), every fact Ernie gave, and its claim status (verified / manufacturer claim / restricted / unknown).
4. Write the issues list: misspoken facts or URLs, asides, dead air, sign-off position, clipping, breaths, noise.
5. Write the questions only Ernie can answer (last names, consignment vs pre-owned, factory vs dealer options, condition).
6. Save the word-timed transcript as `transcript.txt` in the boat folder.

## Outputs
- `01_intake.md` -> `../../boats/{slug}/`
- `transcript.txt` -> `../../boats/{slug}/`
- the record's table filled in (raw file, salesperson); `status: intake`

## Check
Ernie reads the facts and answers the questions. Write his answers into `01_intake.md`, then set the record's status to `intake-confirmed`.
