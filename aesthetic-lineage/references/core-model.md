# Aesthetic Lineage MVP Protocol

Use this protocol for every run. Internal structures guide analysis but are not user-visible.

## 1. Closed-text reconstruction

Analyze the supplied critical text before retrieving external context. The goal is to reconstruct an article-local aesthetic structure, not the critic's permanent worldview and not the reviewed work's accepted place in history.

Build a compact internal chain from:

```text
TextSpan → RhetoricalMove → AttentionObject → Evaluation → AestheticProposition
```

### TextSpan

A locatable phrase, sentence, or passage from the current text. All article-side claims must resolve to one or more spans.

### RhetoricalMove

What the critic is doing with the language: describing, comparing, negating, conceding, questioning, quoting, paraphrasing, using metaphor, shifting scale, or moving from observation to judgment.

Distinguish the critic's position from quotation, reported speech, irony, rhetorical questions, and views introduced only to be rejected.

### AttentionObject

What the critic chooses to notice: duration, silence, gesture, framing, syntax, narrative omission, performance opacity, material texture, moral judgment, spatial relation, repetition, excess, restraint, or another concrete object of attention.

### Evaluation

How the text values the observed feature: approval, rejection, ambivalence, suspicion, conditional acceptance, or unresolved tension. Description alone does not prove approval.

### AestheticProposition

A local hypothesis about what the article treats as artistically valuable, deficient, possible, or worth noticing. Support it with multiple spans when possible. Phrase it as a claim about this article, not a stable fact about the critic.

Do not decide whether the critic is correct. Do not begin from a movement, genre, director, or theoretical label and force the text into it.

## 2. Open divergence

After the article-local reconstruction is stable, generate a broad candidate pool without applying the final gate candidate by candidate.

Explore freely across:

- close formal correspondences;
- themes treated through different forms;
- aesthetic or atmospheric affinities;
- analogous functions across media;
- distant historical or cultural contexts;
- works that answer the same problem differently;
- counterexamples that illuminate the article's proposition;
- documented lineage, influence, or critical comparison;
- connections proposed by the model that are not part of established art-historical groupings.

These are prompts for divergence, not quotas or required categories. Do not force diversity and do not avoid a famous work when it is genuinely the strongest connection.

Prefer candidates whose relevance depends on the article's particular way of seeing, not merely on the reviewed work's plot, genre, director, country, period, or existing recommendation neighborhood.

Innovation is a primary objective. Among candidates that can later pass the hard gate, favor connections that are non-obvious, explanatory, and difficult to obtain from conventional lists or art-history taxonomies.

## 3. Internal connection model

Keep two axes separate.

### Connection content

- `FORMAL_AFFINITY`: specific formal features or operations correspond.
- `THEMATIC_AFFINITY`: the works organize a related problem or motif.
- `AESTHETIC_AFFINITY`: multiple features converge on a related artistic value.
- `ATMOSPHERIC_AFFINITY`: a comparable felt quality is produced by identifiable features.
- `COUNTERPOINT`: the work clarifies the article by answering its problem differently or oppositely.
- `HISTORICAL_LINEAGE`: a historically supported path connects the works, traditions, or concepts.

### Epistemic basis

- `DOCUMENTED_INFLUENCE`: explicit creator testimony, archival evidence, or reliable scholarship supports directional influence.
- `CRITICAL_COMPARISON`: an identifiable critic or source explicitly compares the works.
- `SOURCE_SUPPORTED`: reliable sources support the relevant facts or historical context.
- `MODEL_INFERENCE`: the connection is an interpretive proposal grounded in the text and verified work features, but is not externally documented as a lineage.

The two axes may combine. A connection can be `FORMAL_AFFINITY` with a `MODEL_INFERENCE` basis. High confidence never converts resemblance into influence.

Mood or atmosphere is allowed as an exploratory connection. It must become specific enough to show how the article and candidate work produce or describe that quality.

## 4. Candidate verification

Verify only after generating the candidate pool.

### Article-side truth

- The stated tendency is present in the supplied text.
- The explanation does not invent quotations, observations, or evaluations.
- Quotation, irony, negation, concession, and reported views are attributed correctly.
- The explanation is not derived primarily from the article title, reviewed work metadata, critic identity, or a public label attached to either.

