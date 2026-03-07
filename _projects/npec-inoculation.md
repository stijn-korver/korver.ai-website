---
layout: project
title: End-to-End Inoculation System
summary: Plant inoculation system that does time-consuming, tedious, error-prone work autonomously, built for the Netherlands Plant Eco-phenotyping Centre (NPEC).
category: Automation
tags: [Computer Vision, Robotics]
banner: /assets/images/projects/npec-inoculation/banner.png
icon: 🌱
order: 6
date: January 2026
featured: true
---

<style>
  /* GENERAL */
  .project-body p { text-align: justify; }
  /* PIPELINE — 3 columns top row, 3 columns bottom row on desktop */
  .pipeline-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
    margin: 2.5rem 0;
  }
  .pipeline-row {
    display: contents;
  }
  .pipeline-step {
    background: var(--gray-light);
    border-radius: 0.75rem;
    padding: 1.25rem 0.75rem;
    text-align: center;
    transition: transform 0.2s, box-shadow 0.2s;
    position: relative;
  }
  .pipeline-step:hover { transform: translateY(-4px); box-shadow: 0 12px 24px rgba(45,55,120,0.12); }
  .pipeline-step.highlight { background: var(--black); }
  .step-icon { font-size: 1.5rem; margin-bottom: 0.4rem; }
  .step-title { font-family: var(--font-head); font-size: 0.85rem; font-weight: 700; color: var(--black); margin-bottom: 0.2rem; }
  .pipeline-step.highlight .step-title { color: var(--accent); }
  .step-label { font-size: 0.7rem; color: var(--gray); font-weight: 300; line-height: 1.4; }
  .pipeline-step.highlight .step-label { color: rgba(255,255,255,0.5); }
  .step-num {
    position: absolute;
    top: 0.5rem; left: 0.75rem;
    font-family: var(--font-head);
    font-size: 0.65rem;
    font-weight: 700;
    color: var(--gray-mid);
    letter-spacing: 0.05em;
  }
  .pipeline-step.highlight .step-num { color: rgba(255,255,255,0.2); }
  .step-icon img {
    width: 100%;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    border-radius: 0.4rem;
    margin-bottom: 0.4rem;
  }

  /* BEFORE/AFTER */
  .before-after { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 2.5rem 0; }
  .ba-panel { border-radius: 0.75rem; overflow: hidden; border: 1.5px solid var(--gray-mid); }
  .ba-label { background: var(--black); color: var(--white); font-family: var(--font-head); font-size: 0.8rem; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; padding: 0.6rem 1rem; }
  .ba-label.after { background: var(--accent); color: var(--black); }
  .ba-image { background: var(--gray-light); overflow: hidden; }
  .ba-image img { width: 100%; height: 100%; object-fit: cover; display: block; }
  .ba-stats { padding: 0.75rem 1rem; border-top: 1px solid var(--gray-mid); display: flex; gap: 1.5rem; }
  .ba-stat { font-size: 0.78rem; color: var(--gray); }
  .ba-stat strong { color: var(--black); font-weight: 600; display: block; font-size: 0.9rem; }

  /* CHARTS */
  .chart-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 2.5rem 0; }
  .chart-card { background: var(--gray-light); border-radius: 0.75rem; padding: 1.5rem; }
  .chart-title { font-family: var(--font-head); font-size: 1rem; font-weight: 700; color: var(--black); margin-bottom: 0.2rem; }
  .chart-subtitle { font-size: 0.78rem; color: var(--gray); margin-bottom: 1rem; font-weight: 300; }
  .chart-container { position: relative; height: 220px; }

  /* CALLOUT */
  .callout { background: var(--black); color: var(--white); border-radius: 0.75rem; padding: 1.5rem 2rem; margin: 2rem 0; display: flex; align-items: center; gap: 1.5rem; }
  .callout-icon { font-size: 2rem; flex-shrink: 0; }
  .callout-text { font-size: 0.95rem; font-weight: 300; line-height: 1.7; color: rgba(255,255,255,0.8); }
  .callout-text strong { color: var(--accent); font-weight: 600; }

  /* TABLE */
  .project-body table { width: 100%; table-layout: fixed; border-collapse: collapse; margin: 1.5rem 0; font-size: clamp(0.6rem, 1.5vw, 0.9rem); }
  .project-body th { background: var(--black); color: var(--white); padding: 0.75rem 1rem; text-align: left; font-family: var(--font-head); font-weight: 600; font-size: 0.8rem; }
  .project-body td { padding: 0.5rem; word-break: break-word; border-bottom: 1px solid var(--gray-light); color: var(--gray); }
  .project-body tr:hover td { background: var(--gray-light); }

  @media (max-width: 700px) {
    .chart-grid, .before-after { grid-template-columns: 1fr; }
    .pipeline-grid { grid-template-columns: 1fr; }
    .pipeline-connector { display: none; }
  }
