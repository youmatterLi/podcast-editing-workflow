# Cut Points and Stutter Removal

The AI cannot hear. Whether a cut is good is evidenced by measurements — level, comparison against the source, re-transcription; but these are only evidence or leads. **Anything that couldn't be measured or is uncertain is "pending confirmation by ear", not "passed".**

The numbers here are example thresholds; adjust them to your material's noise floor and the speakers' habits.
## 1. Two kinds of cuts, handled separately

| | Ordinary cut | Connected-speech micro-cut |
| --- | --- | --- |
| What it does | Deletes sentences, passages, pauses, whole repeated sentences | Removes stutters, repeated words said without a break |
| Where the cut goes | True silence | Inside speech (there is no silence to begin with) |
| Main acceptance | Level at the cut point drops to the noise floor | Technical join checks on every cut + human listening to every cut or spot-checking as agreed |
| Can a program alone pass it? | Yes, as agreed in advance | No; when spot-checking, state how many cuts were actually listened to |

## 2. Ordinary cuts: where the cut point goes

1. **Set it by level, not by word timing.** Word-level transcript timings are often off by a few hundred milliseconds, and times mapped from the full-episode transcript are off even more; using them as cut points chops half a word off. Find the silence in the audio energy.
2. **True silence = down to this recording's noise floor.** A local dip between two words doesn't count — it's often still within speech.
3. **Judge the end of a sentence by energy, not transcript timestamps.** A sentence is only finished once the soft trailing syllable, drawl and breath have decayed to the noise floor. Cutting before that "chops the last word" — the most common and most recurrent cut-point problem.
4. **If there's no true silence, don't cut there.** Better to keep a little than force the cut; widen outward to the nearest silence and note by how much in the notes.
5. **Digital silence doesn't count as a pause.** When a pause needs to be added, use room tone from the same material at a matching level; or keep it silent as per your packaging convention (see episode packaging).
6. Keep crossfades at English joins short (example: about 20 ms).
7. When there's video, align cut points to whole frames (see the time map in the main file).

### How to verify ordinary cuts after rendering

Measure **the final file to be delivered** (and measure again after adding the cover or changing subtitles):

- **Against the source:** don't read your own segment list; take only the output audio, compare it with the source, and measure cut by cut (including the start of the first sentence and the end of the last) whether each lands in silence.
- **No word on the other side of the cut:** no word has been cut over to the other side.
- **No clicks or high-frequency jumps**; no sudden level jump across the join.
- **Gap length** matches the speaker's normal speaking rhythm.
- Three outcomes: pass; fail (move it into silence, and if there is none don't cut there); not fully checked (music over speech, speed change, wrong source — find the cause first; note that when a deleted word has been brought back in, the program also often ends up at "not fully checked" rather than "fail", so rule this out first). Anything that can't be measured goes to human judgement item by item, with the reason stated.

Known blind spots: a cut very close to the end of a word with a fade added can't be measured; the same sentence occurring twice in the source may be matched to the wrong place; material with a high noise floor gives more false alarms.

### A check only for "silence-only" removal

If a step **claims to have removed only silence or pauses**, you can screen further: the loudest point in each deleted range is much lower than nearby speech (example: at least 20 dB below). This is only a **screening lead** and cannot prove there was no speech in the range (soft or breathy words can be very quiet); ranges that fail must be listened to, and those that pass should also be spot-checked according to risk. This check **does not apply** to deleting sentences, repetition or stutters — those are supposed to delete speech.

## 3. Connected-speech micro-cuts: removing stutters

**Goal:** sounds smooth, nothing odd, clean joins, meaning unchanged in the slightest.

### Cut

- Stalls and restarts: a single word or the start of a word gets stuck (「我我我」 "I I I", 「因因为」 "be-because").
- A phrase half-said and said again (「我觉得我觉得」 "I think I think").
- Repeated connectives and pronouns (「但是但是」 "but but", 「这个这个」 "this this").
- Sentence-initial 「然后」 ("and then") and 「对吧」 ("right?") used as verbal tics, where removing them doesn't affect the meaning.
- When the same word is said several times in a row with the same meaning, keep only one.

### Don't cut

1. The same word coincidentally at the boundary between two sentences (the previous sentence ends with 「我」 "I" and the next begins with 「我」) — cutting would fuse two sentences into one and change the meaning.
2. Reduplicated words and deliberate doubling (「谢谢」 "thank you", 「看看」 "have a look", 「非常非常」 "very, very").
3. Back-channel agreement (「对对」 "yes yes", 「好好好」 "OK OK OK").
4. Deliberately saying the key point again (both times complete, the second not softer, no stall in between).
5. 「然后」 used mid-sentence as a connective; 「对吧」 used to confirm or to ask a follow-up.

**Read the whole sentence before and after every cut before deciding**, not just the two repeated words. When unsure, leave it as it is.

### How to do it

1. Scan the whole piece for candidates with a program. **Use short transcription windows for the scan** (example: 12-second windows); long-passage transcription tends to swallow repetitions.
2. Don't cut where there's a risk (of damaging neighbouring words); in the delivery notes write "N found in the scan, M cut, K left uncut because of risk".
3. Run join checks on every cut, as **leads**:
   - re-transcribe the join and see whether words on either side are obviously missing or extra;
   - any clicks or high-frequency jumps;
   - whether the gap is unnaturally short or long;
   - any sudden level jump across the join.
   Transcription fills in partial syllables and also misses words, so "the transcript matches" does not prove no word was clipped.
4. **By ear:** you can listen to every cut (render a few seconds around each for the approver), or spot-check by prior agreement. Spot-checking does not mean every cut point has been confirmed by ear; the delivery notes state honestly "N cuts in total, M listened to by ear, the rest only technically checked".

### Subtitles and stutters

Subtitles don't remove words actually present in the audio. An exception that can be agreed: write a stutter only once and omit "um"/"ah", without changing the audio. If you want verbal tics gone from the subtitles, delete them from the audio.

## 4. Trimming the host's own repetition

The most common issue in the host's speech is **saying the same thing or making the same point repeatedly**. In both long and short videos, trim it down to one clear statement (this is an ordinary cut; set cut points per section 2):

- Delete whole or half sentences, then check context coherence.
- **Keep repetition that is necessary or meaningful:** summarising, emphasising a key point, rephrasing so it's understood.
- When unsure, judge by the key point this clip is meant to make; the delivery notes say which repetitions were deleted, which were kept, and why.
- If the same follow-up question is asked twice in the interview, delete the second and keep the first.

## 5. Limits of a machine first pass

You can let a program first remove a few clear-cut categories, then hand it to a person for word-by-word trimming, stating what the program removed:

- verbal tics (such as 「对吧」 "right?", 「你知道吗」 "you know?");
- **sentence-initial** 「然后」 ("and then") (leave it alone mid-sentence as a connective);
- stutter repeats (example: the same character ≥3 times keeps only one; a two-character word said twice is removed only if there's a real pause between the two).

**No semantic trimming** — which sentence is long-winded is an editorial judgement. Where speech is connected on both sides, don't delete — just report. Every spot the program flags is then reviewed again against "cut / don't cut" above.
