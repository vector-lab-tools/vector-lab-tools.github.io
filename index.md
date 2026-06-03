---
layout: default
title: Vector Lab
---

<section class="hero">
  <div class="hero-text">
    <h1>Vector Lab</h1>
    <p class="tagline">Vector methods for vector theory.</p>
  </div>
  <div class="hero-visual">
    <img src="/assets/images/hero.svg" alt="A warped manifold rendered as a wireframe field with sampled points and origin axes.">
  </div>
</section>

<section class="lede">

Large language models, the neural networks behind contemporary AI systems such as ChatGPT, Gemini, and Claude, reorganise meaning as geometry. Every token, every concept, every sentence is assigned a position in a high-dimensional vector space whose axes are no-one's axes and whose distances no-one chose. What any given model can say about democracy, about poltics, the economy, society, or everyday life is filtered through this vector space. Questions even about contested ideas of intelligence are constrained by the geometry that model has learned. And that geometry carries the sedimented assumptions of the corpus, the labour regime, and the economic pressures that produced it.

We could call this the geometrisation of thought. What has been missing is the corresponding set of tools. Reading papers about the manifold is not the same as inspecting the manifold. Claiming that a model has naturalised market-liberal notions of democracy is not the same as measuring the pull. The work is critical-empirical, and vector tools are needed to address this.

Vector Lab is that toolkit. The instruments are arranged in two tiers. The inner tier opens single objects for intensive inspection: a single language model, a single manifold, a single corpus of theoretical texts. The outer tier works across models, asking comparative questions at the level of output embeddings, generated prose, and diffusion trajectories. The inner tier supplies the anatomical detail. The outer tier provides the comparative grounds on which theoretical claims can be tested.

</section>

## The family

<div class="mermaid">
graph TB
  subgraph scopes["Single-model scopes (intensive)"]
    T["Theoryscope\ncorpus"]
    V["Vectorscope\nmodel internals"]
    M["Manifoldscope\none manifold"]
  end

  subgraph comparative["Comparative tools (extensive)"]
    A["Manifold Atlas\nbetween language models"]
    L["LLMbench\nbetween prose outputs"]
    D["Diffusion Atlas\nbetween image models"]
  end

  V -.provenance.-> M
  M -.provenance.-> A
  A -.surface reading.-> L
  T -.eigendirections of theory.-> V

  classDef scope fill:#ffffff,stroke:#a8854d,color:#181818,stroke-width:1.2px;
  classDef comp fill:#ffffff,stroke:#7a2e2e,color:#181818,stroke-width:1.2px;
  class T,V,M scope;
  class A,L,D comp;
</div>

### Comparative tools

<div class="tools-grid">

<article class="tool-card comparative">
  <img class="tool-icon" src="/assets/images/tools/manifold-atlas.svg" alt="">
  <h3><a href="/tools/manifold-atlas.html">Manifold Atlas</a></h3>
  <p class="object">Object: output embeddings across models.</p>
  <p>Concept distance, negation gauge, hegemony compass, silence detector, agonism test, vector logic. The comparative cartographic instrument.</p>
</article>

<article class="tool-card comparative">
  <img class="tool-icon" src="/assets/images/tools/llmbench.svg" alt="">
  <h3><a href="/tools/llmbench.html">LLMbench</a></h3>
  <p class="object">Object: generated prose across models.</p>
  <p>Dual-panel close reading, annotation, logprobs, probability visualisation. The hermeneutic surface instrument.</p>
</article>

<article class="tool-card comparative">
  <img class="tool-icon" src="/assets/images/tools/diffusion-atlas.svg" alt="">
  <h3><a href="/tools/diffusion-atlas.html">Diffusion Atlas (alpha)</a></h3>
  <p class="object">Object: generative trajectories and compositional fidelity across diffusion image models.</p>
  <p>Denoise trajectory, guidance sweep, latent neighbourhood, compositional bench. Atlas and Bench registers in one instrument.</p>
</article>

</div>

### Single-model scopes

<div class="tools-grid">

<article class="tool-card scope">
  <img class="tool-icon" src="/assets/images/tools/vectorscope.svg" alt="">
  <h3><a href="/tools/vectorscope.html">Vectorscope (beta)</a></h3>
  <p class="object">Object: a single open-weight model.</p>
  <p>Layer-by-layer weights, hidden states, attention, precision regimes. The anatomical instrument of the lab.</p>
</article>

<article class="tool-card scope">
  <img class="tool-icon" src="/assets/images/tools/manifoldscope.svg" alt="">
  <h3><a href="/tools/manifoldscope.html">Manifoldscope (beta)</a></h3>
  <p class="object">Object: a single manifold.</p>
  <p>Intrinsic dimension, curvature, density, topology, and the political reading of what a geometry sediments or refuses. Measure and critique bound together.</p>
</article>

<article class="tool-card scope">
  <img class="tool-icon" src="/assets/images/tools/theoryscope.svg" alt="">
  <h3><a href="/tools/theoryscope.html">Theoryscope (beta)</a></h3>
  <p class="object">Object: a corpus of theoretical texts.</p>
  <p>Renormalisation-group flow, eigendirections, fixed points, universality classes. A navigable geometry of theory space.</p>
