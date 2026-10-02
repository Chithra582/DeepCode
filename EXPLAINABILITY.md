# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **DeepCode Open Agentic Coding System** (`deepcode`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** DeepCode Open Agentic Coding System (`deepcode`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Developer Tools / Agentic Coding & Research Paper Code Reproduction  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), OWASP LLM Top 10, MITRE ATLAS  

---

## How the Agent Decides

The DeepCode Open Agentic Coding System is an advanced agentic software engineering platform developed by the HKU Data Intelligence Lab. It automates the complex process of reproducing scientific research papers, authoring complex algorithmic implementations, and analyzing existing software repositories. By orchestrating collaborative multi-agent roles (Planner, Coder, Critic) alongside automated codebase relationship indexing, DeepCode bridges the gap between academic research concepts and functional, verified code.

### 1. Decision Architecture

The paper reproduction, codebase indexing, multi-agent code generation, and iterative testing pipeline operates across a deterministic, five-stage architecture:

```
Research Paper / Specification Trigger (PDF Document / Algorithmic Spec / GitHub Repo)
    │
    ▼
[Stage 1: Paper & Specification Ingestion]
    │  - Extracts mathematical formulas, hyperparameter tables, and architectural flowcharts
    │  - Resolves ambiguities through cross-referencing appendix materials
    │  - Establishes algorithmic contracts and validation test targets
    ▼
[Stage 2: Codebase Indexing & Relationship Mapping]
    │  - Scans target repositories using AST indexing to map existing utilities and data loaders
    │  - Computes affinity scores between planned modules and existing code to maximize reuse
    │  - Constructs symbol dependency graphs to prevent duplicate architecture
    ▼
[Stage 3: Multi-Agent Phased Planning & Review]
    │  - Planner structures modular file trees and sequential implementation phases
    │  - Critic audits architecture for mathematical fidelity and edge case coverage
    │  - Freezes approved plan before invoking code synthesis
    ▼
[Stage 4: Surgical Implementation & Iterative Test Refinement]
    │  - Coder writes modular components adhering to strict typing and docstrings
    │  - Executes test suites in isolated subprocess sandboxes
    │  - Iterates through corrective patch loops if assertions fail (up to 4 cycles)
    ▼
[Stage 5: Artifact Delivery & Trajectory Archival]
    │  - Generates verifiable reproduction reports and executable test suites
    │  - Scrubs private paths, API keys, and model tokens from execution traces
    │  - Dispatches validated deliverables to local workspace for developer review
    ▼
Validated Research Code Reproduction & Auditable Multi-Agent Trajectory Record
```

### 2. Decision Logic & Reproduction Scoring Formulations

DeepCode evaluates formula extraction, code reuse affinity, and reproduction fidelity using deterministic mathematical models:

1. **Codebase Module Reuse Affinity ($A_{\text{reuse}}$)**:
   $$A_{\text{reuse}} = (w_s \cdot S_{\text{ast}}) + (w_t \cdot T_{\text{type}}) + (w_n \cdot N_{\text{name}})$$
   where:
   - $S_{\text{ast}} \in [0, 1]$ represents AST signature compatibility between planned and existing functions.
   - $T_{\text{type}} \in [0, 1]$ represents tensor / type signature compatibility.
   - $N_{\text{name}} \in [0, 1]$ represents semantic naming alignment.
   - Weights: $w_s = 0.50, w_t = 0.30, w_n = 0.20$ ($\sum w_i = 1.0$).

2. **Reproduction Fidelity Score ($F_{\text{reproduce}}$)**:
   $$F_{\text{reproduce}} = \frac{1}{3} \left( M_{\text{math}} + T_{\text{pass}} + D_{\text{doc}} \right)$$
   where $M_{\text{math}}$ certifies mathematical transcription fidelity, $T_{\text{pass}}$ measures unit test passage, and $D_{\text{doc}}$ confirms code documentation completeness. Delivery requires $F_{\text{reproduce}} \ge 0.90$.

### 3. Thresholding & Refusal Decision Criteria

DeepCode Open Agentic Coding System enforces strict operational safety and integrity boundaries:
- **Refusal to Generate Unverified Formulas**: If scanned paper formulas are obscured or ambiguous, generation is refused until explicit user confirmation or LaTeX source is supplied (`ERR_AMBIGUOUS_FORMULA_BLOCKED`).
- **Refusal of Arbitrary Host Commands**: Subprocess terminal execution is restricted to certified build and test commands (`pytest`, `python`, `pip install --dry-run`); arbitrary shell execution is rejected (`ERR_ARBITRARY_EXECUTION_REFUSED`).
- **Turn Ceiling Enforcement**: Multi-agent planning and refinement turns are bounded by `max_turns: 25` to eliminate runaway exploration (`WARN_TURN_BUDGET_REACHED`).
- **Workspace Directory Confinement**: Code generation and file indexing are strictly confined to the local repository directory (`ERR_OUT_OF_BOUNDS_FILE_WRITE`).

### 4. Fallback Decision Mechanism

