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

**Investigate tier**

- **Grammar Probe.** Pattern-specific probes of generation behaviour, organised in five phases that are all now shipped: Phase A (prevalence heatmap, prompt × model × temperature), Phase B (continuation logprobs at each scaffold's fork point, with a Spearman correlation between logprob and cosine(X, Y-phrase) for antithesis patterns), Phase C (forced continuation), Phase D (perturbation), Phase E (temperature sweep). Ships with a library of grammatical constructions (Not X but Y, Hyland hedging triplets, tricolon and parallelism, modal stacking), an Atlas-aligned pattern library, twenty default prompts across six registers, and ten thematic suites along Purpose and Domain axes. Results export as a portable `.grammar.json` bundle that Manifold Atlas can import into its Grammar of Vectors operation for paired geometric analysis. A global Stop button cancels any running phase mid-stream.
- **Sampling Probe** (added v2.15.0). A new Investigate-tier mode that turns sampling itself into an inspectable surface. Per-token transcript, override audit log, completion-style prompting with editable prompt, Panel B no-flash, transcript-matches strip, sample prompts, and PDF export.

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

Mature. Currently at v2.15.43. All five Grammar Probe phases (A through E) are shipped, with a global Stop button (v2.15.30) and first-class logprobs across the app (v2.15.20). The Sampling Probe is the new Investigate-tier mode (v2.15.0). Browser-direct Ollama landed in the v2.15.30–v2.15.43 range alongside the parallel Atlas work, with a copyable `OLLAMA_ORIGINS` command in the unreachable-error message and a proper README setup section. Compact Deep Dive mode (v2.15.17), per-provider API key persistence, and an onboarding guide round out the recent work. In active use for teaching and research.

## Siblings

[Manifold Atlas](/tools/manifold-atlas.html) compares the same models at the geometric level; LLMbench is the presentation layer for that work. [Vectorscope](/tools/vectorscope.html) opens the internals behind the prose. [Manifoldscope](/tools/manifoldscope.html) characterises a single manifold. [Theoryscope](/tools/theoryscope.html) applies comparable methods to corpora of theoretical texts.
