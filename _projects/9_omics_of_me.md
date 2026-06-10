---
layout: page
title: Omics of me — sequencing my twin and me
description: I had my own genome and my fraternal twin brother's whole-genome sequenced, then asked, honestly, whether DNA explains why I've been the heavier one since childhood.
img: assets/img/omics_pipeline.png
importance: 1
category: personal genomics
---

> A personal-genomics side project — and an exercise in honest analysis. **n = 2**, exploratory, hypothesis-generating. No causal claim is made or implied.

I am a **dizygotic (fraternal) twin**. My brother and I grew up in the same home, shared a womb, and yet I have been visibly **heavier since childhood**. As a bioinformatics student with access to my own data, I wanted to ask the obvious question properly: **does our DNA explain the difference?** So we each had a **~60× whole-genome** sequenced (BGI, DNBSEQ) and I built the analysis from raw reads up.

## Sample-to-data timeline

<style>
.omx-tl{display:flex;flex-wrap:wrap;gap:0;margin:1.4rem 0 0.6rem;counter-reset:s}
.omx-step{flex:1 1 160px;position:relative;padding:0 10px}
.omx-step .dot{width:14px;height:14px;border-radius:50%;background:#d05a4f;
  border:3px solid #fff;box-shadow:0 0 0 2px #d05a4f;margin-bottom:12px}
.omx-step:not(:last-child)::after{content:"";position:absolute;top:5px;left:calc(50% + 12px);
  right:calc(-50% + 12px);height:2px;background:#e2c3bf}
.omx-step .date{font-weight:600;font-size:.95rem}
.omx-step .lab{font-size:.85rem;color:#6b7280;margin-top:2px}
</style>
<div class="omx-tl">
  <div class="omx-step"><div class="dot"></div><div class="date">May 18</div><div class="lab">Whole blood drawn, sample shipped to BGI</div></div>
  <div class="omx-step"><div class="dot"></div><div class="date">Jun 2</div><div class="lab">Library preparation complete</div></div>
  <div class="omx-step"><div class="dot"></div><div class="date">Jun 4</div><div class="lab">Sequencing complete</div></div>
  <div class="omx-step"><div class="dot"></div><div class="date">Jun 6</div><div class="lab">Data transfer &amp; download complete → analysis begins</div></div>
</div>

## The pipeline

I built a modern, pangenome-based workflow rather than a textbook linear-reference one — partly because it is closer to 2025 best practice, partly because it is a better thing to learn.

<iframe src="{{ '/assets/omics_pipeline.html' | relative_url }}" title="Twin WGS pipeline schematic" loading="lazy" scrolling="auto" style="width:100%; height:740px; border:1px solid var(--global-divider-color); border-radius:12px; background:#faf8f3;"></iframe>
<p style="font-size:.82rem; color:#7a8694; margin:.3rem 0 0">Scroll the panel sideways to follow the full left-to-right flow — or <a href="{{ '/assets/omics_pipeline.html' | relative_url }}" target="_blank" rel="noopener">open it full width</a>. Vector HTML, not a raster image.</p>
<div class="caption">
  <b>A — Genome assembly &amp; variant discovery:</b> reads → personalized pangenome graph (HPRC, <code>vg giraffe</code>) → surject to GRCh38 → deep-learning small-variant calling (<code>Clair3</code>) + structural variants → joint genotyping (<code>GLnexus</code>).
  <b>B — Twin comparison &amp; obesity genetics:</b> zygosity / kinship → annotation (<code>VEP</code>) → quality-filtered twin-differential variants → monogenic obesity-gene panel, classic BMI variants, and a genome-wide BMI polygenic-score head-to-head.
</div>

## Explore the results

<iframe src="{{ '/assets/omics_dashboard.html' | relative_url }}" title="Twin WGS interactive dashboard" loading="lazy" style="width:100%; height:1680px; border:1px solid var(--global-divider-color); border-radius:12px;"></iframe>
<p style="font-size:.85rem; color:#7a8694; margin-top:.4rem">Best viewed full width — <a href="{{ '/assets/omics_dashboard.html' | relative_url }}" target="_blank" rel="noopener">open the dashboard in its own tab</a>.</p>

## What I found — an honest negative

The most defensible reading of the data is that **common-variant genetics does not explain the difference**, and if anything points the other way:

- **We are confirmed dizygotic twins.** KING kinship ≈ **0.22** with non-zero IBS0 — squarely full-sibling / DZ, ruling out a monozygotic or parent–child relationship. We share roughly **half our genome** identical-by-descent; ~1.8 million genotypes differ between us.
- **No monogenic explanation.** Across a panel of known obesity genes, **zero** rare, damaging variants differ between us.
- **Our genome-wide BMI polygenic scores are essentially identical** — within noise across several independent scores (and, on the most credible ones, nominally *higher* in my leaner brother).
- The few classic BMI common variants that do differ **do not favour me, the heavier twin.**

So the lifelong difference is most likely **non-genetic** — early-life environment, behaviour, and epigenetics — none of which whole-genome sequencing can see. That is not the dramatic answer, but it is the honest one, and arriving at it cleanly was the point.

## Notes

- **Stack.** `vg` (Giraffe / pangenome), KMC, Clair3, GLnexus, bcftools, plink2 (KING + PGS), Ensembl VEP, PGS Catalog. Run on an HPC node from raw FASTQ.
- **Why "honest negative"?** With n = 2 and no reference population, a 0.7% score difference is not a finding — calling it one would be the easy mistake. Reporting a well-built null is the harder, better outcome.
- The schematic above is a hand-drawn vector figure, not an AI raster — every label is real text.
