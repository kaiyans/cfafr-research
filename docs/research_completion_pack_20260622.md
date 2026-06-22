# CF-AFR research completion pack 2026-06-22

This document summarizes the local completion pack `CF-AFR_research_completion_pack_20260622.zip` and maps it to the GitHub issue workflow.

## Most important repository truth

The completion pack warns that the reviewed 2026-06-17 bundle may not contain a persistent `ActiveSetHotStartState` class or persistent Cholesky/factor cache in `attachments/04_code/cfsr_active_set_kernel.py`.

Therefore, before claiming persistent solver-state or numerical factor reuse, complete:

- #26 Repository truth audit and hot-start state instrumentation

Until #26 is complete, the safest manuscript wording is:

> CF-AFR transfers primal, support, and active-face information across mesh refinement to initialize the fine-mesh working set. Same-final-mesh factorized face-solve diagnostics support backend readiness, but persistent numerical factor reuse must be established separately by implementation-level cache-hit and validity measurements.

## Execution order

1. #26 Repository truth and state instrumentation
2. #16 State decomposition ablation
3. #17 Confidence-aware add/release policy
4. #18 Dual/costate transfer + fine KKT repair design
5. #19 Genuine active-set solver integration
6. #20 Production sparse backend evaluation
7. #21 Symbolic factorization reuse
8. #22 Interval-local factor reuse
9. #23 Mesh-asymptotic active-face consistency
10. #24 Confidence calibration theory
11. #25 General nonconvex SQP extension

## Experiment registry

| ID | Experiment | Priority | Dependency | Role |
| --- | --- | --- | --- | --- |
| E0 | Repository truth and state instrumentation | P0 | none | required |
| E1 | State decomposition ablation | P0 | E0 | required |
| E2 | Confidence-aware add/release | P0/P1 | E0 | next-paper/core |
| E3 | Primal-dual/costate transfer | P1 | E0 | next-paper/core |
| E4 | DAQP/qpOASES active-set integration | P1 | E1 | strong if available |
| E5 | Sparse production backend pilot | P1/P2 | E1 | journal bridge |
| E6 | Symbolic and interval-local factor reuse | P2 | E5 | journal |
| E7 | Mesh-asymptotic face consistency | P1/P2 | none | theory support |
| E8 | Residual-to-score certificate | P1 | none | paper/next-paper |
| E9 | Full integration and manuscript validation | P0 | E0-E8 outputs | required last |

## Claim gates

- Do not call residual-aware diagnostics certified screening unless a valid score-error radius is used.
- Do not call cross-mesh warm start full solver-state hot start unless dual/basis/factor state transfer is actually implemented and validated.
- Do not claim production sparse speedup from structural KKT footprint alone.
- Do not present readiness diagnostics as persistent factor reuse.
- Keep OFF-fixed reduction separate from working-set initialization ablations because it can change the mathematical problem.

## Source files in local Obsidian vault

The full pack is stored locally under:

`00_SecondBrain/研究/Projects/CFSR/GPTPro添付/CF-AFR_research_completion_pack_20260622/`

The Obsidian summary note is:

`CF-AFR 研究完成パック統合まとめ 2026-06-22`
