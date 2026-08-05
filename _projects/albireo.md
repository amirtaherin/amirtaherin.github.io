---
layout: page
title: ALBIREO
description: Detector-agnostic, training-free adaptive inference for video object detection on edge GPUs
importance: 2
category: research
related_publications: true
---

Video object detection on the edge runs an expensive detector on every frame, even when
consecutive frames are nearly identical — yet naive frame skipping is content-blind and
fails exactly when it matters: object entry, occlusion recovery, abrupt motion.

ALBIREO lets uncertainty decide. It wraps off-the-shelf detectors, tracks each object with
a 10-dimensional Kalman filter, and invokes the real detector only when prediction
uncertainty exceeds a threshold; skipped frames get predicted boxes at near-zero GPU cost.
A rescue mechanism preserves confirmed objects through brief detector misses, and an
empty-scene screen avoids detector calls on objectless frames. No detector modification or
retraining is required.

Evaluated on BDD100K MOT across three architecturally distinct detectors (YOLO11x,
YOLO26x, RF-DETR-Large) and two Jetson platforms (AGX Thor, AGX Orin):

- AP@50 stays within ±1.2 pp of per-frame inference while total energy drops 12.1–17.6%.
- On the primary YOLO26x configuration, AP@50 *improves* by +0.8 pp while energy falls
  17.6% (Thor), with per-frame energy-delay product reduced by ~25%.
- A fixed-interval skipping baseline with the same skip budget loses 8.6 pp AP@50.

The paper will appear at ACM/IEEE SEC 2026 {% cite taherin2026albireo %}.
