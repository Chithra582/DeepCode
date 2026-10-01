---
name: research-paper-code-reproducer
description: "Extracts algorithmic blueprints and architectures from scientific papers to generate working implementations."
---

# Research Paper Code Reproducer

## Overview
The `research-paper-code-reproducer` skill translates academic research publications into modular, runnable software implementations. It systematically extracts mathematical equations, pseudo-code, architectural hyperparameters, and evaluation protocols from technical PDFs.

## Reproduction Pipeline
1. **Paper Decomposition:** Segment paper text into methodology, architecture, and training objectives.
2. **Formula Translation:** Map mathematical equations into vectorized PyTorch/TensorFlow tensor operations.
3. **Hyperparameter Ingestion:** Identify explicit configurations (learning rates, layer dimensions, loss schedules).
4. **Baseline Verification:** Run forward-pass assertions on mock input batches before full training.
