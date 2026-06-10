---
layout: page
title: Optimising image-to-spatial-expression prediction
description: When does predicting spatial transcriptomics from H&E morphology actually improve? A systematic study of SpatialEx across architecture, biological priors, and post-hoc correction.
img: assets/img/proj_spatialex.png
importance: 3
category: research
---

**Role.** Lead author of the optimisation study. Code: **[github.com/TuTandOvO/SpatialEx_Optimization](https://github.com/TuTandOvO/SpatialEx_Optimization)**.

SpatialEx predicts **spatial gene expression directly from H&E histology**, but its limits are poorly characterised. I asked, systematically, *whether and how* the model can be improved — across **8 optimisation directions in four stages**, on two 10x Xenium datasets (mammary gland and skin).

<div class="row justify-content-sm-center">
  <div class="col-sm-11 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/proj_spatialex.png" title="SpatialEx optimisation workflow" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Four stages: architecture tuning (loss / activation / feature selection) · tissue-specific PPI priors · gene-level post-hoc propagation & GCN correction · conformal-prediction uncertainty.</div>

**Key finding — only external biology helps.**
- **Biological priors are the only lever that genuinely works:** adding tissue-specific **protein–protein-interaction (PPI)** structure raises Pearson correlation by **~22% (mammary)** and **~33% (skin)**.
- **Architecture tweaks are a wash:** loss reweighting, activation swaps, and attention gates give negligible or negative effects.
- **Morphology-uninformative genes can't be rescued** by post-processing — their poor predictability reflects a genuine absence of signal in H&E, not a modelling gap.
- **Conformal coverage** is stable within-slice but degrades ~8 percentage points cross-slice, quantifying where these predictions can (and can't) be trusted.

**Stack.** Python 3.10, PyTorch, graph neural networks (HGNN+, GCN), HumanBase PPI, conformal prediction, 10x Xenium spatial data.
