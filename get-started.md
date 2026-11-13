---
layout: default
title: Get started
---

<div class="section-head" markdown="1">
<p class="num">00 · Get started</p>

# Pick a path
</div>

The Vector Lab is seven instruments. Two questions will put you at the right starting point.

<div class="paths">

<article class="path-card">
  <p class="eyebrow">Path 1</p>
  <h2>I want to comparatively close-read AI models</h2>
  <p>Two models answer the same prompt. You read them side by side, annotate, link passages, inspect token probabilities. The prose is the object.</p>
  <p class="path-primary">
    <strong>Start with LLMbench.</strong> <a href="https://vector-lab-tools.github.io/LLMbench/">Docs →</a>
  </p>
  <p class="path-also">Then: <a href="https://vector-lab-tools.github.io/manifold-atlas/">Manifold Atlas</a> for the geometry underneath the prose, or <a href="https://vector-lab-tools.github.io/diffusionatlas/">Diffusion Atlas</a> for image models.</p>
</article>

<article class="path-card">
  <p class="eyebrow">Path 2</p>
  <h2>I want to research the internals of embedding spaces</h2>
  <p>Watch a particle cross a manifold from one concept to another. Measure how much space a model actually gives to negation. Place a contested concept between two ideological clusters and see which side it drifts to. The manifold is the object; the prose is downstream.</p>
  <p class="path-primary">
    <strong>Start with Manifold Atlas.</strong> <a href="https://vector-lab-tools.github.io/manifold-atlas/">Docs →</a>
  </p>
  <p class="path-also">Then: <a href="https://vector-lab-tools.github.io/vectorscope/">Vectorscope</a> to open a single model's weights, <a href="https://vector-lab-tools.github.io/manifoldscope/">Manifoldscope</a> for one manifold in depth, <a href="https://vector-lab-tools.github.io/theoryscope/">Theoryscope</a> for a corpus of theoretical texts.</p>
</article>

</div>

<p class="browse-all">Or <a href="{{ '/tools.html' | relative_url }}">browse the full family</a>. Teaching a class? See <a href="{{ '/teaching.html' | relative_url }}">activities for students</a>. Stuck on API keys or Ollama? See the <a href="{{ '/faq.html' | relative_url }}">FAQ</a>.</p>

<div class="section-head" markdown="1">
<p class="num">01 · A first month</p>

## For PhD students and new researchers
</div>

A route from a first run to a result you can put in a thesis chapter. Each step links into the instrument's own documentation, which carries the detail. The steps are the same on either path; the links differ.

<ol class="steps">

<li class="step">
  <p class="eyebrow">Step 1 · First day</p>
  <h3>Run the worked example</h3>
  <p>Get one result on screen before reading any theory. Both instruments open on a worked example with its result stated, and the steps to reproduce it beneath.</p>
  <ul class="step-links">
    <li><strong>LLMbench:</strong> <a href="https://vector-lab-tools.github.io/LLMbench/#example">two models part at the first word</a>, reproducible in about twenty minutes.</li>
    <li><strong>Manifold Atlas:</strong> <a href="https://vector-lab-tools.github.io/manifold-atlas/#start">three ways to run it</a>, then the first <a href="https://vector-lab-tools.github.io/manifold-atlas/#examples">worked example</a>: does the model register negation?</li>
  </ul>
  <p class="step-note">No API key is needed for either: run Ollama locally. If setup stalls, the <a href="{{ '/faq.html' | relative_url }}">FAQ</a> covers keys, Ollama and the Safari limitation.</p>
</li>

<li class="step">
  <p class="eyebrow">Step 2 · First week</p>
  <h3>Find your discipline in the case studies</h3>
  <p>Both instruments carry case studies across six disciplines, among them History, Philosophy, Sociology and Literature. Pick the one nearest your own field, reproduce it, then change one thing: your own prompt, your own pair of concepts, a different model.</p>
  <ul class="step-links">
    <li><strong>LLMbench:</strong> <a href="https://vector-lab-tools.github.io/LLMbench/#cases">six fields, six readings</a>.</li>
    <li><strong>Manifold Atlas:</strong> <a href="https://vector-lab-tools.github.io/manifold-atlas/#cases">six fields, six batteries</a>.</li>
  </ul>
</li>

<li class="step">
  <p class="eyebrow">Step 3 · Weeks two and three</p>
  <h3>Design your own study</h3>
  <p>The instruments are built for comparison, and the case studies show the method:</p>
  <ul class="step-list">
    <li><strong>Compare across models.</strong> One model's output describes that model. Run at least two, and if possible three, before claiming anything about language models in general.</li>
    <li><strong>Repeat runs.</strong> Generation is stochastic. In LLMbench, run the same prompt more than once and fix the temperature you report.</li>
    <li><strong>Calibrate before reading a number.</strong> In Manifold Atlas a cosine means nothing until you know where the model's floor sits. Report the calibrated position, not the raw cosine.</li>
    <li><strong>Use controls.</strong> Compare your probe against an edit of the same size that does not change the meaning. Manifold Atlas's case studies were rerun as batteries with matched controls, and four of the six single-probe conclusions did not survive.</li>
    <li><strong>Keep sensitive material local.</strong> Interview data or unpublished text should go through Ollama, so nothing leaves your machine.</li>
  </ul>
</li>

<li class="step">
  <p class="eyebrow">Step 4 · Alongside</p>
  <h3>Read the theory</h3>
  <p>The instruments operationalise claims made in vector theory, and a chapter that uses them needs that frame.</p>
  <ul class="step-links">
    <li>Berry, D. M. (2026) '<a href="https://doi.org/10.1007/s13347-026-01162-w">Vector Theory</a>', <em>Philosophy &amp; Technology</em>. Open access.</li>
    <li>The About sections of <a href="https://vector-lab-tools.github.io/LLMbench/#about">LLMbench</a> and <a href="https://vector-lab-tools.github.io/manifold-atlas/#about">Manifold Atlas</a>, on why the method is shaped as it is.</li>
    <li>The hub's <a href="{{ '/' | relative_url }}#further-reading">further reading</a>.</li>
  </ul>
</li>

<li class="step">
  <p class="eyebrow">Step 5 · Writing up</p>
  <h3>Record, archive and cite</h3>
  <ul class="step-list">
    <li><strong>Record the conditions of every run:</strong> the model and provider, the date, the tool version, and settings such as temperature. Hosted models change without notice, so a result is tied to its date.</li>
    <li><strong>Keep the exports.</strong> Both instruments export results; archive them with your notes so a figure can be traced back to its run.</li>
    <li><strong>Cite the article first, then the tool.</strong> The preferred citation for work using the lab is Berry, D. M. (2026) 'Vector Theory: Epistemology, Political Economy, and Probabilistic Computation', <em>Philosophy &amp; Technology</em>, 39, <a href="https://doi.org/10.1007/s13347-026-01162-w">doi:10.1007/s13347-026-01162-w</a>. Add the tool and the version you used as a second reference, with its Zenodo DOI from the repository or docs page (Manifold Atlas: <a href="https://vector-lab-tools.github.io/manifold-atlas/#cite">Citing</a>). The "Cite this repository" button on each GitHub repository gives both.</li>
  </ul>
</li>

</ol>

<p class="browse-all">Something not working, or not covered here? Each tool's docs end with a FAQ, and problems go to the tool's <a href="https://github.com/vector-lab-tools">repository</a> as an issue.</p>
