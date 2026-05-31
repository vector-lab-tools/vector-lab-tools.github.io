---
layout: default
title: Manifold Atlas
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/manifold-atlas.svg" alt="" class="tool-icon-lg">
<div>
<h1>Manifold Atlas</h1>
<p class="object"><em>Tier:</em> comparative tool. <em>Object:</em> output embeddings across models.</p>
<p><a href="https://github.com/vector-lab-tools/manifold-atlas">github.com/vector-lab-tools/manifold-atlas</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

Manifold Atlas compares multiple embedding models' output geometries on the same inputs. It is the comparative cartographic instrument of the Vector Lab: the tool that operationalises vector theory empirically, turning what a model has learned about democracy, care work, negation, or intelligence into a testable geometry rather than a metaphor.

## Why Manifold Atlas

Without vector theory, a cosine similarity of 0.95 between "fair" and "not fair" is a curiosity. With it, the same number is evidence for the negation deficit, for geometric ideology, for the proprietary encoding of human language that a particular training regime has produced. Atlas lets claims of that kind be tested against the geometry directly, across multiple models on the same inputs, with outputs that are comparable and exportable.

## Operations

The tool packages sixteen operations for the critical testing of vector-theoretic claims:

- **Concept Distance.** Cosine similarity for two terms across enabled models, with angular separation, euclidean distance, vector norms, and top contributing dimensions.
- **Neighbourhood Map.** The local structure of the manifold around a concept, rendered as an interactive 3D scatter plot with cluster detection, connection mesh, and cross-domain analysis.
- **Negation Gauge.** A statement and its auto-generated negation, measured for similarity. How much space the manifold actually gives to negation.
- **Negation Battery.** Automatic runs of 10-40 negation tests, with report card, collapse rate, and CSV export.
- **Semantic Sectioning.** Interpolation between two anchor concepts to reveal what lies between them.
- **Concept Drift.** How context warps the manifold's positioning of a concept, visualised as a drift cloud.
- **Hegemony Compass.** A contested concept placed between two competing ideological clusters; which side does the manifold pull it toward?
- **Real Abstraction Test.** Contrasts a concrete use-value description with its abstract exchange-value equivalent, after Sohn-Rethel.
- **Silence Detector.** Local density across domains. Dense regions are low-resolution (diverse realities compressed); sparse regions are high-resolution (fine-grained distinctions preserved).
- **Distance Matrix.** A pairwise cosine similarity heatmap across concepts and models, with contested-geometry detection when multiple models are enabled.
- **Agonism Test.** Pre-loaded philosophical debates. Does the manifold preserve genuine opposition, or collapse it into proximity?
- **Vector Logic.** A − B + C = ?, the narrowest test of vector logic. Applied to modern embedding models with critical intent.
- **Vector Walk.** A particle walking through the manifold from one concept to another, built with Three.js.
- **Text Vectorisation.** Embedding and inspection of arbitrary text.
- **Grammar of Vectors.** A critique-tier operation that maps discursive quirks of LLM prose onto cosine geometry. Ships with two antithesis patterns ('Not X but Y' and 'Not just X but Y') across four register batteries (Marketing, AI pedagogical, Political op-ed, Technology discourse), ninety-six curated constructions in total. Cosines are reported with observation-only labels rather than interpretive verdicts: the tool surfaces the geometric relationship for the reader to interpret, leaving the call about whether a given construction performs genuine opposition or a near-neighbour rotation to the analyst.

Each operation makes a theoretical claim empirically testable against the geometry a given model has learned.

## Test library and standardisation

Each operation ships with a curated library of pre-built tests. These form a stable instrument against which any model can be measured, and against which models can be compared to each other. Because the tests are fixed, the same battery can be fired at different models at the same moment, at the same model across versions of its embedding API, or at the same model across dates. The result is a standardised testing regime that lets findings be reproduced across research groups and held durable across model generations.

### The library

Representative items in the library:

- **Hegemony Compass:** pre-loaded tests for Freedom (market liberalism vs emancipatory politics), Democracy (liberal proceduralism vs radical democracy), Intelligence (techno-rationalism vs embodied cognition), Security, and Progress. A new **Hegemonic Defaults Sweep** test (research tier) runs three axis presets in one go, Political Compass (economic-left / right, libertarian / authoritarian), Technology Compass (commons / proprietary, human-centred / techno-solutionist), and Knowledge Compass (critical / empiricist, qualitative / quantitative), followed by a pairwise Distance Matrix over an 18-concept political vocabulary.
- **Negation Battery:** pre-built sets for political claims, ethical statements, factual assertions, and epistemological claims, runnable 10-40 at a time.
- **Agonism Test:** forty-eight pre-loaded philosophical debates organised in eight themes (six pairs per theme) including Marx vs Burke, Hegel vs Kierkegaard, and Arendt vs Schmitt, with thematic filtering and observation-only labels rather than interpretive verdicts.
- **Real Abstraction Test:** twelve concrete use-value to abstract exchange-value pairs after Sohn-Rethel, across domains from clothing to care work.
- **Silence Detector:** density comparisons across contested domains, such as financial derivatives vs subsistence farming, Silicon Valley vs indigenous ecological knowledge, and corporate management vs care work.
- **Vector Logic:** pre-loaded analogies including ‘capitalism minus exploitation plus cooperation equals ?’
- **Neighbourhood Map and Vector Walk:** curated concept sets across Philosophy, Carpentry, Critical Theory, Democracy, and other domains, with eight distant-pair presets for walks.

