---
layout: page
title: Omics of me — sequencing my twin and me
description: From a childhood photo to a whole-genome answer — the reasoning and the data flow behind asking, honestly, whether DNA explains why I've been the heavier fraternal twin.
img: assets/img/omics_pipeline.png
importance: 1
category: personal genomics
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600&family=IBM+Plex+Mono:wght@400;500&display=swap');
.omx{--you:#d05a4f;--bro:#3b73c4;--grn:#2f9e6e;--vio:#7a55c4;--amb:#c79a3a;--mut:#7a8694;--ln:#e7e2d6}
.omx h3{font-family:"Fraunces",serif;font-weight:600}
.omx .lead{font-size:15px;line-height:1.6;color:#333}
.omx .mut{color:var(--mut)}
.omx-mono{font-family:"IBM Plex Mono",monospace}
/* logo row */
.omx-emblem{display:flex;align-items:center;gap:18px;flex-wrap:wrap;margin:.4rem 0 0}
.omx-emblem img{height:46px;width:auto}
.omx-emblem .x{color:var(--mut);font-size:13px}
/* flow */
.omx-flow{position:relative;margin:1.6rem 0 1rem}
.omx-step{position:relative;padding:0 0 1.9rem 58px;min-height:42px}
.omx-step::before{content:"";position:absolute;left:18px;top:8px;bottom:-4px;width:2px;background:linear-gradient(#e2c3bf,#e7e2d6)}
.omx-step:last-child::before{display:none}
.omx-num{position:absolute;left:0;top:0;width:38px;height:38px;border-radius:50%;background:var(--you);color:#fff;
  display:flex;align-items:center;justify-content:center;font-family:"Fraunces",serif;font-weight:600;font-size:17px;
  box-shadow:0 3px 9px rgba(208,90,79,.32)}
.omx-step h3{font-size:19px;margin:.15rem 0 .5rem;letter-spacing:-.01em}
.omx-step p{font-size:14.5px;line-height:1.62;color:#333;margin:.45rem 0}
.omx-step .sub{font-family:"IBM Plex Mono",monospace;font-size:11.5px;color:var(--mut);text-transform:uppercase;letter-spacing:.12em}
/* generic card / figure */
.omx-fig{border:1px solid var(--ln);border-radius:14px;background:#fff;padding:14px;margin:.8rem 0}
.omx-fig img{max-width:100%;border-radius:8px;display:block}
.omx-cap{font-size:12px;color:var(--mut);margin-top:8px;line-height:1.45}
/* ancestry 3-col */
.omx-anc{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:.6rem 0}
.omx-anc .col{border:1px solid var(--ln);border-radius:14px;padding:14px 10px;text-align:center;background:#fff}
.omx-anc .ttl{font-weight:600;font-size:13px}
.omx-anc .ic{height:54px;display:flex;align-items:center;justify-content:center;margin:6px 0}
.omx-anc .note{font-size:11px;color:var(--mut);line-height:1.35}
.omx-anc .ok{background:#eef6f0}
/* citation chips */
.omx-cites{display:flex;flex-wrap:wrap;gap:7px;margin:.7rem 0 .2rem}
.omx-cites a,.omx-cites span{font-family:"IBM Plex Mono",monospace;font-size:10.5px;color:#456;background:#f4f1ea;
  border:1px solid var(--ln);border-radius:999px;padding:3px 9px;text-decoration:none}
.omx-cites a:hover{background:#fff}
/* two-model row */
.omx-models{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:.6rem 0}
.omx-model{border:1px solid var(--ln);border-radius:14px;padding:14px;background:#fff}
.omx-model .h{font-weight:600;font-size:13px;display:flex;align-items:center;gap:9px}
.omx-model .d{font-size:11.5px;color:var(--mut);margin-top:6px;line-height:1.45}
/* kinship scale */
.omx-scale{position:relative;height:18px;border-radius:9px;margin:40px 0 10px;
  background:linear-gradient(90deg,#eef1f5,#e9f1fb 28%,#fdeceb 55%,#f6efe1);border:1px solid var(--ln)}
.omx-mk{position:absolute;top:-22px;transform:translateX(-50%);font-size:9.5px;color:var(--mut);font-family:"IBM Plex Mono",monospace;text-align:center;width:84px}
.omx-needle{position:absolute;top:-7px;width:4px;height:32px;border-radius:2px;background:var(--you);transform:translateX(-50%);box-shadow:0 0 0 3px rgba(208,90,79,.18)}
.omx-needle .l{position:absolute;top:-19px;left:50%;transform:translateX(-50%);white-space:nowrap;font-size:11px;font-weight:600;color:var(--you)}
/* chrom bars */
.omx-chrom{display:flex;align-items:flex-end;gap:3px;height:150px;margin:.6rem 0 22px}
.omx-chrom .cb{flex:1;background:linear-gradient(180deg,#e7a59e,#d05a4f);border-radius:2px 2px 0 0;position:relative}
.omx-chrom .cl{font-size:7.5px;color:var(--mut);position:absolute;bottom:-15px;left:0;right:0;text-align:center}
/* stat tiles */
.omx-tiles{display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin:.6rem 0}
.omx-tile{border:1px solid var(--ln);border-radius:11px;padding:11px 12px;background:#fbfaf7}
.omx-tile .v{font-family:"Fraunces",serif;font-weight:600;font-size:26px;line-height:1}
.omx-tile .k{font-size:10.5px;color:var(--mut);margin-top:5px;font-family:"IBM Plex Mono",monospace}
/* prs */
.omx-prs .row{display:grid;grid-template-columns:96px 1fr;align-items:center;gap:9px;margin:7px 0}
.omx-prs .nm{font-size:11px;font-family:"IBM Plex Mono",monospace;color:var(--mut)}
.omx-prs .bar{position:relative;height:36px;background:#f4f1ea;border-radius:7px;overflow:hidden}
.omx-prs .fy,.omx-prs .fb{position:absolute;top:0;bottom:0;border-radius:7px;display:flex;align-items:center;justify-content:flex-end;padding-right:9px;font-size:12px;color:#fff;font-weight:600}
.omx-prs .fy{background:var(--you)}.omx-prs .fb{background:var(--bro);opacity:.92}
.omx-prs .pair{display:flex;flex-direction:column;gap:4px}
/* loci table */
.omx-loci{width:100%;border-collapse:collapse;font-size:12.5px;margin:.4rem 0}
.omx-loci th{text-align:left;font-family:"IBM Plex Mono",monospace;font-size:10px;letter-spacing:.05em;text-transform:uppercase;color:var(--mut);padding:6px 8px;border-bottom:1px solid var(--ln)}
.omx-loci td{padding:7px 8px;border-bottom:1px solid #f1ede3}
.omx-loci .gt{font-family:"IBM Plex Mono",monospace;font-weight:600}
.omx-pill{display:inline-block;font-size:10px;padding:2px 8px;border-radius:999px;font-weight:600}
.omx-pill.b{background:#e9f1fb;color:#2c5aa0}.omx-pill.s{background:#eef1f5;color:#6b7280}
.omx-concl{background:#1d2733;color:#f2efe8;border-radius:16px;padding:22px 24px;margin:1rem 0}
.omx-concl h3{color:#fff;font-size:20px;margin:0 0 8px}
.omx-concl p{color:#eef1f5;font-size:15px;line-height:1.66;margin:0}
.omx-concl em{color:#f0b8b2;font-style:normal;font-weight:600}
@media(max-width:620px){.omx-anc,.omx-models{grid-template-columns:1fr}.omx-tiles{grid-template-columns:repeat(2,1fr)}}
</style>

<div class="omx">

<blockquote style="border-left:3px solid #e2c3bf; margin:1rem 0; padding:.3rem 0 .3rem 1rem; color:#555; font-size:14px"><b>A personal-genomics side project</b> — and an exercise in honest reasoning. <b>n = 2</b>, exploratory, hypothesis-generating. No causal claim is made or implied.</blockquote>

<h2>It started with a photo</h2>

<div style="max-width:230px;margin:1rem auto 0">
  {% include figure.liquid loading="eager" path="assets/img/omics_childhood.jpg" title="My twin brother and me as kids" class="img-fluid rounded z-depth-1" %}
</div>
<div class="omx-cap" style="max-width:430px;margin:.4rem auto 0;text-align:center">My fraternal twin brother and me as kids — that's me on the left. Same womb, same home, same dinner table, and yet I've been the rounder one for as long as there are photos to prove it.</div>

<p class="lead">For most of my life, <i>"why am I the bigger one?"</i> was just a family joke. Then I stepped into <b>bioinformatics</b> at the <b>ZJU–UoE Joint Institute (ZJE)</b> — and realised I could stop guessing and actually <i>ask the data</i>.</p>

<div class="omx-emblem">
  <img src="{{ '/assets/img/logo_zju.png' | relative_url }}" alt="Zhejiang University">
  <span class="x">×</span>
  <img src="{{ '/assets/img/logo_uoe.png' | relative_url }}" alt="University of Edinburgh">
</div>

<p class="lead">So I followed the question all the way down — from a tube of blood to 3 billion base-pairs, reasoning through every step. Here is that flow.</p>

<div class="omx-flow">

<div class="omx-step">
  <div class="omx-num">1</div>
  <div class="sub">From blood to reads</div>
  <h3>Two brothers, two genomes</h3>
  <p>I reached out to <b>BGI</b>, gave a tube of whole blood, and had <b>both</b> of our genomes sequenced at <b>~60× depth</b> on the <b>DNBSEQ</b> short-read platform. Sequencing can't read a chromosome end-to-end, so the DNA is shattered into hundreds of millions of short fragments (<span class="omx-mono">read 1, read 2, read 3 …</span>), each ~150 letters long, and every position is covered ~60 times so we can tell a true variant from a sequencing slip.</p>
  <div style="display:flex;align-items:center;gap:16px;flex-wrap:wrap;margin:.7rem 0 .2rem">
    <svg width="30" height="42" viewBox="0 0 30 42" fill="none"><g stroke="#1d2733" stroke-width="1.7" stroke-linecap="round"><path d="M9 5c0 6.5 12 6.5 12 13s-12 6.5-12 13"/><path d="M21 5c0 6.5-12 6.5-12 13s12 6.5 12 13"/><path d="M11 9.5h8M10 15h10M10 23h10M11 28.5h8"/></g></svg>
    <span style="color:#bbb;font-size:20px">→</span>
    <span class="omx-emblem" style="margin:0"><img src="{{ '/assets/img/logo_bgi.webp' | relative_url }}" alt="BGI" style="height:26px"></span>
    <span style="color:#bbb;font-size:20px">→</span>
    <svg width="92" height="48" viewBox="0 0 60 46"><g><rect x="4" y="6" width="22" height="5" rx="2.5" fill="#2f9e6e"/><rect x="30" y="6" width="16" height="5" rx="2.5" fill="#3b73c4"/><rect x="10" y="15" width="18" height="5" rx="2.5" fill="#c79a3a"/><rect x="32" y="15" width="20" height="5" rx="2.5" fill="#d05a4f"/><rect x="4" y="24" width="14" height="5" rx="2.5" fill="#3b73c4"/><rect x="22" y="24" width="24" height="5" rx="2.5" fill="#2f9e6e"/><rect x="8" y="33" width="20" height="5" rx="2.5" fill="#d05a4f"/><rect x="32" y="33" width="14" height="5" rx="2.5" fill="#c79a3a"/></g></svg>
    <span class="mut omx-mono" style="font-size:11.5px">~150 bp reads · ~60×</span>
  </div>
  <p class="mut" style="font-size:13px">Timeline: <b>May 18</b> blood drawn → BGI · <b>Jun 2</b> library prep · <b>Jun 4</b> sequencing done · <b>Jun 6</b> data downloaded, analysis begins.</p>
</div>

<div class="omx-step">
  <div class="omx-num">2</div>
  <div class="sub">Why a pangenome, not the standard reference</div>
  <h3>The standard genome isn't built for me</h3>
  <p>To make sense of reads you align them to a reference genome. The textbook choice, <b>GRCh38 (hg38)</b>, is built largely from <b>European-ancestry</b> DNA. Aligning my East-Asian genome to a European-leaning reference quietly loses accuracy exactly where I differ from it. The fix is a <b>pangenome</b>: a graph woven from <b>many ancestries at once</b>, so my reads can follow a path that actually fits me.</p>
  <div class="omx-anc">
    <div class="col">
      <div class="ttl">hg38</div>
      <div class="ic">
        <svg width="42" height="54" viewBox="0 0 40 56"><circle cx="22" cy="10" r="7" fill="#3b73c4"/><path d="M15 19c-3 1-5 4-5 8l-1 12 4 1 1-9h1l-2 16h4l1-12h2l1 12h4l-2-16h1l1 9 4-1-1-12c0-4-2-7-5-8z" fill="#3b73c4"/></svg>
      </div>
      <div class="note">European-ancestry reference</div>
    </div>
    <div class="col">
      <div class="ttl">me</div>
      <div class="ic">
        <svg width="42" height="54" viewBox="0 0 40 56"><circle cx="22" cy="10" r="7" fill="#d05a4f"/><path d="M15 19c-3 1-5 4-5 8l-1 12 4 1 1-9h1l-2 16h4l1-12h2l1 12h4l-2-16h1l1 9 4-1-1-12c0-4-2-7-5-8z" fill="#d05a4f"/></svg>
      </div>
      <div class="note">East-Asian genome</div>
    </div>
    <div class="col ok">
      <div class="ttl">pangenome ✅</div>
      <div class="ic">
        <svg width="74" height="54" viewBox="0 0 74 56">
          <g transform="translate(-3,9) scale(0.6)"><circle cx="22" cy="10" r="7" fill="#3b73c4"/><path d="M15 19c-3 1-5 4-5 8l-1 12 4 1 1-9h1l-2 16h4l1-12h2l1 12h4l-2-16h1l1 9 4-1-1-12c0-4-2-7-5-8z" fill="#3b73c4"/></g>
          <g transform="translate(22,2) scale(0.72)"><circle cx="22" cy="10" r="7" fill="#d05a4f"/><path d="M15 19c-3 1-5 4-5 8l-1 12 4 1 1-9h1l-2 16h4l1-12h2l1 12h4l-2-16h1l1 9 4-1-1-12c0-4-2-7-5-8z" fill="#d05a4f"/></g>
          <g transform="translate(48,9) scale(0.6)"><circle cx="22" cy="10" r="7" fill="#2f9e6e"/><path d="M15 19c-3 1-5 4-5 8l-1 12 4 1 1-9h1l-2 16h4l1-12h2l1 12h4l-2-16h1l1 9 4-1-1-12c0-4-2-7-5-8z" fill="#2f9e6e"/></g>
        </svg>
      </div>
      <div class="note">many ancestries → fits more people</div>
    </div>
  </div>
  <div class="omx-cites">
    <a href="https://www.biorxiv.org/content/10.1101/2025.09.29.678807v1" target="_blank" rel="noopener">vg Giraffe pangenome mapping · bioRxiv 2025</a>
    <span>HPRC pangenome · Liao et al., Nature 2023</span>
  </div>
</div>

<div class="omx-step">
  <div class="omx-num">3</div>
  <div class="sub">Mapping with vg Giraffe</div>
  <h3>How reads find their place in a graph</h3>
  <p>A graph reference has many branching paths, so mapping isn't a simple line-up. <b>vg</b> counts my k-mers to pull out a <b>personalized graph</b> (only the haplotypes that look like me), then <b>Giraffe</b> threads each read through that graph, and finally <b>surjects</b> the result back onto GRCh38 coordinates as a standard <span class="omx-mono">BAM</span> file the rest of the world can read.</p>
  <div class="omx-fig">
    {% include figure.liquid loading="lazy" path="assets/img/vg_workflow.png" title="vg Giraffe workflow" class="img-fluid" %}
    <div class="omx-cap">The vg / Giraffe pangenome mapping workflow: reads → personalized graph → graph alignment → surject to a linear BAM.</div>
  </div>
</div>

<div class="omx-step">
  <div class="omx-num">4</div>
  <div class="sub">Variant calling with Clair3</div>
  <h3>Finding where my letters changed</h3>
  <p>With the BAM and the reference, the next job is to read out, position by position, where I differ from the reference. <b>Clair3</b> does this with two deep-learning models working together:</p>
  <div class="omx-fig">
    <svg viewBox="0 0 372 100" style="width:100%;max-width:500px;display:block;margin:2px auto">
      <text x="6" y="13" font-size="11" fill="#555" font-family="monospace">read stack at one position</text>
      <g transform="translate(6,20)">
        <rect x="0" y="0" width="15" height="13" fill="#2f9e6e"/><rect x="16" y="0" width="15" height="13" fill="#3b73c4"/><rect x="32" y="0" width="15" height="13" fill="#c79a3a"/><rect x="48" y="0" width="15" height="13" fill="#d05a4f"/><rect x="64" y="0" width="15" height="13" fill="#2f9e6e"/><rect x="80" y="0" width="15" height="13" fill="#3b73c4"/>
        <rect x="0" y="14" width="15" height="13" fill="#2f9e6e"/><rect x="16" y="14" width="15" height="13" fill="#3b73c4"/><rect x="32" y="14" width="15" height="13" fill="#c79a3a"/><rect x="48" y="14" width="15" height="13" fill="#3b73c4"/><rect x="64" y="14" width="15" height="13" fill="#2f9e6e"/><rect x="80" y="14" width="15" height="13" fill="#3b73c4"/>
        <rect x="0" y="28" width="15" height="13" fill="#2f9e6e"/><rect x="16" y="28" width="15" height="13" fill="#3b73c4"/><rect x="32" y="28" width="15" height="13" fill="#c79a3a"/><rect x="48" y="28" width="15" height="13" fill="#d05a4f"/><rect x="64" y="28" width="15" height="13" fill="#2f9e6e"/><rect x="80" y="28" width="15" height="13" fill="#3b73c4"/>
        <rect x="0" y="42" width="15" height="13" fill="#2f9e6e"/><rect x="16" y="42" width="15" height="13" fill="#3b73c4"/><rect x="32" y="42" width="15" height="13" fill="#c79a3a"/><rect x="48" y="42" width="15" height="13" fill="#3b73c4"/><rect x="64" y="42" width="15" height="13" fill="#2f9e6e"/><rect x="80" y="42" width="15" height="13" fill="#3b73c4"/>
        <rect x="0" y="56" width="15" height="13" fill="#2f9e6e"/><rect x="16" y="56" width="15" height="13" fill="#3b73c4"/><rect x="32" y="56" width="15" height="13" fill="#c79a3a"/><rect x="48" y="56" width="15" height="13" fill="#d05a4f"/><rect x="64" y="56" width="15" height="13" fill="#2f9e6e"/><rect x="80" y="56" width="15" height="13" fill="#3b73c4"/>
        <rect x="47" y="-3" width="17" height="75" fill="none" stroke="#1d2733" stroke-width="2" rx="2"/>
      </g>
      <path d="M118 48 h24" stroke="#999" stroke-width="2"/>
      <g transform="translate(152,22)">
        <g fill="#7a55c4"><circle cx="6" cy="6" r="4"/><circle cx="6" cy="20" r="4"/><circle cx="6" cy="34" r="4"/><circle cx="6" cy="48" r="4"/><circle cx="30" cy="14" r="4"/><circle cx="30" cy="28" r="4"/><circle cx="30" cy="42" r="4"/><circle cx="54" cy="24" r="4"/></g>
        <g stroke="#cbb8e6" stroke-width="1"><path d="M6 6l24 8M6 6l24 22M6 20l24-6M6 20l24 14M6 34l24-6M6 34l24 8M6 48l24-6M6 48l24-20M30 14l24 10M30 28l24-4M30 42l24-18"/></g>
      </g>
      <text x="156" y="90" font-size="10" fill="#777" font-family="monospace">small CNN</text>
      <path d="M220 48 h22" stroke="#999" stroke-width="2"/>
      <rect x="246" y="36" width="48" height="26" rx="5" fill="#fdeceb" stroke="#d05a4f"/>
      <text x="270" y="53" font-size="13" fill="#d05a4f" text-anchor="middle" font-family="monospace" font-weight="600">0/1</text>
      <text x="304" y="52" font-size="10" fill="#777">fast ·</text><text x="304" y="64" font-size="10" fill="#777">most sites</text>
    </svg>
    <div class="omx-cap"><b>Pileup model — fast first pass.</b> The column of bases stacked over each position feeds a small network; most sites are settled instantly.</div>
  </div>
  <div class="omx-fig">
    <svg viewBox="0 0 372 100" style="width:100%;max-width:500px;display:block;margin:2px auto">
      <text x="6" y="13" font-size="11" fill="#555" font-family="monospace">full local alignment window (gray = indel gap)</text>
      <g transform="translate(6,20)">
        <rect x="0" y="0" width="13" height="12" fill="#2f9e6e"/><rect x="14" y="0" width="13" height="12" fill="#3b73c4"/><rect x="28" y="0" width="13" height="12" fill="#e6e3da"/><rect x="42" y="0" width="13" height="12" fill="#c79a3a"/><rect x="56" y="0" width="13" height="12" fill="#d05a4f"/><rect x="70" y="0" width="13" height="12" fill="#2f9e6e"/><rect x="84" y="0" width="13" height="12" fill="#3b73c4"/>
        <rect x="0" y="13" width="13" height="12" fill="#2f9e6e"/><rect x="14" y="13" width="13" height="12" fill="#3b73c4"/><rect x="28" y="13" width="13" height="12" fill="#7a55c4"/><rect x="42" y="13" width="13" height="12" fill="#c79a3a"/><rect x="56" y="13" width="13" height="12" fill="#d05a4f"/><rect x="70" y="13" width="13" height="12" fill="#2f9e6e"/><rect x="84" y="13" width="13" height="12" fill="#3b73c4"/>
        <rect x="0" y="26" width="13" height="12" fill="#2f9e6e"/><rect x="14" y="26" width="13" height="12" fill="#3b73c4"/><rect x="28" y="26" width="13" height="12" fill="#e6e3da"/><rect x="42" y="26" width="13" height="12" fill="#c79a3a"/><rect x="56" y="26" width="13" height="12" fill="#d05a4f"/><rect x="70" y="26" width="13" height="12" fill="#2f9e6e"/><rect x="84" y="26" width="13" height="12" fill="#3b73c4"/>
        <rect x="0" y="39" width="13" height="12" fill="#2f9e6e"/><rect x="14" y="39" width="13" height="12" fill="#3b73c4"/><rect x="28" y="39" width="13" height="12" fill="#7a55c4"/><rect x="42" y="39" width="13" height="12" fill="#c79a3a"/><rect x="56" y="39" width="13" height="12" fill="#d05a4f"/><rect x="70" y="39" width="13" height="12" fill="#2f9e6e"/><rect x="84" y="39" width="13" height="12" fill="#3b73c4"/>
        <rect x="0" y="52" width="13" height="12" fill="#2f9e6e"/><rect x="14" y="52" width="13" height="12" fill="#3b73c4"/><rect x="28" y="52" width="13" height="12" fill="#e6e3da"/><rect x="42" y="52" width="13" height="12" fill="#c79a3a"/><rect x="56" y="52" width="13" height="12" fill="#d05a4f"/><rect x="70" y="52" width="13" height="12" fill="#2f9e6e"/><rect x="84" y="52" width="13" height="12" fill="#3b73c4"/>
      </g>
      <path d="M112 48 h22" stroke="#999" stroke-width="2"/>
      <g transform="translate(144,14)">
        <g fill="#7a55c4"><circle cx="6" cy="6" r="3.6"/><circle cx="6" cy="18" r="3.6"/><circle cx="6" cy="30" r="3.6"/><circle cx="6" cy="42" r="3.6"/><circle cx="6" cy="54" r="3.6"/><circle cx="28" cy="12" r="3.6"/><circle cx="28" cy="24" r="3.6"/><circle cx="28" cy="36" r="3.6"/><circle cx="28" cy="48" r="3.6"/><circle cx="50" cy="18" r="3.6"/><circle cx="50" cy="30" r="3.6"/><circle cx="50" cy="42" r="3.6"/><circle cx="72" cy="30" r="3.6"/></g>
        <g stroke="#cbb8e6" stroke-width=".8"><path d="M6 6l22 6M6 18l22-6M6 30l22 6M6 42l22 6M6 54l22-6M28 12l22 6M28 24l22 6M28 36l22-6M28 48l22-6M50 18l22 12M50 30l22 0M50 42l22-12"/></g>
      </g>
      <text x="148" y="90" font-size="10" fill="#777" font-family="monospace">deeper CNN</text>
      <path d="M224 48 h22" stroke="#999" stroke-width="2"/>
      <rect x="248" y="36" width="48" height="26" rx="5" fill="#f2ecfb" stroke="#7a55c4"/>
      <text x="272" y="53" font-size="13" fill="#7a55c4" text-anchor="middle" font-family="monospace" font-weight="600">1/1</text>
      <text x="306" y="52" font-size="10" fill="#777">hard ·</text><text x="306" y="64" font-size="10" fill="#777">indels</text>
    </svg>
    <div class="omx-cap"><b>Full-alignment model — for the hard sites.</b> Near indels and repeats, the entire 2-D local alignment is re-read by a deeper network.</div>
  </div>
  <p class="mut" style="font-size:13px">Clair3 is the lightweight, GPU-free stand-in for DeepVariant; it also catches structural variants via <span class="omx-mono">vg call</span>. Out comes a per-person genotype at every position: <span class="omx-mono">0/0</span> reference, <span class="omx-mono">0/1</span> heterozygous, <span class="omx-mono">1/1</span> homozygous-variant.</p>
</div>

<div class="omx-step">
  <div class="omx-num">5</div>
  <div class="sub">Joint genotyping & relatedness</div>
  <h3>Putting the two of us side by side</h3>
  <p><b>GLnexus</b> genotypes both of us together at every variant site, so a position is judged consistently for me and my brother. Then two questions: how related are we really, and where along the genome do we differ?</p>

  <p class="sub" style="margin-top:1rem">First — are we really dizygotic?</p>
  <div class="omx-scale">
    <div class="omx-mk" style="left:0%">unrelated<br>0</div>
    <div class="omx-mk" style="left:25%">half-sib<br>0.125</div>
    <div class="omx-mk" style="left:50%">full-sib / DZ<br>0.25</div>
    <div class="omx-mk" style="left:100%">identical / MZ<br>0.50</div>
    <div class="omx-needle" style="left:43.4%"><span class="l">us · 0.217</span></div>
  </div>
  <div class="omx-tiles">
    <div class="omx-tile"><div class="v">0.217</div><div class="k">KING kinship → DZ</div></div>
    <div class="omx-tile"><div class="v">0.047</div><div class="k">IBS0 (&gt;0 ⇒ not MZ)</div></div>
    <div class="omx-tile"><div class="v">58%</div><div class="k">genotype concordance</div></div>
    <div class="omx-tile"><div class="v">~1.79M</div><div class="k">differing genotypes</div></div>
  </div>
  <p class="mut" style="font-size:13px"><b>plink2 / KING</b> puts our kinship at 0.217 with non-zero IBS0 — squarely full-sibling / dizygotic, ruling out an identical (MZ) or parent–child relationship. We share roughly half our genome.</p>

  <p class="sub" style="margin-top:1rem">Second — where do we differ, chromosome by chromosome?</p>
  <div class="omx-chrom" id="omxChrom"></div>
  <p class="omx-cap">Differing genotypes per chromosome (quality-filtered). Lower bars are chromosomes where we happen to share more — chr20, for instance, dips sharply.</p>
</div>

<div class="omx-step">
  <div class="omx-num">6</div>
  <div class="sub">Annotation & obesity genetics</div>
  <h3>Of the millions of differences, which could matter for weight?</h3>
  <p><b>Ensembl VEP</b> annotates every variant — which gene, what consequence, how rare, predicted damage — and I keep only sites where the two of us truly differ at high confidence (both <span class="omx-mono">GQ ≥ 20, DP ≥ 10</span>). Then I ask the obesity question three ways, each grounded in the literature rather than picked by eye:</p>

  <table class="omx-loci">
    <tr><th>classic BMI locus</th><th>me</th><th>my brother</th><th>more risk</th></tr>
    <tr><td>GNPDA2 · rs10938397</td><td class="gt">A/G</td><td class="gt">G/G</td><td><span class="omx-pill b">my brother</span></td></tr>
    <tr><td>TMEM18 · rs2867125</td><td class="gt">C/C</td><td class="gt">C/C</td><td><span class="omx-pill s">same</span></td></tr>
    <tr><td>NEGR1 · rs2815752</td><td class="gt">G/G</td><td class="gt">G/G</td><td><span class="omx-pill s">same</span></td></tr>
  </table>

  <p style="font-size:14px"><b>And the whole-genome BMI polygenic score</b> — thousands of small-effect variants summed by published weights. Same-ancestry twins are directly comparable:</p>
  <div class="omx-prs">
    <div class="row"><div class="nm">PGS000027<br><span style="font-size:9px">2.1M variants</span></div><div class="pair">
      <div class="bar"><div class="fy" style="width:99.3%">me · 8.53e-6</div></div>
      <div class="bar"><div class="fb" style="width:100%">my brother · 8.59e-6</div></div></div></div>
    <div class="row"><div class="nm">PGS002313<br><span style="font-size:9px">1.1M variants</span></div><div class="pair">
      <div class="bar"><div class="fy" style="width:54%">me</div></div>
      <div class="bar"><div class="fb" style="width:100%">my brother</div></div></div></div>
  </div>
  <p class="mut" style="font-size:13px">Why look at <b>FTO, MC4R, GNPDA2…</b> at all? Because these are the loci the field has repeatedly tied to body weight. The reasoning rests on:</p>
  <div class="omx-cites">
    <span>monogenic panel · Farooqi &amp; O'Rahilly · Pigeyre 2016</span>
    <span>variant grading · ACMG, Richards 2015</span>
    <span>FTO · Frayling 2007</span>
    <span>MC4R · Loos 2008</span>
    <span>GWAS · Willer 2009</span>
    <span>meta · Locke 2015 · Yengo 2018</span>
    <span>PGS · Khera 2019 · LDpred, Vilhjálmsson 2015</span>
    <span>weights · PGS Catalog</span>
  </div>
</div>

<div class="omx-step">
  <div class="omx-num">7</div>
  <div class="sub">The answer</div>
  <h3>An honest negative</h3>
  <p>Three independent readings all point the same way: <b>zero</b> monogenic obesity-gene variants differ between us; our genome-wide BMI polygenic scores are <b>essentially identical</b> (within noise, and nominally <em>higher</em> in my leaner brother); and the one classic BMI variant that does differ, GNPDA2, carries <b>more</b> risk in him, not me.</p>
</div>

</div>

<div class="omx-concl">
  <h3>So — does DNA explain it?</h3>
  <p>On this data, <em>no</em>. Common-variant genetics does not account for why I've been the heavier twin, and if anything leans the other way. A lifelong difference between two people who shared a womb, a home and a diet is most likely driven by something <em>genetics can't see here</em> — early-life environment, behaviour and epigenetics. That isn't the dramatic answer, but it's the honest one, and reaching it cleanly was the entire point.</p>
</div>

<p class="omx-cap" style="margin-top:1rem">Tooling: vg Giraffe (HPRC pangenome) · Clair3 · GLnexus · bcftools · plink2 (KING + PGS) · Ensembl VEP · PGS Catalog. Built from raw FASTQ on an HPC node. The icons and schematic are hand-drawn vector art, not AI rasters. — <a href="{{ '/assets/omics_dashboard.html' | relative_url }}" target="_blank" rel="noopener">open the full interactive dashboard</a></p>

</div>

<script>
(function(){
  var d=[["1",176500],["2",122755],["3",101138],["4",158138],["5",71874],["6",104505],["7",151832],["8",61069],["9",78097],["10",59745],["11",110660],["12",111523],["13",71860],["14",59705],["15",50193],["16",72232],["17",35127],["18",53630],["19",75023],["20",11367],["21",25596],["22",36774],["X",27481],["Y",178]];
  var mx=Math.max.apply(null,d.map(function(x){return x[1]}));
  var el=document.getElementById('omxChrom'); if(!el) return;
  d.forEach(function(x){var h=(x[1]/mx*100).toFixed(1);
    el.insertAdjacentHTML('beforeend','<div class="cb" style="height:'+h+'%" title="chr'+x[0]+': '+x[1].toLocaleString()+' differing"><div class="cl">'+x[0]+'</div></div>');});
})();
</script>
