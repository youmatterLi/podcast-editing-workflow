---
name: podcast-editing-workflow
description: A reference method for editing interview podcasts and videos — full-episode edits, mid-length videos and vertical short clips. Use it when you have recordings to cut, need to remove stutters and filler words, set cut points, build hooks and chapters, or self-check before delivery. A Chinese version is in zh/.
---

# Podcast Editing Workflow

A reference method for editing interview podcasts, suited to a division of labour where "the AI does the cutting, a human listens, watches and signs off". The AI cannot hear, so every judgement about how something sounds needs **measured evidence**; anything that could not be measured is reported honestly as "not checked". Final listening/viewing and editorial choices are made by the host (or another agreed approver).

This file describes methods and acceptance targets only; it is not tied to any tool, and any tool named here is just one possible implementation. Except where a delivery spec is explicitly stated, the numbers in this document are **examples — adjust them for your show**.

Three kinds of output:

| Output | Depth of work | Review focus |
| --- | --- | --- |
| Full podcast episode | All five stages in full; content structure, multitrack sync, privacy, every join | Full listen/watch of the candidate episode, with focus on cuts and reordering |
| Mid-length video (single topic) | Five stages, streamlined; keep necessary context, technical checks, subtitles | Full watch, with focus on cuts and subtitles |
| Short clip | Only what is necessary; three core checks: privacy, original meaning, joins | Full listen/watch of the whole clip |

**Five stages** (these names are used throughout): Prepare → Locate → Cut → Post → Deliver.

**Audio-only works** are exempt from: everything visual (camera angles, the video side of frame alignment, frame sampling, progress-bar visuals, subtitle burn-in, safe areas, watermarks, covers, end cards). Chapter markers, loudness, cut points, semantics and music still apply. Items that don't apply are recorded as "N/A + reason" in the check log.

Reference files — read them when needed:

- `references/cuts-and-stutters.md`: how to set and verify the two kinds of cuts (ordinary cuts, connected-speech micro-cuts); what to cut / not cut when removing stutters
- `references/audio.md`: deciding the processing chain from the actual material, loudness, multi-speaker level balance
- `references/episode-packaging.md`: hooks, chapters, progress bar, music, subtitles, name tags, watermark (mostly example settings)
- `references/full-checklist.md`: the item-by-item pre-delivery checklist, with applicability

---

## 1. Principles that apply throughout

1. **Finish one piece before starting the next.** Several queued clips are a queue, not parallel work. Parallel work burdens the reviewer — they only ever see half of each piece.
2. **Agree in advance who approves what.** Before starting, make clear: who decides content choices, who confirms how it sounds, which technical processing (transcoding, resolution changes, loudness normalisation) only needs review in the agreed way, and who approves publication.
3. **Silence is not approval.** A reply of only "got it" or "will look later", or no reply, does not count as confirmation. Record the scope of each confirmation: which version, which aspect (sound / semantics / picture / text), and the approver's actual words. Confirming the sound does not mean the semantics also pass.
4. **Substantive edits need re-confirmation.** Don't touch already-confirmed content, cut points, camera choices or title text in later revisions; if something really must change, record why and send it to the approver to confirm again. Processing that doesn't change content (resolution change, transcoding) only needs review in the agreed way, but you must verify via the time map that content is unchanged (see section 6).
5. **New general rules apply only going forward**; don't retroactively change work already approved for publication.
6. **Passing technically is not passing semantically**; check and record them separately.
7. **Decide what you can decide yourself**; batch the things only the approver can decide into a single ask, and give one recommendation per item rather than a multiple-choice question for someone else to pick from.
8. **Where possible, have someone who wasn't involved in production review independently** before it goes to the approver. The reviewer only checks and raises change requests; they don't make changes on the maker's behalf. Independent review is a recommendation, not a precondition for delivery; if there is no reviewer, state "not independently reviewed" in the delivery notes.
9. **Checks themselves can lie.** See "Lessons" in section 6.

---

## 2. Prepare: inspect the material, build anchors

### First find out how it was recorded and how good it is

