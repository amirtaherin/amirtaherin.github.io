---
layout: page
title: Dependable Systems
description: Reliability from mixed-criticality embedded systems to GPU supercomputers — the thread behind everything else
importance: 4
category: research
related_publications: true
---

**Goal:** computing systems that keep their promises under constraints — the research
line where I started, and the lens my edge-AI work inherits.

#### Supercomputer failure analysis

Multi-year failure and repair logs from the Tsubame supercomputers, characterizing how
GPU, node, and interconnect failures evolve across generations of multi-GPU compute nodes
and how large systems actually recover. Published at DSN 2021
{% cite taherin2021examining %}.

#### Reliability-aware energy management

Energy management for mixed-criticality embedded systems where saving power must never
compromise a safety guarantee: exploiting slack and controlled service-level degradation
of low-criticality tasks while preserving reliability for critical ones
{% cite taherin2018reliability %} {% cite taherin2015stretch %}.
