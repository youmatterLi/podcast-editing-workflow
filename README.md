# podcast-editing-workflow

## English

A Claude Code skill: a reference method for editing interview podcasts with an AI agent — full episodes, mid-length videos and vertical short clips. It covers source checking, cut-point rules, stutter removal, keeping context coherent after cuts, loudness, hooks/chapters/music, and a pre-delivery checklist. It is tool-agnostic and contains no program code.

The AI cannot hear, so the emphasis is: **judgements about how something sounds need measured evidence; anything that couldn't be measured is reported as not checked; anything that needs human ears goes to human ears**.

### Two language versions

```
SKILL.md                            English (the version Claude reads by default)
references/cuts-and-stutters.md     two kinds of cuts; what to cut / not cut when removing stutters
references/audio.md                 processing chain by actual material, loudness, multi-speaker levels
references/episode-packaging.md     hooks, chapters, progress bar, music, subtitles, name tags, watermark (example settings)
references/full-checklist.md        item-by-item pre-delivery checklist
references/example.md               a fully fictional worked example
references/report-template.md       fill-in delivery report template
zh/SKILL.md                         Chinese original
zh/references/                      the six reference files in Chinese
LICENSE                             CC BY-NC 4.0
```

The two versions have the same content. Claude loads the top-level `SKILL.md` (English); it points to `zh/` for the Chinese version.

### Install

Put the whole folder at:

```
~/.claude/skills/podcast-editing-workflow/
```

with `SKILL.md` at the root of that folder. Claude Code discovers it automatically; it's used when editing podcasts or videos, or you can say "use podcast-editing-workflow to edit this episode".

If you'd rather Claude read the Chinese version by default, copy the contents of `zh/` (its `SKILL.md` and `references/`) into this folder instead:

```
~/.claude/skills/podcast-editing-workflow/SKILL.md        <- from zh/SKILL.md
~/.claude/skills/podcast-editing-workflow/references/     <- from zh/references/
```

### What you need to bring

This skill **contains no program code** and doesn't prescribe tools. Its steps (word-level transcription, noise reduction, finding silence by level, checking cut points against the source, re-transcribing the output, rendering a progress bar, etc.) are implemented with your own tools. Common open-source choices include ffmpeg, faster-whisper and DeepFilterNet, but all are replaceable.

Apart from delivery specs, the numbers in this skill are **example settings — adjust them for your show**; they don't represent a universal standard. Items marked "example practice" are style or content choices, not requirements.

- "Host / approver" means whoever signs off; "reviewer" means someone who reviews independently where possible.
- Add or remove rules to suit you, especially the checklist — it should grow with the problems you run into.

### License

Text licensed under CC BY-NC 4.0: you may use and adapt it with attribution, but not for commercial purposes. See `LICENSE`.

---

## 中文

一份面向访谈播客的剪辑方法参考，适合「AI 动手剪、人来听看定稿」的分工。工具无关，不含任何程序代码。AI 听不到声音，所以重点是：**听感上的判断要有量出来的证据，量不了的如实说没查，需要人耳的就交给人耳**。

### 两个语言版本

```
SKILL.md                        英文版（Claude 默认读这一份）
references/                     英文参考文件 6 个
zh/SKILL.md                     中文原版
zh/references/刀口与删结巴.md    两类剪切；删结巴的剪／不剪
zh/references/声音处理.md        按实际情况决定处理链、响度、多人音量
zh/references/整集包装.md        钩子、章节、进度条、音乐、字幕、名牌、水印（示例设置）
zh/references/全片检查清单.md    交付前逐条核的清单
zh/references/示例.md            一个完全虚构的小例子
zh/references/交付报告模板.md    可直接填的交付报告模板
LICENSE                         CC BY-NC 4.0
```

两版内容相同。

### 安装

把整个文件夹放到：

```
~/.claude/skills/podcast-editing-workflow/
```

确保根目录有 `SKILL.md`。Claude Code 会自动发现它；剪辑播客或视频时会被调用，也可以直接说「用 podcast-editing-workflow 剪这一期」。

想让 Claude 默认读中文版，就把 `zh/` 里的内容复制到这个文件夹，代替英文版：

```
~/.claude/skills/podcast-editing-workflow/SKILL.md        <- 来自 zh/SKILL.md
~/.claude/skills/podcast-editing-workflow/references/     <- 来自 zh/references/
```

### 需要你自己准备的

这个 skill 不含程序代码，也不指定工具；里面的步骤用你自己的工具实现，常见的开源选择有 ffmpeg、faster-whisper、DeepFilterNet，都可以替换。文中的数字除交付规格外都是**示例设置，可按你的节目调整**，不代表通用标准。标为「示例做法」的是风格或内容取舍，不是要求。

- 「主持人／批准人」指拍板定稿的人；「复核人」指条件允许时独立复核的人。
- 按自己的情况增删规则，尤其是检查清单——它应当随着你踩过的坑一起长。

### 许可

文本以 CC BY-NC 4.0 授权：可以使用和改编，须注明出处，不得用于商业用途。见 `LICENSE`。