1. **Is it the original recording?** Look at the file's production metadata (codec, bitrate, export time, software name). Files copied straight off a camera or recorder, and per-person tracks supplied by a recording platform, count as original; anything re-exported from editing software, merged or compressed does not.
2. **Is there a more original version?** For remote recordings, check for one audio track per person and per-camera video; for camera recordings, check for a separate recorder or external mic. If there is one, use the original.
3. **Quality of the sound and picture themselves:** sample rate, bitrate, whether there's real high-frequency content, how loud the noise floor is, any clipping distortion, overall loudness; for picture, the actual resolution and bitrate.

Write the findings into this episode's source record. If only compressed files are available, first tell the approver "this is the best material we can get, and here's what's wrong with it", and proceed once they agree. If the base material changes midway, re-render every affected segment and say so in the delivery notes.

### Choose the right source

- Full episode or first standalone video: use the original material.
- Short clips and derivative cuts: use the **approved release version** (with all required deletions already applied); for landscape versions with a watermark, use its watermark-free master. Don't cut clips from the original recording, so deleted content can't come back.
- A transcript must match the file it is used with; the original's transcript cannot be used with the release version.

### Other preparation

- **Check the material:** duration, resolution, frame rate, audio tracks, sample rate, rotation metadata, decode errors.
- **Multi-camera:** identify cameras by real identity and audio source, not by guessing from file order; align using shared sound events or waveforms, record each segment's offset separately, and check drift at the start, middle and end.
- **Remote recording:** first inventory the separate tracks and composite video you actually received — don't assume it's all there; if you only have the composite, cut with the existing framing.
- **Solo video:** for livestreams check waiting segments, on-screen notifications and username privacy; for phones check rotation and variable frame rate; for cameras check file splits and external audio.
- **Do audio processing first** (see `references/audio.md`); transcribe and cut from the processed audio.
- **Transcription** (word-level): for long material, extract the audio first and then split it into chunks; **restore source time using each chunk's actual start and end**, not "chunk index × chunk length"; check around chunk boundaries for cut-off sentences and re-transcribe a window spanning the boundary if needed. Keep intermediate files in your working directory, not the system temp directory.
- **Merging:** de-duplicate at chunk boundaries; once segment numbers are fixed, don't renumber; when correcting typos keep the original transcript and a change record.

**Minimum per-episode record:** purpose of this episode; source (how recorded, original files, quality); content that must be deleted and must be kept; synonyms for sensitive topics (for searching); guest consent and public boundaries; confirmed special editing decisions (with source times where they map to a location).

---

## 3. Locate: turn suggestions and feedback into cut ranges

- Read this episode's must-delete, must-keep and public boundaries first, then the latest feedback. Source anchors don't drift when the text is edited.
- Sort feedback into "delete audio", "subtitle-only change", "keep", "reorder" and "to discuss". Polishing wording does not automatically trigger an audio deletion; ambiguous annotations stay as they are and go on the review list.
- Locate using **first sentence plus last sentence** together; disambiguate repeated sentences using context, speaker and source time. Don't delete based on a single text match.

**Sign-off medium (choose your own tool):** for a full episode use an **annotated transcript** — the complete transcript, word for word, with your suggested deletions marked, which the approver edits directly (delete, restore, add deletions). It's better than a checklist of candidates: the approver can propose cuts you didn't think of. Short clips can use the same annotated transcript or an **edit decision table** (one sentence per row: keep / delete / change subtitle). Whichever you use, it must satisfy:

