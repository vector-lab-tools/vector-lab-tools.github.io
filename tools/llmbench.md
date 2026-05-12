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

Modes are organised across three tiers: Compare, Analyse, and Investigate.

**Compare tier**

- **Compare.** Dual-panel generation from two models on the same prompt, with annotation and cross-panel linking.

**Analyse tier**

- **Stochastic.** Repeated generation from the same model to see the distribution of responses.
- **Temperature.** Generation across temperature settings to see how stochasticity plays at different parameter values.
- **Divergence.** Cross-model divergence metrics including cosine similarity, Jaccard, word overlap (Dice), and uniqueness.
- **Probs.** Probability visualisation for models that return logprobs: heatmap, pixel map, and 3D probability net.

**Investigate tier** (new in v2.10.0, extended through v2.12.0)

- **Grammar Probe.** Pattern-specific probes of generation behaviour. Ships with a library of grammatical constructions (Not X but Y, Hyland hedging triplets, tricolon and parallelism, modal stacking), twenty default prompts across six registers, and ten thematic suites organised along Purpose and Domain axes. Phase A runs a prevalence heatmap (prompt × model × temperature). Phase B captures continuation logprobs at each scaffold's fork point; for antithesis patterns, it also plots logprob against cosine(X, Y-phrase) with a Spearman correlation headline, showing whether the construction is rhetorical or collapses into a nearest-neighbour reflex. Results export as a portable `.grammar.json` bundle that Manifold Atlas can import into its Grammar of Vectors operation for paired geometric analysis.

Across the Compare and Analyse modes, ten guided exercises are available as scholarly presets drawing on Hyland, Lakoff and Johnson, Hayden White and others. Each exercise supplies a preset prompt, methodological context, and guided questions.

## Annotation and cross-panel linking

Annotations layer on both panels independently. A new cross-panel link feature connects annotations across the two outputs with typed relations (contrast, parallel, divergence, convergence, echo, absence, note) and free-text notes. Annotations and links persist in a saved comparison format.

## Providers

Seven providers supported: OpenAI, Anthropic, Google, Hugging Face, OpenRouter, OpenAI-compatible endpoints, and local Ollama. Logprob support varies by provider; the interface is explicit about what each provider can return.

## Theoretical background

LLMbench operationalises the commitment that AI-generated text deserves hermeneutic reading, not just dismissal or statistical critique. It sits above the geometric instruments in the Vector Lab and is often the presentation layer for findings that begin lower down. A claim tested at the geometric level in Manifold Atlas can be illustrated, read closely, and compared across models in LLMbench.

## Stack

Next.js, TypeScript, Three.js. Multi-provider adapters with explicit capability flags. Persistent local storage for prompt history, annotations, and saved comparisons.

## Status

Mature. Currently at v2.13.0. The Grammar Probe Investigate tier ships Phase A (prevalence), Phase B (continuation logprobs, with a geometry upgrade in v2.12.0), and Phase E (temperature sweep, added in v2.13.0). The pattern library is Atlas-aligned for round-tripping through the `.grammar.json` bundle. Other recent additions: ten thematic prompt suites along Purpose and Domain axes, multi-select pattern selection, summary-statistics banners across the Analyse modes, cross-panel annotation linking with seven relation types. In active use for teaching and research.

## Siblings

[Manifold Atlas](/tools/manifold-atlas.html) compares the same models at the geometric level; LLMbench is the presentation layer for that work. [Vectorscope](/tools/vectorscope.html) opens the internals behind the prose. [Manifoldscope](/tools/manifoldscope.html) characterises a single manifold. [Theoryscope](/tools/theoryscope.html) applies comparable methods to corpora of theoretical texts.
