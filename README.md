# Aesthetic Lineage Skill

从一篇影评或评论出发，沿着作者的观察和表达方式，找到几部值得继续探索的电影、书籍或其他作品。它不是普通的“相似推荐”，而是试着找出作品之间更具体、可解释的审美联系。

Aesthetic Lineage turns a review or critical essay into a short, text-grounded path toward films, books, and other works. Instead of asking *what might you like next?*, it asks:

> What does this criticism notice, and which works could extend, reverse, or complicate that way of seeing?

It reconstructs the critic's concrete observations—about form, action, emotion, tension, and value—then finds works that can answer them. Each result connects what the original work does, how the critic understands it, and how another work illuminates the same problem from a different direction.

## Why use it?

- **Recommendations continue the criticism.** Reasons come from the supplied text, not broad genre labels or a guessed taste profile.
- **Connections can be surprising without becoming arbitrary.** Works may meet through form, aesthetic value, atmosphere, history, or contrasting answers to the same question—not only through plot or genre.
- **The relationship is already organized.** The reader does not have to reconstruct why the original work, the criticism, and the recommendation belong together.
- **Claims remain inspectable.** Textual evidence, work-specific features, critical comparison, inference, and documented influence are not treated as interchangeable.
- **The list stays selective.** Each run returns one to five works rather than transferring the filtering burden back to the user.
- **Each run begins with the current text.** Temporary constraints from earlier requests do not become a persistent preference profile.

## Same titles, different work

In a development-stage blind A/B test, a standard recommendation prompt and Aesthetic Lineage both began with a review of *She Said*. Both selected *Sorry, Baby* and *Black Box Diaries*, making the comparison less about choosing different titles than about what the recommendation helps the reader understand.

| Work | Standard prompt | Aesthetic Lineage |
| --- | --- | --- |
| *Sorry, Baby* | Described it as a smaller, more private story about everyday life after sexual assault. | Began with the review's attention to motherhood, fatigue, and professional labor in *She Said*. It then framed *Sorry, Baby* as a reverse extension: where one film follows testimony becoming public consequence, the other asks how a survivor reclaims time after institutions fail to provide a satisfying response. Its nonlinear time, dark humor, and pauses become formal choices, not just stylistic traits. |
| *Black Box Diaries* | Presented it as a Japanese real-world counterpart to *She Said*, emphasizing the journalist's overlapping roles as survivor, witness, and investigator. | Connected those roles to the review's emphasis on ordinary investigative labor: filing reports, locating witnesses, requesting documents, and confronting redactions. It then brought in the conflict among footage rights, source privacy, and public interest, treating testimony as a film form with real ethical costs rather than simply the correct subject. |

> A standard recommendation explains why works are similar. Aesthetic Lineage explains how they respond to a specific problem in the criticism—and lets the recommendation deepen the reading of both the work and the review.

This is not a fixed output template. A recommendation may begin with an image, a formal device, a contradiction, a question, or a cross-media connection. What remains stable is the requirement that every result grows from a concrete observation in the current text and makes the relationship clear, credible, and worth exploring.

## Installation

Download the [`aesthetic-lineage`](aesthetic-lineage/) directory and place it in the personal or project skills directory used by an Agent Skills-compatible tool.

- Codex: install as `~/.codex/skills/aesthetic-lineage/`. Relevant requests can trigger it automatically; `$aesthetic-lineage` remains available for explicit use.
- Claude Code: install as `~/.claude/skills/aesthetic-lineage/` and invoke with `/aesthetic-lineage`.
- Other compatible agents may use a different skills directory or invocation syntax. The portable instructions are in [`SKILL.md`](aesthetic-lineage/SKILL.md) and [`core-model.md`](aesthetic-lineage/references/core-model.md); [`agents/openai.yaml`](aesthetic-lineage/agents/openai.yaml) is Codex-specific.

## Basic use

```text
Extend the following review into works worth exploring:

[paste the review or critical essay]
```

Explicit invocation remains available with `$aesthetic-lineage`.

## Strict preference reset

The Skill treats user preferences and constraints as request-scoped. Long conversations can still anchor a model toward earlier years, regions, media, genres, creator identities, exclusions, or recommendation neighborhoods. When strict preference isolation matters, prepend one of the following instructions to the request.

```text
忽略本次对话中此前出现的所有偏好和限制，包括年份、地区、媒介、类型、创作者身份和排除条件。只使用本条消息明确给出的限制；如果本条没有给出限制，则将本次分析视为完全不受限制。
```

```text
Ignore all preferences and constraints from earlier turns, including year, region, medium, genre, creator identity, and exclusions. Use only constraints stated in this message; if none are stated, treat this run as unconstrained.
```

Starting a new conversation remains the strongest option when complete context isolation is required.
