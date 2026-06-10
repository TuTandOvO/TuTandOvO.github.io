---
layout: page
title: Omics of me — sequencing my twin and me
description: I had my own genome and my fraternal twin brother's whole-genome sequenced, then asked, honestly, whether DNA explains why I've been the heavier one since childhood.
img: assets/img/omics_pipeline.png
importance: 1
category: personal genomics
---

> A personal-genomics side project — and an exercise in honest analysis. **n = 2**, exploratory, hypothesis-generating. No causal claim is made or implied.

## It started with a photo

<div style="max-width:240px; margin:1.1rem auto 0">
  {% include figure.liquid loading="eager" path="assets/img/omics_childhood.jpg" title="My twin brother and me as kids" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption" style="max-width:440px; margin-left:auto; margin-right:auto">My fraternal twin brother and me as kids — that's me on the left. Same womb, same home, same dinner table, and yet I've been the rounder one for as long as there are photos to prove it.</div>

I'm a **dizygotic (fraternal) twin**. For most of my life, "why am I the bigger one?" was just a family joke. Then I stepped into **bioinformatics** — and realised I could stop guessing and actually *ask the data*: **does our DNA explain the difference?**

## Getting the data

<p style="display:flex; align-items:center; gap:14px; flex-wrap:wrap; margin:.6rem 0 1.1rem">
  <img src="{{ '/assets/img/logo_bgi.webp' | relative_url }}" alt="BGI" style="height:32px; flex:0 0 auto">
  <span style="flex:1 1 320px">So I did. I reached out to <b>BGI</b>, gave a tube of blood, and had <b>both</b> of our genomes sequenced end to end at <b>~60× depth</b> (DNBSEQ short-read platform). Nineteen days from needle to data:</span>
</p>

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

## Tools &amp; citations

Everything here is open source. The tools, what each one did, and the papers behind them:

<style>
.omx-tools{display:grid; grid-template-columns:repeat(2,1fr); gap:12px; margin:1rem 0}
.omx-tool{display:flex; gap:13px; align-items:flex-start; border:1px solid var(--global-divider-color,#e7e2d6); border-radius:12px; padding:13px 14px; background:#fff}
.omx-tool .ic{width:42px; height:42px; flex:0 0 42px; display:flex; align-items:center; justify-content:center; border-radius:9px; background:#faf8f3; border:1px solid #efeae0; overflow:hidden}
.omx-tool .ic img{max-width:90%; max-height:90%}
.omx-tool .ic .txt{font-family:"IBM Plex Mono",monospace; font-weight:600; font-size:12px; color:#3b73c4}
.omx-tool .nm{font-weight:600; font-size:14px; line-height:1.15}
.omx-tool .nm a{color:inherit}
.omx-tool .rl{font-size:12px; color:#7a8694; margin:3px 0 4px}
.omx-tool .ci{font-size:11px; color:#9aa3ad}
@media(max-width:600px){.omx-tools{grid-template-columns:1fr}}
</style>
<div class="omx-tools">
  <div class="omx-tool"><div class="ic"><img src="{{ '/assets/img/logo_bgi.webp' | relative_url }}" alt="BGI"></div><div><div class="nm"><a href="https://www.bgi.com/" target="_blank" rel="noopener">BGI · DNBSEQ</a></div><div class="rl">~60× whole-genome sequencing</div><div class="ci">DNBSEQ short-read platform</div></div></div>
  <div class="omx-tool"><div class="ic"><img src="{{ '/assets/img/logo_hprc.png' | relative_url }}" alt="HPRC"></div><div><div class="nm"><a href="https://humanpangenome.org/" target="_blank" rel="noopener">HPRC pangenome</a></div><div class="rl">graph reference genome</div><div class="ci">Liao et al., <i>Nature</i> 2023</div></div></div>
  <div class="omx-tool"><div class="ic"><img src="{{ '/assets/img/logo_vg.png' | relative_url }}" alt="vg"></div><div><div class="nm"><a href="https://github.com/vgteam/vg" target="_blank" rel="noopener">vg Giraffe</a></div><div class="rl">pangenome read mapping</div><div class="ci">Sirén et al., <i>Science</i> 2021</div></div></div>
  <div class="omx-tool"><div class="ic"><img src="{{ '/assets/img/logo_clair3.png' | relative_url }}" alt="Clair3"></div><div><div class="nm"><a href="https://github.com/HKU-BAL/Clair3" target="_blank" rel="noopener">Clair3</a></div><div class="rl">deep-learning SNV / indel calling</div><div class="ci">Zheng et al., <i>Nat. Comput. Sci.</i> 2022</div></div></div>
  <div class="omx-tool"><div class="ic"><svg width="26" height="26" viewBox="0 0 26 26" fill="none"><path d="M4 6h18l-7 8v6l-4 2v-8z" stroke="#c79a3a" stroke-width="1.8" stroke-linejoin="round"/></svg></div><div><div class="nm"><a href="https://github.com/dnanexus-rnd/GLnexus" target="_blank" rel="noopener">GLnexus</a></div><div class="rl">joint genotyping</div><div class="ci">Yun et al., <i>Bioinformatics</i> 2020</div></div></div>
  <div class="omx-tool"><div class="ic"><svg width="26" height="26" viewBox="0 0 26 26" fill="none"><rect x="4" y="5" width="18" height="16" rx="2" stroke="#3b73c4" stroke-width="1.8"/><path d="M4 10.5h18M10 5v16" stroke="#3b73c4" stroke-width="1.3"/></svg></div><div><div class="nm"><a href="https://samtools.github.io/bcftools/" target="_blank" rel="noopener">bcftools</a></div><div class="rl">variant processing &amp; filtering</div><div class="ci">Danecek et al., <i>GigaScience</i> 2021</div></div></div>
  <div class="omx-tool"><div class="ic"><svg width="26" height="26" viewBox="0 0 26 26"><g fill="#d05a4f"><circle cx="9" cy="9" r="3"/><circle cx="17" cy="9" r="3"/><path d="M3.5 19c.5-3 2.6-4.6 5.5-4.6S14 15.8 14.5 19zM11.5 19c.5-3 2.6-4.6 5.5-4.6S22 15.8 22.5 19z"/></g></svg></div><div><div class="nm"><a href="https://www.cog-genomics.org/plink/2.0/" target="_blank" rel="noopener">plink2 · KING</a></div><div class="rl">kinship &amp; polygenic scoring</div><div class="ci">Manichaikul 2010 · Chang 2015</div></div></div>
  <div class="omx-tool"><div class="ic"><img src="{{ '/assets/img/logo_vep.png' | relative_url }}" alt="Ensembl VEP"></div><div><div class="nm"><a href="https://www.ensembl.org/vep" target="_blank" rel="noopener">Ensembl VEP</a></div><div class="rl">variant annotation</div><div class="ci">McLaren et al., <i>Genome Biol.</i> 2016</div></div></div>
  <div class="omx-tool"><div class="ic"><img src="{{ '/assets/img/logo_pgs.png' | relative_url }}" alt="PGS Catalog"></div><div><div class="nm"><a href="https://www.pgscatalog.org/" target="_blank" rel="noopener">PGS Catalog</a></div><div class="rl">BMI polygenic-score weights</div><div class="ci">Lambert et al., <i>Nat. Genet.</i> 2021</div></div></div>
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
