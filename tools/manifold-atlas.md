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

The tool packages fifteen operations for the critical testing of vector-theoretic claims:

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

Each operation makes a theoretical claim empirically testable against the geometry a given model has learned.

## Theoretical background

Manifold Atlas follows from [*The Vector Medium*](https://stunlaw.blogspot.com/2026/03/the-vector-medium.html) and [*What Is the Manifold?*](https://stunlaw.blogspot.com/). The tool names operations after vector-theoretic concepts (negation gauge, hegemony compass, real abstraction test) rather than statistical generics, so the connection between theory and instrument is explicit.

## Stack

Next.js 16, React 19, TypeScript 5, Tailwind, Three.js. Talks to the major embedding APIs: OpenAI, Anthropic, Google, Hugging Face, Cohere, and local Ollama.

## Status

The most mature instrument in the Vector Lab. Fifteen operations live, editorial design system settled, currently at v1.0.3. In active use for research and teaching.

## Siblings

[Manifoldscope](/tools/manifoldscope.html) is anatomical on a single manifold; Atlas is cartographic across many. The two are complementary. [Vectorscope](/tools/vectorscope.html) opens the model internals that Atlas compares at the output. [Theoryscope](/tools/theoryscope.html) applies comparable methods to corpora of theory rather than models. [LLMbench](/tools/llmbench.html) handles the prose surface.