- A simple, unambiguous read-back rule (e.g. "marked = delete, unmarked = keep"; don't rely on colour to carry meaning);
- Every sentence can be mapped back to source time, even when only half a sentence is marked;
- Every deletion read back is then placed at a cuttable position according to the cut-point rules; where no suitable position exists, don't force the cut — widen outward, and say by how much.

With each version you can produce a fresh annotated transcript marked with the actual deletions for the approver to check. Which words were deleted is established mainly from **alignment of a fresh transcript of the output with the source transcript**, then confirmed by listening at suspicious spots; word-level timestamps can be far off, so don't use them alone to decide what was cut. Original text that a guest asked to delete is not put in the shared transcript — only a placeholder.

**Quality gate:** every executed range can be traced back to its source position, first/last sentence, action and reason. Ambiguous ranges are not deleted automatically.

---

## 4. Cut: produce the candidate from the adopted decisions

**Fix the decisions first:** save a checkpoint; merge overlapping deletions on the same source; check must-keep ranges and question–answer dependencies. Deletions apply to every audio track and every camera at once; subtitles are rebuilt from the same time map; crossfades and filler footage must not bring deleted material back.

### Time map (single definition)

For each kept segment i, record three things separately:

- **Source in** `in[i]` and **source out** `out[i]`: start and end in the source, precise to the sample; when there is video, snapped to frame boundaries `round(t×fps)/fps`.
- **Segment length** `len[i] = out[i] − in[i]` (not the difference between adjacent in-points — there may be a deleted range in between).
- **Output start** `start[0] = 0`, `start[i] = start[i−1] + len[i−1] − overlap[i]`, where `overlap[i]` is the crossfade length at this join (0 for a hard cut).

Constraints on overlap:

- `overlap[i]` must not exceed the usable length of either adjacent segment (`overlap[i] ≤ min(len[i−1], len[i])`), or it will eat a whole segment.
- When there is video, `overlap[i]` must land on a whole number of frames; if it can't, state how the sub-frame remainder is handled (e.g. round the audio side to the frame, or add the remainder to the next segment's in-point), and handle audio and video the same way.
- The overlap region may only use material inside the kept range: fades must not extend beyond `in[i]` / `out[i]` and must not bring back must-delete content. If extra material is needed for a crossfade, take it from inside the kept range rather than extending outward.

Rules:

1. **Compute everything in frames / samples, never round to seconds**; give video lengths as frame counts. Per-segment rounding accumulates into visible audio–video drift.
2. **Audio and video use the same time map.** When the audio crossfades with overlap, the video is handled with the same `overlap` (overlap, or trim the same amount at the same place), so both sides have the same `start[i]`. Changing only one side accumulates misalignment.
3. **After every render, compare total audio and video duration**; if they differ by more than 1 frame, stop and investigate. Count the actual video frames and compare with the duration derived from the audio sample count.
4. **After every audio processing pass, check coverage:** the head, the tail and both sides of every join must be within the processed range; **measure in segments**, not as one average over the whole file.
5. While revising, render only small previews; once content is settled, render the full-quality version once and check that its kept-segment list and chapter list match the preview.
6. Give people only one file path to listen to / watch each time; move old versions to an archive, and put the version number and time in the file name.
7. Use one time zone, stated explicitly, for times in logs and records.

### Removing stutters, filler words and the host's repetition

In the release version, remove them for both host and guest; the version sent to the guest for review doesn't remove them (it only removes what the guest asked to delete and messy parts such as setup at the start or interruptions). The goal: **sounds smooth, nothing odd, clean joins, meaning unchanged in the slightest**. Details in `references/cuts-and-stutters.md`.

