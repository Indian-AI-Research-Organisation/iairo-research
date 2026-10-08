---
title: "Context Preservation in Long-Form Video Generation via Scene Graphs"
summary: A scene graph built from each generated chunk gives a video generator an object-level memory, so identities and relations hold up over long videos.
area: Computer Vision / Video Generation
status: active
featured: false
duration: 2026 - Present
order: 20
paper_key: context-preservation-scene-graphs
contact: anushka.pawar@iairo.ai, madhur.thareja@iairo.ai
---

 Long videos are generated chunk by chunk, and each chunk sees only a short window of what came before. Objects that leave the frame are forgotten and errors compound. After each chunk, a perception pipeline records what is in it (objects, attributes, actions, relations) as a scene graph. That graph is fed back to the generator as context for the next chunk.

## Project Motive

Autoregressive and diffusion-based video models often drift over time because they must rely on their own generated outputs during inference. That mismatch between training and generation leads to context loss, scene hallucination, and degraded temporal consistency.

## Method

- A frozen Wan2.1-T2V-1.3B video generator (Self-Forcing) reads the graph as extra tokens alongside the text prompt.
- Only the graph encoder and the adapters that connect it to the generator are trained.
- Training is two phases: first on real video chunks, then on the model's own long generations.


## Evaluation

The project will be evaluated on a small benchmark of roughly 50 examples using:

- FVD, CLIP Score, VBench Subject Consistency, MAWE, drift across chunks, and Re-identification Accuracy after Dormancy (RAD), which measures whether an object is recognised after it leaves and re-enters the frame.

## Status

The work is in progress, with the current focus on graph extraction, continuous graph translation, and conditioning strategy design for Wan 2.1.