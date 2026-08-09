---
layout: page
title: "Hydra — Phase-Aware LLM Inference Characterization on Edge SoCs"
permalink: /projects/hydra/
nav: false
---

Hydra is a common-schema, phase-aware workload characterization framework
for LLM inference on edge SoCs. It instruments two structurally different
inference backends — HuggingFace Transformers (Python) and llama.cpp
(C++/GGML) — with one per-prompt timing schema, fuses that timing with
high-resolution `tegrastats`/NVML telemetry, and attributes CPU, GPU,
memory, power, energy, and thermal behavior to the **prefill** and
**decode** phases of every prompt. To appear at IISWC 2026
{% cite taherin2026hydra %} — see the
[publication page](/publications/taherin2026hydra/) for the abstract and
BibTeX.

<div class="text-center">
  <img src="/assets/img/hydra_pipeline.png" alt="Hydra pipeline: profilers, telemetry fusion, canonical schema, analysis" style="max-width: 100%; margin: 1rem 0;">
</div>

## Code and dataset

Both the framework and the full measurement corpus are openly available:

- **Code** — [github.com/amirtaherin/hydra](https://github.com/amirtaherin/hydra):
  the cross-backend profilers, telemetry fusion pipeline, canonical
  cross-platform schema, and analysis pipeline, organized after the
  paper's architecture. One command
  (`bash scripts/ae_reproduce.sh`) verifies the shipped corpus and
  regenerates every data-derived figure and table of the paper on any
  Linux or macOS machine in about five minutes — no GPU required.
- **Dataset** — archived on Zenodo, DOI
  [10.5281/zenodo.21844843](https://doi.org/10.5281/zenodo.21844843):
  **107,110 per-prompt records** covering three consecutive NVIDIA Jetson
  generations (AGX Xavier, Orin, Thor), 13 instruction-tuned LLMs from
  seven families, five execution formats (`bf16`, `F16`, `Q8_0`, `Q6_K`,
  `Q4_K_M`), and input/output-length sensitivity sweeps — every telemetry
  signal phase-attributed to prefill and decode windows.

## Selected results

Aggregate latency hides where time, power, and energy actually go. Three
findings that only a phase-aware, cross-backend view exposes:

- **A backend can win end-to-end while being slower per token.** On Thor,
  HuggingFace generates a token in 33 ms but delivers it in 63.5 ms
  (CPU-side orchestration and de-tokenization); llama.cpp generates in
  58.5 ms and delivers in 58.6 ms — runtime structure, not kernel speed,
  decides responsiveness.
- **Power is not monotonic in bit-width.** `Q6_K` draws more power and
  runs hotter than `Q8_0` on every platform measured — quantization
  format is a compute/memory tradeoff, not just a footprint knob.
- **The same utilization number means different things across SoC
  generations.** An identical workload reads 27% GPU utilization on Orin
  and 86% on Thor because of DVFS policy — raw counters are not
  cross-platform comparable.

<div class="row text-center">
  <div class="col-md-6">
    <img src="/assets/img/hydra_phase_motivation.png" alt="Phase-aware latency, bandwidth, and power across three Jetson generations" style="max-width: 100%; margin: 0.5rem 0;">
  </div>
  <div class="col-md-6">
    <img src="/assets/img/hydra_q4_throughput.png" alt="Q4_K_M decode throughput across Xavier, Orin, and Thor" style="max-width: 100%; margin: 0.5rem 0;">
  </div>
</div>
