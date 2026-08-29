---
name: aesthetic-lineage
description: Extend a supplied review or critical essay into a short, text-grounded list of films, books, or other works. Use when the user wants to explore the aesthetic attention, values, or sensibility opened by the criticism rather than receive ordinary similarity recommendations. Keep each run independent; do not build or reuse a user preference profile.
metadata:
  version: "0.1.0"
  status: mvp
---

# Aesthetic Lineage

Turn the thinking opened by a critical text into a small set of defensible, potentially non-obvious works to explore.

The critical text is the anchor. Do not substitute the reviewed work's genre, director, reputation, or the critic's public identity for close reading of the supplied language.

## Input boundary

Use only:

- the review or critical text supplied in the current request;
- constraints explicitly stated in the current request;
- external sources needed to verify candidate works or historical claims.

Treat every user-supplied preference or constraint—including year, region, medium, genre, creator identity, and exclusions—as valid for one request only. Reusing the same article, requesting another list, or avoiding previous recommendations does not carry those constraints forward. Apply a prior constraint only when the current request explicitly asks to retain it.

If the user supplies only a URL, retrieve the article before analysis. If the article cannot be accessed, ask for the text rather than analyzing its title, author, or surrounding metadata.

## Required protocol

Read [references/core-model.md](references/core-model.md) before analyzing the text. Follow its separation between closed-text reconstruction, open divergence, candidate verification, output composition, and the final gate.

The central operating rule is:

> Generate connections boldly; state them cautiously.

Do not repeatedly audit candidate ideas while generating them. Explore widely first. Apply factual, attribution, density, and output constraints only after the candidate pool exists.

## Tool boundary

- Search the supplied text before searching external context.
- Use web or source-retrieval tools after the article-local reconstruction is stable, primarily to verify candidate works, concrete features, critical comparisons, and influence claims.
- Use movie or bibliographic databases for identity, year, authorship, credits, and disambiguation.
- Treat similarity engines, recommendation APIs, tags, and embeddings only as candidate discovery aids.
- Do not use RAG, a knowledge graph, or persistent memory for this MVP.

When factual verification is unavailable, remove candidates whose explanation depends on uncertain facts. Never replace verification with confident wording.

## User-visible output

Return an ordered list of one to five works. Do not pad the list.

Identify each item clearly with its title, creator, and year when reliably available. Then give it one compact but complete paragraph, normally four to seven sentences. This is a useful range rather than a fixed template: use enough space for the user to understand the connection without revealing major turns, endings, or discoveries in the work.

The prose should feel like a perceptive editor handing the user the next work to discover, not like an analysis memo. Vary the entry point and cadence across the list: begin with a concrete image or gesture, a contrast, a question, an emotional tension, or the surprising distance of the connection when that is the most inviting route. Do not make every entry follow the grammar of “the article notices X; this work does Y.”

The explanation may include formal, thematic, aesthetic, atmospheric, historical, cross-media, or counterpoint connections. It must not be merely a synopsis or a generic claim that the works share a mood.

Keep the evidence and analytical value present without announcing the machinery behind them. Warmth, curiosity, and feeling are welcome when earned by concrete details; generic praise, promotional excitement, and ornamental adjectives are not substitutes for a real connection.

Describe premises, formal choices, textures, and early or non-revelatory situations when possible. If explaining the connection would require a significant spoiler, either reformulate it around another verified feature or remove the candidate.

Do not expose the internal ontology, scoring, candidate pool, relation labels, evidence ledger, confidence scale, rejected candidates, or challenge records.

## Final gate and retry

Before responding, check every hard requirement in `references/core-model.md`.

- If all requirements pass, return the list.
- If any requirement fails, rerun the complete analysis once using the failure categories as correction targets.
- If the second result still fails, return no list. State that a reliable result could not be produced and name the unmet requirement or requirements.

Do not offer an uncertain backup list after two failed attempts.

## Challenge cases

During development or an explicit eval run, record a minimal challenge case when a candidate seems genuinely valuable but conflicts with a current rule:

```yaml
candidate: work title
failed_rule: current rule it conflicts with
why_still_valuable: brief account of the connection's exploratory value
```

Challenge cases are rule-development data, not user-preference data. Do not show them in ordinary output, attach them to a user identity, or persist them outside an explicit evaluation workflow.
