---
layout: page
title: Cross-Platform VLA Scaling
description: How vision-language-action models scale from power-constrained edge SoCs to datacenter GPUs
importance: 4
category: research
related_publications: true
---

Vision-language-action models are becoming the standard policy class for robotic control,
but robots ship with edge SoCs while most VLA benchmarking happens on datacenter GPUs.

We evaluated five representative VLA models — state-of-the-art baselines and two newly
proposed architectures — on the LIBERO benchmark across edge platforms under varying power
budgets and across datacenter GPU configurations, measuring task accuracy jointly with
latency, throughput, and peak memory.

Key findings:

- Architectural choices (action tokenization, backbone size) strongly influence throughput
  and memory footprint, independent of raw hardware capability.
- Power-constrained edge devices degrade non-linearly — yet well-chosen edge
  configurations can match or exceed older datacenter GPUs, challenging the assumption
  that robotic inference belongs in the cloud.
- High-throughput VLA variants are achievable without significant accuracy loss.

Published at GLSVLSI 2026 {% cite taherin2026crossplatform %}; the related VOTE
trajectory-ensemble optimization {% cite lin2025vote %} reaches 46 Hz throughput on edge
platforms with public code.