</article>

</div>

## Theoretical Background

The vector lab tools are designed to open the "vector box" of artificial intelligence. The key argument is that there is a shift from the digital to the vector. Our tools and approaches have to correspondingly shift also. Commercial embedding APIs return sentence-level composites from separately-trained embedding models, the output of a pipeline rather than a window into the representations themselves. This is fine for some tasks. It is inadequate for critical work. If we want to know what the geometry of a particular model has sedimented, we have to work with open-weight models where the weights, activations, and token embeddings can be read at every layer. Vector Lab tools therefore privilege open-weight models wherever the question requires internal access, and treat commercial outputs as a separate object, the retrieval surface, with its own interest.

The result is a set of instruments that do things other research tools do not. Vectorscope runs the same inputs across precision regimes, FP32 through BF16, INT8, INT4, FP4, INT2, to observe how signal degrades as the medium is quantised, on the principle that the material substrate of a representation shapes what it can hold. Manifoldscope treats each manifold as a geometric object (intrinsic dimension, curvature, density) and as an ideological object (what it naturalises, suppresses, sediments), binding measure to critique so that no interpretive claim goes without its attestation. Theoryscope applies renormalisation-group and eigenvector methods to corpora of theoretical texts, asking which positions are fixed points under coarse-graining and which traditions are universality classes of one another. Manifold Atlas runs fifteen operations across multiple embedding models, turning particular vector-theoretic claims into empirically testable propositions. LLMbench sets two models' prose outputs side by side and enables the dual-panel close reading that hermeneutic work requires.

The tools are designed to explore the new media-theoretic terrain of AI, which are listed in each repository's documentation and developed in the essays that motivate them. Critical work on large language models has, for a decade, been constrained by a tooling deficit. Either work with commercial APIs, and accept the interpretive costs, or do without tools and write essays that assert what a geometry looks like without ever seeing one. Vector Lab is an attempt to close that gap, to produce instruments that are continuous with the theoretical project rather than imported from outside it, and to make them public so that others can use, extend, or disagree with the work they do.

## How the instruments relate

The instruments work at two scales and across two modalities. The single-model scopes are anatomical: they open one object (a model, a manifold, a corpus) and read its internal geometry at depth. The comparative tools are cartographic: they survey across many objects (across language models, across diffusion models, across generated outputs) and ask what each kind of geometry has naturalised. Anatomical and cartographic readings are complementary; a finding flagged at the comparative level is sharpened by an anatomical attestation, and an anatomical reading needs the comparative ground to know whether what it has found is local or generic.

The modality split is doing work too. Language models and diffusion models share the underlying vector regime, but their geometries are not interchangeable. The manifold framing migrates more cleanly to diffusion than it does to autoregressive text, and that asymmetry is itself an argument the lab is set up to develop. Theoretical corpora sit alongside the model registers as a third object whose geometry can be read with comparable methods, opening reflexive comparisons between the eigendirections of a body of theory and the model trained on it.

Generated prose is the hermeneutic surface that sits above the geometric work. It is the level at which models are usually encountered, and it is often the presentation layer for findings that begin lower down: a claim tested geometrically can be illustrated, read closely, and compared across models in prose form.

## Further reading

The tools operationalise claims developed across the vector theory sequence on Stunlaw and in the wider research programme. The essays are the conceptual statements; the tools are the empirical instruments that test, extend, and sometimes contradict them.

### The vector theory sequence (Stunlaw)

