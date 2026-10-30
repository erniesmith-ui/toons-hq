# 04_publish - write the posts and the YouTube package

One job: write the Facebook post, YouTube package and thumbnail for an approved video.

## Inputs
- Working (this boat): `../../boats/{slug}/01_intake.md` (the confirmed facts)
- Working (this boat): `../../boats/{slug}/03_render-report.md` (file names, duration, edit times for chapters)
- Reference (every boat): `../../_shared/publish-rules.md`
- Reference (every boat): `../../_shared/brand.md`
- Reference (every boat): `Desktop\Toons Listings\Toons Listing Formula.txt` on Ernie's computer
- Example (optional): `../../boats/2024-hurricane-sundeck-191/04_publish.md`

Do NOT load: the edit recipe, the transcript (facts come from 01), other boats' copy.

## Process
1. If the record's status isn't `video-approved`, stop and say so.
2. Claim-check every fact against `01_intake.md`; anything not confirmed stays out and goes on the "To confirm" list.
3. Write the Facebook post and Reel caption, then the YouTube package doc, as the publish rules say. No price anywhere in the text.
4. Make the vertical thumbnail.
5. Write the thumbnail and `Facebook_post.txt` into `<Boat>\Final\`.

## Outputs
- `04_publish.md` -> `../../boats/{slug}/` (the copy, the package doc link, the To confirm list)
- package doc (a Claude doc), thumbnail in `<Boat>\Final\`

## Check
Ernie reads the copy and approves or edits it (the Formula requires approval before publishing). Then set status `package-approved`. Once it's live, add the YouTube and Facebook links to the record and set `published`.
