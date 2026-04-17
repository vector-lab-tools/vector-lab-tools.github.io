---
layout: default
title: Vector Lab
---

<div class="hero">
  <h1>Vector Lab</h1>
  <p class="tagline">Research instruments for critical vector theory.</p>
</div>

<section class="intro">

Vector Lab is a family of tools that make the internal geometry of large
language models, the comparative structure of embedding spaces, and the
topography of theoretical corpora legible as objects of empirical and
critical analysis. The instruments share a design language and a
commitment: geometry is not neutral, and the critical humanities need
instruments of their own.

</section>

## The family

The lab has two tiers. The inner tier opens up a single object for
intensive inspection. The outer tier compares across objects and supplies
the raw material those inspections sit on.

<div class="mermaid">
graph TB
  subgraph scopes["Single-object scopes (intensive)"]
    T[Theoryscope<br/><i>corpus</i>]
    V[Vectorscope<br/><i>model internals</i>]
    M[Manifoldscope<br/><i>one manifold</i>]
  end

  subgraph comparative["Comparative instruments (extensive)"]
    A[Manifold Atlas<br/><i>between models</i>]
    L[LLMbench<br/><i>between prose outputs</i>]
  end

  V -.provenance.-> M
  M -.provenance.-> A
  A -.surface reading.-> L
  T -.eigendirections of theory.-> V

  classDef scope fill:#1a1a1a,stroke:#d4af37,color:#f5f5f0,stroke-width:1px;
  classDef comp fill:#1a1a1a,stroke:#8b3a3a,color:#f5f5f0,stroke-width:1px;
  class T,V,M scope;
  class A,L comp;
</div>

### Single-object scopes

<div class="tools-grid">

<article class="tool-card scope">
  <h3><a href="https://github.com/vector-lab-tools/vectorscope">Vectorscope</a></h3>
  <p class="object">Object: a single open-weight model.</p>
  <p>Layer-by-layer weights, hidden states, attention, precision regimes.
  The anatomical instrument of the lab.</p>
</article>

<article class="tool-card scope">
  <h3><a href="https://github.com/vector-lab-tools/manifoldscope">Manifoldscope</a></h3>
  <p class="object">Object: a single manifold.</p>
  <p>Intrinsic dimension, curvature, density, topology, and the political
  reading of what a geometry sediments or refuses. Measure and critique
  bound together.</p>
</article>

<article class="tool-card scope">
  <h3><a href="https://github.com/vector-lab-tools/theoryscope">Theoryscope</a></h3>
  <p class="object">Object: a corpus of theoretical texts.</p>
  <p>Renormalisation-group flow, eigendirections, fixed points,
  universality classes. A navigable geometry of theory space.</p>
</article>

</div>

### Comparative instruments

<div class="tools-grid">

<article class="tool-card comparative">
  <h3><a href="https://github.com/vector-lab-tools/manifold-atlas">Manifold Atlas</a></h3>
  <p class="object">Object: output embeddings across models.</p>
  <p>Concept distance, negation gauge, hegemony compass, silence detector,
  agonism test, vector logic. The comparative cartographic instrument.</p>
</article>

<article class="tool-card comparative">
  <h3><a href="https://github.com/vector-lab-tools/LLMbench">LLMbench</a></h3>
  <p class="object">Object: generated prose across models.</p>
  <p>Dual-panel close reading, annotation, logprobs, probability
  visualisation. The hermeneutic surface instrument.</p>
</article>

</div>

## How the instruments relate

- **Vectorscope and Manifoldscope** share provenance: Vectorscope explains
  the internal geometry; Manifoldscope characterises a single manifold in
  its own right, often produced by a Vectorscope-inspected model.
- **Manifold Atlas and Manifoldscope** are cartographic and anatomical of
  the same object at different scales. Atlas maps the terrain between
  models; Manifoldscope opens up any one terrain to sustained reading.
- **Theoryscope** stands apart in its object: it looks at the geometry of
  written theoretical positions rather than the geometry of a model.
  It opens a reflexive move, comparing the eigendirections of a theoretical
  corpus against the model trained on that corpus.
- **LLMbench** is the surface: hermeneutic reading of generated prose,
  the level at which models are usually encountered. It sits above the
  geometric instruments and is often the presentation layer for findings
  that begin lower down.

## Licensing and citation

Tools are research instruments. Each repository declares its own licence.
If Vector Lab tools support published research, citation details are
provided in each repository's README.

{% include mermaid.html %}
