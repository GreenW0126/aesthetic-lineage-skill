# Aesthetic Lineage Skill

A text-grounded Agent Skill that extends a supplied review or critical essay into a short list of films, books, or other works. It is designed to follow the article's particular way of seeing rather than produce ordinary similarity recommendations.

The Skill keeps formal, thematic, aesthetic, atmospheric, historical, and model-inferred connections distinct. Recommendations are limited to one to five works, explained without major spoilers, and checked for factual and attribution accuracy.

## Installation

Download the [`aesthetic-lineage`](aesthetic-lineage/) directory and place it in the personal or project skills directory used by an Agent Skills-compatible tool.

- Codex: install as `~/.codex/skills/aesthetic-lineage/` and invoke with `$aesthetic-lineage`.
- Claude Code: install as `~/.claude/skills/aesthetic-lineage/` and invoke with `/aesthetic-lineage`.
- Other compatible agents may use a different skills directory or invocation syntax. The portable instructions are in [`SKILL.md`](aesthetic-lineage/SKILL.md) and [`core-model.md`](aesthetic-lineage/references/core-model.md); [`agents/openai.yaml`](aesthetic-lineage/agents/openai.yaml) is Codex-specific.

## Basic use

```text
$aesthetic-lineage

Extend the following review into works worth exploring:

[paste the review or critical essay]
```

## Strict preference reset

The Skill treats user preferences and constraints as request-scoped. Long conversations can still anchor a model toward earlier years, regions, media, genres, creator identities, exclusions, or recommendation neighborhoods. When strict preference isolation matters, prepend one of the following instructions to the request.

```text
忽略本次对话中此前出现的所有偏好和限制，包括年份、地区、媒介、类型、创作者身份和排除条件。只使用本条消息明确给出的限制；如果本条没有给出限制，则将本次分析视为完全不受限制。
```

```text
Ignore all preferences and constraints from earlier turns, including year, region, medium, genre, creator identity, and exclusions. Use only constraints stated in this message; if none are stated, treat this run as unconstrained.
```

Starting a new conversation remains the strongest option when complete context isolation is required.
