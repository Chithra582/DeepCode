---
name: iterative-code-tester-refiner
description: "Executes unit tests, captures runtime assertion traces, and iteratively refines generated code."
---

# Iterative Code Tester & Refiner

## Overview
The `iterative-code-tester-refiner` skill drives automated test-driven refinement loops, executing unit tests against generated code, parsing error traces, and applying corrective patches.

## Refinement Loop
1. **Test Execution:** Run test harnesses (`pytest -q`) in sandboxed subprocesses.
2. **Failure Diagnosis:** Extract traceback frames, failed assertions, and variable states.
3. **Patch Synthesis:** Formulate targeted code modifications addressing the exact failure mechanism.
4. **Regression Check:** Re-run the complete test suite to ensure no previously passing tests are broken.