</style>

## Overview

Plant research requires precise, repeatable inoculation of hundreds of plants. This is a process that is traditionally manual, time-consuming, and prone to inconsistency. For meaningful scientific results, researchers need standardized conditions across large sample sizes.

Developed at Breda University of Applied Sciences for the **Netherlands Plant Eco-phenotyping Centre (NPEC)**, this project delivers a fully autonomous end-to-end inoculation system. It handles the entire workflow: from real-time plant detection using image segmentation, to precise inoculation delivery via robotic control targeting *Arabidopsis thaliana* roots across NPEC's Hades system, which processes up to 10,000 seedlings across 2,000+ Petri dishes.

---

## System Pipeline

The full system runs autonomously from image capture to inoculation delivery.

<div class="pipeline-grid">
  <div class="pipeline-step">
    <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-capture.png" alt="Image Capture" /></div>
    <div class="step-title">01. Image Capture</div>
    <div class="step-label">Daily Time-Series Photography of Petri Dishes</div>
  </div>
  <div class="pipeline-step highlight">
    <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-segmentation.png" alt="Segmentation" /></div>
    <div class="step-title">02. Segmentation</div>
    <div class="step-label">U-Net Detects Roots</div>
  </div>
  <div class="pipeline-step highlight">
    <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-roottip.png" alt="Root Tip Detection" /></div>
    <div class="step-title">03. Root Tip Detection</div>
    <div class="step-label">Post-Processing Localises Inoculation Targets</div>
  </div>
  <div class="pipeline-step">
    <div class="step-icon"><img src="/assets/images/projects/npec-inoculation/pipeline-inoculation.gif" alt="Inoculation" /></div>
    <div class="step-title">04. Inoculation</div>
    <div class="step-label">Autonomous Delivery to Root Tips</div>
  </div>
</div>

---

## Computer Vision: Instance Segmentation

A key challenge was separating individual plant roots in dense images. Early model versions detected too many spurious instances — small noise artifacts classified as separate plants. After improving the segmentation pipeline, spurious detections were eliminated and root length measurements became significantly more accurate.

<div class="before-after">
  <div class="ba-panel">
    <div class="ba-label">Before</div>
    <div class="ba-image">
      <img src="/assets/images/projects/npec-inoculation/segmentation-before.png" alt="Before: instance segmentation with spurious detections" />
    </div>
    <div class="ba-stats">
      <div class="ba-stat"><strong>5 instances</strong>Plants detected</div>
      <div class="ba-stat"><strong>566 · 8 · 231 · 1 · 35 px</strong>Root lengths</div>
    </div>
  </div>
  <div class="ba-panel">
    <div class="ba-label after">After</div>
    <div class="ba-image">
      <img src="/assets/images/projects/npec-inoculation/segmentation-after.png" alt="After: improved instance segmentation" />
    </div>
    <div class="ba-stats">
      <div class="ba-stat"><strong>2 instances</strong>Plants detected</div>
      <div class="ba-stat"><strong>569 · 236 px</strong>Root lengths</div>
    </div>
  </div>
</div>

<div class="callout">
  <div class="callout-icon">🏆</div>
  <div class="callout-text">
    The segmentation model achieved an <strong>F1-score of 0.83</strong> after 39 training iterations, and placed <strong>12th on the Kaggle leaderboard</strong> with a root length sMAPE of 6.877 on the blind test set.
  </div>
</div>

---

## Robotic Control: PID vs Reinforcement Learning

