---
layout: page
title: scSAID — a single-cell skin super-atlas
description: A cross-species single-cell skin atlas and interactive web platform — 1.2M cells, 252 samples, 49 studies. (Manuscript in preparation; target Nucleic Acids Research.)
img: assets/img/proj_skindb.png
importance: 2
category: research
---

**Role.** Undergraduate researcher in the lab of A/Prof. Chaochen Wang (ZJU–UoE Institute). Live resource: **[skin-scsaid.com](https://skin-scsaid.com/)**.

**scSAID** (Single-Cell Skin & Appendages Integrated Database) is a "skin single-cell transcriptomic super atlas": **1.2 million cells across 252 samples, 49 studies, and two species (human & mouse)**, all reprocessed through one standardized pipeline so studies become directly comparable.

<div class="row justify-content-sm-center">
  <div class="col-sm-11 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/proj_skindb.png" title="scSAID workflow" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">Curation → standardized preprocessing (Cell Ranger / Scanpy) → cross-study integration (scVI) → harmonized annotation → interactive web platform.</div>

**What I built / contributed.**
- Curated and processed **50+ public scRNA-seq datasets (>1M cells)** with standardized preprocessing and **scVI** integration for consistent cross-study comparison.
- Implemented automated/assisted **cell-type annotation** and downstream analyses (differential expression, enrichment), and contributed to **cross-species (human↔mouse) mapping** with ortholog handling and harmonized labels.
- Contributed to the **web platform**: data organization, metadata schema, and query / visualization modules — interactive feature plots, dataset comparison, and download.

**On the site you can** browse datasets by species / sex / age / anatomical region / condition, search genes via interactive feature plots, compare datasets, and download standardized objects.

**Stack.** Cell Ranger, Scanpy, scVI, Python/R, web platform. *Manuscript in preparation (analysis + platform module complete); target journal: Nucleic Acids Research.*
