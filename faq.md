---
layout: default
title: FAQ
---

<div class="section-head" markdown="1">
<p class="num">00 · FAQ</p>

# Common problems across the lab
</div>

The cross-cutting problems that affect every tool. Provider-specific setup, with the exact failure each key causes, lives in each tool's own documentation.

<div class="section-head" markdown="1">
<p class="num">01 · API keys</p>

## Getting API keys
</div>

### What's the easiest way to run the vector lab?

Install **Ollama** locally and pull two models: an embedding model (`nomic-embed-text`) and a chat model (`llama3.2` is a reasonable default). Nothing else is required. No keys, no paid providers, no rate limits. Instructions in [Running Ollama](#running-ollama) below. The free path also works with **Hugging Face Inference** for embedding tools, which gives you access to models you cannot run locally in exchange for sign-up and a rate limit.

### Which tools need which keys?

<div class="keys-grid">

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/LLMbench/">LLMbench</a></h4>
  <dl>
    <dt>Keys</dt><dd>One chat provider: OpenAI, Anthropic, Google, Hugging Face, OpenRouter, or any OpenAI-compatible endpoint.</dd>
    <dt>Free route</dt><dd>Ollama, no key.</dd>
  </dl>
</div>

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/manifold-atlas/">Manifold Atlas</a></h4>
  <dl>
    <dt>Keys</dt><dd>One embedding provider: OpenAI, Voyage, Google, Cohere, OpenRouter, or Hugging Face.</dd>
    <dt>Free route</dt><dd>Ollama, no key. Hugging Face is free but needs a token.</dd>
  </dl>
</div>

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/manifoldscope/">Manifoldscope</a></h4>
  <dl>
    <dt>Keys</dt><dd>None by default. Hosted embedding providers are optional.</dd>
    <dt>Free route</dt><dd>Built in: MiniLM through sentence-transformers. Ollama also works.</dd>
  </dl>
</div>

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/vectorscope/">Vectorscope</a></h4>
  <dl>
    <dt>Keys</dt><dd>A Hugging Face token, only for gated models such as Llama 3.2 and Mistral 7B.</dd>
    <dt>Free route</dt><dd>GPT-2 and Qwen3 load with no account.</dd>
  </dl>
</div>

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/theoryscope/">Theoryscope</a></h4>
  <dl>
    <dt>Keys</dt><dd>A Zotero key, read access, to load your library.</dd>
    <dt>Free route</dt><dd>All models run locally. No provider key.</dd>
  </dl>
</div>

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/diffusionatlas/">Diffusion Atlas</a></h4>
  <dl>
    <dt>Keys</dt><dd>Replicate or Fal, for hosted image generation.</dd>
    <dt>Free route</dt><dd>The local backend, which downloads weights from Hugging Face.</dd>
  </dl>
</div>

<div class="key-card">
  <h4><a href="https://vector-lab-tools.github.io/vectorography/">Vectorography</a></h4>
  <dl>
    <dt>Keys</dt><dd>None.</dd>
    <dt>Free route</dt><dd>Runs as it is.</dd>
  </dl>
</div>

</div>

### Where do I get an API key for each provider?

- **OpenAI**: <https://platform.openai.com/api-keys>. Starts `sk-`. Paid; no free tier.
- **Anthropic**: <https://console.anthropic.com/settings/keys>. Starts `sk-ant-`. Paid; no free tier.
- **Google (Gemini)**: <https://aistudio.google.com/apikey>. Starts `AIza`. Free tier, generous for research.
- **Hugging Face**: <https://huggingface.co/settings/tokens>. Starts `hf_`. The free hosted route, no payment method needed. A fine-grained token must have the **Inference Providers** permission ticked, or every call returns unauthorised; this one setting accounts for most "my new token doesn't work" reports.
- **OpenRouter**: <https://openrouter.ai/keys>. Starts `sk-or-`. Pay-as-you-go across many providers. Where a tool treats OpenRouter as an OpenAI-compatible endpoint, the base URL field must be filled in alongside the key; left empty, the call goes to OpenAI, which rejects an OpenRouter key.
- **Voyage AI**: <https://dashboard.voyageai.com/api-keys>. Starts `pa-`. Free tier; recommended by Anthropic for use with Claude.
- **Cohere**: <https://dashboard.cohere.com/api-keys>. Starts `co-`. Free tier.
- **Replicate**: <https://replicate.com/account/api-tokens>. Starts `r8_`. Pay-per-second.
- **Fal**: <https://fal.ai/dashboard/keys>. Pay-per-image.
- **Zotero**: <https://www.zotero.org/settings/security#applications>. Create a new key, give it library read access.

### Are my keys sent anywhere I'm not expecting?

Keys are stored in your browser's `localStorage`, not on any Vector Lab server. What happens next depends on the tool and the provider:

- **Hosted apps** (LLMbench, for example, served from Vercel): a hosted-provider key can pass through the app's own serverless function, which forwards the request to the provider and keeps no copy of the key or the request. Each tool's FAQ states its own route.
- **Locally-run tools** (Vectorscope, Manifoldscope, Theoryscope, running on `http://localhost:3000` through `npm run dev`): the browser calls the provider directly; nothing transits a Vector Lab server at any point.
- **Ollama, in either case**: no key is involved, and nothing leaves your machine.

Clearing browser data or using a private window drops the keys from the browser. The lab operates no persistent store of them.

### How much does hosted use cost in practice?

Research sessions are usually under a few cents each on paid providers, because the lab's tools send short texts (a few sentences per request, not full documents). An afternoon of exploratory work with OpenAI typically lands below a dollar. Large batches (Manifold Atlas protocols that embed hundreds of texts, for example) will push into the one-to-few-dollar range. Set spend limits in your provider dashboard before starting.

<div class="section-head" markdown="1">
<p class="num">02 · Ollama</p>

## Running Ollama
</div>

Ollama runs language and embedding models on your own machine, with no key and no account. Three tools can use it in place of a hosted provider: Manifold Atlas and Manifoldscope (embeddings) and LLMbench (chat). Vectorscope, Theoryscope and Diffusion Atlas load their models directly and do not use Ollama.

### Install and pull models

1. Install from <https://ollama.com/download>.
2. Pull the two defaults:
   ```
   ollama pull nomic-embed-text
   ollama pull llama3.2
   ```
   `nomic-embed-text` is the embedding default for Manifold Atlas and Manifoldscope. `llama3.2` is the chat default for LLMbench, and is also what Manifold Atlas's Manifold Scan feature uses to generate related terms.
3. `ollama serve` (if it is not already running as a background service).

### The origins problem

This is where nearly everyone stalls. The hosted apps call Ollama directly from your browser. Ollama by default accepts calls only from `localhost`, so when a hosted app at an `https://` address calls `http://localhost:11434`, Ollama refuses it as a cross-origin request. The tool shows a connection error that has nothing to do with keys or models.

The fix is to tell Ollama which origins may call it, by setting `OLLAMA_ORIGINS` when you start the server. The origin to list is the **app** you run, not its documentation page. The documentation sites on `vector-lab-tools.github.io` never call Ollama and never need to be listed.

```
OLLAMA_ORIGINS="https://manifold-atlas.vercel.app,https://llm-bench-mu.vercel.app,http://localhost:3000,http://127.0.0.1:3000" ollama serve
```

Keep only the apps you use. Each app's Settings panel detects the origin you are on and pre-fills this command for you, so copying it from there is the safest route.

If you run a tool locally with `npm run dev` on `localhost:3000`, a plain `ollama serve` is enough, since Ollama already accepts `localhost`.

On macOS, to make the setting permanent when Ollama runs as a background service:

```
launchctl setenv OLLAMA_ORIGINS "https://manifold-atlas.vercel.app,https://llm-bench-mu.vercel.app,http://localhost:3000"
```

then quit and restart Ollama.

### Safari

Safari cannot reach a local Ollama from a hosted app. It blocks an `https://` page from calling `http://localhost` whatever `OLLAMA_ORIGINS` says, and this cannot be worked around from the lab side. For Ollama-backed work in the hosted Manifold Atlas or LLMbench, use **Chrome, Firefox, Edge, Arc or Brave**, or run a local copy.

Safari is fine against a local copy on `localhost:3000`, where both sides share an origin, and for every part of the lab that does not call Ollama from the browser.

### Which Ollama model should I pick?

**Embedding models** (Manifold Atlas, Manifoldscope)

- `nomic-embed-text` (262 MB): the default, if you pull only one.
- For comparison across models in Manifold Atlas, pull three whose floors are far apart, since agreement between near-identical geometries is not evidence of anything: `all-minilm` (44 MB, lowest floor), `nomic-embed-text` (mid floor), `snowflake-arctic-embed` (638 MB, highest floor). If disk is tight, `all-minilm` and `granite-embedding` together come to 104 MB and still span a usable range.
- `mxbai-embed-large` (1024d) and `embeddinggemma` (768d) also work in both tools.

**Chat models** (LLMbench)

- `llama3.2` (3B) or `gemma3`: light and quick, the local default.
- `qwen3`, `phi4`, `mistral`: stronger mid-size options.
- `llama3.3:70b` or `qwen2.5:72b`: approach the hosted models for quality, if you have the memory.

On a current Ollama every chat model returns token probabilities, so LLMbench's Probs view and probes work with any of them. If the Probs view stays empty, update Ollama.

Pull any of these with `ollama pull <model>`. Each tool's docs give the full reasoning and the floor measurements.

All of these are free, all run locally, none send data anywhere.

<div class="section-head" markdown="1">
<p class="num">03 · Other common questions</p>

## Everything else
</div>

### When was the Vector Lab started, and how has it developed?

The first instrument was LLMbench, begun in February 2026 as a workbench for close-reading the outputs of two language models side by side. Manifold Atlas followed in March 2026, moving from the prose surface to the geometry of embedding spaces.

The Vector Lab itself was founded on 17 April 2026, when the existing tools were brought together under one GitHub organisation, [vector-lab-tools](https://github.com/vector-lab-tools), with this site as its hub. Vectorscope had been started two days earlier; Manifoldscope and Theoryscope began the same day. This gave the lab its two tiers: comparative tools that work across models, and single-model scopes that open one model, one manifold or one corpus for intensive reading. Diffusion Atlas extended the comparative tier to image models later in April, and Vectorography, a type-design instrument, followed in August 2026.

In October 2026 each instrument took over its own documentation site, and the hub became the shared entry point, with this FAQ and the [Get started](get-started.html) page. The lab is developed by David M. Berry at the University of Sussex.

The hub and six of the instruments (LLMbench, Manifold Atlas, Vectorscope, Manifoldscope, Theoryscope and Diffusion Atlas) were built at Copenhagen Business School, Denmark, during an Otto Mønsted Visiting Professorship in 2026. The support of the Otto Mønsted Fond (grant 25-12-1849) is gratefully acknowledged.

Source code:

- [Vector Lab organisation](https://github.com/vector-lab-tools)
- [LLMbench](https://github.com/vector-lab-tools/LLMbench)
- [Manifold Atlas](https://github.com/vector-lab-tools/manifold-atlas)
- [Vectorscope](https://github.com/vector-lab-tools/vectorscope)
- [Manifoldscope](https://github.com/vector-lab-tools/manifoldscope)
- [Theoryscope](https://github.com/vector-lab-tools/theoryscope)
- [Diffusion Atlas](https://github.com/vector-lab-tools/diffusionatlas)
- [Vectorography](https://github.com/vector-lab-tools/vectorography)
- [This hub site](https://github.com/vector-lab-tools/vector-lab-tools.github.io)

### Which browser should I use?

Chrome, Edge, Brave, Arc, or Firefox for any work that calls Ollama. Safari works for everything else.

### Can I use the tools fully offline?

Yes, if every provider you have configured is local (Ollama). After the tool's page loads once, no outbound call is made beyond `localhost:11434`. You can disconnect from the network and keep working.

### The tool produces a different result each time I run it. Is that a bug?

No. Language and embedding model outputs are stochastic by default. Many of the lab's tools expose a temperature control (LLMbench, Diffusion Atlas) or a seed (Diffusion Atlas, Vectorography). Reproducing a specific result means fixing the seed and temperature explicitly.

### How do I cite the lab?

Cite the article first: Berry, D. M. (2026) 'Vector Theory: Epistemology, Political Economy, and Probabilistic Computation', *Philosophy & Technology*, 39, [doi:10.1007/s13347-026-01162-w](https://doi.org/10.1007/s13347-026-01162-w). It sets out the theory the instruments operationalise.

Then cite the tool you used, pinned to the version, with its Zenodo DOI from its repository README or docs page. To cite the Vector Lab as a whole rather than one tool, the hub has a concept DOI: [doi:10.5281/zenodo.23763598](https://doi.org/10.5281/zenodo.23763598).

### A tool is broken in a way not covered here

Each tool's documentation carries a troubleshooting section with the specific failures that tool produces. Start there. If it is not on this page, open an issue on the tool's [repository](https://github.com/vector-lab-tools) to report the problem. If you have a fix, a pull request is welcome.
