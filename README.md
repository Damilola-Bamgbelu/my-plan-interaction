# My plan — week interaction

A weekly workout plan card. Tap a day and the session folds out from under the frame; switch to Progress
and four months of daily activity draw themselves in, scrubbable a week at a time.

Interaction study, inspired by [@malikyoloo's Bills date picker](https://x.com/malikyoloo/status/2085371287116136620).

**[Live demo →](https://damilola-bamgbelu.github.io/my-plan-interaction/)**

## Backgrounds (for recording)

The page plays a looping video behind the card, so a screen recording isn't a flat grey rectangle.
Switch it from the URL:

| URL | What you get |
|---|---|
| `/` | `assets/wallpaper.mp4`, looping, muted, cover-fit |
| `/?bg=gradient` | Generated wallpaper — warm light top-left, cool bottom-right. No file, no download weight |
| `/?bg=photo` | A still from `assets/wallpaper.jpg` |
| `/?bg=plain` | Flat `#EDEFF2` and no card shadow — clean crop, nothing to mask around |

The gradient sits under the video at all times, so if autoplay is blocked or the file can't load,
the page falls back to it rather than going blank.

To swap the clip, replace `assets/wallpaper.mp4`. It's committed as-is with no re-encode — the
current one is H.264 1280×720, 24fps, 10s at 7.6 Mbps. Note that 720p will upscale on a Retina or
4K capture; a higher-resolution source is the only way to sharpen that.

The card only gets a drop shadow in the wallpaper modes; `plain` stays completely flat.

## Running it

One file, no build, no dependencies:

```bash
open index.html
```

Or serve it:

```bash
npx serve .
```

## What's in it

**Schedule**
- Seven day pills, each holding the date and the workout type
- Selecting a day floods the pill with black from the bottom up, like filling a tank, and springs
  as the fill tops out
- The session card is hinged at its top edge and folds out below the frame; land on a rest day and
  it folds back in
- The week alternates — Mon / Wed / Fri / Sun on, everything else a rest day

**Progress**
- 112 hairline strokes, one per day, 16 weeks ending Sun 27 Sep
- Hovering lights the whole week under the cursor and lifts it ~9%; the tooltip glides to follow
- Both figures are odometers — every digit spins a full turn before landing, later digits landing last
- The stroke sweep and the odometers replay every time you open the tab

## Notes

- Type is Helvetica Neue throughout; the card itself is strictly black and white, with colour only in
  the workout emoji
- The emoji are placeholders for a 3D icon pack — the slots are sized for drop-in image assets
  (19px in the strip, 28px in the session card)
- All the plan data lives in the `PLAN` array and the daily minutes are generated from a per-weekday
  `SHAPE`, so the copy and the figures derive from the data rather than being written in
- Every animation is CSS; the JS only sets state and toggles attributes
