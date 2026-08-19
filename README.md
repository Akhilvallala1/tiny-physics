# Tiny-Physics

Master's thesis research (Florida Atlantic University, MS Data Science) on fine-tuning small language models to solve physics word problems on-device.

Published on ProQuest: https://digitalcommons.fau.edu/etd_general/16/

## What this is

Fine-tuned **SmolLM2-360M** and **SmolLM2-135M** with LoRA and full instruction-tuning on a synthetic, domain-specific physics dataset, then quantized and deployed the result for real-time, on-device inference.

## Results

- Built a multi-agent synthetic data generation pipeline (GPT-4o) that produced and validated **6,000+ instruction-tuned QA pairs**
- Instruction-tuned SmolLM2-360M scored **0.2451 accuracy on MMLU College Physics** (Lighteval), a **>30% improvement over the base model**
- Deployed quantized GGUF variants (Q4_K_M, Q8_0) for real-time on-device inference, with the full GGUF conversion pipeline included
- Compared LoRA vs. full instruction-tuning vs. full fine-tuning trade-offs, and contributed carbon-footprint estimates for the training runs

## Structure

| Folder | Contents |
|---|---|
| `Dataset Creation/` | Synthetic QA generation, LaTeX-to-text extraction from physics textbooks, dataset analysis |
| `Fine-Tuning-360M/`, `LoRa/` | LoRA and instruction-tuning runs for SmolLM2-360M / 135M |
| `Instruction Fine Tuned code/`, `Supervised Fine Tuning on smolLM2/` | Training scripts and notebooks |
| `Decontamination/` | Train/eval overlap checks against MMLU College Physics |
| `Evaluation/` | Lighteval benchmarking notebooks |
| `Tiny-Physics.pdf` | Full thesis writeup |

## Source data

Built from [camel-ai/physics](https://huggingface.co/datasets/camel-ai/physics) plus custom LaTeX-processed physics textbook content (`content/`, `csv/`).
