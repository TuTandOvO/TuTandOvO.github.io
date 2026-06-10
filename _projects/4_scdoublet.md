---
layout: page
title: Do deep representations beat PCA for doublet detection?
description: A controlled scRNA-seq doublet-detection benchmark across ground-truth tiers and cell-count scales (10K–1M) — eight tools, a representation × classifier factorial, and downstream-clustering impact.
img: assets/img/proj_scdoublet.png
importance: 4
category: research
---

**Role.** Sole author. CMML3 ICA2 miniproject. Code: **[github.com/TuTandOvO/scDoubletBench](https://github.com/TuTandOvO/scDoubletBench)**.

Doublets are a core scRNA-seq artefact, and new deep-learning detectors keep arriving — but do they actually beat simple baselines under a fair comparison? I ran a controlled benchmark of **eight standalone tools** plus a **(representation × classifier) factorial**, across **four datasets, three ground-truth tiers, and cell-count scales from 10K to 1M**.

<div class="row justify-content-sm-center">
  <div class="col-sm-11 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/proj_scdoublet.png" title="Doublet benchmark overview" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Pipeline & dataset overview: scRNA-seq data across three ground-truth tiers feed eight tools and a representation × classifier factorial, evaluated on a five-axis metric stack (discrimination, calibration, cross-tool agreement, compute cost, downstream clustering impact).</div>

**Headline findings.**
- **No universal winner** — per-dataset winners diverge across ground-truth tiers; the mean-AUPRC convention hides per-dataset failures.
- **Rankings invert with scale:** between 10K and 100K cells, scDblFinder loses ~35% of its AUPRC while Solo gains ~94%.
- **Deep representations do not beat PCA** under controlled comparison: in a (PCA / scVI / Geneformer) × (XGBoost / MLP) factorial, the strongest cell is **(PCA, XGBoost)** — echoing the "DL vs simple baseline" framing of Ahlmann-Eltze et al. 2025.
- **Engineering fragility is the atlas-scale bottleneck:** four of five tools attempted at 1M cells fail to complete; only scDblFinder and Solo deploy.
- **Downstream clustering impact is tool-dependent** and grows with dataset complexity (ARI 0.99→0.65 across settings).

**Stack.** Python 3.11, R 4.3, Scanpy, scVI, Geneformer, XGBoost, GPU + LSF/HPC for the 1M-cell scale.