### Work-side truth

- The work exists and is correctly identified.
- Creator and year are accurate when shown.
- The concrete feature used in the explanation is genuinely present in the work or supported by a reliable source.
- A plot summary, database tag, recommender result, or broad genre label does not by itself establish the correspondence.

Remove a candidate when its value depends on a feature that cannot be verified. Verification should improve factual precision, not collapse the pool toward only canonical or easily searchable works.

## 5. Attribution discipline

Use language proportionate to the evidence.

- Similar form, theme, atmosphere, chronology, geography, or movement membership does not establish influence.
- `DOCUMENTED_INFLUENCE` requires a locatable creator statement, archival record, or reliable scholarly claim addressing the direction of influence.
- `HISTORICAL_LINEAGE` requires a supported transmission path, shared institution, pedagogy, circulation context, collaboration, or recognized tradition. Chronology alone is insufficient.
- `CRITICAL_COMPARISON` records that a critic made a comparison; it does not prove influence.
- `MODEL_INFERENCE` may be highly valuable. Describe it as resonance, correspondence, an illuminating comparison, or an exploratory extension rather than historical fact.
- When scholarship is unsettled, prefer bounded language such as “can be read alongside,” “forms a useful correspondence,” or “offers a distant extension.”

## 6. Selection and composition

Select one to five verified works. Do not fill a quota.

Rank primarily by closeness to the article-local aesthetic structure. When two candidates are comparably grounded, prefer the one with greater exploratory or explanatory value.

Each explanation must contain:

1. a concrete article-side finding;
2. a concrete work-side correspondence;
3. the value of following that connection.

These are informational ingredients, not a visible sentence pattern. They may be braided together in any order. Do not give every entry the same opening, argumentative sequence, sentence count, or rhetorical rhythm.

Use one compact but complete paragraph, normally four to seven sentences, so the relation can unfold rather than merely be asserted. Open through a precise image, gesture, contrast, question, emotional stake, or unexpected leap when it makes the connection easier to feel. Write with the ease and curiosity of a perceptive recommendation, while retaining the specificity of criticism.

Avoid major plot turns, endings, concealed identities, and revelations. Prefer premises, formal choices, recurring textures, and early or non-revelatory situations. If the connection cannot be explained meaningfully without a spoiler, find another verified basis or remove the candidate.

A synopsis, reputation statement, string of aesthetic adjectives, generic “similar atmosphere” description, or repeated “the article says X; the work does Y” scaffold fails even when factually correct. Do not manufacture enthusiasm with vague superlatives; emotional force must arise from the details of the connection.

Use natural prose. Do not display internal terminology unless the user explicitly asks for methodology.

## 7. Hard output gate

The proposed response passes only if every item below is true:

- [ ] The list contains one to five works and is not padded.
- [ ] Every item includes title, creator, year when reliably available, and a concise explanation.
- [ ] Every article-side statement is grounded in the current supplied text.
- [ ] Every recommended work and described feature is real and sufficiently verified.
- [ ] Every explanation makes a specific correspondence rather than relying on tags or generic mood words.
- [ ] Every explanation provides analytical information beyond synopsis.
- [ ] Every explanation is substantial enough to make the relation intelligible without relying on spoilers.
- [ ] The entries do not repeat a mechanical explanatory template or identical rhetorical sequence.
- [ ] The language is fluid and inviting while remaining specific, information-dense, and factually grounded.
- [ ] Influence and art-historical claims use evidence-proportionate language.
- [ ] The response does not expose internal schemas, labels, scores, candidate pools, or challenge records.
- [ ] The response does not use a preference from an earlier request unless the user explicitly repeated it in the current request.

If the first result fails, rerun the entire protocol once, targeting the failed categories. If the second result fails, return no works and identify the unmet categories.

## 8. Minimal challenge record

In an explicit development or eval context, record a candidate that appears valuable but conflicts with a current rule:

```yaml
candidate: work title
failed_rule: concise rule identifier or description
why_still_valuable: one short explanation
```

Do not reward challenge volume. A useful challenge is specific, factually plausible, and capable of revealing a missing relation, an over-broad restriction, or a verification limitation. Ordinary uncertainty, fabricated facts, and vague novelty are not useful challenges.

Do not persist challenge records during ordinary use.
