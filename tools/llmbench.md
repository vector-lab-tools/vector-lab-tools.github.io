---
layout: default
title: LLMbench
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/llmbench.svg" alt="" class="tool-icon-lg">
<div>
<h1>LLMbench</h1>
<p class="object"><em>Tier:</em> comparative tool. <em>Object:</em> generated prose across models.</p>
<p><a href="https://github.com/vector-lab-tools/LLMbench">github.com/vector-lab-tools/LLMbench</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

LLMbench sends a prompt to two models simultaneously, displays their responses side-by-side, and enables researchers to build layered interpretive readings across both outputs. It is the hermeneutic surface instrument of the Vector Lab: the layer at which models are usually encountered. Where Manifold Atlas compares models at the geometric level and Vectorscope inspects internals, LLMbench handles comparative close reading of generated text.

## Why LLMbench

AI-generated text is rarely read closely. It is skimmed, summarised, or dismissed. LLMbench asks a different question: what happens when two models generate in response to the same prompt, and what does the comparison reveal about the geometries below? The tool reuses annotation infrastructure from the Critical Code Studies Workbench, reoriented from source code analysis to LLM output comparison.

## Modes

Six modes cover the range of comparative work:

- **Compare.** Dual-panel generation from two models on the same prompt, with annotation and cross-panel linking.
- **Stochastic.** Repeated generation from the same model to see the distribution of responses.
- **Temperature.** Generation across temperature settings to see how stochasticity plays at different parameter values.
- **Divergence.** Cross-model divergence metrics including cosine similarity, Jaccard, word overlap (Dice), and uniqueness.
- **Probs.** Probability visualisation for models that return logprobs: heatmap, pixel map, and 3D probability net.
- **Guided exercises.** Scholarly presets drawing on Hyland, Lakoff and Johnson, Hayden White and others. Each exercise provides a preset prompt, methodological context, and guided questions.

## Annotation and cross-panel linking

Annotations layer on both panels independently. A new cross-panel link feature connects annotations across the two outputs with typed relations (contrast, parallel, divergence, convergence, echo, absence, note) and free-text notes. Annotations and links persist in a saved comparison format.

## Providers

Seven providers supported: OpenAI, Anthropic, Google, Hugging Face, OpenRouter, OpenAI-compatible endpoints, and local Ollama. Logprob support varies by provider; the interface is explicit about what each provider can return.

## Theoretical background

LLMbench operationalises the commitment that AI-generated text deserves hermeneutic reading, not just dismissal or statistical critique. It sits above the geometric instruments in the Vector Lab and is often the presentation layer for findings that begin lower down. A claim tested at the geometric level in Manifold Atlas can be illustrated, read closely, and compared across models in LLMbench.

## Stack

Next.js, TypeScript, Three.js. Multi-provider adapters with explicit capability flags. Persistent local storage for prompt history, annotations, and saved comparisons.

## Status

Mature. Currently at v2.8.0 with prompt history in all Analyse modes, cross-panel annotation links, cosine similarity in divergence, and ten guided exercises. In active use for teaching and research.

## Siblings

[Manifold Atlas](/tools/manifold-atlas.html) compares the same models at the geometric level; LLMbench is the presentation layer for that work. [Vectorscope](/tools/vectorscope.html) opens the internals behind the prose. [Manifoldscope](/tools/manifoldscope.html) characterises a single manifold. [Theoryscope](/tools/theoryscope.html) applies comparable methods to corpora of theoretical texts.
