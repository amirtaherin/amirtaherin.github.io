---
layout: page
title: Robotics & Physical AI
description: Vision-language-action models from edge to cloud — and where world models take embodied intelligence next
importance: 3
category: research
related_publications: true
---

**Goal:** understand and optimize the policies that let machines act in the physical
world — across the full hardware spectrum robots actually ship with.

#### Cross-platform VLA scaling

Five representative vision-language-action models evaluated on the LIBERO benchmark from
power-constrained edge SoCs to datacenter GPUs, measuring task accuracy jointly with
latency, throughput, and peak memory. Architectural choices dominate throughput and
memory; edge devices degrade non-linearly yet well-chosen edge configurations match or
exceed older datacenter GPUs — challenging the assumption that robotic inference belongs
in the cloud. Published at GLSVLSI 2026 {% cite taherin2026crossplatform %}.

#### VOTE — efficient VLA optimization

A training framework that finetunes VLA models to emit far fewer action tokens, plus a
voting-based ensemble over action trajectories: 39× faster inference than OpenVLA with
46 Hz throughput on edge platforms, at higher success rates {% cite lin2025vote %}.

#### World models

With collaborators, a unified perspective on world models organized by the cognitive
functions each line of work innovates — memory, perception, language, reasoning,
imagining, motivation, and metacognition — identifying motivation and metacognition as
drastically under-researched and introducing epistemic world models for scientific
discovery {% cite rupprecht2026human %}. From my systems perspective: predictive models of
physical environments add sustained memory, latency, and energy pressure exactly where
they can least be afforded — the edge.
