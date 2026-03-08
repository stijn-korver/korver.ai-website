---
layout: project
title: End-to-End Inoculation
summary: Fully autonomous plant inoculation system combining image segmentation and robotic control to deliver precise inoculation to root tips across thousands of Petri dishes.
category: Automation
tags: [Computer Vision, Robotics]
banner: /assets/images/projects/end-to-end-inoculation/banner.png
icon: 🌱
order: 6
date: January 2026
featured: true
---

<style>
  /* ── RESET & BASE ── */
  .project-body p { text-align: justify; }

  /* ── SECTION DIVIDERS ── */
  .section-label {
    font-family: var(--font-head);
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 0.4rem;
  }

  /* ── PIPELINE CAROUSEL ── */
  .pipeline-carousel-wrap {
    position: relative;
    margin: 2rem 0 2.5rem;
  }
  .pipeline-carousel {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
    transition: none;
  }
  .pipeline-step {
    background: var(--gray-light);
    border-radius: 0.75rem;
    padding: 1.25rem 0.75rem 1.25rem;
    text-align: center;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s, background 0.2s;
    position: relative;
    user-select: none;
  }
  .pipeline-step:hover  { transform: translateY(-4px); box-shadow: 0 12px 24px rgba(45,55,120,0.12); }
  .pipeline-step.highlight { background: var(--black); }
  .step-num {
    position: absolute; top: 0.5rem; left: 0.75rem;
    font-family: var(--font-head); font-size: 0.65rem; font-weight: 700;
    color: var(--gray-mid); letter-spacing: 0.05em;
  }
  .pipeline-step.highlight .step-num { color: rgba(255,255,255,0.2); }
  .step-icon { margin-bottom: 0.4rem; }
  .step-icon img { width: 100%; aspect-ratio: 1/1; object-fit: cover; border-radius: 0.4rem; display: block; }
  .step-title { font-family: var(--font-head); font-size: 0.85rem; font-weight: 700; color: var(--black); margin-bottom: 0.2rem; }
  .pipeline-step.highlight .step-title { color: var(--accent); }
  .step-label { font-size: 0.7rem; color: var(--gray); font-weight: 300; line-height: 1.4; }
  .pipeline-step.highlight .step-label { color: rgba(255,255,255,0.5); }

  /* nav arrows */
  .carousel-arrow {
    display: none; /* hidden on desktop, shown on mobile */
    position: absolute;
    top: 50%; transform: translateY(-50%);
    width: 2rem; height: 2rem;
    background: var(--black); color: var(--white);
    border: none; border-radius: 50%; cursor: pointer;
    font-size: 1rem; line-height: 1;
    align-items: center; justify-content: center;
    z-index: 2; box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    transition: background 0.2s;
  }
  .carousel-arrow:hover { background: var(--accent); color: var(--black); }
  .carousel-arrow.prev { left: -1rem; }
  .carousel-arrow.next { right: -1rem; }

  /* dots */
  .carousel-dots {
    display: none;
    justify-content: center;
    gap: 0.4rem;
    margin-top: 1rem;
  }
  .carousel-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--gray-mid); cursor: pointer;
    transition: background 0.2s, transform 0.2s;
  }
  .carousel-dot.active { background: var(--black); transform: scale(1.4); }

  @media (max-width: 700px) {
    .pipeline-carousel {
      grid-template-columns: repeat(4, calc(100% - 2rem));
      overflow-x: auto;
      scroll-snap-type: x mandatory;
      -webkit-overflow-scrolling: touch;
      gap: 0.75rem;
      scrollbar-width: none;
      padding-bottom: 0.25rem;
    }
    .pipeline-carousel::-webkit-scrollbar { display: none; }
    .pipeline-step { scroll-snap-align: center; min-width: 0; }
    .carousel-dots { display: flex; }
  }

  /* ── BEFORE / AFTER ── */
  .before-after { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 2.5rem 0; }
  .ba-panel { border-radius: 0.75rem; overflow: hidden; border: 1.5px solid var(--gray-mid); }
  .ba-label { background: var(--black); color: var(--white); font-family: var(--font-head); font-size: 0.8rem; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; padding: 0.6rem 1rem; }
  .ba-label.after { background: var(--accent); color: var(--black); }
  .ba-image { background: var(--gray-light); overflow: hidden; }
  .ba-image img { width: 100%; display: block; }
  .ba-stats { padding: 0.75rem 1rem; border-top: 1px solid var(--gray-mid); display: flex; gap: 1.5rem; flex-wrap: wrap; }
  .ba-stat { font-size: 0.78rem; color: var(--gray); }
  .ba-stat strong { color: var(--black); font-weight: 600; display: block; font-size: 0.9rem; }

  /* ── CALLOUT ── */
  .callout { background: var(--black); color: var(--white); border-radius: 0.75rem; padding: 1.5rem 2rem; margin: 2rem 0; display: flex; align-items: center; gap: 1.5rem; }
  .callout-icon { font-size: 2rem; flex-shrink: 0; }
  .callout-text { font-size: 0.95rem; font-weight: 300; line-height: 1.7; color: rgba(255,255,255,0.8); }
  .callout-text strong { color: var(--accent); font-weight: 600; }

  /* ── KAGGLE CHART ── */
  .kaggle-wrap { background: var(--gray-light); border-radius: 0.75rem; padding: 1.5rem; margin: 1.5rem 0; }
  .kaggle-title { font-family: var(--font-head); font-size: 1rem; font-weight: 700; margin-bottom: 0.2rem; }
  .kaggle-sub { font-size: 0.78rem; color: var(--gray); margin-bottom: 1rem; font-weight: 300; }
  .chart-container { position: relative; height: 220px; }
  .kaggle-highlight {
    display: flex; align-items: center; gap: 1rem; background: var(--white);
    border-radius: 0.6rem; padding: 0.75rem 1.25rem; margin-top: 1rem;
    border: 1.5px solid var(--gray-mid);
  }
  .kaggle-rank { font-family: var(--font-head); font-size: 2rem; font-weight: 700; color: var(--accent); line-height: 1; }
  .kaggle-rank-label { font-size: 0.78rem; color: var(--gray); }
  .kaggle-rank-label strong { color: var(--black); display: block; font-size: 0.88rem; }

  /* ── CHARTS GRID ── */
  .chart-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 2.5rem 0; }
  .chart-card { background: var(--gray-light); border-radius: 0.75rem; padding: 1.5rem; }
  .chart-title { font-family: var(--font-head); font-size: 1rem; font-weight: 700; color: var(--black); margin-bottom: 0.2rem; }
  .chart-subtitle { font-size: 0.78rem; color: var(--gray); margin-bottom: 1rem; font-weight: 300; }

  /* ── CODE DIFF ── */
  .code-diff { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 1.5rem 0; }
  .code-pane { border-radius: 0.75rem; overflow: hidden; border: 1.5px solid var(--gray-mid); }
  .code-pane-label { padding: 0.5rem 1rem; font-family: var(--font-head); font-size: 0.75rem; font-weight: 700; letter-spacing: 0.06em; text-transform: uppercase; }
  .code-pane-label.before-label { background: var(--black); color: var(--gray); }
  .code-pane-label.after-label  { background: var(--accent); color: var(--black); }
  .code-pane pre {
    margin: 0; padding: 1.25rem; background: #1a1d2e;
    font-family: 'JetBrains Mono', 'Fira Code', monospace;
    font-size: 0.82rem; line-height: 1.7; color: #a8b2d8;
    overflow-x: auto;
  }
  .code-kw  { color: #82aaff; }
  .code-fn  { color: #c3e88d; }
  .code-arg { color: #ffcb6b; }
  .code-val { color: #f78c6c; }
  .code-dot { color: #89ddff; }

  /* ── TABLE ── */
  .project-body table { width: 100%; border-collapse: collapse; margin: 1.5rem 0; font-size: clamp(0.62rem, 1.5vw, 0.88rem); }
  .project-body th { background: var(--black); color: var(--white); padding: 0.75rem 1rem; text-align: left; font-family: var(--font-head); font-weight: 600; font-size: 0.8rem; }
  .project-body td { padding: 0.6rem 1rem; border-bottom: 1px solid var(--gray-light); color: var(--gray); }
  .project-body tr:hover td { background: var(--gray-light); }
  .td-win { color: #1e8449 !important; font-weight: 700; }

  /* ── STAT ROW ── */
  .stat-row { display: flex; gap: 1rem; flex-wrap: wrap; margin: 1.5rem 0; }
  .stat-box { flex: 1; min-width: 120px; background: var(--gray-light); border-radius: 0.75rem; padding: 1rem 1.25rem; text-align: center; }
  .stat-num { font-family: var(--font-head); font-size: 1.6rem; font-weight: 700; color: var(--black); line-height: 1; }
  .stat-num span { color: var(--accent); }
  .stat-lbl { font-size: 0.72rem; color: var(--gray); margin-top: 0.25rem; }

  /* ── LIMITATIONS / NEXT STEPS GRID ── */
  .two-col-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 1.5rem 0; }
  .info-card { background: var(--gray-light); border-radius: 0.75rem; padding: 1.25rem 1.5rem; }
  .info-card h4 { font-family: var(--font-head); font-size: 0.85rem; font-weight: 700; color: var(--black); margin: 0 0 0.75rem; text-transform: uppercase; letter-spacing: 0.06em; }
  .info-card ul { margin: 0; padding-left: 1.1rem; }
  .info-card li { font-size: 0.85rem; color: var(--gray); line-height: 1.8; }
  .info-card li strong { color: var(--black); }
  .info-card.dark { background: var(--black); }
  .info-card.dark h4 { color: var(--accent); }
  .info-card.dark li { color: rgba(255,255,255,0.6); }

  @media (max-width: 700px) {
    .before-after,
    .chart-grid, .code-diff, .two-col-cards { grid-template-columns: 1fr; }
    .stat-row { gap: 0.75rem; }
  }
</style>

## Overview

Plant research requires precise, repeatable inoculation of hundreds of plants. This process is traditionally manual, time-consuming, and prone to inconsistency. For meaningful scientific results, our client needed standardized conditions across large sample sizes.

This project delivers a **fully autonomous end-to-end inoculation system** built for a large-scale plant phenotyping facility. It handles the complete workflow: from real-time plant detection using deep learning segmentation, to precise inoculation delivery via robotic control targeting *Arabidopsis thaliana* roots across a high-throughput system capable of processing up to 10,000 seedlings across over 2,000 Petri dishes.

<div class="stat-row">
  <div class="stat-box"><div class="stat-num">10k</div><div class="stat-lbl">Seedlings</div></div>
  <div class="stat-box"><div class="stat-num">2k+</div><div class="stat-lbl">Petri Dishes</div></div>
  <div class="stat-box"><div class="stat-num">93.6%</div><div class="stat-lbl">Accuracy</div></div>
  <div class="stat-box"><div class="stat-num">100%</div><div class="stat-lbl">Inoculation Success</div></div>
</div>

---

## Proposed Solution

The solution that we proposed to our client is a fully autonomous system that uses the cleints existing infrastructure to capture images, segment the plants from the image, locate the root-tips and communicates these to the robot so it can deliver the inoculation using a PID controller we designed. Click each step to explore what happens and why.

<div class="pipeline-carousel-wrap">
  <div class="pipeline-carousel" id="pipelineCarousel">
    <div class="pipeline-step">
      <div class="step-num">01</div>
      <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-capture.png" alt="Image Capture" /></div>
      <div class="step-title">Image Capture</div>
      <div class="step-label">Daily Photographs of Petri Dishes</div>
    </div>
    <div class="pipeline-step highlight">
      <div class="step-num">02</div>
      <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-segmentation.png" alt="Segmentation" /></div>
      <div class="step-title">Segmentation</div>
      <div class="step-label">Detects Roots</div>
    </div>
    <div class="pipeline-step highlight">
      <div class="step-num">03</div>
      <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-roottip.png" alt="Root Tip Detection" /></div>
      <div class="step-title">Root Tip Detection</div>
      <div class="step-label">Locate Root-Tips</div>
    </div>
    <div class="pipeline-step">
      <div class="step-num">04</div>
      <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-inoculation.gif" alt="Inoculation" /></div>
      <div class="step-title">Inoculation</div>
      <div class="step-label">Autonomous Delivery to Root Tips</div>
    </div>
  </div>
  <div class="carousel-dots" id="pipelineDots">
    <div class="carousel-dot active" onclick="carouselScrollTo(0)"></div>
    <div class="carousel-dot" onclick="carouselScrollTo(1)"></div>
    <div class="carousel-dot" onclick="carouselScrollTo(2)"></div>
    <div class="carousel-dot" onclick="carouselScrollTo(3)"></div>
  </div>
</div>

---

## Image Segmentation Model

The segmentation backbone is a **U-Net** trained to classify every pixel in a Petri dish image. The dataset consists of high-resolution grayscale scans with expert-labelled ground truth masks.

### Training Strategy

A key challenge was class imbalance: roots and seeds occupy only a small fraction of each image. The training pipeline addresses this by tiling images into 128×128 patches and applying aggressive background filtering.

<div class="section-label">Patch sampling strategy</div>
<div class="before-after" style="margin-top:0.5rem;">
  <div class="ba-panel">
    <div class="ba-label">Background-only patches</div>
    <div class="ba-image"><img src="/assets/images/projects/end-to-end-inoculation/pipeline-capture.png" alt="Patch sampling" /></div>
    <div class="ba-stats">
      <div class="ba-stat"><strong>90% removed</strong>Background-only tiles discarded</div>
      <div class="ba-stat"><strong>10% kept</strong>To preserve global context</div>
    </div>
  </div>
  <div class="ba-panel">
    <div class="ba-label after">Root / Seed / Shoot patches</div>
    <div class="ba-image"><img src="/assets/images/projects/end-to-end-inoculation/pipeline-segmentation.png" alt="Root patches" /></div>
    <div class="ba-stats">
      <div class="ba-stat"><strong>100% kept</strong>All informative patches retained</div>
      <div class="ba-stat"><strong>128×128 px</strong>Patch size</div>
    </div>
  </div>
</div>

### Model Iteration

The model improved significantly across 39 training iterations. Each change addressed a specific weakness — from class imbalance, to data efficiency, to optimiser behaviour.

| Itr | Change | Loss | F1-score |
|---|---|---|---|
| 2 | Baseline | 5.6364 | 0.2681 |
| 3 | Square root class weights | 0.3444 | 0.6671 |
| 6 | Filter background-only patches | 0.0451 | 0.7628 |
| 24 | Data augmentation | 0.0534 | 0.7705 |
| **39** | **Reduce LR on plateau** | **0.0048** | **0.8308** |

---

## Kaggle Leaderboard

The model was benchmarked via a Kaggle competition using root length sMAPE (Symmetric Mean Absolute Percentage Error) on a blind test set — a measure of how accurately extracted root lengths match ground truth.

<div class="kaggle-wrap">
  <div class="kaggle-title">Root Length sMAPE by Submission</div>
  <div class="kaggle-sub">Lower is better — public and private leaderboard scores</div>
  <div class="chart-container"><canvas id="kaggleChart"></canvas></div>
  <div class="kaggle-highlight">
    <div class="kaggle-rank">#12</div>
    <div class="kaggle-rank-label"><strong>Leaderboard position</strong>sMAPE of 6.877 on blind test set — down from 73% error at submission 1</div>
  </div>
</div>

---

## Instance Segmentation: Before & After

A key challenge was separating individual plant roots in dense images. Early model versions detected spurious instances — small noise artifacts classified as separate plants — inflating plant counts and corrupting root length measurements.

<div class="before-after">
  <div class="ba-panel">
    <div class="ba-label">Before</div>
    <div class="ba-image"><img src="/assets/images/projects/end-to-end-inoculation/segmentation-before.png" alt="Before: spurious detections" /></div>
    <div class="ba-stats">
      <div class="ba-stat"><strong>5 instances</strong>Plants detected</div>
      <div class="ba-stat"><strong>566 · 8 · 231 · 1 · 35 px</strong>Root lengths</div>
    </div>
  </div>
  <div class="ba-panel">
    <div class="ba-label after">After</div>
    <div class="ba-image"><img src="/assets/images/projects/end-to-end-inoculation/segmentation-after.png" alt="After: clean instance segmentation" /></div>
    <div class="ba-stats">
      <div class="ba-stat"><strong>2 instances</strong>Plants detected</div>
      <div class="ba-stat"><strong>569 · 236 px</strong>Root lengths</div>
    </div>
  </div>
</div>

<div class="callout">
  <div class="callout-icon">🏆</div>
  <div class="callout-text">After improving the pipeline, spurious detections were eliminated entirely and root length measurements became significantly more accurate — reflecting the true 2 plants present in the dish rather than 5.</div>
</div>

---

## Robotic Control: PID vs Reinforcement Learning

Two independent controllers were designed and benchmarked in a **physics simulation** of the target robot platform for positioning a pipette over detected root tips.

<div class="chart-grid">
  <div class="chart-card">
    <div class="chart-title">PID Controller</div>
    <div class="chart-subtitle">Mean positioning error across all axes (200 steps)</div>
    <div class="chart-container"><canvas id="pidChart"></canvas></div>
  </div>
  <div class="chart-card">
    <div class="chart-title">RL Controller</div>
    <div class="chart-subtitle">Mean positioning error across all axes (14 steps)</div>
    <div class="chart-container"><canvas id="rlChart"></canvas></div>
  </div>
</div>

| Controller | Success Rate | Settling Time | X-Error | Y-Error | Z-Error |
|---|---|---|---|---|---|
| **PID** | <span class="td-win">100%</span> | ~70 steps | <span class="td-win">0.12 mm</span> | <span class="td-win">0.15 mm</span> | <span class="td-win">0.03 mm</span> |
| RL | 12% | ~3 steps | 1.05 mm | 0.98 mm | 0.51 mm |

The **PID controller** — with Kp = 15.0, Ki = 0.5, Kd = 1.0 — proved highly reliable, achieving 100% success across 50 targets with sub-millimetre accuracy on all axes. It is the controller used in the delivered system.

The **RL controller** converges in far fewer steps (3 vs 70) but lacks the precision required for inoculation. Its reward function (distance penalty + boundary penalty of −1.0 + success bonus of +50.0) was insufficiently shaped to incentivise fine-grained accuracy over coarse convergence. Longer training runs and a more granular reward signal are the most promising avenues for closing this gap.

---

## Simulation Architecture

Getting images out of the simulation environment required a structural refactor. Initially, simulation was nested inside controller execution, meaning images could only be captured mid-run. Decoupling the simulation lifecycle made it possible to extract frames independently at any stage of the pipeline.

<div class="code-diff">
  <div class="code-pane">
    <div class="code-pane-label before-label">Before</div>
    <pre><span class="code-fn">sys</span><span class="code-dot">.</span><span class="code-fn">extract_tips</span>
<span class="code-fn">sys</span><span class="code-dot">.</span><span class="code-fn">run_controller</span>
  ├── <span class="code-fn">sim</span>(<span class="code-arg">num_agents</span>=<span class="code-val">1</span>)
  └── <span class="code-fn">sim</span><span class="code-dot">.</span><span class="code-fn">close</span>()</pre>
  </div>
  <div class="code-pane">
    <div class="code-pane-label after-label">After</div>
    <pre><span class="code-fn">sim</span>(<span class="code-arg">num_agents</span>=<span class="code-val">1</span>)

<span class="code-fn">sys</span><span class="code-dot">.</span><span class="code-fn">extract_tips</span>
<span class="code-fn">sys</span><span class="code-dot">.</span><span class="code-fn">run_controller</span>
<span class="code-fn">sim</span><span class="code-dot">.</span><span class="code-fn">close</span>()</pre>
  </div>
</div>

<p style="font-size:0.75rem;color:var(--gray);margin-top:-1rem;">* Illustrative — not actual syntax</p>

---

## Limitations & Next Steps

<div class="two-col-cards">
  <div class="info-card dark">
    <h4>Current Limitations</h4>
    <ul>
      <li>Only <strong>650 of 1,350</strong> available Petri dishes were used for training</li>
      <li>Limited variation in training data — edge cases (condensation, occlusion, very short roots) not handled</li>
      <li>Training capped at <strong>60 hours / 39 iterations</strong> due to hardware constraints</li>
      <li>RL controller precision insufficient for production use in current form</li>
    </ul>
  </div>
  <div class="info-card">
    <h4>Next Steps</h4>
    <ul>
      <li>Scale to <strong>256×256</strong> patches for finer root detail</li>
      <li>Incorporate remaining <strong>700 dishes</strong> into training</li>
      <li>Extensive error analysis on failed and edge-case images</li>
      <li>Add dedicated <strong>seed detection</strong> for earlier-stage inoculation</li>
      <li>Refine RL reward shaping and extend training budget</li>
    </ul>
  </div>
</div>

---

## Outcome

The delivered system provides a scalable, automated alternative to manual plant inoculation. Root detection is reliable under normal conditions, the PID controller meets production accuracy requirements, and the modular pipeline architecture makes future improvements straightforward to integrate. The RL controller, while not yet production-ready, demonstrated meaningful convergence behaviour that warrants further exploration.

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
  /* ── STEPPER ── */
  function showStep(group, idx, total) {
    const nav = document.getElementById(group + 'Nav');
    const tabs = nav.querySelectorAll('.stepper-tab');
    tabs.forEach((t, i) => t.classList.toggle('active', i === idx));
    for (let i = 0; i < total; i++) {
      const el = document.getElementById(group + '-' + i);
      if (el) el.classList.toggle('active', i === idx);
    }
  }

  /* ── CHART HELPERS ── */
  const navy  = '#2d3778';
  const red   = '#e74c3c';
  const green = '#27ae60';
  const gray  = '#7a7f9a';
  const lgray = 'rgba(45,55,120,0.07)';

  function decay(steps, start, end, rate, noise) {
    return Array.from({length: steps}, (_, i) => {
      const base = start * Math.exp(-rate * i) + end;
      return Math.max(end * 0.8, base + (Math.random() - 0.5) * base * noise);
    });
  }

  const commonOpts = (maxY, maxTicks) => ({
    responsive: true,
    maintainAspectRatio: false,
    plugins: { legend: { labels: { font: { size: 10 }, boxWidth: 10, color: gray } } },
    scales: {
      x: { title: { display: true, text: 'Steps', color: gray, font: { size: 10 } },
           ticks: { maxTicksLimit: maxTicks, color: gray, font: { size: 9 } }, grid: { color: lgray } },
      y: { title: { display: true, text: 'Mean Error (mm)', color: gray, font: { size: 10 } },
           ticks: { color: gray, font: { size: 9 } }, grid: { color: lgray }, min: 0, max: maxY }
    }
  });

  new Chart(document.getElementById('pidChart'), {
    type: 'line',
    data: {
      labels: Array.from({length: 200}, (_, i) => i),
      datasets: [
        { label: 'X-axis', data: decay(200, 70, 0.12, 0.05, 0.25), borderColor: red,   backgroundColor: 'rgba(231,76,60,0.07)',  borderWidth: 2, pointRadius: 0, tension: 0.4, fill: true },
        { label: 'Y-axis', data: decay(200, 60, 0.15, 0.055,0.25), borderColor: navy,  backgroundColor: 'rgba(45,55,120,0.05)',  borderWidth: 2, pointRadius: 0, tension: 0.4, fill: true },
        { label: 'Z-axis', data: decay(200, 50, 0.03, 0.07, 0.20), borderColor: green, backgroundColor: 'rgba(39,174,96,0.05)',  borderWidth: 2, pointRadius: 0, tension: 0.4, fill: true },
        { label: '1mm threshold', data: Array(200).fill(1), borderColor: gray, borderWidth: 1.5, borderDash: [5,4], pointRadius: 0, fill: false }
      ]
    },
    options: commonOpts(75, 8)
  });

  new Chart(document.getElementById('rlChart'), {
    type: 'line',
    data: {
      labels: Array.from({length: 14}, (_, i) => i),
      datasets: [
        { label: 'X-axis', data: decay(14, 70, 1.05, 0.45, 0.5), borderColor: red,   backgroundColor: 'rgba(231,76,60,0.07)', borderWidth: 2, pointRadius: 3, tension: 0.3, fill: true },
        { label: 'Y-axis', data: decay(14, 60, 0.98, 0.50, 0.5), borderColor: navy,  backgroundColor: 'rgba(45,55,120,0.05)', borderWidth: 2, pointRadius: 3, tension: 0.3, fill: true },
        { label: 'Z-axis', data: decay(14, 50, 0.51, 0.60, 0.4), borderColor: green, backgroundColor: 'rgba(39,174,96,0.05)', borderWidth: 2, pointRadius: 3, tension: 0.3, fill: true },
        { label: '1mm threshold', data: Array(14).fill(1), borderColor: gray, borderWidth: 1.5, borderDash: [5,4], pointRadius: 0, fill: false }
      ]
    },
    options: commonOpts(75, 7)
  });

  /* ── KAGGLE CHART ── */
  new Chart(document.getElementById('kaggleChart'), {
    type: 'bar',
    data: {
      labels: ['Sub 1','Sub 2','Sub 3','Sub 4','Sub 5','Sub 6','Sub 7','Sub 8','Sub 10','Sub 11','Sub 12'],
      datasets: [
        {
          label: 'Public sMAPE',
          data: [73, 55, 41, 35, 28, 22, 18, 13, 10, 8, null],
          backgroundColor: 'rgba(45,55,120,0.25)',
          borderColor: navy,
          borderWidth: 1.5,
          borderRadius: 4
        },
        {
          label: 'Private sMAPE',
          data: [null, null, null, null, null, null, null, null, null, null, 6.877],
          backgroundColor: 'rgba(245,184,0,0.85)',
          borderColor: '#c9970a',
          borderWidth: 1.5,
          borderRadius: 4
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: { legend: { labels: { font: { size: 10 }, boxWidth: 10, color: gray } } },
      scales: {
        x: { ticks: { color: gray, font: { size: 9 } }, grid: { color: lgray } },
        y: {
          title: { display: true, text: '% Error (sMAPE)', color: gray, font: { size: 10 } },
          ticks: { color: gray, font: { size: 9 } }, grid: { color: lgray }, min: 0
        }
      }
    }
  });
</script>