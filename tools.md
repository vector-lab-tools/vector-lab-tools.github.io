---
layout: default
title: Tools
---

# Tools

A brief guide to each instrument. Each tool has its own README with full
documentation; this page gives the lab-level picture.

---

## Vectorscope

*Tier: single-object scope. Object: a single open-weight model.*

[github.com/vector-lab-tools/vectorscope](https://github.com/vector-lab-tools/vectorscope)

Vectorscope opens a single open-weight language model for forensic
inspection. Where commercial embedding APIs return sentence-level
composites from a separately-trained embedding model, Vectorscope works
directly with open weights so that activations, attention, and token
embeddings are legible at every layer. The signal-degradation capability
runs the same inputs across precision regimes (FP32, BF16, INT8, INT4,
FP4, INT2) to observe how meaning compresses as the medium is quantised.

**Stack:** Next.js + FastAPI + PyTorch + transformers.

---

## Manifoldscope

*Tier: single-object scope. Object: a single manifold.*

[github.com/vector-lab-tools/manifoldscope](https://github.com/vector-lab-tools/manifoldscope)

Manifoldscope treats a single manifold (an embedding output with its
sampling) as both a geometric and an ideological object. It measures
intrinsic dimension, curvature, density, and topology, and reads the same
manifold critically: what it naturalises, what it suppresses, what it
sediments. Every critique is backed by a measure attestation. Probes
include ideological topography, archaeology of absence, colonial geometry,
market-colonisation index, grammatical ideology, and dissensus detection.

**Status:** concept / proposal stage.

---

## Theoryscope

*Tier: single-object scope. Object: a corpus of theoretical texts.*

[github.com/vector-lab-tools/theoryscope](https://github.com/vector-lab-tools/theoryscope)

Theoryscope maps a corpus of theoretical texts as a high-dimensional point
cloud and asks renormalisation-group-style questions of it. Operations
include eigendirection analysis (the axes that actually structure the
field, which may be orthogonal to the axes its participants name), RG
flow under coarse-graining (which positions are scale-invariant), fixed
points, and universality classes (positions that look opposed but
converge, and positions that look similar but diverge).

**Stack:** Next.js + FastAPI, shared geometry library with the other scopes.

---

## Manifold Atlas

*Tier: comparative instrument. Object: output embeddings across models.*

[github.com/vector-lab-tools/manifold-atlas](https://github.com/vector-lab-tools/manifold-atlas)

Manifold Atlas compares multiple embedding models' output geometries on
the same inputs. The tool packages fifteen operations for the critical
testing of vector theory claims: Concept Distance, Neighbourhood Map,
Negation Gauge, Negation Battery, Semantic Sectioning, Concept Drift,
Hegemony Compass, Real Abstraction Test, Silence Detector, Distance Matrix,
Agonism Test, Vector Logic, Vector Walk, Text Vectorisation, and more.
Each operation makes a theoretical claim empirically testable against the
geometry that a given model has learned.

**Stack:** Next.js 16 + React 19 + TypeScript + Three.js.

---

## LLMbench

*Tier: comparative instrument. Object: generated prose across models.*

[github.com/vector-lab-tools/LLMbench](https://github.com/vector-lab-tools/LLMbench)

LLMbench sends a prompt to two models simultaneously and displays their
responses side-by-side for annotated close reading. Six modes cover
comparison, annotation, and probability visualisation (heatmap, pixel map,
3D probability net). Supports OpenAI, Anthropic, Google, Hugging Face,
OpenRouter, and Ollama. Annotation infrastructure is shared with the
Critical Code Studies Workbench.

**Stack:** Next.js + TypeScript + Three.js, multi-provider adapters.

---

## A note on naming

The naming grammar is consistent across the lab:

- **-scope**: an instrument of intensive inspection of a single object.
  Named after the real-instrument convention (vectorscope, oscilloscope,
  microscope).
- **Atlas**: a comparative cartographic instrument that maps across
  objects.
- **bench**: a workbench for close, iterative work with the surface of
  an object.

{% include mermaid.html %}
