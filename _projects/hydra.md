---
layout: page
title: Hydra
description: Phase-aware characterization of LLM inference across three generations of edge SoCs
importance: 1
category: research
related_publications: true
---

Deploying a language model on an edge SoC means choosing a platform, an inference backend,
and a quantization level — and the consequences of those choices are entangled. Aggregate
metrics like tokens per second hide where time and energy actually go.

Hydra is a common-schema, phase-aware characterization framework: it instruments
HuggingFace Transformers and llama.cpp with a shared per-prompt timing schema, fuses those
records with hardware telemetry, and attributes latency, power, energy, and memory
behavior to the prefill and decode phases of inference. Using Hydra we characterized 13
instruction-tuned LLMs (1B–8B) across five execution formats on three consecutive NVIDIA
Jetson generations — AGX Xavier, AGX Orin, and AGX Thor — producing a corpus of roughly
107K per-prompt records that will be released with the tool.

Key findings:

- A backend can win end-to-end while being slower per token: runtime structure
  (orchestration, de-tokenization) shifts where latency is introduced.
- Quantization reduces memory traffic and energy, but bit-width does not predict power —
  Q6_K can draw more power than Q8_0.
- Identical utilization readings mean different things across SoC generations because of
  DVFS behavior.
- Deployability can be limited by allocator behavior rather than nominal memory capacity.

The paper will appear at IISWC 2026 {% cite taherin2026hydra %}.
