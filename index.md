---
layout: default
title: Vector Lab
---

<section class="hero">
  <div class="hero-text">
    <h1>Vector Lab</h1>
    <p class="tagline">Vector methods for vector theory.</p>
  </div>
  <div class="hero-visual">
    <img src="/assets/images/hero.svg" alt="A warped manifold surveyed by five small instruments, rendered as a wireframe grid over a dark editorial background.">
  </div>
</section>

<section class="lede">

Large language models reorganise meaning as geometry. Every token, every concept, every sentence is assigned a position in a high-dimensional vector space whose axes are no-one's axes and whose distances no-one chose. What any given model can say about democracy, about poltics, democracy, the economy or society, even about contested ideas of intelligence, is constrained by the geometry that model has learned. And that geometry carries the sedimented assumptions of the corpus, the labour regime, and the economic pressures that produced it.

We could call this the geometrisation of thought. What has been missing is the corresponding set of tools. Reading papers about the manifold is not the same as inspecting the manifold. Claiming that a model has naturalised market-liberal notions of democracy is not the same as measuring the pull. The work is critical-empirical, and vector tools are needed to address this.

Vector Lab is that toolkit. Five instruments, arranged in two tiers. The inner tier, Vectorscope, Manifoldscope, Theoryscope, opens single objects for intensive inspection: a single open-weight model, a single manifold, a single corpus of theoretical texts. The outer tier, Manifold Atlas and LLMbench, works across models, asking comparative questions at the level of output embeddings and generated prose. The inner tier supplies the anatomical detail. The outer tier provides the comparative grounds on which theoretical claims can be tested.

</section>

## The family

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
  <img class="tool-icon" src="/assets/images/tools/vectorscope.svg" alt="">
  <h3><a href="https://github.com/vector-lab-tools/vectorscope">Vectorscope</a></h3>
  <p class="object">Object: a single open-weight model.</p>
  <p>Layer-by-layer weights, hidden states, attention, precision regimes. The anatomical instrument of the lab.</p>
</article>

<article class="tool-card scope">
  <img class="tool-icon" src="/assets/images/tools/manifoldscope.svg" alt="">
  <h3><a href="https://github.com/vector-lab-tools/manifoldscope">Manifoldscope</a></h3>
  <p class="object">Object: a single manifold.</p>
  <p>Intrinsic dimension, curvature, density, topology, and the political reading of what a geometry sediments or refuses. Measure and critique bound together.</p>
</article>

<article class="tool-card scope">
  <img class="tool-icon" src="/assets/images/tools/theoryscope.svg" alt="">
  <h3><a href="https://github.com/vector-lab-tools/theoryscope">Theoryscope</a></h3>
  <p class="object">Object: a corpus of theoretical texts.</p>
  <p>Renormalisation-group flow, eigendirections, fixed points, universality classes. A navigable geometry of theory space.</p>
</article>

</div>

### Comparative instruments

<div class="tools-grid">

<article class="tool-card comparative">
  <img class="tool-icon" src="/assets/images/tools/manifold-atlas.svg" alt="">
  <h3><a href="https://github.com/vector-lab-tools/manifold-atlas">Manifold Atlas</a></h3>
  <p class="object">Object: output embeddings across models.</p>
  <p>Concept distance, negation gauge, hegemony compass, silence detector, agonism test, vector logic. The comparative cartographic instrument.</p>
</article>

<article class="tool-card comparative">
  <img class="tool-icon" src="/assets/images/tools/llmbench.svg" alt="">
  <h3><a href="https://github.com/vector-lab-tools/LLMbench">LLMbench</a></h3>
  <p class="object">Object: generated prose across models.</p>
  <p>Dual-panel close reading, annotation, logprobs, probability visualisation. The hermeneutic surface instrument.</p>
</article>

</div>

## Theoretical Background

The vector lab tools are designed to open the "vector box" of artificial intelligence. The key argument is that there is a shift from the digital to the vector. Our tools and approaches have to correspondingly shift also. Commercial embedding APIs return sentence-level composites from separately-trained embedding models, the output of a pipeline rather than a window into the representations themselves. This is fine for some tasks. It is inadequate for critical work. If we want to know what the geometry of a particular model has sedimented, we have to work with open-weight models where the weights, activations, and token embeddings can be read at every layer. Vector Lab tools therefore privilege open-weight models wherever the question requires internal access, and treat commercial outputs as a separate object, the retrieval surface, with its own interest.

The result is a set of instruments that do things other research tools do not. Vectorscope runs the same inputs across precision regimes, FP32 through BF16, INT8, INT4, FP4, INT2, to observe how signal degrades as the medium is quantised, on the principle that the material substrate of a representation shapes what it can hold. Manifoldscope treats each manifold as a geometric object (intrinsic dimension, curvature, density) and as an ideological object (what it naturalises, suppresses, sediments), binding measure to critique so that no interpretive claim goes without its attestation. Theoryscope applies renormalisation-group and eigenvector methods to corpora of theoretical texts, asking which positions are fixed points under coarse-graining and which traditions are universality classes of one another. Manifold Atlas runs fifteen operations across multiple embedding models, turning particular vector-theoretic claims into empirically testable propositions. LLMbench sets two models' prose outputs side by side and enables the dual-panel close reading that hermeneutic work requires.

The tools are designed to explore the new media theoretic landscape of AI, which are listed in each repository's documentation and developed in the essays that motivate them. Critical work on large language models has, for a decade, been constrained by a tooling deficit. Either work with commercial APIs, and accept the interpretive costs, or do without tools and write essays that assert what a geometry looks like without ever seeing one. Vector Lab is an attempt to close that gap, to produce instruments that are continuous with the theoretical project rather than imported from outside it, and to make them public so that others can use, extend, or disagree with the work they do.

## How the instruments relate

Vectorscope explains the internal geometry of a single model

Manifoldscope characterises a single manifold in its own right, often one produced by a Vectorscope-inspected model. 
Manifoldscope opens up any one terrain for sustained close reading.

Manifold Atlas maps the terrain between models
 
Manifold Atlas and Manifoldscope are cartographic and anatomical of the same object at different scales. 

Theoryscope stands apart in its object, addressing the geometry of meso structures in vector space rather than the geometry of a model, and so opens a reflexive possibility, comparing the eigendirections of a theoretical corpus against the model trained on that corpus. 

LLMbench is oriented to the hermeneutic reading of generated prose, the level at which models are usually encountered. It sits above the geometric instruments and is often the presentation layer for findings that begin lower down.

## Using the tools

Each repository contains full documentation, dependencies, and setup instructions. Tools are research instruments and are offered as-is under permissive licences. If Vector Lab tools support published research, please cite the specific tool and version, and cite the relevant theoretical essays where the claims being tested are developed.

{% include mermaid.html %}
