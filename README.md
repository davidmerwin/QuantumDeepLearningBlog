# QuantumDeepLearningBlog
https://medium.com/@davidjeffreymerwin

---

## Key sources in context

Background for the quantum deep-learning writing linked above and for the notebook in this repository, written as a compact annotated bibliography. None is used to claim a quantum advantage. <sup>[E1](#en1)</sup>

**How to read each entry.** The *caption*, *metadata*, *descriptors*, *tags* and *labels* form the catalog card. The *abstract*, *gloss*, *commentary* (with its *elucidation* and *exposition*), *exegesis* and *critique* are the reading. *Marginalia* point to files in this repository, *scholia* compare the sources with each other, and each entry has one *footnote*. The anchors (`#b11`, `#b11-fn`) are the *markup*. Code comments, docstrings, directives and decorators in this repository are listed after the entries.

**Sources:** [B19](#b19) · [B26](#b26) · [B24](#b24) · [B39](#b39) · [B38](#b38) · [B27](#b27) · [B23](#b23) <sup>[E2](#en2)</sup>

<a id="b19"></a>

### B19 · TensorFlow Quantum: A Software Framework for Quantum Machine Learning

> **Caption.** Cirq circuits as Keras layers: hybrid quantum-classical ML.

**Metadata.** Michael Broughton, Guillaume Verdon, Trevor McCourt, et al. (2020). *arXiv:2003.02989*. Preprint. [arxiv.org/abs/2003.02989](https://arxiv.org/abs/2003.02989). Verified 10 Nov 2026.<br>
**Descriptors.** Software toolchain · Quantum machine learning · **Tags.** `tfq` `keras` `pqc` `hello-many-worlds` · **Labels.** `evidence:preprint` `role:tool` `type:preprint` `status:verified`

- **Abstract.** Describes TensorFlow Quantum's design for representing circuits as tensors, differentiating parameterised circuits, and combining them with classical Keras models, with example applications.
- **Gloss.** *PQC*: Parameterised quantum circuit, the trainable layer. *Parameter shift*: A rule for exact gradients of circuit expectation values.
- **Commentary.** TensorFlow Quantum, the QML layer built on TensorFlow. *Elucidation:* `lang_c.ipynb` is TensorFlow's 'Install TensorFlow for C' guide. It is classical TensorFlow, not TFQ, and it sits under the same framework TFQ extends. *Exposition:* Encode data into circuits, apply a PQC, measure expectation values, and back-propagate through them alongside classical layers.
- **Exegesis.** A software paper: it shows *what can be built*, not that quantum layers improve accuracy.<sup>[1](#b19-fn)</sup>
- **Critique.** TFQ releases can lag current TensorFlow versions; check compatibility before running a copied notebook.
- **Marginalia.**
  - `lang_c.ipynb`: Classical C API setup (`libtensorflow` 2.15.0 CPU build). No quantum code in this file.
  - `README.md`: The Medium writing linked above is where TFQ ideas are discussed.
- **Scholia.** [B24](#b24): The model family TFQ tutorials implement. [B26](#b26): The field TFQ serves.
- **Footnote.** <a id="b19-fn"></a>¹ TFQ documentation: tensorflow.org/quantum.
- **In context.** The software link between this repository's TensorFlow notebook and quantum deep learning.

<a id="b26"></a>

### B26 · Quantum machine learning

> **Caption.** The landmark QML review, caveats included.

**Metadata.** Jacob Biamonte, Peter Wittek, Nicola Pancotti, et al. (2017). *Nature 549(7671): 195–202*. Journal article. DOI: [10.1038/nature23474](https://doi.org/10.1038/nature23474). Verified 10 Nov 2026.<br>
**Descriptors.** Quantum machine learning · **Tags.** `review` `qram` `linear-algebra-speedups` · **Labels.** `evidence:peer-reviewed` `role:foundation` `type:journal-article` `status:verified`

- **Abstract.** Reviews quantum machine learning: quantum linear-algebra subroutines, quantum-enhanced models, annealing-based learning, and practical obstacles such as data loading.
- **Gloss.** *QRAM*: Hypothetical quantum random-access memory for loading classical data in superposition.
- **Commentary.** The landmark map of quantum machine learning. *Elucidation:* It sorts claims into three kinds: speedups from linear algebra, quantum-enhanced models, and annealing-based learning. Each comes with assumptions, such as fast data loading, that a blog post should state. *Exposition:* Speedups often come from fast linear algebra on quantum states; the cost of preparing those states can erase them.
- **Exegesis.** Lists *potential* speedups with their assumptions. It does not report demonstrated practical advantage.<sup>[1](#b26-fn)</sup>
- **Critique.** Several linear-algebra speedups it surveys were later weakened by 'dequantized' classical algorithms (from 2018), and most rely on qRAM-style data loading that does not yet exist. Read it as a map of hopes with stated assumptions.
- **Marginalia.**
  - `README.md`: Use as the survey frame for any post that promises a QML speedup.
- **Scholia.** [B39](#b39): A concrete experiment in the kernel branch. [B38](#b38): A broader, later review.
- **Footnote.** <a id="b26-fn"></a>¹ Later 'dequantization' work weakened several of the speedups surveyed.
- **In context.** Survey background for the blog.

<a id="b24"></a>

### B24 · Classification with Quantum Neural Networks on Near Term Processors

> **Caption.** Parameterised circuits as binary classifiers.

**Metadata.** Edward Farhi, Hartmut Neven (2018). *arXiv:1802.06002*. Preprint. [arxiv.org/abs/1802.06002](https://arxiv.org/abs/1802.06002). Verified 10 Nov 2026.<br>
**Descriptors.** Quantum machine learning · Variational algorithms · **Tags.** `qnn` `binary-classification` `mnist` · **Labels.** `evidence:preprint` `role:foundation` `type:preprint` `status:verified`

- **Abstract.** Proposes a quantum neural network in which a parameterised circuit acts on an input state and a measured readout qubit gives the class label; tested in simulation, including downsampled MNIST.
- **Gloss.** *Readout qubit*: The qubit measured to produce the prediction.
- **Commentary.** The quantum neural network idea at the center of 'quantum deep learning'. *Elucidation:* It defines a QNN concretely: a parameterised circuit acting on a quantum state, with one readout qubit measured to give the label. *Exposition:* Encode input as a quantum state, apply trainable unitaries, measure a Pauli on the readout qubit, minimise a loss over parameters.
- **Exegesis.** Shows *the model can learn small tasks in simulation*. It does not show an advantage over classical networks.<sup>[1](#b24-fn)</sup>
- **Critique.** Simulated, small-scale; trainability caveats arrived soon after (B27).
- **Marginalia.**
  - `README.md`: Cite when a post explains what a QNN is.
- **Scholia.** [B27](#b27): Why QNNs can be hard to train. [B39](#b39): The kernel alternative.
- **Footnote.** <a id="b24-fn"></a>¹ Tested in simulation, including on downsampled MNIST.
- **In context.** The definition the blog's QNN posts build on.

<a id="b39"></a>

### B39 · Supervised learning with quantum-enhanced feature spaces

> **Caption.** Quantum kernels on real hardware, with synthetic data.

**Metadata.** Vojtěch Havlíček, Antonio D. Córcoles, Kristan Temme, et al. (2019). *Nature 567(7747): 209–212*. Journal article. DOI: [10.1038/s41586-019-0980-2](https://doi.org/10.1038/s41586-019-0980-2). Verified 10 Nov 2026.<br>
**Descriptors.** Quantum machine learning · Gate-model computing · **Tags.** `quantum-kernel` `feature-map` `svm` · **Labels.** `evidence:peer-reviewed` `role:foundation` `type:journal-article` `status:verified`

- **Abstract.** Proposes two classifiers that use a quantum circuit as a feature map, a variational classifier and a quantum kernel estimator, and demonstrates both on a superconducting processor using two qubits and artificially constructed data.
- **Gloss.** *Feature map*: A circuit that encodes a data point into a quantum state. *Kernel*: Inner product of two encoded states, used by an SVM.
- **Commentary.** Quantum kernels demonstrated on real hardware. *Elucidation:* It gives the blog a second route besides variational QNNs: encode the data with a circuit, estimate overlaps between encoded points, then train a classical SVM. *Exposition:* Map data into a large Hilbert space with a hard-to-simulate circuit, estimate pairwise overlaps on hardware, then train a classical SVM.
- **Exegesis.** Shows the methods *work on a small device with data designed to suit the feature map*. It does not show advantage on real-world datasets.<sup>[1](#b39-fn)</sup>
- **Critique.** Two-qubit demo; later work found kernel concentration problems at scale analogous to barren plateaus.
- **Marginalia.**
  - `README.md`: A candidate topic for a post. Label it as literature, not as an experiment run here.
- **Scholia.** [B24](#b24): The variational sibling. [B27](#b27): Kernels face a similar concentration problem.
- **Footnote.** <a id="b39-fn"></a>¹ The experiment used two qubits and data built to suit the feature map.
- **In context.** Kernel-method background for the blog.

<a id="b38"></a>

### B38 · Variational quantum algorithms

> **Caption.** The review of VQAs: QAOA, VQE, QNNs and their obstacles.

**Metadata.** M. Cerezo, Andrew Arrasmith, Ryan Babbush, et al. (2021). *Nature Reviews Physics 3(9): 625–644*. Journal article. DOI: [10.1038/s42254-021-00348-9](https://doi.org/10.1038/s42254-021-00348-9). Verified 10 Nov 2026.<br>
**Descriptors.** Variational algorithms · Trainability · Quantum machine learning · **Tags.** `vqe` `qaoa` `ansatz` `error-mitigation` · **Labels.** `evidence:peer-reviewed` `role:foundation` `type:journal-article` `status:verified`

- **Abstract.** Reviews variational quantum algorithms: cost functions, ansatz design, optimisers, applications from chemistry to optimization and ML, and challenges including barren plateaus, noise and error mitigation.
- **Gloss.** *Ansatz*: The parameterised circuit template. *Error mitigation*: Post-processing that reduces noise bias without full error correction.
- **Commentary.** The review that unifies variational quantum algorithms. *Elucidation:* QNNs, QAOA and VQE share one loop (circuit cost, classical update) and one set of obstacles. Posts can explain all three in one frame. *Exposition:* A quantum circuit evaluates a cost; a classical optimiser updates parameters; the loop repeats. Everything hinges on cost design and trainability.
- **Exegesis.** The review presents VQAs as *leading candidates* for near-term advantage. It does not report a demonstrated practical advantage.<sup>[1](#b38-fn)</sup>
- **Critique.** A 2021 snapshot; trainability theory has advanced since.
- **Marginalia.**
  - `README.md`: The survey frame for posts on variational methods.
- **Scholia.** [B27](#b27): The obstacle it reviews. [B23](#b23): The NISQ context.
- **Footnote.** <a id="b38-fn"></a>¹ Crossref lists 11 authors.
- **In context.** The map for variational topics.

<a id="b27"></a>

### B27 · Barren plateaus in quantum neural network training landscapes

> **Caption.** Gradients that vanish exponentially: the QML counterweight.

**Metadata.** Jarrod R. McClean, Sergio Boixo, Vadim N. Smelyanskiy, et al. (2018). *Nature Communications 9: 4812*. Journal article. DOI: [10.1038/s41467-018-07090-4](https://doi.org/10.1038/s41467-018-07090-4). Verified 10 Nov 2026.<br>
**Descriptors.** Trainability · Quantum machine learning · **Tags.** `barren-plateau` `counterevidence` `random-circuits` · **Labels.** `evidence:peer-reviewed` `role:caution` `type:journal-article` `status:verified` `claim:counterweight`

- **Abstract.** Shows that for sufficiently random parameterised circuits, gradient variance decays exponentially in qubit number, making gradient-based training impractical at scale.
- **Gloss.** *Barren plateau*: A flat loss landscape where gradients are exponentially small. *2-design*: A circuit ensemble that mimics random unitaries up to second moments.
- **Commentary.** The key counterweight to optimistic QNN claims. *Elucidation:* It explains why a training curve from a small simulation should not be extrapolated in a post. *Exposition:* Random deep circuits concentrate expectation values; derivatives concentrate around zero, so the optimiser sees noise.
- **Exegesis.** Applies to *circuits that form approximate 2-designs*. It does not say all QNNs are untrainable; structured or shallow circuits may escape.<sup>[1](#b27-fn)</sup>
- **Critique.** Follow-ups (e.g., B38's summary) refine conditions: cost locality, depth and noise all matter.
- **Marginalia.**
  - `README.md`: Pair it with any post that shows a QNN training curve.
- **Scholia.** [B24](#b24): The model it constrains. [B38](#b38): Its follow-ups, summarised.
- **Footnote.** <a id="b27-fn"></a>¹ The DOI was verified on Crossref after a wrong first draft was rejected.
- **In context.** A caution for the blog.

<a id="b23"></a>

### B23 · Quantum Computing in the NISQ era and beyond

> **Caption.** The essay that named NISQ and set expectations.

**Metadata.** John Preskill (2018). *Quantum 2: 79*. Journal article. DOI: [10.22331/q-2018-08-06-79](https://doi.org/10.22331/q-2018-08-06-79). Verified 10 Nov 2026.<br>
**Descriptors.** Gate-model computing · Benchmarking · **Tags.** `nisq` `perspective` `expectations` · **Labels.** `evidence:peer-reviewed` `role:caution` `type:journal-article` `status:verified` `claim:counterweight`

- **Abstract.** An influential perspective defining noisy intermediate-scale quantum devices and assessing what they might achieve before full error correction, including optimization and ML, with deliberate caution.
- **Gloss.** *NISQ*: Noisy intermediate-scale quantum: tens to hundreds (now thousands) of qubits without full error correction.
- **Commentary.** The framing for what today's noisy devices can and cannot do. *Elucidation:* It keeps the blog's claims measured: near-term usefulness is something to test, not to assume. *Exposition:* Noise limits circuit depth; useful near-term advantage is possible but must be demonstrated, and error correction remains the long-run route.
- **Exegesis.** Preskill says NISQ devices *may* be useful and are worth exploring; he explicitly does not promise near-term transformative applications.<sup>[1](#b23-fn)</sup>
- **Critique.** A perspective, not data; the qubit-count range has since shifted.
- **Marginalia.**
  - `README.md`: Link from any post that predicts near-term impact.
- **Scholia.** [B26](#b26): The field it tempers. [B38](#b38): The algorithms NISQ invites.
- **Footnote.** <a id="b23-fn"></a>¹ Based on a keynote Preskill gave in December 2017.
- **In context.** The tone-setter for the blog.

### Code annotations in this repository

Where the four code-annotation elements appear in this repository's own files.<sup>[E3](#en3)</sup>

| Element | Example in this repository |
| --- | --- |
| Code comment | `lang_c.ipynb`: the Apache license header (`# Unless required by applicable law…`) is the only code comment; the rest is explained in Markdown cells |
| Docstring | None; the guide explains code in Markdown cells |
| Directive | `%%bash` and `%%writefile` cell magics in `lang_c.ipynb` tell Jupyter how to run a cell; `#include <stdio.h>` in its C example is a preprocessor directive; `#@title` is a Colab form directive |
| Decorator | None in this repository |

<a id="excursus"></a>

### Excursus: What 'quantum deep learning' can mean today

In the literature, 'quantum deep learning' covers three different things. The first is variational QNNs, trainable circuits used like neural-network layers ([B24](#b24), [B38](#b38)). The second is quantum kernels, circuits that embed data for a classical learner ([B39](#b39)). The third is speedups from quantum linear algebra that assume fast data loading ([B26](#b26)). All three are real research programmes, and none has shown a practical advantage on real-world data. The obstacles are specific and well studied: barren plateaus and concentration ([B27](#b27)) and NISQ noise ([B23](#b23)). TensorFlow Quantum ([B19](#b19)) is how one would experiment with the first two. This repository's only notebook is classical TensorFlow setup, which is an honest starting point for writing about all of this.

### Endnotes

1. <a id="en1"></a>**Verification.** Every source was checked on 10 November 2026 (America/New_York). DOIs were resolved at doi.org and matched against Crossref; preprints were checked on arXiv, the patent on Google Patents, and documentation and course pages on the live page.
2. <a id="en2"></a>**Numbering.** B-numbers are stable identifiers shared across David Merwin's annotated bibliographies, so a source keeps the same number in every repository. Gaps in the numbering are expected.
3. <a id="en3"></a>**Scope.** Sources are cited for background and method. None is used to claim a quantum advantage. The code-annotation table describes files as they are; no code was changed.

### P.S.

P.S. When a post cites one of these sources, the exegesis line says what that source does not claim. It is a good sentence to quote.
