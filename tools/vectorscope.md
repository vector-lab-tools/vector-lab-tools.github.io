---
layout: default
title: Vectorscope
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/vectorscope.svg" alt="" class="tool-icon-lg">
<div>
<h1>Vectorscope</h1>
<p class="object"><em>Tier:</em> single-model scope (alpha). <em>Object:</em> a single open-weight model.</p>
<p><a href="https://github.com/vector-lab-tools/vectorscope">github.com/vector-lab-tools/vectorscope</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

Vectorscope opens a single open-weight language model for forensic inspection. It reads weights, activations, attention, and token embeddings at every layer, turning the model from a black box into an object of empirical analysis. It is the anatomical instrument of the Vector Lab.

## Why Vectorscope

Commercial embedding APIs return sentence-level composites from separately-trained embedding models, the output of a pipeline rather than a window into the model itself. That is fine for some applications and inadequate for critical work on how language models actually organise meaning. Vectorscope privileges open-weight models where every layer can be inspected: weights, attention matrices, hidden states, token embeddings, and the operations that compose them. The tool is designed to make the internal geometry of a model legible, on its own terms, at the resolution the question demands.

## Operations

- **Layer-by-layer inspection.** Hidden states, residual stream contributions, and intermediate representations at each transformer layer. Follow a concept through the stack and observe how its position drifts.
- **Attention analysis.** Which heads activate on which inputs, and what structural patterns do they encode? Visualise attention matrices per head, per layer, per token.
- **Token embedding exploration.** The pre-contextual vocabulary, before any input has been read. Which tokens sit as neighbours, which as antipodes, and which have no neighbours at all?
- **Signal degradation laboratory.** Run the same input across precision regimes, FP32 through BF16, INT8, INT4, FP4, INT2, and observe how the signal compresses as the medium is quantised. The material substrate of a representation shapes what it can hold; Vectorscope measures the shaping.

## Theoretical background

Vectorscope is the empirical instrument that follows from the essays [*What Is Vector Space?*](https://stunlaw.blogspot.com/2026/03/what-is-vector-space.html) and [*Vector Theory*](https://stunlaw.blogspot.com/2026/02/vector-theory.html). Where those essays characterise vector space as a new medium constituted by dimensionality, Vectorscope is the instrument that makes that space legible. The signal-degradation laboratory implements the methodological commitment of the Leverhulme Centre for Vector Media bid, treating precision regime as a material parameter that shapes meaning.

## Stack

Next.js frontend for the interface and visualisations, FastAPI backend running PyTorch and Hugging Face Transformers for model loading and forward passes. Model weights are loaded locally; nothing is sent to third-party services. Works with any open-weight model Hugging Face can load.

## Status

Alpha. The architecture is stable; individual operations are at varying levels of maturity. See the repository for the current state of each operation and its known limitations.

## Siblings

[Manifoldscope](/tools/manifoldscope.html) takes the output of a Vectorscope-inspected model and characterises it as a manifold in its own right. [Manifold Atlas](/tools/manifold-atlas.html) compares output geometries across models. [Theoryscope](/tools/theoryscope.html) extends the same critical posture from a model to a corpus of theoretical texts. [LLMbench](/tools/llmbench.html) handles the prose surface.
