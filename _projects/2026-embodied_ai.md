---
title: "Long-Range Embodied QA: Benchmarking and Memory-Augmented Navigation in Multi-Room VLM Agents"
summary: A procedurally generated benchmark for embodied question answering with controllable room-count horizon, paired with a KG-augmented episodic memory system showing that structured trajectory memory improves answering accuracy by up to 6.6 points on route-history questions.
area: Embodied AI / Vision-Language Models / Benchmarking
status: active
featured: true
duration: 2026 - Present
order: 11
paper_key: embodied-ai
contact: niyati.rawal@iairo.ai, shubh.garg@iairo.ai

# Media — add/remove any of the fields below as needed

# YouTube video: paste only the video ID from the URL (the part after ?v=)
# youtube_id: dQw4w9WgXcQ

# Slides: use slides_url for an embeddable link (Google Slides "Publish to web" URL)
# and/or slides_link for a direct URL to open in a new tab
# slides_url: https://docs.google.com/presentation/d/YOUR_ID/embed
# slides_link: https://docs.google.com/presentation/d/YOUR_ID

# Image gallery: list one or more images stored in assets/images/
# gallery:
#   - src: /assets/images/embodied-fig1.png
#     alt: Navigation architecture diagram
#     caption: System overview showing the perception–planning pipeline
#   - src: /assets/images/embodied-fig2.png
#     alt: Results on benchmark
#     caption: Performance on HM3D benchmark across five runs
---

This project develops NaviGraph (VROOM-TO-ROOM), a benchmark and evaluation framework for long-range embodied question answering in procedurally generated multi-room environments. Agents navigate ProcTHOR houses to locate target objects and answer visually grounded multiple-choice questions about them. The benchmark controls navigation difficulty through a room-count horizon parameter (S1–S4 strata), enabling precise attribution of model failures across navigation, perception, and question answering rather than reporting a single aggregate score. The project has since extended to training and evaluating KG-augmented memory systems that condition answering on accumulated scene graph records of the trajectory.

## Project Motive

Existing EQA benchmarks either fix navigation difficulty arbitrarily or do not measure how performance degrades as task horizon grows. This leaves a critical gap: it is unclear whether current VLM agents fail because they cannot reason, cannot perceive, or simply cannot navigate. NaviGraph addresses this by making horizon a controllable generation-time parameter and by providing a structured intervention ladder — blind baselines, frame-oracle, and oracle trajectory replay — that isolates each failure mode independently. The second phase of the project asks whether structured episodic memory built from scene graph observations can close the gap that navigation failure opens.

## Where we are

- Built a procedurally generated episode pipeline on ProcTHOR-10K with AI2-THOR, scaling to 200 test episodes and 800 questions across S1–S4 horizon strata, with instance-based success criteria and fully discrete, replayable ground-truth trajectories.
- Introduced a six-rung evaluation ladder (E0–E5) separating language leakage, navigation execution, evidence gathering, and question-answering capacity as independent failure axes.
- Found that closed-loop VLM agents achieve 0% success rate (78/90 stuck), while ground-truth trajectory replay attains SR 100% and EQA accuracy that rises from 52.5% to 63.4% as rooms increase — a 29.6-point gap at S4 isolating navigation execution as the bottleneck.
- Designed and trained a KG-augmented episodic memory system: scene graphs are constructed from trajectory observations, encoded via R-GCN, and injected into the VLM decoder via cross-attention, with a joint navigation and answer training objective.
- Text memory improves MomaGraph-R1 from 64.81% to 71.44% (+6.62pp) and Gemma-3-4B from 63.69% to 66.69% (+3.00pp) on 800 test questions; gains concentrate on route-history question families (Order, Presence-change, Rooms-visited) at +18.90pp for MomaGraph-R1.
- Evaluated a panel of six vision-language models including MomaGraph-R1, Qwen2.5-VL-7B, Qwen3-VL-4B, and LLaVA-1.6-7B, confirming the failure pattern and memory gain hold across model families.
- Accepted at NEmo 2026 (NeurIPS Workshop on Neuro-Symbolic Embodied Intelligence, December 2026, Sydney). Full paper under review at ICLR 2027.

## Status

Active. Current open threads include world-model-based plan verification for long-horizon navigation, scaling the dataset for a full public release on Hugging Face, and human validation of the benchmark question set.
