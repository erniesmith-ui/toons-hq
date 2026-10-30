# Edit recipe - the technical steps behind 01-03

How the approved result (2024 Hurricane SunDeck 191 FINAL, "this looks great") was made. Stage contracts point at sections here. Rules about *what* to do live in [house rules](house-rules.md); this file is *how*.

## Review

1. `ffprobe`: resolution, fps, duration, streams, pix_fmt, color_range, color tags. Phone footage is often full range (yuvj420p, pc) with sRGB transfer tags: convert it at Render. If there is a mov_text subtitle stream, always pass `-sn` when writing intermediates (otherwise ffmpeg runs out of memory).
2. Transcribe with word timestamps. Hugging Face is blocked: get Whisper small (CTranslate2 int8) from npm with `npm pack @skillninja/shortmovie-telop-model-p0` through `-p3`, cat `model.bin.part0-3` into `model.bin`, verify against `model.sha256`, load with faster-whisper, pass a numpy float32 array, and give an initial_prompt with brand and boat terms.
3. Whisper word times can run late (it timed Kevin's "forty-six" ~0.7 s late). Confirm every in/out point against the 20-50 ms RMS energy envelope.
4. Contact sheet every 5 s; ebur128 loudness; count clipped samples; frame-difference scan of the raw to find shot changes that already exist, including joins inside the original recording.
5. List issues: misspoken facts or URLs, asides, dead air, where the sign-off falls, clipping, breaths, noise.

## Plan

- Burned-in old graphics: crop above them (9:16) and scale back to 1080x1920.
- Trimming dead air on either side of an existing shot change is fine.

## Render

- One intermediate per kept stretch, straight from the original: `scale=in_range=pc:out_range=tv:in_color_matrix=bt709:out_color_matrix=bt709,format=yuv420p,eq=contrast=1.04:saturation=1.06,setsar=1,fps=<source fps>`, x264 `-preset fast -crf 8` with `-color_range tv -colorspace bt709 -color_primaries bt709 -color_trc bt709`.
- No unsharp or sharpening (halos and noise compress badly on upload). No stabilization unless Ernie asks: phone footage is already stabilized and vidstab's zoom softens the picture.
- Join stretches with the concat demuxer (`-c copy`). On the last stretch, hold the final frame (tpad clone) for the end-card time and pad the audio.
- Never split or trim the same input twice in one graph, or xfade long inputs (out of memory). Run long renders with `setsid nohup` and poll for a log file, in waits under 10 minutes.

## Cards

- One style: dark rounded panel, blue accent bar, blue caps eyebrow, white Inter Black title, grey subtitle; 0.3 s fade + 50 px slide.
- Position: the spot empty in every shot (outdoors: sky top-left, y~150; showroom: clear lower area). Check each card at 4 points across its shot.
- Usual set, each on the line naming it: hook (year/make/model/hours), pre-owned or consignment message, name + phone + toonsusa.com, features, extras (e.g. "We Ship to Your Door"), directions. At least 0.4 s between cards. No price card.
- Load card PNGs with `movie=card.png,loop=loop=-1:size=1,setpts=N/FPS/TB,trim=duration=D`, never `-loop 1` inputs.
- End card, 5 s: real Toons logo (white on the navy card), "Eufaula, Oklahoma", "Top-Notch Pre-Owned & Consignment", toonsusa.com, phone, "Ask for <salesperson>", trade-ins/consignment line, directions, socials. Overlay with a 0.6 s fade over the held last frame; make it run past the video end (no flash on the last frame; Shorts loop).

## Audio

1. adeclip if clipped; resample 48 kHz; highpass 80 Hz.
2. Denoise with arnndn using `_Brand\rnnoise_cb.rnnn` (or GregorR/rnnoise-models from GitHub), mix 0.9.
3. Breath ducking: in pauses between words, turn audio down ~11 dB with 40 ms smoothing, protecting any frame louder than -24 dB (80 ms margin). No blunt gate.
4. Light EQ (-1.5 dB @250 Hz, +1.5 dB @3 kHz), gentle compression (ratio 2, no make-up), limiter, two-pass linear loudnorm to -14 LUFS, TP -1.5.
5. Measure speech level, pause noise floor, speech-to-breath gap, and per-shot speech level (within ~1.5 dB).

## Captions

SRT from word timestamps mapped to the output timeline. Fix brand and spec words, join hyphen tokens, lines of 34 characters or fewer, capitalise only after sentence ends. Mux as mov_text and deliver the .srt. Don't use `-shortest`.

## Export

One final pass from the near-lossless base with cards, watermark and end card overlaid, encoded once:

- **1080p master** (Facebook + archive): `-preset slow -crf 16 -profile:v high -level 4.2 -g 60 -bf 2 -maxrate 30M -bufsize 60M -pix_fmt yuv420p` + BT.709 tags (range tv), AAC 320k 48 kHz, `+faststart`, captions as mov_text. Name: `<Year>_<Make>_<Model>_FINAL.mp4`.
- **1440p YouTube version**: same graph + `scale=1440:2560:flags=lanczos`, `-preset slow -crf 17 -level 5.1 -maxrate 22M -bufsize 44M` (stays under the 500 MB chat limit for ~2.5 min). Name: `<Year>_<Make>_<Model>_YouTube_1440p.mp4`.
- Write `UPLOAD_SETTINGS.txt` into the boat's Final folder: which file goes where; wait for YouTube HD processing; upload to Facebook from a computer or with HD uploads on; never pass the file through text, Messenger or email.

## Verify

- Frame-difference scan of the final: list every spike. Allowed only at planned edits (existing shot changes) and joins already in the original recording; name each one.
- Check the last frame.
- Sharpness and color: crops of source vs final at the same moments; edge variance within ~5% of the source, no halos, colors close.
- Re-transcribe the final audio at the start, every edit and the end: every word intact.
- ebur128 about -14 LUFS; contact sheet at every edit and card.
