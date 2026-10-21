---
name: humanizer-zh
description: |
  Edit Chinese prose to reduce formulaic AI phrasing while preserving its purpose and genre.
  Three modes: A, remove AI-style writing; B, polish formal or administrative writing;
  C, improve marketing or social-media copy. Select the mode from the user's request
  and the supplied text. Chinese phrases in the references are examples to inspect,
  not a request to switch the output language.
allowed-tools:
  - Read
  - Write
  - Edit
  - AskUserQuestion
metadata:
  trigger: Edit or review Chinese writing for clarity, natural tone, formal polish, marketing copy, or AI-style phrasing.
  source: Translated from blader/humanizer; also informed by hardikpandya/stop-slop.
---

# Humanizer-zh: Edit Chinese Prose

Act as an experienced Chinese-language editor. Diagnose the text before revising it. **Write the edited text in Chinese.**

## Step Zero: Choose a Mode

| Signal | Mode |
|---|---|
| User asks to remove `AI痕迹`, `机器味`, or `AI生成的` phrasing | **A: Remove AI-style writing** |
| User asks for `润色`, `公文`, `签报`, `正式文件`, `报告`, or `领导审阅` | **B: Formal-text polish** |
| User asks for `文案`, `朋友圈`, `宣传`, `营销`, `推文`, or `种草` | **C: Marketing/social copy** |
| Text includes formal phrases such as `特此报告` or `请审阅` | **B** |
| Text is promotional, uses many emoji, numbered slogans, or calls to action | **C** |
| Intent is unspecified and the text is visibly formulaic AI prose | **A** |
| Ambiguous | Ask which of A, B, or C the user wants. |

Tell the user your choice in one short Chinese sentence and invite correction.

## Mode A: Remove AI-Style Writing

Use for AI-generated or noticeably mechanical prose. Default to a **medium** revision: remove clear AI patterns, vary rhythm, and preserve the basic structure.

| Intensity | Trigger | Action |
|---|---|---|
| Light | `只去痕迹`, `微调`, `保留风格`, `别改太多` | Remove obvious stock wording and templates only. |
| Medium (default) | No intensity specified | Remove AI patterns and adjust rhythm while keeping the original frame. |
| Heavy | `大改`, `注入个性`, `像人写的`, `自然流畅` | Rebuild formulaic structure and add a more distinctive voice. |

First inspect [Chinese AI clichés](references/chinese-ai-cliches.md), then apply the rules below. An older configuration mentions `references/content-patterns.md`, but that file is not included here; do not invent its rules. In heavy mode, also read [Voice and Soul](references/voice-and-soul.md).

Core rules:

1. Remove filler openings and emphasis crutches.
2. Break formulaic binary contrasts, dramatic segmentation, and rhetorical setups.
3. Vary sentence length; avoid repetitive three-part lists.
4. Trust the reader: state facts directly without needless hand-holding.
5. In medium or heavy mode, rewrite slogan-like lines that sound designed as quotations.

Self-check on five dimensions, each scored from 1 to 10: directness, rhythm, trust in the reader, human voice, and concision. A total of 45–50 is strong; 35–44 needs refinement; below 35 needs another pass.

## Mode B: Formal or Administrative Text

Use for official documents, reports, briefing notes, performance records, and work summaries. Preserve the formal register and required structure while improving grammar and logic.

**Before editing, ask the user to choose the intensity:**

1. Correct errors only: typos, grammar, and improper collocations.
2. Polish (recommended): correct errors, remove redundancy, and clarify logic.
3. Rewrite: preserve the formal register while restructuring the expression.

Do not exceed the chosen scope. At every intensity:

- Do not turn formal stock phrases into casual speech.
- Preserve required structures such as `一是……二是……三是……`.
- Do not remove ordinary administrative phrases such as `高度重视` or `扎实推进` unless clearly wrong.
- Do not automatically replace passive voice with active voice.
- Do not add personal views or emotion or lower the formality.

Example, intensity 2:

> Before: 通过积极努力地开展工作，在各项任务的完成方面取得了一定的成效，为下一步工作的顺利推进打下了良好基础。
>
> After: 各项任务稳步推进，为后续工作奠定了基础。

## Mode C: Marketing or Social-Media Copy

Use for social posts, public-account articles, promotional copy, and product descriptions. Keep persuasive intent while removing mechanical or excessive phrasing.

- Retain useful praise, recommendations, and calls to action.
- Remove empty adjective stacking; add concrete, real details where available.
- Improve rhythm with concise sentences; keep emoji when appropriate.
- Do not turn the copy into a news report, strip out all promotion, or make the voice too casual for the brand.

## File Handling

| File type | Method | Avoid |
|---|---|---|
| `.docx` | Use the available `docx` skill. | Do not treat it as plain text with `Read`. |
| `.txt`, `.md` | Use the text read/write tools. | Do not change unrelated files. |

For edited files, append `_润色版` to the output filename. Do not use an ad hoc Python script to manipulate the document or write code into a DOCX.

## Output

1. The revised Chinese text.
2. A brief summary of changes, if useful.

## References

- [Chinese AI clichés](references/chinese-ai-cliches.md): patterns in sentence structure, judgment, tone, vocabulary, and rhetoric.
- `references/content-patterns.md` is mentioned in the original configuration but is absent here.
- [Voice and Soul](references/voice-and-soul.md): perspective and voice in heavy rewrites.
