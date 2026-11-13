---
layout: default
title: Teaching
---

<div class="section-head" markdown="1">
<p class="num">00 · Teaching</p>

# Using the lab with students
</div>

Short activities for a single class, built on the two hosted instruments, [LLMbench](https://vector-lab-tools.github.io/LLMbench/) and [Manifold Atlas](https://vector-lab-tools.github.io/manifold-atlas/), so nothing needs installing. Each one gives what students do, what they should see, and questions for discussion. Times are approximate. Adapt the prompts and concepts to your subject.

<div class="section-head" markdown="1">
<p class="num">01 · Before the class</p>

## Setting up a room
</div>

The apps run in the browser. A model has to sit behind them, and there are three ways to provide one:

- **Your university's AI gateway.** If your institution runs one, students can create their own key on it and enter it under the OpenAI-compatible provider. The [LLMbench FAQ](https://vector-lab-tools.github.io/LLMbench/#faq) walks through the settings. This also teaches students what an API key is.
- **Ollama on the lab machines.** Free and local, with nothing leaving the room. Use Chrome, Firefox or Edge, not Safari, and set `OLLAMA_ORIGINS` as the [FAQ]({{ '/faq.html' | relative_url }}#running-ollama) describes.
- **One key, at the front.** The instructor runs the app on a projector and the class directs it.

Keys are kept in each browser, so students on shared machines should clear them at the end.

<div class="section-head" markdown="1">
<p class="num">02 · LLMbench</p>

## Reading generated text
</div>

<div class="activities">

<article class="activity">
  <p class="eyebrow">Activity 1 · about 15 minutes</p>
  <h3>Tokens are not words</h3>
  <p><strong>Do.</strong> Generate a short answer to any prompt, then switch on the Probs view.</p>
  <p><strong>See.</strong> The text breaks into the units the model actually produces: parts of words, words with a leading space, punctuation on its own.</p>
  <p><strong>Discuss.</strong> Why would a model work in these units rather than words? What happens to a rare name or a technical term?</p>
</article>

<article class="activity">
  <p class="eyebrow">Activity 2 · about 20 minutes</p>
  <h3>The likeliest word is not always chosen</h3>
  <p><strong>Do.</strong> Start a sentence such as "The most important quality in a leader is" and open the Probs view on the next token.</p>
  <p><strong>See.</strong> The chosen token next to the alternatives the model weighed, each with its probability. The chosen one is often not the most probable.</p>
  <p><strong>Discuss.</strong> If the model is not picking the likeliest word, what is it doing? What does that mean for treating its output as an answer?</p>
</article>

<article class="activity">
  <p class="eyebrow">Activity 3 · about 20 minutes</p>
  <h3>Turning the temperature dial</h3>
  <p><strong>Do.</strong> Run one prompt across several temperatures in the Temperature Gradient mode.</p>
  <p><strong>See.</strong> At low settings the answers converge; as the setting rises, content, tone and even the strategy of the answer change.</p>
  <p><strong>Discuss.</strong> Which setting would you want for a contract, a poem, a news summary? Who chooses it in the AI tools you use?</p>
</article>

<article class="activity">
  <p class="eyebrow">Activity 4 · about 30 minutes</p>
  <h3>Same prompt, two models</h3>
  <p><strong>Do.</strong> In Compare, give two models the same writing task. Turn on the Tone overlay and annotate where they differ.</p>
  <p><strong>See.</strong> Each model's hedges, boosters and self-mentions marked in the text, and the points where the two answers part.</p>
  <p><strong>Discuss.</strong> Does each model have a voice? Which one would you trust, and on what grounds?</p>
</article>

<article class="activity">
  <p class="eyebrow">Activity 5 · about 30 minutes</p>
  <h3>Which genres are templated?</h3>
  <p><strong>Do.</strong> Ask for the opening of an essay in your own discipline, then the opening of a short story, and compare the perplexity of the first token.</p>
  <p><strong>See.</strong> Some genres leave the model almost certain of its first word; others leave it divided. LLMbench's <a href="https://vector-lab-tools.github.io/LLMbench/#cases">case studies</a> show the pattern across six fields.</p>
  <p><strong>Discuss.</strong> What does it mean that a genre is predictable to a model? Is the predictability in the model or in the genre?</p>
</article>

</div>

<div class="section-head" markdown="1">
<p class="num">03 · Manifold Atlas</p>

## Meaning as geometry
</div>

<div class="activities">

<article class="activity">
  <p class="eyebrow">Activity 6 · about 15 minutes</p>
  <h3>A walk between two concepts</h3>
  <p><strong>Do.</strong> Choose two concepts from your subject and run a Vector Walk from one to the other.</p>
  <p><strong>See.</strong> The path the model's geometry takes, and the concepts it passes on the way.</p>
  <p><strong>Discuss.</strong> Are the stops on the way the ones you would expect? What does the path say about how the model has organised the field?</p>
</article>

<article class="activity">
  <p class="eyebrow">Activity 7 · about 20 minutes</p>
  <h3>Does "not" move the meaning?</h3>
  <p><strong>Do.</strong> Enter a statement in the Negation Gauge and compare it with its negation.</p>
  <p><strong>See.</strong> How far apart the model places a claim and its denial, on that model's own calibrated scale.</p>
  <p><strong>Discuss.</strong> If a statement and its opposite sit close together, what follows for search, summarising or fact-checking built on these models?</p>
</article>

<article class="activity">
  <p class="eyebrow">Activity 8 · about 30 minutes</p>
  <h3>Where does a contested word sit?</h3>
  <p><strong>Do.</strong> Place a word such as "freedom" or "democracy" in the Hegemony Compass, between two competing framings, and repeat across models.</p>
  <p><strong>See.</strong> Which framing each model pulls the word towards.</p>
  <p><strong>Discuss.</strong> Where could that default have come from? Who decides what the neutral position is?</p>
</article>

</div>

<div class="section-head" markdown="1">
<p class="num">04 · With an install</p>

## For a lab session
</div>

These instruments run locally, so they suit a session where students can install software, or a seminar with a demonstration at the front.

- **[Vectorscope](https://vector-lab-tools.github.io/vectorscope/):** open GPT-2, which needs no account, and look inside it layer by layer.
- **[Diffusion Atlas](https://vector-lab-tools.github.io/diffusionatlas/):** run a Guidance Sweep and watch one prompt's image change as guidance rises.
- **[Vectorography](https://vector-lab-tools.github.io/vectorography/):** treat a typeface as a point in a space of letterforms, and move it with the sliders.
- **[Theoryscope](https://vector-lab-tools.github.io/theoryscope/):** load the built-in demonstration corpus and read the geometry of a body of theory.

<p class="browse-all">For research use beyond a single class, see the <a href="{{ '/get-started.html' | relative_url }}">first-month route</a> on Get started. If you teach with the lab, an issue on the tool's <a href="https://github.com/vector-lab-tools">repository</a> describing what you did helps others plan theirs.</p>
