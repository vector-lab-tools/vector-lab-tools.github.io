---
layout: default
title: Manifoldscope
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/manifoldscope.svg" alt="" class="tool-icon-lg">
<div>
<h1>Manifoldscope</h1>
<p class="object"><em>Tier:</em> single-model scope (beta). <em>Object:</em> a single manifold.</p>
<p><a href="https://github.com/vector-lab-tools/manifoldscope">github.com/vector-lab-tools/manifoldscope</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

Manifoldscope treats a single manifold, understood as an embedding output together with its sampling, as both a geometric object and an ideological object. It measures shape (intrinsic dimension, curvature, density, topology) and reads the same manifold critically, asking what it naturalises, what it suppresses, what it sediments, what it refuses to represent. Every critique is backed by a measure attestation. The instrument binds the two registers.

## Why Manifoldscope

The other Vector Lab instruments each have a clear object: models compared (Atlas), model internals (Vectorscope), corpus as geometry (Theoryscope), prose outputs (LLMbench). None treats a single manifold *as manifold*: as an intrinsic mathematical and political object characterisable in its own right. Atlas tests claims on the manifold; Manifoldscope characterises the manifold that the claims stand on. Manifoldscope also produces the provenance layer that strengthens Atlas's critical claims. A finding like "democracy sits closer to market-liberalism than to radical democracy" gains defensibility when an independent instrument has already attested the local intrinsic dimension, curvature, and sampling density of that region.

## Two registers, one instrument

Every operation in Manifoldscope can be asked in either key:

- **Measure.** Intrinsic geometry. Intrinsic dimension, curvature, geodesic structure, density field, topological invariants, projection distortion, sampling bias. The posture is descriptive, the outputs geometric.
- **Critique.** Critical-theoretical investigation of the same manifold as an ideological object. What it naturalises, what it marginalises, what it sediments, what it refuses. The posture is interpretive, the outputs readings backed by geometric evidence.

## Operations

Manifold-wide and systematic rather than pointwise:

- **Intrinsic dimension field.** Local ID at every sampled point, rendered as a heatmap on the projection. The manifold is not uniformly N-dimensional; the map shows where it is not.
- **Curvature estimation.** Ollivier-Ricci on the discrete graph; sectional-curvature proxies. Shape claims with a shape instrument behind them.
- **Density and sampling bias.** Local density as a critical variable. Dense regions are low resolution (diverse realities compressed into few coordinates); sparse regions are high resolution (fine-grained distinctions preserved).
- **Ideological topography.** Reads the manifold critically as a political object.
- **Archaeology of absence.** What is not here, and what the geometry of the absence looks like.
- **Colonial geometry probe, market-colonisation index, grammatical ideology, dissensus detector.** Manifold-wide probes that cannot be reduced to pointwise tests.

## What counts as "a single manifold"

An embedding output plus its sampling. Could be:
- The OpenAI `text-embedding-3-large` manifold queried with 5,000 concepts.
- A nomic-embed-text manifold queried with a Zotero corpus.
- An exported Vectorscope hidden-state cloud from a specified layer of a specified model.
- A Theoryscope corpus map under a specified embedder.

The instrument is sampling-aware throughout; the sample is part of the manifold.

## Theoretical background

Manifoldscope continues lines developed in Berry's [*Vector Theory*](https://doi.org/10.1007/s13347-026-01162-w) (*Philosophy & Technology*, 2026), the Stunlaw essay [*What Is Vector Space?*](https://stunlaw.blogspot.com/2026/03/what-is-vector-space.html), and the *AI Critical Theory* book in progress. The manifold as medium shaped by capital, the geometry as ideology topologically encoded, the real abstraction performed at the level of meaning, the negation deficit, the taxonomy of silence: Manifoldscope is the empirical arm that takes those claims from illustration to sustained systematic investigation.

## Stack

Next.js frontend, FastAPI backend. Shares the geometry library with the other scopes.

## Status

Concept and prototype stage. The operations listed above are the proposed set; individual probes are at varying stages of implementation.

## Siblings

[Manifold Atlas](/tools/manifold-atlas.html) is cartographic and comparative; Manifoldscope is anatomical on one terrain. [Vectorscope](/tools/vectorscope.html) produces the kinds of manifolds Manifoldscope characterises. [Theoryscope](/tools/theoryscope.html) applies the same critical posture to corpora of theoretical texts. [LLMbench](/tools/llmbench.html) handles the prose surface.