### Tests

Tests bundle operations into named sequences, runnable in one click and exportable as a single composite dataset. Eight tests ship with the current version:

- **Grammar of Vectors Sweep** (research). Both launch grammars ('Not X but Y' and 'Not just X but Y') across all four register batteries, around a hundred pairs per model per run. Empirical backbone for the Grammar of Vectors argument on synthetic dialectic in LLM prose.
- **Hegemonic Defaults Sweep** (research). Three Hegemony Compass probes plus a Distance Matrix over eighteen political concepts. Tests which ideological framings the manifold has naturalised as defaults.
- **'Fake' News Test** (research). All four pre-built batteries plus the eight-pair Agonism Test, ninety-six claim-and-counter-claim tests per model. Exposes the structural condition behind the fake-news problem, a medium whose geometry cannot sustain truth-and-falsehood.
- **Political Contestation Test** (research). Ten steps mixing Concept Distance, Semantic Sectioning, and Negation Gauge across politically contested pairs.
- **Vector Logic Test** (research). Six A − B + C analogical inferences run in one batch, each producing a per-model top-eight nearest-concept table.
- **Negation Audit** (critique). Ethical battery, three contested-claim gauges, and the full agonism battery. Establishes the negation deficit empirically and at scale.
- **Concept Distance Demo** and **Vector Logic Demo** (demos). Minimal runs intended as working demonstrations of the pipeline.

Users can also author their own tests as markdown files with YAML front matter, persisted in localStorage and round-trippable through a text editor.

### Testing across models and versions

Atlas runs any test against any combination of enabled embedding models. Supported providers cover OpenAI, Anthropic, Google, Hugging Face, Cohere, and local Ollama. The Distance Matrix operation, running across multiple enabled models at once, flags the pairs where models most disagree, surfacing contested geometry for critical analysis.

### Export and archive

Operations export to CSV, JSON, PDF, or PNG depending on the visualisation. Exports carry enough metadata (model identifier, date, test preset, parameter values) to reconstruct the run. These exports form the raw material for a longitudinal, comparative archive, a historical resource documenting how large language models have encoded contested concepts over time. Rather than a single ephemeral run against a single version of a single model, findings can be accumulated into a durable record.

## Theoretical background

Manifold Atlas follows from [*The Vector Medium*](https://stunlaw.blogspot.com/2026/03/the-vector-medium.html) and [*What Is the Manifold?*](https://stunlaw.blogspot.com/). The tool names operations after vector-theoretic concepts (negation gauge, hegemony compass, real abstraction test) rather than statistical generics, so the connection between theory and instrument is explicit.

## Stack

Next.js 16, React 19, TypeScript 5, Tailwind, Three.js. Talks to the major embedding APIs: OpenAI, Anthropic, Google, Hugging Face, Cohere, and local Ollama.

## Status

The most mature instrument in the Vector Lab. Currently at v1.8.0, with sixteen operations live and a deep-dive panel on every visualisation-heavy operation. The recent line of work runs: browser-direct Ollama so the deployed Atlas can reach a local Ollama instance for real (v1.6.0, with origin-aware setup help and Gemma models added in v1.5.3 and structured CORS error handling in v1.6.1–v1.6.2); a Negation Gauge "Not A" override (v1.6.3); a Neighbourhood Map fix that suppresses misleading single-group cross-domain bridges (v1.6.4); and a methodological shift on the critique-tier operations to observation-only labels rather than interpretive verdicts, with the Agonism Test expanded to forty-eight pairs across eight themes (v1.6.5–v1.6.8). v1.7.0 removed the LLMbench Grammar Probe Bundle handover (the two tools operate on different manifolds, so the round-trip claim was misleading); v1.8.0 is the release marker on top of that decision. Earlier recent work also includes the Grammar of Vectors operation, Deep Dive Phase 5 enrichment (v1.4.0–v1.4.2), a sticky bottom status bar, and Getting Started help. In active use for research and teaching.

## Siblings

[Manifoldscope](/tools/manifoldscope.html) is anatomical on a single manifold; Atlas is cartographic across many. The two are complementary. [Vectorscope](/tools/vectorscope.html) opens the model internals that Atlas compares at the output. [Theoryscope](/tools/theoryscope.html) applies comparable methods to corpora of theory rather than models. [LLMbench](/tools/llmbench.html) handles the prose surface.