Continuous engineering problem-solving is maintained through multi-tier fault recovery:
- **Model Cascade Failover**: When the primary foundation model experiences latency spikes or HTTP 429 rate limits, the orchestrator cascades automatically between `claude-3-5-sonnet`, `gpt-4o`, and `gemini-2.0-flash`.
- **Hardware-Agnostic Fallback**: When paper implementations depend on specialized GPU hardware (TPUs, H100s), the agent generates modular CPU/CUDA fallback implementations.
- **Mock Dataset Generator Fallback**: If multi-gigabyte paper benchmark datasets cannot be downloaded locally, the agent generates synthetic mock data tensors for forward/backward test passes.

### 5. Human-in-the-Loop Governance

Human engineers retain complete supervisory control over the reproduction pipeline:
- **Explicit Operator Approval Gates**: Applying git commits, writing new files, or modifying existing modules requires explicit human developer sign-off.
- **Emergency Session Kill Switch**: Operators can halt agent execution loops at any point using standard `Ctrl+C` interrupt signals.
- **Inspectable Trajectory Traces**: Every Planner thought, Coder diff, and Critic evaluation is recorded in structured trajectory logs for full transparency.

---

## The Data It Uses

DeepCode operates under strict privacy, data minimization, and local workspace isolation standards.

### 1. Ingested Input Data

The agent processes only operational assets necessary to fulfill paper reproduction:
- **Research Paper Content**: PDF papers, LaTeX source files, mathematical formulas, and algorithm pseudo-code.
- **Repository Source Code**: Local Python files, model wrappers, datasets, and configuration YAML files.
- **Test Output Traces**: Compiler outputs, stack traces, and numerical assertion logs.

### 2. Configuration & Reference Data

- **Codebase Relationship Index**: AST symbol dependency graphs and function signature maps.
- **Multi-Agent Role Prompts**: Specialized system prompts for Planner, Coder, and Critic agents.
- **Algorithmic Verification Schemas**: Numerical precision tolerances (e.g., `atol=1e-5`) for mathematical tensor operations.

### 3. Base Model & Inference Lineage

- **Deterministic Algorithmic Engines**: AST parser analyzers, subprocess test runners, and symbol relationship indexers executed natively in Python (100% deterministic with zero LLM variance).
- **Foundation LLMs**: High-capability frontier models (`claude-3-5-sonnet`, `gpt-4o`, `gemini-2.0-flash`) utilized for complex formula transcription, multi-agent debate, and code authoring.
- **Zero Training on Research Repositories**: Proprietary codebases, unpublished manuscripts, and user data are never transmitted to external cloud training corpora.

### 4. Data Privacy, Storage, and Retention

- **OWASP LLM & MITRE ATLAS Hardened**: Defended against prompt injection, context leakage, and excessive authority.
- **Local-Only Working Storage**: Relationship index JSON files, generated implementations, and test traces reside exclusively on the user's filesystem.
- **Credential Scrubbing**: Environment variables, authentication tokens, and user paths are scrubbed from generation logs.
- **Zero Commercial Monetization**: Research manuscripts, generated implementations, and trajectory histories are never monetized, aggregated, or shared with third parties.

---

## Limitations

Understanding the operational boundaries and technical constraints of DeepCode is essential for effective engineering deployment.

### 1. Complex Scanned Mathematical PDFs
- **Limitation**: Heavily degraded or non-OCR scanned paper PDFs may contain distorted mathematical formulas that cannot be accurately transcribed.
- **Mitigation**: The parser flags low-confidence formula extractions and requests LaTeX source files or manual formula confirmation.

### 2. Proprietary Hardware Accelerator Dependencies
- **Limitation**: Deep learning papers relying on proprietary TPU kernels or specialized distributed clusters cannot be fully benchmarked on standard local GPUs.
- **Mitigation**: The agent generates modular hardware-agnostic fallbacks (CPU/CUDA) and isolates specialized accelerator kernels into separate modules.

### 3. External Dataset Download Bottlenecks
- **Limitation**: Datasets exceeding hundreds of gigabytes cannot be automatically downloaded or preprocessed during active agent sessions.
- **Mitigation**: The agent creates synthetic mock dataset generators to test model forward/backward passes without requiring full dataset downloads.

### 4. Multi-Model Behavior Variance
- **Limitation**: Differing LLM backends (Anthropic vs. OpenAI vs. DeepSeek) exhibit varying sensitivities to code editing instructions.
- **Mitigation**: DeepCode standardizes tool prompt interfaces and validates tool call schemas across all supported model providers.

### 5. Highly Obfuscated Legacy Codebases
- **Limitation**: Target repositories written in legacy dynamic styles without type annotations slow down AST dependency resolution.
- **Mitigation**: The indexer combines static AST analysis with runtime symbol inspection to resolve dynamic attributes.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Decision logic & reproduction scoring formulations | Section 2 | Verified |
| - Thresholding & refusal decision criteria | Section 3 | Verified |
| - Fallback decision mechanism | Section 4 | Verified |
| - Human-in-the-loop governance & oversight | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested paper content, source code & test outputs | Section 1 | Verified |
| - Configuration, relationship index & role prompts | Section 2 | Verified |
| - Base model lineage & deterministic engines | Section 3 | Verified |
| - Data privacy, retention lifecycle & MITRE/OWASP | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Complex scanned mathematical PDFs | Section 1 | Verified |
| - Proprietary hardware accelerator dependencies | Section 2 | Verified |
| - External dataset download bottlenecks | Section 3 | Verified |
| - Multi-model behavior variance | Section 4 | Verified |
| - Highly obfuscated legacy codebases | Section 5 | Verified |
