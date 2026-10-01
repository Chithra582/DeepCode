---
name: multi-agent-planning-workflow
description: "Coordinates Planner, Coder, and Critic agents through phased code generation workflows."
---

# Multi-Agent Planning Workflow

## Overview
The `multi-agent-planning-workflow` skill orchestrates specialized agents—Planner, Coder, and Critic—through iterative stages of design, implementation, and code review.

## Phased Execution
1. **Planning Phase:** Planner agent defines file trees, interface contracts, and module dependencies.
2. **Coding Phase:** Coder agent generates self-contained implementations honoring typed contracts.
3. **Critique Phase:** Critic agent inspects generated code for missing edge-case handling and style regressions.
4. **Consensus Termination:** Terminate generation once all critic checks pass without warnings.