Two controllers were designed and benchmarked for positioning the pipette over detected root tips using a PyBullet simulation of the Opentrons OT-2 robot.

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
| **PID** | **100%** | ~70 steps | 0.12 mm | 0.15 mm | 0.03 mm |
| RL | 12% | ~3 steps | 1.05 mm | 0.98 mm | 0.51 mm |

The PID controller proved highly reliable and accurate, making it the practical choice for the delivered system. The RL controller converged faster but lacked precision — pointing to future improvements with longer training runs and refined reward shaping.

---

## Outcome

The delivered system provides NPEC with a scalable, automated alternative to manual inoculation. The PID controller is accurate enough for production use, while the RL approach shows promise for future development with more training data and a refined reward function.

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
  const navy = '#2d3778';
  const gray = '#7a7f9a';
  const lgray = 'rgba(45,55,120,0.07)';

  function decay(steps, start, end, rate, noise) {
    return Array.from({length: steps}, (_, i) => {
      const base = start * Math.exp(-rate * i) + end;
      return Math.max(end * 0.8, base + (Math.random() - 0.5) * base * noise);
    });
  }

  const commonOptions = (maxY, maxTicks) => ({
    responsive: true,
    maintainAspectRatio: false,
    plugins: { legend: { labels: { font: { size: 10 }, boxWidth: 10, color: gray } } },
    scales: {
      x: {
        title: { display: true, text: 'Steps', color: gray, font: { size: 10 } },
        ticks: { maxTicksLimit: maxTicks, color: gray, font: { size: 9 } },
        grid: { color: lgray }
      },
      y: {
        title: { display: true, text: 'Mean Error (mm)', color: gray, font: { size: 10 } },
        ticks: { color: gray, font: { size: 9 } },
        grid: { color: lgray },
        min: 0, max: maxY
      }
    }
  });

  new Chart(document.getElementById('pidChart'), {
    type: 'line',
    data: {
      labels: Array.from({length: 200}, (_, i) => i),
      datasets: [
        { label: 'X-axis', data: decay(200, 70, 0.12, 0.05, 0.25), borderColor: '#e74c3c', backgroundColor: 'rgba(231,76,60,0.07)', borderWidth: 2, pointRadius: 0, tension: 0.4, fill: true },
        { label: 'Y-axis', data: decay(200, 60, 0.15, 0.055, 0.25), borderColor: navy, backgroundColor: 'rgba(45,55,120,0.05)', borderWidth: 2, pointRadius: 0, tension: 0.4, fill: true },
        { label: 'Z-axis', data: decay(200, 50, 0.03, 0.07, 0.2), borderColor: '#27ae60', backgroundColor: 'rgba(39,174,96,0.05)', borderWidth: 2, pointRadius: 0, tension: 0.4, fill: true },
        { label: '1mm threshold', data: Array(200).fill(1), borderColor: gray, borderWidth: 1.5, borderDash: [5,4], pointRadius: 0, fill: false }
      ]
    },
    options: commonOptions(75, 8)
  });

  new Chart(document.getElementById('rlChart'), {
    type: 'line',
    data: {
      labels: Array.from({length: 14}, (_, i) => i),
      datasets: [
        { label: 'X-axis', data: decay(14, 70, 1.05, 0.45, 0.5), borderColor: '#e74c3c', backgroundColor: 'rgba(231,76,60,0.07)', borderWidth: 2, pointRadius: 3, tension: 0.3, fill: true },
        { label: 'Y-axis', data: decay(14, 60, 0.98, 0.5, 0.5), borderColor: navy, backgroundColor: 'rgba(45,55,120,0.05)', borderWidth: 2, pointRadius: 3, tension: 0.3, fill: true },
        { label: 'Z-axis', data: decay(14, 50, 0.51, 0.6, 0.4), borderColor: '#27ae60', backgroundColor: 'rgba(39,174,96,0.05)', borderWidth: 2, pointRadius: 3, tension: 0.3, fill: true },
        { label: '1mm threshold', data: Array(14).fill(1), borderColor: gray, borderWidth: 1.5, borderDash: [5,4], pointRadius: 0, fill: false }
      ]
    },
    options: commonOptions(75, 7)
  });
</script>
