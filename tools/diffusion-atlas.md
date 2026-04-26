---
layout: default
title: Diffusion Atlas
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/diffusion-atlas.svg" alt="" class="tool-icon-lg">
<div>
<h1>Diffusion Atlas</h1>
<p class="object"><em>Tier:</em> comparative tool (in development). <em>Object:</em> generative trajectories and compositional fidelity across diffusion image models.</p>
<p><a href="https://github.com/vector-lab-tools/diffusion-atlas">github.com/vector-lab-tools/diffusion-atlas</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

Diffusion Atlas reads diffusion image models as vector processes rather than black-box generators. Where Manifold Atlas reads the *static* manifold of a frozen embedding model and LLMbench compares *generated prose* across language models, Diffusion Atlas reads the *generative trajectory* of a denoising model, the path through latent space that produces an image, and combines that geometric reading with scored compositional evaluation.

## Why Diffusion Atlas

Two surfaces that current diffusion tools keep apart get unified in one instrument:

- **Atlas** register: per-step latents, CFG sweeps, latent-neighbourhood sampling. Reveals diffusion as a vector process, not a black box.
- **Bench** register: GenEval-style compositional tasks with reproducible scoring. Lets the same model be probed and judged in one app.

The unification is theoretical, not cosmetic. Atlas operations expose where in latent space a model decides; Bench shows what those decisions cost in compositional fidelity. Together they let critical theorists treat diffusion outputs as traces of a vector logic rather than finished pictures.

## Operations (v0.1)

Four operations ship in the first version, organised across two top-level tabs:

### Atlas

- **Denoise Trajectory.** Per-step latent capture during a single image generation, projected to 3D via UMAP or PCA and rendered as a Three.js path with frame-stamped image thumbnails along the curve. Local-only, requiring per-step latent access via the FastAPI + diffusers backend. The deep dive surfaces per-step L2 step size, cosine to final, and the scheduler sigma table.
- **Guidance Sweep.** Same prompt and seed across a list of CFG values (e.g. 1, 3, 5, 7.5, 10, 15). Hosted-capable. Outputs an image grid keyed by CFG, plus a Plotly drift curve and a mode-collapse indicator measuring variance across the sweep.
- **Latent Neighbourhood.** Anchor seed plus k samples within a perturbation radius. Hosted backends jitter the seed; the local backend perturbs the initial latent at a chosen σ. Output is a UMAP scatter of result-image embeddings (or initial latents) with a thumbnail grid, plus pairwise distances and a DBSCAN cluster count.

### Bench

- **Compositional Bench.** GenEval-lite task pack covering single-object, two-object, counting, colour, position, and colour-attribution prompts. N seeds per task. Scoring via local CLIP plus simple object-detector heuristics, aggregated to per-category accuracy. Output is a leaderboard plot with a per-task gallery and pass / fail overlays.

## Backend strategy

Hybrid by design. Hosted APIs (Replicate, Fal, Together, Stability) are the default; convenient and require no local GPU. A local FastAPI + diffusers backend mirrors the Vectorscope architecture and is required for operations that need per-step latent access (Denoise Trajectory) or are enhanced by it (latent-space perturbation in Latent Neighbourhood). The dispatcher returns a typed CapabilityError when an operation needs local features and the active provider is hosted-only, prompting the user to switch backend.

## Theoretical background

Diffusion Atlas extends the *vector turn* argument from text to image. The manifold framing migrates more cleanly to diffusion than it does to autoregressive text, and the asymmetry is itself an argument the lab wants to develop.

Cross-tool triangulation: Diffusion Atlas (latent vector logic) sits beside [Vectorscope](/tools/vectorscope.html) (token vector logic) as the two regimes of the vector turn the lab can currently inspect. The pair sets up a comparative argument about where vector logic differs between modalities.

## Stack

Next.js 16, React 19, TypeScript 5, Tailwind, sharing the editorial design system and tab grouping with Manifold Atlas. Visualisation through Three.js (trajectory paths) and Plotly (sweep, scatter, leaderboard). Local backend in Python 3.11, FastAPI, diffusers, and torch (mps / cuda), mirroring Vectorscope. IndexedDB caching for latents and image blobs, with separate counters and LRU eviction at a configurable cap.

## Status

v0.1, in early development. Plan and architecture finalised on 26 April 2026; scaffolding in progress. M1 ships the app shell with hosted Replicate generation; M2 the local FastAPI backend and Denoise Trajectory streaming; M3 Guidance Sweep and Latent Neighbourhood; M4 Compositional Bench with GenEval-lite tasks; M5 polish, exports, and docs.

## Siblings

[Manifold Atlas](/tools/manifold-atlas.html) reads the static geometry of language-model embeddings; Diffusion Atlas reads the generative geometry of image models. [LLMbench](/tools/llmbench.html) is the prose-surface counterpart for language-model output. [Vectorscope](/tools/vectorscope.html) opens single language-model internals in the way Diffusion Atlas's local backend opens single diffusion-model internals. [Manifoldscope](/tools/manifoldscope.html) and [Theoryscope](/tools/theoryscope.html) round out the lab.
