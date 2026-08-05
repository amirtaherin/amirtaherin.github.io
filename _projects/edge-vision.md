---
layout: page
title: Efficient Edge Vision
description: Real-time visual perception within edge power budgets — from FPGA co-design to adaptive detector scheduling
importance: 2
category: research
related_publications: true
---

**Goal:** deliver real-time visual perception on devices where every joule counts, by
restructuring the computation — in hardware or at runtime — instead of simply shrinking
models.

#### ALBIREO — adaptive video object detection

A detector-agnostic, training-free framework that wraps off-the-shelf detectors and skips
detector invocations when a per-object Kalman state is confident enough; skipped frames
get predicted boxes at near-zero GPU cost, with a rescue mechanism preserving objects
through brief detector misses. On BDD100K MOT across three detector families and two
Jetson generations, accuracy stays within ±1.2 pp of per-frame inference while energy
drops 12.1–17.6% — and on the primary configuration accuracy *improves* by +0.8 pp while
energy falls 17.6%. To appear at ACM/IEEE SEC 2026 {% cite taherin2026albireo %}.

#### Algorithm–architecture co-design for 360° video

Real-time 360° AR/VR video rendering restructured to fit FPGA on-chip memory budgets:
co-designing the rendering algorithm with the architecture enabled energy-efficient
processing on a Zynq UltraScale+ MPSoC without performance loss versus commercial
pipelines. Published at FPGA 2020 {% cite sun2020energy %}.
