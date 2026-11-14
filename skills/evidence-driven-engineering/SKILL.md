---
name: evidence-driven-engineering
description: Use when a task has meaningful technical uncertainty, difficult implementation or debugging, unfamiliar or changing APIs, repeated failed attempts, or external resources that must be obtained or reused.
---

# Evidence-Driven Engineering

Make difficult work tractable by turning uncertainty into evidence. Inspect the project, research the unknowns that matter, apply the smallest supported change, and verify the result with checks that match the risk.

## Workflow

1. **Frame the uncertainty.** Read applicable project instructions, inspect the relevant code and existing checks, and state what is unknown. Prefer the repository and its current dependency versions as the starting point.
2. **Research the unknown, when needed.** Check current official documentation, release notes, standards, or the upstream GitHub repository. Use broader web sources when primary sources do not answer the question. Check dates and version compatibility. Do not rely on remembered API behavior when it may have changed.
3. **Synthesize useful context.** Extract only the findings that affect the decision: expected behavior, supported versions, constraints, and alternatives. Keep source links beside claims. Put durable findings in a project note only when future work will reuse them; otherwise keep this short working context in the task.
4. **Implement the smallest supported change.** Follow nearby project patterns. For code, add or update focused tests for changed behavior where practical, then run relevant tests and project checks such as type checking, linting, builds, or integration tests. Choose checks based on what could break; do not claim a check passed unless it ran and passed.
5. **Use failures as evidence.** When a check or implementation attempt fails, read the full error, locate the failing boundary, and compare observed behavior with the expected behavior. After two unsuccessful attempts, stop repeating similar patches: form a specific hypothesis, inspect a smaller reproduction or trace, and research the unresolved point before trying a different fix. Re-run the focused check and relevant regression checks.
6. **Record external resources.** Before downloading or incorporating an external asset, dataset, code sample, model, or other reusable resource, identify its creator/source and license or terms. If included in the deliverable, create or update `ATTRIBUTION.md` with its name, author/creator, source URL, license/terms, retrieval date, and modifications. Preserve any required notices. Public availability is not permission to reuse. If terms cannot be established, do not present it as cleared for reuse; find a suitable alternative or report the limitation.
7. **Close with evidence.** Summarize the change, the checks actually run and their outcomes, relevant research sources, and remaining uncertainty. Separate verified facts from assumptions.

## Quick Reference

| Signal | Response |
|---|---|
| API, standard, or tool behavior may have changed | Verify against current primary sources and the project's version |
| First fix fails | Diagnose the failure before changing the approach |
| Two similar attempts fail | Stop patching symptoms; isolate the cause and research the unknown |
| Code behavior changes | Add/adjust a focused test where practical and run relevant regression checks |
| External resource is downloaded or reused | Check reuse terms and record provenance in `ATTRIBUTION.md` |
| Evidence is incomplete | State the gap; do not imply certainty or successful verification |

## Common Mistakes

- Searching broadly before checking the repository, project instructions, or installed versions.
- Treating search snippets, old examples, or a passing narrow test as proof of overall correctness.
- Repeating near-identical fixes without learning from the failure output.
- Downloading something because it is publicly reachable, then postponing license checks or attribution.
- Writing a long research dump instead of a compact decision-ready synthesis with sources.
- Reporting tests as successful when they were skipped, unavailable, or only partially run.
