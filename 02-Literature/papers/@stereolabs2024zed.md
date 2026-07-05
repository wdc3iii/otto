---
type: paper
citekey: stereolabs2024zed
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Stereolabs
year: 2024
venue: Version 5.1
doi: null
arxiv: null
url: https://www.stereolabs.com/docs
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- stereolabs_zed_sdk
---

# ZED SDK

> [!info] Stereolabs · 2024 · Version 5.1

## Summary
> [!note] AI-drafted from the vendor documentation — a base to refine. This is a software SDK citation, not a research paper.
**TL;DR** — The ZED SDK is Stereolabs' spatial-perception framework for their stereo cameras, providing depth maps, point clouds, positional tracking, and spatial mapping.
**Problem** — Robotics/AR applications need reliable metric depth from passive stereo, including in low-texture and low-light scenes where classical block-matching degrades.
**Method** — Neural-network disparity estimation with selectable depth modes (NEURAL, NEURAL_PLUS, NEURAL_LIGHT) trading accuracy against latency/GPU load, with GPU-accelerated inference and Jetson support.
**Key results** — Not applicable (software release); the SDK exposes the depth/point-cloud APIs downstream pipelines consume.

## Takeaways
- Cited as the perception/depth-sensing toolchain, not for a scientific result — treat it as an infrastructure dependency.
- NEURAL depth modes are the practical default for outdoor/low-texture terrain sensing; mode choice is an accuracy-vs-compute knob.
- Version-specific behavior matters; pin the SDK version when reporting deployment results.

## Relevance to your work
Cited by [[@terrain2026consistent]] as the onboard depth/point-cloud source that feeds terrain estimation and elevation mapping for perceptive legged locomotion.

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `stereolabs_zed_sdk`
