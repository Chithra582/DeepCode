# EXPLAINABILITY — DeepCode Open Agentic Coding System

> **Admissibility & Transparency Report for OpenGAP / Agent Passport**  
> *Agent Name:* DeepCode Open Agentic Coding System (`deepcode-agent`)  
> *Specification:* OpenGAP v0.1.0  
> *Domain:* Developer Tools / Agentic Coding & Research Paper Code Reproduction  

---

## 1. Overview & Operational Purpose

The **DeepCode Open Agentic Coding System** (`deepcode-agent`) is an advanced agentic software engineering platform developed by the HKU Data Intelligence Lab. It automates the complex process of reproducing scientific research papers, authoring complex algorithmic implementations, and analyzing existing software repositories. By orchestrating collaborative multi-agent roles (Planner, Coder, Critic) alongside automated codebase relationship indexing, DeepCode bridges the gap between academic research concepts and functional, verified code.

Through rigorous formula transcription, AST dependency analysis, and iterative test-driven refinement, DeepCode delivers verifiable, reproducible, and explainable software engineering workflows.

---

## 2. How the Agent Decides (Decision-Making Logic)

DeepCode Open Agentic Coding System operates across a deterministic, multi-stage decision pipeline:

```
[Stage 1: Paper & Spec Ingestion] ──> [Stage 2: Codebase Indexing & Mapping] ──> [Stage 3: Multi-Agent Phased Planning]
                                                                                                    │
                                                                                                    ▼
[Stage 6: Artifact Delivery & Git Commit] <── [Stage 5: Test Execution & Linting] <── [Stage 4: Surgical Implementation]
```

### 2.1 Ingestion & Paper Decomposition
- **Decision:** Parses research PDFs and requirements specifications, extracting mathematical formulas, model architectures, and experimental hyperparameters.
- **Rules:** If mathematical notations or hyperparameters are ambiguous, cross-reference supplementary materials or prompt the user for clarification.

### 2.2 Codebase Indexing & Symbol Resolution
- **Decision:** Scans target repositories using AST indexing tools to map existing utilities, model wrappers, and data loaders.
- **Rules:** Compute affinity scores between planned modules and existing code to maximize code reuse and prevent architectural duplication.

### 2.3 Multi-Agent Phased Planning & Review
- **Decision:** The Planner agent structures the target file tree, the Coder writes modular components, and the Critic reviews for edge cases.
- **Rules:** Do not allow code generation without prior approved architecture plans. Require critic approval before code is finalized.

### 2.4 Test Execution & Iterative Refinement
- **Decision:** Executes unit tests in isolated subprocesses, parsing error tracebacks and synthesizing targeted corrective patches.
- **Rules:** If tests fail, iterate through the test-refine loop up to 4 cycles. If failures persist, escalate with full diagnostic traces.

---

## 3. Data & Privacy

| Category | Policy / Handling |
|---|---|
| **Input Data** | In-memory evaluation of research PDFs, source code files, and user engineering instructions. |
| **Output Artifacts** | Local Python implementations, relationship index JSON files, and test execution reports. |
| **Telemetry & Logging** | Local deterministic console logging; zero telemetry transmission to external cloud services. |
| **Third-Party APIs** | Model inference routed solely through operator-configured API gateways with no secondary retention. |

DeepCode Open Agentic Coding System complies with operational security and privacy standards:
- **No Cloud Data Exfiltration:** Operates entirely within the local repository workspace without sending proprietary code or papers to unapproved servers.
- **Epistemic Isolation:** Memory structures, indexes, and intermediate files are scoped strictly to the current project directory.
- **Sanitized Model Payloads:** Sensitive credentials, local user paths, and private environment tokens are scrubbed before payload transmission.
- **Data Minimization:** Only code slices and paper sections directly relevant to the target task are ingested into active prompt context windows.

---

## 4. Known Limitations & Failure Modes

Reviewers, auditors, and users should note the following operational constraints:

1. **Complex Mathematical Scanned PDFs**
   - *Limitation:* Heavily degraded or non-OCR scanned paper PDFs may contain distorted mathematical formulas that cannot be accurately transcribed.
   - *Mitigation:* The parser flags low-confidence formula extractions and requests LaTeX source files or manual formula confirmation.

2. **Proprietary Hardware Accelerators**
   - *Limitation:* Deep learning papers relying on proprietary TPU kernels or specialized distributed hardware cannot be fully benchmarked on standard local GPUs.
   - *Mitigation:* The agent generates modular hardware-agnostic fallbacks (CPU/CUDA) and isolates specialized accelerator kernels into separate modules.

3. **External Dataset Download Bottlenecks**
   - *Limitation:* Datasets exceeding hundreds of gigabytes cannot be automatically downloaded or preprocessed during active agent sessions.
   - *Mitigation:* The agent creates synthetic mock dataset generators to test model forward/backward passes without requiring full dataset downloads.

4. **Multi-Model Behavior Variance**
   - *Limitation:* Differing LLM backends (Anthropic vs. OpenAI vs. DeepSeek) exhibit varying sensitivities to code editing instructions.
   - *Mitigation:* DeepCode standardizes tool prompt interfaces and validates tool call schemas across all supported model providers.

---

## 5. Verification, Safety & Human Oversight

The agent implements comprehensive oversight mechanisms:
- **Real-Time Human Approval Gate:** Mandatory explicit operator confirmation is required prior to applying git commits, deleting files, or running shell commands outside the project tree.
- **Emergency Session Interrupt:** Operators can abort the agent execution loop at any moment via standard `Ctrl+C` interrupt signals.
- **Step Quota Guardrails:** Multi-agent design and refinement loops enforce a default step ceiling (default: 20 turns) to prevent runaway exploration.
- **Structured Audit Logging:** Every agent thought, tool invocation, input parameter, and tool output is recorded in structured trajectory files for auditing.
