---
name: ki-control
description: Use when choosing among Luna, Terra, Sol, and Astra, deciding whether to delegate to a subagent, or trying to improve model quality without overusing stronger models.
---

# KI Control

Route work to the least costly model that can meet the task's quality bar. Begin with the use-case heatmap, then adjust for uncertainty, stakes, visual or computer-use needs, and evidence from the current task. A heatmap score is guidance, not an automatic model switch.

## Use-case fit heatmap

These 0–100 scores are **initial routing heuristics**, not measured accuracy, probability of success, or a share of workload. A row is independent; scores do not add to 100. They summarize the models' published positioning and must be replaced or adjusted when representative task evaluations provide better evidence.

| Use case | Luna | Terra | Sol | Astra | Starting route |
|---|---:|---:|---:|---:|---|
| Clear extraction, formatting, short rewrite, or narrowly specified edit | 95% | 78% | 76% | 72% | Luna |
| Visual interpretation, screenshot/UI review, or defined computer-use workflow | 70% | 96% | 81% | 88% | Terra |
| Everyday coding, research, or multi-step writing with a clear goal | 78% | 82% | 92% | 95% | Sol when Luna's task scope or quality bar is insufficient; otherwise Luna |
| Ambiguous, multi-source, or technically complex work with competing evidence | 50% | 66% | 90% | 97% | Sol; Astra if the stakes, ambiguity, or quality requirement warrants it |
| High-stakes or unusually exacting analysis requiring broad judgment | 40% | 60% | 85% | 98% | Astra when verification and lower-cost routing cannot meet the required bar |

**Why these routes:** OpenAI describes Luna as efficient for focused, high-volume work; Terra as suited to visual reasoning and precise computer use; Sol as near-Astra capability for complex work at lower cost; and Astra as the most capable option for the most demanding work. The percentages above are this skill's provisional rubric, not claims made or benchmarked by OpenAI. See [model selection](https://developers.openai.com/api/docs/guides/model-selection), the [model catalog](https://developers.openai.com/api/docs/models), and [GPT-6 guidance](https://developers.openai.com/api/docs/guides/latest-model).

## Routing procedure

1. **Classify the work.** Identify the task type, ambiguity, stakes, visual/computer-use requirements, acceptance criteria, and whether it can be split into independent workstreams.
2. **Pick the least costly sufficient model.** Use Luna for clear, bounded work. Route directly to Terra when visual interpretation or a computer-use workflow is central. Route to Sol for sustained reasoning, complex coding, or multi-source synthesis. Reserve Astra for genuinely demanding, ambiguous, high-stakes, or exacting tasks when the quality gain matters.
3. **Do not escalate on vague signals.** “Quality matters,” a long prompt, or the fact that a stronger model exists is not enough on its own. A small, well-specified edit stays with Luna when Luna can meet the stated criteria.
4. **Escalate on evidence.** If the current route reaches a concrete blocker, cannot resolve a decision that changes the outcome, or fails an appropriate verification after a diagnosed repair, isolate the unresolved part. Research or inspect the evidence first when that can answer it; then route only the gap to the next least costly capable model. Do not repeat the same failed approach or restart the whole task at Astra by default.
5. **Use subagents selectively.** Delegate when work can be split into independent research, review, or implementation tasks and parallel work can materially improve speed or quality. Give each agent a narrow question, relevant context, expected output, and model suited to that subtask. Use one or two agents by default; do not create agents just to make a simple task feel safer, and avoid parallel edits to the same files.
6. **Synthesize and verify.** The root agent owns the final answer and result. Compare delegated findings, resolve disagreements with evidence, and verify important claims or code changes before reporting completion.

## Model and tool limits

- This skill cannot change the model running the current conversation. Use a model selector or a model override on a subagent only when the host exposes it and current instructions allow it.
- Before selecting a subagent model, use the exact model IDs exposed by the current runtime. The current GPT-6 family IDs documented for these names are `gpt-6-luna`, `gpt-6.1-terra`, `gpt-6.1-sol`, and `gpt-6-astra`; availability can differ by host and change over time.
- Current user, developer, repository, and safety instructions govern whether delegation is allowed. This skill never overrides them. If model selection or subagents are unavailable, continue with available tools and report the limitation without claiming an upgrade occurred.
- Avoid model escalation for dependent steps that must run sequentially. Delegation does not replace research, tests, visual inspection, or other evidence the task requires.

## Calibrate the heatmap

Treat scores as a starting hypothesis. For recurring work, compare models on the same representative inputs and acceptance criteria. Record task success, errors, review/repair time, latency, and cost; update scores only when the evidence supports a change. Keep the original provisional values labeled until they have been evaluated. OpenAI recommends experimenting with representative tasks and choosing the lightest setting that meets the quality bar.
