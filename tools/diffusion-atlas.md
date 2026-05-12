---
layout: default
title: Diffusion Atlas
---

<section class="tool-deep-dive">

<div class="tool-entry-head">
<img src="/assets/images/tools/diffusion-atlas.svg" alt="" class="tool-icon-lg">
<div>
<h1>Diffusion Atlas</h1>
<p class="object"><em>Tier:</em> comparative tool (alpha). <em>Object:</em> generative trajectories and compositional fidelity across diffusion image models.</p>
<p><a href="https://github.com/vector-lab-tools/diffusionatlas">github.com/vector-lab-tools/diffusionatlas</a> · <a href="/tools.html">All tools</a></p>
</div>
</div>

</section>

Diffusion Atlas reads diffusion image models as vector processes rather than black-box generators. Where Manifold Atlas reads the *static* manifold of a frozen embedding model and LLMbench compares *generated prose* across language models, Diffusion Atlas reads the *generative trajectory* of a denoising model, the path through latent space that produces an image, and combines that geometric reading with scored compositional evaluation.

## Why Diffusion Atlas

Two surfaces that current diffusion tools keep apart get unified in one instrument:

- **Atlas** register: per-step latents, CFG sweeps, latent-neighbourhood sampling. Reveals diffusion as a vector process, not a black box.
- **Bench** register: GenEval-style compositional tasks with reproducible scoring. Lets the same model be probed and judged in one app.

The unification is theoretical, not cosmetic. Atlas operations expose where in latent space a model decides; Bench shows what those decisions cost in compositional fidelity. Together they let critical theorists treat diffusion outputs as traces of a vector logic rather than finished pictures.

## Operations

Four operations are live, organised across two top-level tabs:

### Atlas

- **Denoise Trajectory.** Per-step latent capture during a single image generation, projected via Film, PCA, or UMAP, and rendered as a Three.js path with frame-stamped image thumbnails along the curve. Local backend required. Each completed run is auto-saved as a temporary layer that can be locked, kept, and compared against future runs. White edge-print metadata strip and clickable RGB histogram per frame. Stop button on long runs (`AbortController` + signal-on-fetch; partial trajectories saved as temp layers labelled "stopped @N").
- **Guidance Sweep.** Same prompt and seed across a list of CFG values. Hosted-capable. Sequential sweep with rate-limit retry and live "Rate limited; retrying in Ns" countdown per cell; one failure does not tank the rest. Gold warning banner when the active model ignores guidance (schnell, flux-2-*).
- **Latent Neighbourhood.** Anchor seed plus k samples within a perturbation radius. Hosted backends jitter the seed; the local backend perturbs the initial latent at a chosen σ. UMAP scatter with thumbnail grid, pairwise distances, and DBSCAN cluster count.

### Bench

- **Compositional Bench.** GenEval-lite task pack covering single-object, two-object, counting, colour, position, and colour-attribution prompts. N seeds per task. Scoring via local CLIP with plain-English bands and a per-metric definition tooltip. Leaderboard plot with per-task gallery and pass / fail overlays.

Across all four operations: shuffle and increment seed modes with per-mode dice animations; collapsible Deep Dive with CSV / JSON / PDF export (PDF groups per layer, each layer's camera roll, latent geometry, and image-stats tables together newest-first); cross-backend comparison; click-to-modal on result images.

## Backend strategy

Hybrid. Hosted providers (Replicate by default, Fal alongside) and a local FastAPI + diffusers backend that mirrors the Vectorscope architecture. The local backend exposes `/health` (with `nativeWidth` / `nativeHeight` reporting), `/generate`, streaming `/trajectory`, and `/score`. Native-resolution auto-snap reads dimensions from the loaded model. Denoise Trajectory requires the local backend (per-step latent access); Guidance Sweep, Latent Neighbourhood, and Compositional Bench are hosted-capable. The dispatcher returns typed errors normalised to UI: `auth` (401), `payment_required` (402, with billing link), `rate_limit` (429), `capability` (422). Backend pre-flight refuses unsupported resolutions with HTTP 422 plus diagnostic.

## Theoretical background

Diffusion Atlas extends the *vector turn* argument from text to image. The manifold framing migrates more cleanly to diffusion than it does to autoregressive text, and the asymmetry is itself an argument the lab wants to develop.

Cross-tool triangulation: Diffusion Atlas (latent vector logic) sits beside [Vectorscope](/tools/vectorscope.html) (token vector logic) as the two regimes of the vector turn the lab can currently inspect. The pair sets up a comparative argument about where vector logic differs between modalities.

## Stack

Next.js 16, React 19, TypeScript 5, Tailwind, sharing the editorial design system and tab grouping with Manifold Atlas. Visualisation through Three.js (trajectory paths) and Plotly (sweep, scatter, leaderboard). Local backend in Python 3.11, FastAPI, diffusers, and torch (mps / cuda), mirroring Vectorscope. IndexedDB caching for latents and image blobs, with separate counters and LRU eviction at a configurable cap.

## Status

Alpha, v0.3.13. M1 (app shell + hosted generation), M2 (local FastAPI + Denoise Trajectory), M3 (Guidance Sweep, Latent Neighbourhood), and M4 (Compositional Bench with CLIP scoring) are all shipped. v0.3.13 lifts a generic stacking primitive (`useLayerStack` + `LayerStackPanel`) so Sweep, Neighbourhood, and Bench can adopt the same layer model as Trajectory in roughly twenty lines each, and pulls Sweep and Neighbourhood onto the contact-sheet aesthetic via shared `ContactSheetFrame` and `SprocketRow` primitives. Step Inspector is now a click-to-open modal with thumbnail, RGB histogram, and Play / Stop animation. Per-operation state persists in IDB (`op_state` store, structured-cloned latents survive) with a per-operation Reset. Backend hardening: EulerDiscreteScheduler pinned after DPM++ 2M produced sporadic NaN on MPS, scheduler reset on every forward to dodge the `step_index` leak. Up next on the 0.3.x track: Clippy / Hackerman easter eggs, object-detection-based Bench scoring, Library run loader, attention-map visualisation, h-space steering.

## Siblings

[Manifold Atlas](/tools/manifold-atlas.html) reads the static geometry of language-model embeddings; Diffusion Atlas reads the generative geometry of image models. [LLMbench](/tools/llmbench.html) is the prose-surface counterpart for language-model output. [Vectorscope](/tools/vectorscope.html) opens single language-model internals in the way Diffusion Atlas's local backend opens single diffusion-model internals. [Manifoldscope](/tools/manifoldscope.html) and [Theoryscope](/tools/theoryscope.html) round out the lab.
