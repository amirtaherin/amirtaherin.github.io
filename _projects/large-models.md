---
layout: page
title: Large Models on Edge Systems
description: Measuring where LLM and RAG inference spends time and energy on edge hardware — and adapting it at runtime
importance: 1
category: research
related_publications: true
---

**Goal:** make large-model inference efficient and predictable on hardware with hard
limits on power, memory, and heat. The recurring method: characterize phase by phase,
attribute costs to where they arise, then turn what the measurements expose into runtime
adaptation — always charging the adaptation's own overhead against its savings.

#### Hydra — phase-aware LLM characterization

A common-schema characterization framework that instruments HuggingFace Transformers and
llama.cpp with a shared per-prompt timing schema and fuses it with hardware telemetry.
Applied to 13 instruction-tuned LLMs across five execution formats on three consecutive
Jetson SoC generations (Xavier, Orin, Thor), yielding a ~107K-record corpus. Aggregate
latency hides key effects: backend structure shifts where latency is introduced,
quantization cuts memory traffic and energy but does not predict power monotonically, and
utilization means different things on different SoC generations. To appear at IISWC 2026
{% cite taherin2026hydra %}.

#### RAGMark — stage-level RAG benchmarking

Joint work with Zlatan Feric: benchmark the RAG pipeline the way a systems person profiles
a program — attributing latency, GPU utilization, memory, power, and answer quality to
retrieval, reranking, compression, and generation individually. Reranking and compression
compound, cutting energy by up to 66%; small upstream context reductions cascade through
downstream cost. To appear at IISWC 2026 {% cite feric2026ragmark %}.

#### Adaptive compression for edge RAG

Once stage-level costs are measurable, context compression stops being a preprocessing
step and becomes a runtime control knob. On the Jetson AGX Thor, intermediate compression
rates cut GPU energy by up to 53.2% with negligible quality loss — but the best rate moves
with workload and system state, motivating telemetry-informed adaptive control. To appear
in the ACM AI Leadership Summit proceedings {% cite feric2026retrieved %}.