- [*The Vector Medium*](https://stunlaw.blogspot.com/2026/03/the-vector-medium.html), names the vector regime as a periodising category for contemporary media.
- [*Vector Theory*](https://stunlaw.blogspot.com/2026/02/vector-theory.html?m=1) - gives the theoretisation of the move from digital to vectors. 
- [*Generation Vector*](https://stunlaw.blogspot.com/2026/02/generation-vector.html), examines the implications for a generation that is surrounded by AI.
- [*What Is Vector Space?*](https://stunlaw.blogspot.com/2026/03/what-is-vector-space.html), characterises vector space as a new medium constituted by dimensionality. Vectorscope is the empirical instrument that follows.
- *What Is the Manifold?* Coming soon, develops the manifold as the medium through which large language models render meaning legible. Manifold Atlas and Manifoldscope follow.
- *What Is Theory Space?* Coming soon, names the space of counterfactual media from which any particular manifold is selected.

### Books and longer work on Vectors

- Beguš, N. (2025) *Artificial Humanities*. University of Michigan Press.
- Berry, D. M. (2014) *Critical Theory and the Digital*. Bloomsbury.
- Berry, D.M. (2025) ‘Synthetic media and computational capitalism: towards a critical theory of artificial intelligence’, *AI & SOCIETY*, 40(7), pp. 5257–5269. Available at: https://doi.org/10.1007/s00146-025-02265-2.
- Impett, L. and Offert, F. (2026) *Vector Media*. University of Minnesota Press.
- Kittler, F. (1999) *Gramophone, Film, Typewriter*. Stanford University Press.
- McLuhan, M. (1962) *The Gutenberg Galaxy: The Making of Typographic Man*. University of Toronto Press.
- Pasquinelli, M. (2023) *The Eye of the Master: A Social History of AI*. Verso.

### Further reading

Wider background in media theory, critical theory of technology, and the pre-history of AI.

- Ackerman, A., Gefen, A., Somaini, A. and Viewing, P. (eds.) (2025) *The World Through AI: Exploring Latent Spaces*. Exhibition catalogue. Paris: Jeu de Paume / JBE Books.
- Alpaydin, E. (2016) *Machine Learning: The New AI*. Cambridge, Massachusetts: The MIT Press (MIT Press Essential Knowledge series).
- Berry, D.M. (2011) *The Philosophy of Software: Code and Mediation in the Digital Age*. Basingstoke: Palgrave Macmillan.
- Berry, D.M. (2019) ‘Against Infrasomatization: Towards a Critical Theory of Algorithms’, in Bigo, D., Isin, E. and Ruppert, E. (eds.) *Data Politics*. London: Routledge.
- Castells, M. (2013) *Communication Power*. Oxford: Oxford University Press.
- Chun, W.H.K. (2021) *Discriminating Data: Correlation, Neighborhoods, and the New Politics of Recognition*. Cambridge, MA: MIT Press.
- Ciston, S., Berry, D.M., Hay, A., Marino, M.C., Millican, P., Shrager, J., Schwarz, A. and Weil, P. (2026) *Inventing ELIZA: How the First Chatbot Shaped the Future of AI*. Software Studies series. MIT Press.
- Deleuze, G. (1992) ‘Postscript on the Societies of Control’, *October*, 59, pp. 3–7.
- Dourish, P. (2017) *The Stuff of Bits: An Essay on the Materialities of Information*. Cambridge, MA: MIT Press.
- Ernst, W. (2013) *Digital Memory and the Archive*. Minneapolis: University of Minnesota Press.
- Galloway, A.R. (2004) *Protocol: How Control Exists After Decentralization*. Cambridge, MA: MIT Press.
- Hayles, N.K. (2017) *Unthought: The Power of the Cognitive Nonconscious*. Chicago: University of Chicago Press.
- Hayles, N.K. (2025) *Bacteria to AI: Human Futures with Our Nonhuman Symbionts*. Chicago: University of Chicago Press.
- Kittler, F. (1997) *Literature, Media, Information Systems*. Abingdon, New York: Routledge.
- Kittler, F. (1997) ‘There Is No Software’, in *Literature, Media, Information Systems*. Abingdon, New York: Routledge, pp. 147–155.
- Krämer, S. (2025) ‘How should the generative power of Large Language Models (LLMs) be interpreted? Do chatbots understand linguistic meaning?’, *Philosophy & Digitality*, 2(1), pp. 122–141. Available at: <https://doi.org/10.18716/pd.v2i1.11660>.
- Liu, L.H. (2023) ‘After Turing: How Philosophy Migrated to the AI Lab’, *Critical Inquiry*, 50(1), pp. 2–30.
- Manovich, L. (2002) *The Language of New Media*. Cambridge, Mass.: MIT Press.
- Manovich, L. and Arielli, E. (2024) *Artificial Aesthetics: Generative AI, Arts and Visual Media*.
- Polanyi, M. (2009) *The Tacit Dimension*. Revised ed. Chicago: University of Chicago Press.
- Rogers, R. (2013) *Digital Methods*. Cambridge, Massachusetts: MIT Press.
- Silverstone, R. (1999) *Why Study the Media?* London: SAGE Publications.
- Simondon, G. (2017) *On the Mode of Existence of Technical Objects*. Minneapolis: University of Minnesota Press.
- Sofroniew, N., Kauvar, I., Saunders, W., Chen, R., Henighan, T., Hydrie, S., Citro, C., Pearce, A., Tarng, J., Gurnee, W., Batson, J., Zimmerman, S., Rivoire, K., Fish, K., Olah, C. and Lindsey, J. (2026) ‘Emotion Concepts and their Function in a Large Language Model’, *Transformer Circuits Thread*, 2 April. Available at: <https://transformer-circuits.pub/2026/emotions/index.html>.
- Somaini, A. (2023) ‘A Theory of Latent Spaces’, *Grey Room*, 93.
- Steyerl, H. (2025) *Medium Hot: Images in the Age of Heat*. London: Verso.
- Stiegler, B. (2016) *Automatic Society: Volume 1: The Future of Work*. Cambridge: Polity.
- Weizenbaum, J. (1976) *Computer Power and Human Reason: From Judgment to Calculation*. San Francisco: Freeman.
- Winner, L. (1980) ‘Do Artifacts Have Politics?’, *Daedalus*, 109(1), pp. 121–136.

## Using the tools

Each repository contains full documentation, dependencies, and setup instructions. Tools are research instruments and are offered as-is under permissive licences. If Vector Lab tools support published research, please cite the specific tool and version, and cite the relevant theoretical essays where the claims being tested are developed.

{% include mermaid.html %}