- Cut: stalls and restarts (「我我我」 "I I I", 「因因为」 "be-because"), half-said phrases said again, repeated connectives and pronouns, sentence-initial 「然后」 ("and then") and 「对吧」 ("right?") used as verbal tics.
- Don't cut: the same word coincidentally at a boundary between two sentences, reduplicated words, back-channel agreement, deliberate repetition for emphasis, 「然后」 used mid-sentence as a connective.
- **Where the host repeats the same point, trim it down to one clear statement**; keep meaningful repetition (summarising, emphasis, rephrasing so it's understood).
- Don't cut where there's a risk of damaging neighbouring words; in the delivery notes write "N found in the scan, M cut, K left uncut because of risk".

### Two kinds of cuts

- **Ordinary cuts** (deleting sentences, passages, pauses): the cut point lands in **true silence** — found by level, with trailing soft syllables and breath decayed to the noise floor; if there's no true silence, don't cut there.
- **Connected-speech micro-cuts** (removing stutters, removing repeated words said without a break): there is no silence to begin with, so the cut has to be inside speech. Don't apply the silence threshold; **run technical checks on every cut** (re-transcription, clicks, level jumps, rhythm — as leads). A human can listen to every cut, or spot-check by prior agreement; **spot-checking does not mean every cut point has been confirmed by ear** — the delivery notes must state how many cuts were actually listened to out of how many in total.

### Context stays coherent after edits

Check after every edit (including small deletions within a sentence), extending the range backward and forward until the relationships are confirmed:

- Does every question still have its answer? Does an answer depend on a question or background that was deleted?
- Do words like "those", "what I just said", "so", "but" still have a clear referent or premise?
- Have people, events and times been introduced? Are negation, conditions, degree, reported speech and speaker attribution preserved?
- After deleting an example, is only an unsupported conclusion left?
- Does joining segments create a cause, agreement or viewpoint that wasn't in the original interview?
- A fix can delete a connective, but confirm the remaining answer still responds to the current question. **Never restore must-delete content to bridge a gap; never synthesise or invent sentences.**

### Multi-camera and solo

- For a complete statement prefer the speaker's shot; for overlapping speech or uncertain identity use the wide shot from the same moment. Reaction shots use only real footage from the same moment; if there's no suitable shot, use an honest jump cut.
- Unflattering moments such as a guest crying, wiping their nose or getting up are replaced with the host's shot or a two-shot; switch shots between sentences or in pauses, with only one switch in and one out per instance.
- Cut solo video around complete sentences and demonstration steps; don't delete a key step and then use subtitles to describe an action that never happened on screen.

### Join checks

At every join, re-transcribe a window on each side covering a complete short sentence and compare it with the source segment that should be kept; sample frames before and after cut points that have video; run peak, loudness, silence and black-frame detection on the output. **A transcript match is only a lead**: transcription misses words and also fills in partial syllables, so a match doesn't prove the words are intact, and a mismatch still needs listening to confirm. Don't use it to claim "joins sound natural" or "lip sync is correct".

For multi-speaker level balance and loudness see `references/audio.md`.

---

## 5. Post: subtitles, packaging, short clips

### Short clips: ask three questions first

1. **Opening:** is the first sentence the start of a sentence, or is it tacked onto the tail of the previous one?
2. **Middle:** does it stand on its own? Is a "why" or "how" left outside the clip? If the same question is asked twice or the same point made twice, keep only one; if they can't be separated, delete the whole sentence, find a different entry point or restructure.
3. **Ending:** it's enough that the meaning is complete and it ends where it should end; don't force a fixed ending template.

If any one fails, go back to the source and look 40–60 seconds either side to pull in what's missing. Candidate clips machine-cut by topic routinely break mid-sentence at both ends — check every one. **Get into the topic within five seconds**, with the most gripping line up front. Whether a clip gets made is the approver's call: you can recommend, but starting work is decided by the approver as agreed.

### Acceptance targets for short clips (step order and tools are up to you)

| Target | How to verify |
| --- | --- |
| Audio processing is done before cutting | Processing coverage check (see audio) |
| Word-by-word trimming uses this clip's own transcript | Re-transcribe from this clip's own audio; don't map times from the full-episode transcript |
| Words the transcript missed don't escape deletion | Listen one by one to ranges the transcript marks as "silence" but which actually have significant level (example: ≥0.3 s, peak > −40 dB); add genuinely missed words to the transcript |
| What the final edit deleted is really gone, and everything to keep is there | At least one independent check that **listens only to the output audio** (re-transcribe and compare with the final edit, listening to each difference); same-source comparisons like "what's burned in matches the script" are not enough |
| No cut point clips a word | Measure each cut in the final file against the source (see the cuts reference); measure the final file again after adding the cover or changing subtitles |
| Subtitles, vertical crop, cover, safe areas and audio/video duration are correct | Frame sampling plus duration comparison |
| Approver signs off | As agreed in advance (usually explicit approval after listening to / watching the whole clip) |

Shorten unnecessary long pauses (example: ≥0.6 s within the same topic), and note why any remaining ones were kept. A shorter version made for a platform length limit is cut from the approved long version; whether it goes back to the approver is as agreed in advance.

### Subtitles, chapters, music etc.

Details and example settings are in `references/episode-packaging.md`. Key points:

- Subtitles come from the finalised text, not the transcript; don't remove words actually present in the audio (stutters may be written once, "um"/"ah" may be omitted); one line at a time, natural line breaks; checking is done in two passes, "against the audio" and "reading for meaning".
- 3–5 opening hooks, each understandable on its own; pauses between hooks are filled with room tone, not digital silence.
- Chapters are large blocks following how the content develops, starting at the beginning of the question that opens a topic; the same chapter list is used for the on-screen progress bar, file chapter markers and the platform's chapter list.
- Music: the intro comes in after the hooks and leaves soon after the main content starts; the outro sits under the last stretch of speech; intro and outro use different tracks; no music in the middle by default, with transitions only where the topic jumps a lot.
- Any re-edit means rebuilding subtitles and recalculating chapters and the progress bar.

---

## 6. Deliver: deliver with evidence

### Check statuses

| Status | Meaning |
| --- | --- |
| PASS | Actually performed, evidence meets the criterion (valid only for that item and that version) |
| FAIL | Breaks a baseline rule or the delivery spec; fix and re-check |
| REVIEW | Ambiguity or a judgement call that needs a human; submit location, impact and recommendation together |
| NOT CHECKED | Should have been doable but wasn't done or was blocked by tooling; state why |
| N/A | State why (e.g. visual items for an audio-only work) |

Every item records the version; an old version's result can't stand for a new version. A version with any FAIL or NOT CHECKED can only be called a "review candidate". The delivery report lists every checklist item with its status, not only the ones done. Checklist: `references/full-checklist.md`.

### Sending for review

- **Semantic issues:** judge and fix them yourself; send only the ones you can't resolve to the approver, as text: original context, the joined result (mark cut points with ｜), the concern, and a recommendation. Don't send two isolated sentences and leave them to guess the background.
- **Sound issues** are the only ones sent as audio: state which two words the cut falls between and at what second; leave enough margin before and after; state whether it's raw audio, an unmixed join or the final mix.
- Don't send items already confirmed and unaffected. Sending less for review doesn't mean checking less yourself.
- **Compare the new version with the previous one:** which source segments each version keeps and in what order; list anything falling within confirmed ranges separately with the reason. The listening list includes only: new cut points, changed cut points, and issues newly found in this version.
- Once the approver has listened to / watched one full version, a new version just lists what changed, with the spots to review cut into a single "highlights" clip with context before and after; and verify the unchanged parts are unchanged: align the corresponding ranges of the final outputs via the two versions' time maps and compare; if lossless and the processing chain is unchanged you can compare sample-by-sample and frame-by-frame, and if encoding is lossy or processing changed, compare with an appropriate tolerance (e.g. audio level difference, video PSNR), review each anomalous range that exceeds tolerance, and confirm they all fall within this round's changes.

### What to deliver

The output file, any necessary subtitles, plus a summary: version, main edits, automated check results, items pending review, and whether it was independently reviewed. If no human has listened/watched, say "automated checks complete, pending listen/watch", not "all sorted". After revisions update only the affected range and re-run the relevant checks; a revised candidate does not inherit the previous version's approval.

### Lessons

- **Don't use your own filter to verify your own output.** To tell whether something finished, look for strings that appear only on success / failure, not symbols that appear all over the body text. After a run, first look at the raw tail of the output unfiltered. Check exit codes: a pipeline by default returns only the last command's exit code (`cmd | grep | tail; echo $?` gives you tail's, usually 0), and behaviour differs again with `pipefail` enabled; the safest approach is not to pipe, and to save and check each command's output and exit code separately (e.g. `cmd > out.log 2>&1; rc=$?`). In Bash you can also use `${PIPESTATUS[@]}` to get each command's exit code in a pipeline (this is Bash-only). **The command you verify with must itself be verified once.**
- **Checks based only on the transcript or written edit script are same-source comparisons**; they can only prove "what's burned in matches the script". There must be at least one check that listens only to the output audio.
- **Two checks must not share blind spots.** Time-based frame sampling skips very short subtitles; content-based transcription misses whole passages it failed to recognise.
- **Rule out measurement artefacts before concluding:** a window hitting a boundary, sampling across a join, a frame grab off by one, duplicate frames in the source itself — all look like real bugs.
- **Verify against the old version as reference**: test old and new in the same table, changing one variable at a time.
- **If the processing chain changes, redo old segments:** heads and transitions made before the chain changed are void.
- **Measure audio–video sync on its own:** only checking "matches the reference version" misses misalignment in the reference itself; compare original audio and picture from the same camera.
- **Reuse methods that have worked** rather than making many versions for someone to choose from each time; when the situation doesn't match known cases, measure the cause first, then produce one sample.
- **Whole-file averages hide local problems:** measure loudness, processing coverage and level differences in segments.
- **Read video frames one at a time and release them after use**, rather than loading everything into memory.
