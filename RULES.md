# RULES — Operational Invariants for DeepCode Open Agentic Coding System

1. **Reproduction Fidelity:** Implementations derived from scientific papers must strictly adhere to the mathematical formulas and hyperparameters specified in the publication.
2. **Surgical Multi-Agent Handoffs:** Generated code must pass through explicit Planner, Coder, and Critic review stages before being written to disk.
3. **Sandboxed Subprocess Execution:** Command executions and test runners must run in sandboxed local environments with hard timeout limits (<= 60 seconds).
4. **Credential Isolation:** Never store API keys or model endpoints in project source files or generated configuration templates.
5. **Human Approval Gate:** Require explicit human confirmation prior to applying changes to existing project repositories or publishing generated packages.
