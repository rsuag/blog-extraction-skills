---
name: changwen-tilian
description: "Distill a podcast transcript, blog post, or long article into one Chinese-language blog digest with main content, new and important ideas, a mind map, transferable lessons, information bullets, related knowledge, and a final glossary. Use when the user asks to distill long-form material, extract key ideas or information bullets, build a mind map, identify transferable knowledge, or explain technical terms. Not for a short summary, pure translation, or format conversion."
---

# Long-Form Content Distillation

Turn a podcast transcript, blog post, or long article into **one complete blog digest**. Do not split the same source into separate information-bullet and content-report files. Put all analysis, bullets, mind map, transferable knowledge, and glossary in one Markdown file. Also export a PDF with the same base name by default; the PDF must include the mind map.

## Input

The user may supply a podcast transcript, a full article or blog post, or a video transcript. Speaker labels are optional. Source length and language are unrestricted. **The output is always in Chinese.**

## Output

Produce one Markdown file and one PDF by default:

- `{slug}_博客提炼.md`
- `{slug}_博客提炼.pdf`

The PDF must contain the core Markdown content, especially the `思维导图` and `专业名词解释` sections. Use this structure:

```markdown
# {标题}｜博客提炼

## 主要内容

- ...

## 新的和重要的观点

- **观点**：...
  **为什么重要**：...

## 思维导图

- 中心主题
  - 分支
    - 子分支或例子

## 可执行可迁移的知识和智慧

- **原则/方法**：...
  **可迁移场景**：...
  **怎么用**：...

## 信息子弹

- ...

## 相关知识串联

- ...

## 专业名词解释

- **术语**：先用一句人话解释，再补必要背景。
```

`专业名词解释` must be the final top-level section. Do not append a conclusion, disclaimer, or trailing note.

## Information-Bullet Standard

- **Self-contained:** Each bullet is a complete unit of thought that makes sense without surrounding context. It normally includes a claim, supporting fact or reasoning, and a closing thought.
- **Length:** Write a substantial paragraph of roughly five to eight sentences, not a one-line fragment or a list of labels.
- **Rhythm:** Use Chinese full stops (`。`) as the main internal separator. Commas create short pauses; semicolons are occasional. Vary sentence lengths instead of stretching one sentence indefinitely.
- **Ending:** Many bullets should close with a crisp judgment, reversal, or concrete image. Do not force this in every bullet.
- **Count:** Let the source's information density determine the number of bullets. Merge repetitions rather than padding.
- **Order:** Follow the source's narrative roughly, but prioritize logical flow. Combine related points scattered across the source.

## Voice: Cool Essay

- **Literary, not academic:** Use complete sentences and some complex syntax without sounding stiff. An occasional conversational ending, question, or dark joke is acceptable.
- **Observant, with a perspective:** Use frameworks, analogies, and data to locate a point of view without explicit value judgments.
- **Third-person observer:** Reorganize the material for readers rather than retelling who said each line.

## Subject Rule

**Omit the grammatical subject by default and state the point directly.**

- Begin many paragraphs with the idea itself.
- Name a person only when the fact depends on that person's identity or action, or when preserving a direct quotation.
- Rarely use `我`, even if the user participated in the podcast.
- Do not guess when the speaker is unclear; state the idea instead.
- Avoid generic attribution such as `嘉宾认为`, `主播提到`, `有人指出`, `文章指出`, or `据报道`.

## Data Anchors and Explanatory Links

Preserve concrete numbers, names, companies, and dates. Distillation removes filler, not evidence. You may add a very thin explanatory link to make an existing causal relationship clear, but do not turn that link into a new fact or let it dominate the source.

## Added Material and Quotations

- You may restate with metaphor or analogy if meaning stays the same.
- Add external facts, data, or examples only when reliable and genuinely useful; identify their source naturally.
- Never invent details, data, or cases from memory.
- Preserve at most three to five especially effective original lines as marked quotations. Exclude catchphrases and transitions.

## Transcript Handling

- Remove spoken ads, show promotion, opening pleasantries, and empty mutual praise.
- Remove filler words, repetitions, unfinished sentences, and back-channel agreement such as `对对对`.
- When several speakers repeat a point, keep its clearest or strongest version.
- Skip digressions unless they contain a valuable idea.

## Section Standards

### Main Content

Report the actual topics, facts, questions, and conclusions discussed. Each entry needs information; avoid empty framing such as `本期围绕某某展开讨论`.

### New and Important Ideas

“New” means an addition to common knowledge or a clearer frame for a familiar issue. “Important” means it may change a judgment, choice, or action. Explain why each point matters.

### Mind Map

Use a Markdown hierarchy with one central topic and as many branches as the material warrants. Do not force symmetry. The PDF must preserve this map, either as a hierarchy or a clear tree.

### Transferable Knowledge

Derive reusable principles, methods, checklists, or decision frameworks. Explain what each is and how to use it. When it cannot become a direct action, give a decision criterion.

### Information Bullets

Keep the bullets inside the single digest file. Each remains a self-contained paragraph in the cool-essay voice, with sentence-level rhythm and a strong ending where appropriate.

### Related Knowledge

Check for meaningful connections to earlier processed podcasts, blogs, industry concepts, methods, or investment frameworks. Explain what is shared, what the new material adds or corrects, what should be read together, and where the idea transfers. Do not force a connection without a common mechanism or variable.

### Glossary

Place `专业名词解释` at the very end. Explain each term briefly for a non-specialist: first in plain language, then its role in this piece. Do not define jargon with jargon or pile up English abbreviations; when one is needed, give its Chinese meaning.

### Boundary

Do not present information absent from the source as fact. Light abstraction is acceptable only when it remains traceable to the transcript or article.

## Workflow

1. Read the whole source before writing; identify the topic, central claims, and their relationships.
2. Mark material for each required section, including terms that need explanation.
3. Write one digest in one Markdown file.
4. Review every bullet for independence, information density, minimal subject use, preserved data anchors, no unverified additions, and narrative flow. Check that the glossary is last and the PDF includes the mind map.
5. Apply `humanizer-zh` in mode A at medium intensity, then recheck this skill's subject rule, full-stop rhythm, endings, and clear glossary.
6. After validating the Markdown and PDF, remove unnecessary intermediate audio, temporary HTML, screenshot caches, raw JSON, and superseded split drafts created during this task.

## Do Not

- Split one source into multiple digest Markdown files.
- Move the glossary into the body or deliver a PDF without the mind map.
- Keep intermediate files that are no longer needed.
- Add empty introductions or conclusions such as `本期播客讨论了...` or `综上所述...`.
- Append generic commentary such as `这一点值得深思` to a bullet.
- Give every speaker equal space regardless of information density.
- Copy the source's sentence structure or overload a sentence that should end with a full stop.
