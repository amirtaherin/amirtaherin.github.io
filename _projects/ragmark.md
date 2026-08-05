---
layout: page
title: RAGMark & Adaptive Edge RAG
description: Stage-level benchmarking of retrieval-augmented generation, and compression as a runtime control knob
importance: 3
category: research
related_publications: true
---

A RAG pipeline is a chain of very different stages — retrieval, reranking, context
compression, generation — but it is usually measured as a single black box. RAGMark
(joint work with Zlatan Feric) benchmarks the pipeline the way a systems person would
profile a program: attributing latency, GPU utilization, memory, power, and answer quality
to each stage, while sweeping retrieval depths, model scales, reranking, compression, and
vector-database configurations efficiently.

Key findings:

- Autoregressive generation dominates naive pipelines, but context-reduction techniques
  shift the bottleneck across compute, memory bandwidth, and preprocessing stages.
- Reranking and compression compound: reranking shrinks the compressor's own workload, and
  together they cut prefill and KV-cache traversal costs — lowering energy by up to 66%.
- Small upstream context reductions cascade through downstream latency, memory traffic,
  and energy.

The follow-on work turns compression into a runtime control knob for edge RAG: on the
Jetson AGX Thor, intermediate compression rates reduce GPU energy by up to 53.2% with
negligible quality loss — but the best rate shifts with workload and system state,
motivating telemetry-informed adaptive control.

RAGMark will appear at IISWC 2026 {% cite feric2026ragmark %}, and the adaptive-compression
paper in the ACM AI Leadership Summit proceedings {% cite feric2026retrieved %}.
