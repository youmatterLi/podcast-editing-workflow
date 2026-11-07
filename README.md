# podcast-editing-workflow

## English

A Claude Code skill: a reference method for editing interview podcasts with an AI agent — full episodes, mid-length videos and vertical short clips. It covers source checking, cut-point rules, stutter removal, keeping context coherent after cuts, loudness, hooks/chapters/music, and a pre-delivery checklist. It is tool-agnostic and contains no program code.

The AI cannot hear, so the emphasis is: **judgements about how something sounds need measured evidence; anything that couldn't be measured is reported as not checked; anything that needs human ears goes to human ears**.

### Two language versions

```
SKILL.md                          English (the version Claude reads by default)
references/cuts-and-stutters.md   two kinds of cuts; what to cut / not cut when removing stutters
references/audio.md               processing chain by actual material, loudness, multi-speaker levels
references/episode-packaging.md   hooks, chapters, progress bar, music, subtitles, name tags, watermark (example settings)
references/full-checklist.md      item-by-item pre-delivery checklist
zh/SKILL.md                       Chinese original
zh/references/                    the four reference files in Chinese
```

The two versions have the same content. Claude loads the top-level `SKILL.md` (English); the English file points to `zh/` for the Chinese version.

### Install

Put the whole folder at:

```
~/.claude/skills/podcast-editing-workflow/
```

with `SKILL.md` at the root of that folder. Claude Code discovers it automatically; Claude may pick it automatically for podcast or video editing requests, or you can say "use podcast-editing-workflow to edit this episode".

If you'd rather Claude read the Chinese version by default, copy the contents of `zh/` (its `SKILL.md` and `references/`) into `~/.claude/skills/podcast-editing-workflow/` instead.

### What you need to bring

This skill **contains no program code** and doesn't prescribe tools. Its steps (word-level transcription, noise reduction, finding silence by level, checking cut points against the source, re-transcribing the output, rendering a progress bar, etc.) are implemented with your own tools. Common open-source choices include ffmpeg, faster-whisper and DeepFilterNet, but all are replaceable.

Apart from delivery specs, the numbers in this skill are **example settings — adjust them for your show**; they don't represent a universal standard.

- "Host / approver" means whoever signs off; "reviewer" means someone who reviews independently where possible.
- Add or remove rules to suit you, especially the checklist — it should grow with the problems you run into.

---

## 中文

一份面向访谈播客的剪辑方法参考，适合「AI 动手剪、人来听看定稿」的分工。工具无关，不含任何程序代码。AI 听不到声音，所以重点是：**听感上的判断要有量出来的证据，量不了的如实说没查，需要人耳的就交给人耳**。

### 两个语言版本

- 英文版：根目录的 `SKILL.md` 和 `references/`（cuts-and-stutters.md、audio.md、episode-packaging.md、full-checklist.md）。Claude 默认读这一份。
- 中文原版：`zh/SKILL.md` 和 `zh/references/`（刀口与删结巴.md、声音处理.md、整集包装.md、全片检查清单.md）。

两版内容相同。

### 安装

把整个文件夹放到：

```
~/.claude/skills/podcast-editing-workflow/
```

确保根目录有 `SKILL.md`。Claude Code 会自动发现它；Claude 可能会根据剪辑播客或视频的请求自动选用，也可以直接说「用 podcast-editing-workflow 剪这一期」。

想让 Claude 默认读中文版，就把 `zh/` 里的内容（`SKILL.md` 和 `references/`）复制到 `~/.claude/skills/podcast-editing-workflow/`，代替英文版。

### 需要你自己准备的

这个 skill 不含程序代码，也不指定工具；里面的步骤用你自己的工具实现，常见的开源选择有 ffmpeg、faster-whisper、DeepFilterNet，都可以替换。文中的数字除交付规格外都是**示例设置，可按你的节目调整**，不代表通用标准。

- 「主持人／批准人」指拍板定稿的人；「复核人」指条件允许时独立复核的人。
- 按自己的情况增删规则，尤其是检查清单——它应当随着你踩过的坑一起长。
