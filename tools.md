---
layout: default
title: Tools
---

# Tools

A brief guide to each instrument. Follow the **Deep dive** link on any tool for its extended page with operations, theoretical background, and status. The comparative tools are the most mature and are listed first; the single-model scopes are in beta and are listed below.

---

## Comparative tools

<section class="tool-entry comparative">

<div class="tool-entry-head">
<img src="/assets/images/tools/manifold-atlas.svg" alt="" class="tool-icon-lg">
<div>
<h2><a href="/tools/manifold-atlas.html">Manifold Atlas</a></h2>
<p class="object"><em>Tier:</em> comparative model tool. <em>Object:</em> output embeddings across models.</p>
<p><a href="/tools/manifold-atlas.html">Deep dive</a> · <a href="https://github.com/vector-lab-tools/manifold-atlas">github.com/vector-lab-tools/manifold-atlas</a></p>
</div>
</div>

Manifold Atlas compares multiple embedding models' output geometries on the same inputs. The tool packages fifteen operations for the critical testing of vector-theoretic claims: Concept Distance, Neighbourhood Map, Negation Gauge, Negation Battery, Semantic Sectioning, Concept Drift, Hegemony Compass, Real Abstraction Test, Silence Detector, Distance Matrix, Agonism Test, Vector Logic, Vector Walk, Text Vectorisation, and more. Each operation makes a theoretical claim empirically testable against the geometry that a given model has learned.

<p class="tool-meta"><em>Stack:</em> Next.js 16, React 19, TypeScript, Three.js.</p>

</section>

<section class="tool-entry comparative">

<div class="tool-entry-head">
<img src="/assets/images/tools/llmbench.svg" alt="" class="tool-icon-lg">
<div>
<h2><a href="/tools/llmbench.html">LLMbench</a></h2>
<p class="object"><em>Tier:</em> comparative model tool. <em>Object:</em> generated prose across models.</p>
<p><a href="/tools/llmbench.html">Deep dive</a> · <a href="https://github.com/vector-lab-tools/LLMbench">github.com/vector-lab-tools/LLMbench</a></p>
</div>
</div>

LLMbench sends a prompt to two models simultaneously and displays their responses side-by-side for annotated close reading. Six modes cover comparison, annotation, and probability visualisation, including heatmap, pixel map, and 3D probability net. Supports OpenAI, Anthropic, Google, Hugging Face, OpenRouter, and Ollama. Annotation infrastructure is shared with the Critical Code Studies Workbench.

<p class="tool-meta"><em>Stack:</em> Next.js, TypeScript, Three.js, with multi-provider adapters.</p>

</section>

<section class="tool-entry comparative">

<div class="tool-entry-head">
<img src="/assets/images/tools/diffusion-atlas.svg" alt="" class="tool-icon-lg">
<div>
<h2><a href="/tools/diffusion-atlas.html">Diffusion Atlas</a> <small>(in development)</small></h2>
<p class="object"><em>Tier:</em> comparative model tool. <em>Object:</em> generative trajectories and compositional fidelity across diffusion image models.</p>
<p><a href="/tools/diffusion-atlas.html">Deep dive</a> · <a href="https://github.com/vector-lab-tools/diffusionatlas">github.com/vector-lab-tools/diffusionatlas</a></p>
</div>
</div>

Diffusion Atlas reads diffusion image models as vector processes, unifying two surfaces in one instrument: an Atlas register for per-step latents, CFG sweeps, and latent-neighbourhood sampling, and a Bench register for GenEval-style compositional scoring. v0.1 ships four operations across the two registers (Denoise Trajectory, Guidance Sweep, Latent Neighbourhood, Compositional Bench) with hosted backends (Replicate, Fal, Together, Stability) and a local FastAPI + diffusers backend for operations needing per-step latent access.

<p class="tool-meta"><em>Stack:</em> Next.js + TypeScript + Three.js + Plotly; Python + FastAPI + diffusers + torch for the local backend.</p>

</section>

---

## Single-model scopes (beta)

<section class="tool-entry scope">

<div class="tool-entry-head">
<img src="/assets/images/tools/vectorscope.svg" alt="" class="tool-icon-lg">
<div>
<h2><a href="/tools/vectorscope.html">Vectorscope</a></h2>
<p class="object"><em>Tier:</em> single-model scope. <em>Object:</em> a single open-weight model.</p>
<p><a href="/tools/vectorscope.html">Deep dive</a> · <a href="https://github.com/vector-lab-tools/vectorscope">github.com/vector-lab-tools/vectorscope</a></p>
</div>
</div>

Vectorscope opens a single open-weight language model for forensic inspection. Where commercial embedding APIs return sentence-level composites from a separately-trained embedding model, Vectorscope works directly with open weights so that activations, attention, and token embeddings are legible at every layer. The signal-degradation capability runs the same inputs across precision regimes (FP32, BF16, INT8, INT4, FP4, INT2) to observe how meaning compresses as the medium is quantised.

<p class="tool-meta"><em>Stack:</em> Next.js and FastAPI, with PyTorch and transformers for model loading.</p>

</section>

<section class="tool-entry scope">

<div class="tool-entry-head">
<img src="/assets/images/tools/manifoldscope.svg" alt="" class="tool-icon-lg">
<div>
<h2><a href="/tools/manifoldscope.html">Manifoldscope</a></h2>
<p class="object"><em>Tier:</em> single-model scope. <em>Object:</em> a single manifold.</p>
<p><a href="/tools/manifoldscope.html">Deep dive</a> · <a href="https://github.com/vector-lab-tools/manifoldscope">github.com/vector-lab-tools/manifoldscope</a></p>
</div>
</div>

Manifoldscope treats a single manifold, understood as an embedding output together with its sampling, as both a geometric and an ideological object. It measures intrinsic dimension, curvature, density, and topology, and reads the same manifold critically, asking what it naturalises, what it suppresses, what it sediments. Every critique is backed by a measure attestation. Probes include ideological topography, archaeology of absence, colonial geometry, market-colonisation index, grammatical ideology, and dissensus detection.

<p class="tool-meta"><em>Status:</em> concept and prototype stage.</p>

</section>

<section class="tool-entry scope">

<div class="tool-entry-head">
<img src="/assets/images/tools/theoryscope.svg" alt="" class="tool-icon-lg">
<div>
<h2><a href="/tools/theoryscope.html">Theoryscope</a></h2>
<p class="object"><em>Tier:</em> single-model scope. <em>Object:</em> a corpus of theoretical texts.</p>
<p><a href="/tools/theoryscope.html">Deep dive</a> · <a href="https://github.com/vector-lab-tools/theoryscope">github.com/vector-lab-tools/theoryscope</a></p>
</div>
</div>

Theoryscope maps a corpus of theoretical texts as a high-dimensional point cloud and asks renormalisation-group-style questions of it. Operations include eigendirection analysis, which reveals the axes that actually structure the field (often orthogonal to the axes its participants name), renormalisation-group flow under coarse-graining, fixed points, and universality classes. The critical payoff is the ability to show that positions which look opposed may converge under coarse-graining, and that positions which look similar may diverge.

<p class="tool-meta"><em>Stack:</em> Next.js and FastAPI, shared geometry library with the other scopes.</p>

</section>

## A note on naming

The naming grammar is consistent across the lab:

- <strong>-scope</strong>: an instrument of intensive inspection. Named after the real-instrument convention (vectorscope, oscilloscope, microscope).
- <strong>Atlas</strong>: a comparative cartographic instrument that maps across objects.
- <strong>bench</strong>: a workbench for close, iterative work with the surface of an object.

{% include mermaid.html %}
