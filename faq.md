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

### What's the cheapest way to try the lab?

Install **Ollama** locally and pull two models: an embedding model (`nomic-embed-text`) and a chat model (`llama3.2` is a reasonable default). Nothing else is required. No keys, no paid providers, no rate limits. Instructions in [Running Ollama](#running-ollama) below. The free path also works with **Hugging Face Inference** for embedding tools, which gives you access to models you cannot run locally in exchange for sign-up and a rate limit.

### Which tools need which keys?

| Tool              | Needs a key for                                                                 | Free local route                                     |
|-------------------|---------------------------------------------------------------------------------|------------------------------------------------------|
| LLMbench          | Chat models: OpenAI, Anthropic, Google, HF, OpenRouter, OpenAI-compatible       | Ollama for chat                                      |
| Manifold Atlas    | Embedding models: OpenAI, Voyage, Google, Cohere, HF                            | Ollama for embeddings                                |
| Vectorscope       | Hugging Face token (read scope) only for gated models (Llama 3.2 1B, Mistral 7B v0.3); GPT-2 and Qwen3 need no account | Runs locally through Transformers; weights cache in `~/.cache/huggingface/` after first load |
| Manifoldscope     | Embedding models (same set as Manifold Atlas), when you want hosted ones        | Runs MiniLM via sentence-transformers out of the box |
| Theoryscope       | Zotero (to read your library)                                                   | Every embedding runs locally; no provider key needed |
| Diffusion Atlas   | Replicate or Fal for hosted generation                                          | Local diffusers backend (downloads weights from HF)  |
| Vectorography     | Nothing. Runs on its own Hugging Face Space.                                    | n/a                                                  |

### Where do I get an API key for each provider?

- **OpenAI** — <https://platform.openai.com/api-keys>. Starts `sk-`. Paid; no free tier.
- **Anthropic** — <https://console.anthropic.com/settings/keys>. Starts `sk-ant-`. Paid; no free tier.
- **Google (Gemini)** — <https://aistudio.google.com/apikey>. Starts `AIza`. Free tier, generous for research.
- **Hugging Face** — <https://huggingface.co/settings/tokens>. Starts `hf_`. Free inference API, rate limited.
- **OpenRouter** — <https://openrouter.ai/keys>. Starts `sk-or-`. Pay-as-you-go across many providers.
- **Voyage AI** — <https://dashboard.voyageai.com/api-keys>. Starts `pa-`. Free tier; recommended by Anthropic for use with Claude.
- **Cohere** — <https://dashboard.cohere.com/api-keys>. Starts `co-`. Free tier.
- **Replicate** — <https://replicate.com/account/api-tokens>. Starts `r8_`. Pay-per-second.
- **Fal** — <https://fal.ai/dashboard/keys>. Pay-per-image.
- **Zotero** — <https://www.zotero.org/settings/security#applications>. Create a new key, give it library read access.

### Are my keys sent anywhere I'm not expecting?

No. Every tool in the lab runs client-side. Keys are stored in your browser's `localStorage` and sent directly to the provider you configured. The lab operates no servers that see your keys or your requests. If you clear your browser data or use a private window, the keys are gone.

### How much does hosted use cost in practice?

Research sessions are usually under a few cents each on paid providers, because the lab's tools send short texts (a few sentences per request, not full documents). An afternoon of exploratory work with OpenAI typically lands below a dollar. Large batches (Manifold Atlas protocols that embed hundreds of texts, for example) will push into the one-to-few-dollar range. Set spend limits in your provider dashboard before starting.

<div class="section-head" markdown="1">
<p class="num">02 · Ollama</p>

## Running Ollama
</div>

Ollama runs language and embedding models on your own machine. Every Vector Lab tool can use it in place of a paid provider. The setup is the same across the family.

### Install and pull models

1. Install from <https://ollama.com/download>.
2. Pull the models the lab uses most:
   ```
   ollama pull nomic-embed-text
   ollama pull llama3.2
   ```
   `nomic-embed-text` is a 768-dimensional embedding model and is the safe default for Manifold Atlas, Manifoldscope, Theoryscope. `llama3.2` is a compact chat model for LLMbench and for Theoryscope's Manifold Scan feature.
3. `ollama serve` (if it is not already running as a background service).

### The browser-direct origins problem

The lab's tools run in your browser. Ollama by default rejects requests from any origin other than `localhost`. When your browser at `vector-lab-tools.github.io` calls Ollama at `http://localhost:11434`, Ollama refuses the request as a cross-origin violation. The tool will show a connection error that is not about keys or models; it is about origins.

The fix is to tell Ollama which origins may call it. Set `OLLAMA_ORIGINS` when you start the server:

```
OLLAMA_ORIGINS="https://vector-lab-tools.github.io,https://vector-humanities.github.io,http://localhost:3000,http://127.0.0.1:3000" ollama serve
```

Include every origin from which you run the lab's tools: the hosted sites you use, and any local development servers. On macOS, if Ollama is installed as a service, you can set the variable permanently:

```
launchctl setenv OLLAMA_ORIGINS "https://vector-lab-tools.github.io,http://localhost:3000"
```

then restart Ollama.

### Safari does not work for browser-direct Ollama

Safari refuses to call `http://localhost` from an `https://` page, even with `OLLAMA_ORIGINS` set. This is a WebKit security policy that cannot be worked around from the lab side. Use **Chrome, Edge, Brave, Arc, or Firefox** for any work that calls Ollama from the browser. Safari is fine for every other part of the lab.

### Which Ollama model should I pick?

- **Embedding**: `nomic-embed-text` (768-d, fast) is the general-purpose default. `snowflake-arctic-embed` is larger and better calibrated for English, but slower. `all-minilm` (384-d) is the smallest and useful when you want a model whose floor the rest of the lab calibrates against.
- **Chat**: `llama3.2` (3B) is the compact default. `gemma3` and `qwen2.5` are reasonable alternatives. `llama3.1:8b` is better for longer-form generation in LLMbench if your machine has the memory.

All of these are free, all run locally, none send data anywhere.

<div class="section-head" markdown="1">
<p class="num">03 · Other common questions</p>

## Everything else
</div>

### Which browser should I use?

Chrome, Edge, Brave, Arc, or Firefox for any work that calls Ollama. Safari works for everything else.

### Can I use the tools fully offline?

Yes, if every provider you have configured is local (Ollama). After the tool's page loads once, no outbound call is made beyond `localhost:11434`. You can disconnect from the network and keep working.

### The tool produces a different result each time I run it. Is that a bug?

No. Language and embedding model outputs are stochastic by default. Many of the lab's tools expose a temperature control (LLMbench, Diffusion Atlas) or a seed (Diffusion Atlas, Vectorography). Reproducing a specific result means fixing the seed and temperature explicitly.

### How do I cite the lab?

Each tool carries its own DOI on its repository README; cite the tool you used, pinned to the version. If you want to cite the Vector Lab as a whole, the hub has a concept DOI: [doi:10.5281/zenodo.23763598](https://doi.org/10.5281/zenodo.23763598).

### A tool is broken in a way not covered here

Each tool's documentation carries a troubleshooting section with the specific failures that tool produces. Start there. If it is a cross-cutting problem not on this page, let David know and I'll add it.
