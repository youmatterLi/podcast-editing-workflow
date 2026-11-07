# Audio Processing: Noise Reduction, Loudness, Multi-Speaker Levels

## 1. How much to process depends on the actual material

**Not all material should be denoised.** Whether to denoise, and how much, is decided by this material's **actual noise, distortion and a listening test**, not by a blanket rule based on how it was recorded or how loud it is.

Measure first:
- noise-floor level and the nature of the noise (steady hiss, hum, air conditioning, intermittent noises);
- any clipping, a limiter clamped hard, or "watery" artefacts left by earlier noise reduction;
- the gap between speech and the noise floor;
- whether there's real high-frequency content.

Then take a representative stretch of speech (example: at least 20 seconds) and compare two short samples by ear: "no processing (loudness only)" and "processed".

**A hint (not a criterion):** audio recorded by meeting software (Zoom etc.) has often already had noise reduction and automatic gain applied, and denoising again easily adds slight artefacts — for such material **first try loudness only**, and add more if it doesn't sound good enough. Conversely, original recordings from cameras and recorders are often quiet with a noticeable noise floor and often need denoising; but confirm by listening too.

## 2. Points to watch when denoising

- **Bring the level into the noise-reduction model's suitable input range before denoising.** If the signal is too quiet the model misjudges: quiet parts aren't cleaned properly and weak words get suppressed along with the noise. **Calculate the gain from measuring this material**, don't hard-code a constant — a gain set for quiet material applied to loud material will clamp the limiter hard and produce nothing but distortion.
- A common order is gain, then noise reduction, then loudness. Use a limiter only when needed (e.g. when raising the gain would push peaks over the limit); not every file needs one.
- When the source is clipped or its dynamic range is too wide, some loudness-normalisation tools silently fall back to dynamic compression without reporting it — check for this and flag it.
- If it sounds dull after processing: first measure why (did the noise reduction damage the voice frequency range; was the original high end just noise to begin with), then try a small amount of processing and confirm by listening. Don't apply a fixed EQ recipe.
- Before reusing a proven processing chain, first confirm that this material's input conditions (level, sample rate, channels, noise type) and the tools' requirements match the original case; if they match, reuse the whole chain rather than copying just one step.
- Record what has worked as "measured situation → method used", so next time you can use it directly when it matches, rather than making many versions for someone to choose from.

One possible implementation: ffmpeg gain + limiter → DeepFilterNet noise reduction → two-pass loudnorm. The tools can be swapped; the points stay the same.

## 3. Loudness (example delivery spec)

Example programme loudness: −16 LUFS, true peak no higher than −1.5 dBTP (set according to the target platform's requirements). After every processing pass measure coverage **in segments**: the head, the tail and both sides of every join must be within the processed range.

## 4. Multi-speaker level balance

If two people's levels differ too much, it sounds jarring.

- **How to measure:** on the voice track of the final output, take the seconds where "only the host is speaking" and those where "only the guest is speaking", compute the median level of each, and see how far apart they are. Seconds where both speak don't count.
- **Who is speaking:** with separate tracks, judge by each track's own level (example: per second, a track counts as speaking if it is 10 dB or more above the other and loud enough in its own right). With only a mixed track you first need reliable speaker segmentation.
- **How much is too much:** example working threshold 2 dB; if the approver still hears too big a difference, the ear wins.
- **Where to adjust:** with separate tracks, adjust before mixing them down; with only a mixed track, adjust per speaker segment and state where the segmentation came from. Measure again afterwards and put it in the delivery notes.

## 5. Overlapping speech

Where two people talk over each other, **listen per microphone**: transcribe each track separately with tight windows, then compare levels. Listening only to the mix makes it easy to misjudge an interjection or miss it altogether.

## 6. Picture brightness (in passing; not applicable to audio-only)

Fix only clearly over-bright or over-dark spots and leave normal variations in brightness alone; colour and skin tones should look natural — don't sacrifice colour for perfect consistency. When matching colour across cameras, use skin tone as the reference.
