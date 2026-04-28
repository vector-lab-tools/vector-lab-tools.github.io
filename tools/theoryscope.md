---
layout: default
title: Theoryscope
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/theoryscope.svg" alt="" class="tool-icon-lg">
<div>
<h1>Theoryscope</h1>
<p class="object"><em>Tier:</em> single-model scope (beta). <em>Object:</em> a corpus of theoretical texts.</p>
<p><a href="https://github.com/vector-lab-tools/theoryscope">github.com/vector-lab-tools/theoryscope</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

Theoryscope maps a corpus of theoretical texts as a high-dimensional point cloud and asks renormalisation-group-style questions of it. The tool makes visible what critics have until now asserted intuitively. Claims like "Foucault, Deleuze, and Guattari really come down to X" are claims about RG flow toward a fixed point. Claims like "Habermas and Rorty look opposed but converge" are universality-class claims. Theoryscope lets these be posed and inspected against a corpus rather than only asserted from the critic's reading.

## Why Theoryscope

Manifold Atlas and Vectorscope both take a model as their object. Theoryscope extends the same critical posture to intellectual fields: the corpus of critical theory, the literature on AI ethics, a single theorist's output, a tradition across time. This is the move that lets the Vector Lab address not just the geometry of the machine but the geometry of the thought written about the machine. It opens a reflexive possibility: compare the eigendirections of a theoretical corpus against the eigendirections of a model trained on that corpus.

## Operations

Drawing on renormalisation group theory and linear algebra:

- **Eigendirection analysis.** Principal components of the corpus cloud are the eigendirections of the field. Unlike the oppositions practitioners name in their debates, these eigendirections are computed rather than asserted. They often do not match the debates as the debates are conducted. The tool makes visible the axes that actually structure variation, which may be orthogonal to the axes its participants think structure it.
- **Renormalisation-group flow.** Coarse-graining as a chosen operation on the corpus. RG flow is the trajectory of corpus points under successive coarse-grainings. Fixed points are positions invariant under further coarse-graining.
- **Universality classes.** Sets of starting positions that flow to the same fixed point. The critical value is twofold: identifying hidden affinities (positions that look opposed but converge) and hidden divergences (positions that look similar but diverge).
- **Meso-structure mapping.** Midscale structure in the corpus cloud that neither local density nor global axes alone capture.

## A corpus as an object

The tool operates on a corpus of theoretical texts. Each text (or passage, concept, author, tradition, depending on the grain) becomes a point in a high-dimensional embedding space produced by an open-weight embedding model. The corpus becomes a cloud of points. Theoryscope provides operations for inspecting the cloud's structure using language drawn from renormalisation group theory and linear algebra.

## Theoretical background

Theoryscope is the empirical instrument that follows from [*Renormalising Theory*](https://stunlaw.blogspot.com/) and the forthcoming *What Is Theory Space?*, and continues the genealogy established in Hessler's RG / deep-learning reading list together with Mehta and Schwab (2014) and Lin, Tegmark and Rolnick (2017). It operationalises the vocabulary: coarse-grain, observe flow, locate fixed points, classify universality. Applied to a corpus rather than a physical system or a neural network.

## Stack

Next.js frontend, FastAPI backend. Shared geometry library with the other scopes.

## Status

Beta, v0.8.0. Inspect, Flow, and Critique tabs are all complete (Phase 4A through 4D), and Phase 5A added the Corpus-vs-Model Probe, the reflexive operation that compares the eigendirections of a theoretical corpus against an open-weight model trained on related text. Recent additions include the Symmetry Breaking Map, Phase Diagram, Translated Corpus Probe, and the Relevant / Irrelevant Operator Spectrum on the Flow tab. See the repository for a per-operation status table.

## Siblings

[Vectorscope](/tools/vectorscope.html) treats model internals; Theoryscope treats a corpus. The reflexive move is comparing the two. [Manifoldscope](/tools/manifoldscope.html) characterises a single manifold, which could be a Theoryscope corpus map. [Manifold Atlas](/tools/manifold-atlas.html) works across models rather than across texts. [LLMbench](/tools/llmbench.html) reads the prose surface.
