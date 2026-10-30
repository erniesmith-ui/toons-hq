# Where the files are, and tool limits

## On Ernie's computer (reached through the Claude desktop app's device link)

- Project folder: `C:\Users\Grove Marine\Desktop\Toons Video Projects`
  - one folder per boat with `Raw\` and `Final\`, plus `README.md`
  - `_Brand\`: `Toons_logo_watermark.png` (real logo), `Toons_end_card_logo_Kevin.png` (current end card style), `Toons_watermark_white_overlay.png`, `Anton.ttf`, `rnnoise_cb.rnnn`, `toons_video_scripts.tgz` (`final_pipeline.sh` + card, caption and check scripts), `YouTube_playlist_descriptions.txt`
- `Desktop\toonsvideowatermark-1.png`: the Toons video watermark / logo
- `Desktop\Toons Listings\`: text listings and `Toons Listing Formula.txt`

Open the project folder through the device link at the start of a session instead of asking Ernie to upload.

## Limits

- Staging from the computer: up to ~400 MB per file.
- Claude can't write files over 30 MB back to the computer: Ernie saves finished videos into `Final\` himself.
- Chat attachments cap at 500 MB.
- Hugging Face is blocked from the cloud workspace (Whisper comes from npm; see the [edit recipe](edit-recipe.md)).
- Canva uploads are blocked from the cloud workspace.

## Naming

- Boat record slug: `<year>-<make>-<model>`, kebab-case (`2024-hurricane-sundeck-191`).
- Video files: `<Year>_<Make>_<Model>_FINAL.mp4`, `<Year>_<Make>_<Model>_YouTube_1440p.mp4`, `<Year>_<Make>_<Model>_captions.srt`.
