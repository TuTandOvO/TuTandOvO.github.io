---
layout: page
title: Pubertal high-fat diet & mammary morphogenesis
description: How a high-fat diet reshapes the pubertal mammary microenvironment — snRNA-seq, spatial transcriptomics, and a dual-force model. (Co-first author; ISSCR / Society for Developmental Biology 2026.)
img: assets/img/proj_hfd.png
importance: 1
category: research
related_publications: false
---

**Role.** Co-first author. Undergraduate researcher in the lab of A/Prof. Chaochen Wang (ZJU–UoE Institute).

Puberty is a window of rapid mammary-gland morphogenesis and heightened vulnerability, yet how a **high-fat diet (HFD)** perturbs it at single-cell resolution was unclear. Using a mouse HFD model across the pubertal window, we combined **single-nucleus RNA-seq, spatial transcriptomics, and computational analysis** to dissect how diet reshapes the mammary microenvironment.

<div class="row justify-content-sm-center">
  <div class="col-sm-11 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/proj_hfd.png" title="HFD mammary workflow" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">snRNA-seq + spatial workflow: QC, integration/batch correction, annotation, and lineage / trajectory analysis of the HFD vs normal-diet mammary gland.</div>

**What we found.**
- HFD **reduces ductal branching** while promoting **periductal collagen deposition** and depleting epithelial populations — a remodelled stromal microenvironment.
- HFD **selectively disrupts puberty-activated functional modules in the luminal (not basal) lineage**, reflected in altered mitochondrial / metabolic function.
- Unsupervised clustering identified an **ECM-remodelling stromal subset marked by *Adam12***; cell–cell communication implicated **Angpt1–Col3a1** signalling as an extrinsic mechanical barrier to ductal outgrowth. The subset expands with ageing and is conserved in humans.
- Together these support a **dual-force model**: HFD simultaneously attenuates intrinsic epithelial growth programmes and activates extrinsic stromal barriers, nominating **IGF1 / Areg signalling and *Adam12* stromal cells** as candidate targets.

**Stack.** snRNA-seq (10x), Scanpy/Seurat, scVI integration, Monocle3 / scVelo trajectories, cell–cell communication inference, spatial transcriptomics; plus wet-lab validation (IHC, IF, dissection).

*Accepted to ISSCR / Society for Developmental Biology 2026.*
