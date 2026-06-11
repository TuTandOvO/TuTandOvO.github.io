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
.omx-scale{position:relative;height:13px;border-radius:7px;margin:34px 0 8px;
  background:linear-gradient(90deg,#eef1f5,#e9f1fb 28%,#fdeceb 55%,#f6efe1);border:1px solid var(--ln)}
.omx-mk{position:absolute;top:-22px;transform:translateX(-50%);font-size:9.5px;color:var(--mut);font-family:"IBM Plex Mono",monospace;text-align:center;width:84px}
.omx-needle{position:absolute;top:-5px;width:3px;height:23px;border-radius:2px;background:var(--you);transform:translateX(-50%);box-shadow:0 0 0 3px rgba(208,90,79,.18)}
.omx-needle .l{position:absolute;top:-19px;left:50%;transform:translateX(-50%);white-space:nowrap;font-size:11px;font-weight:600;color:var(--you)}
/* chrom bars */
.omx-chrom{display:flex;align-items:flex-end;gap:2px;height:96px;margin:.4rem 0 20px}
.omx-chrom .cb{flex:1;background:linear-gradient(180deg,#e7a59e,#d05a4f);border-radius:2px 2px 0 0;position:relative}
.omx-chrom .cl{font-size:7.5px;color:var(--mut);position:absolute;bottom:-15px;left:0;right:0;text-align:center}
/* stat tiles */
.omx-tiles{display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin:.6rem 0}
.omx-tile{border:1px solid var(--ln);border-radius:11px;padding:11px 12px;background:#fbfaf7}
.omx-tile .v{font-family:"Fraunces",serif;font-weight:600;font-size:21px;line-height:1}
.omx-tile .k{font-size:10.5px;color:var(--mut);margin-top:5px;font-family:"IBM Plex Mono",monospace}
/* prs */
.omx-prs .row{display:grid;grid-template-columns:96px 1fr;align-items:center;gap:9px;margin:7px 0}
.omx-prs .nm{font-size:11px;font-family:"IBM Plex Mono",monospace;color:var(--mut)}
.omx-prs .bar{position:relative;height:26px;background:#f4f1ea;border-radius:6px;overflow:hidden}
.omx-prs .fy,.omx-prs .fb{position:absolute;top:0;bottom:0;border-radius:6px;display:flex;align-items:center;justify-content:flex-end;padding-right:8px;font-size:10.5px;color:#fff;font-weight:600}
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
.omx-concl p{color:#cfd5dc;font-size:14px;line-height:1.62;margin:0}
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
  <div class="omx-emblem"><img src="{{ '/assets/img/logo_bgi.webp' | relative_url }}" alt="BGI" style="height:30px"></div>
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
        <svg width="40" height="40" viewBox="0 0 40 40" fill="none"><path d="M13 9c0-3.5 14-3.5 14 0v8c0 6.5-3.2 14-7 14s-7-7.5-7-14z" stroke="#3b73c4" stroke-width="2"/><rect x="13" y="16" width="14" height="3.2" rx="1" fill="#3b73c4"/><path d="M16 23v6M20 23v6.5M24 23v6" stroke="#3b73c4" stroke-width="1.6" stroke-linecap="round"/></svg>
      </div>
      <div class="note">European-ancestry reference</div>
    </div>
    <div class="col">
      <div class="ttl">me</div>
      <div class="ic">
        <svg width="40" height="40" viewBox="0 0 40 40" fill="none"><rect x="18" y="5" width="4" height="17" rx="2" fill="#c79a3a"/><path d="M15.5 22h9l-2.4 9h-4.2z" fill="#1d2733"/><path d="M19.4 31l.6 4 .6-4" stroke="#1d2733" stroke-width="1.4"/></svg>
      </div>
      <div class="note">East-Asian genome</div>
    </div>
    <div class="col ok">
      <div class="ttl">pangenome ✅</div>
      <div class="ic">
        <svg width="50" height="40" viewBox="0 0 50 40"><circle cx="12" cy="15" r="5" fill="#d05a4f"/><circle cx="25" cy="11" r="5" fill="#3b73c4"/><circle cx="38" cy="15" r="5" fill="#2f9e6e"/><circle cx="18" cy="26" r="5" fill="#c79a3a"/><circle cx="32" cy="26" r="5" fill="#7a55c4"/></svg>
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
  <div class="omx-models">
    <div class="omx-model">
      <div class="h">
        <svg width="34" height="30" viewBox="0 0 46 40"><g stroke="#d05a4f" stroke-width="2.4" stroke-linecap="round"><path d="M6 9h12M6 15h12M6 21h12M6 27h12M6 33h12"/></g><rect x="20.5" y="6" width="3" height="30" fill="#d05a4f" opacity=".28"/><rect x="30" y="11" width="10" height="18" rx="2" fill="none" stroke="#d05a4f" stroke-width="2"/></svg>
        Pileup model
      </div>
      <div class="d">Fast first pass. Looks at the <b>stack of bases</b> sitting over each position and classifies most sites instantly.</div>
    </div>
    <div class="omx-model">
      <div class="h">
        <svg width="34" height="30" viewBox="0 0 46 40"><g stroke="#7a55c4" stroke-width="2" stroke-linecap="round"><path d="M5 10h14M9 16h12M5 22h16M7 28h13"/></g><rect x="28" y="11" width="12" height="18" rx="2" fill="none" stroke="#7a55c4" stroke-width="2"/><circle cx="34" cy="16" r="1.5" fill="#7a55c4"/><circle cx="31" cy="22" r="1.5" fill="#7a55c4"/><circle cx="37" cy="22" r="1.5" fill="#7a55c4"/></svg>
        Full-alignment model
      </div>
      <div class="d">Called in only for the <b>hard sites</b> (near indels, repeats), where it re-examines the whole local alignment in detail.</div>
    </div>
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
