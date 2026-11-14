---
name: clear-progress
description: "Use when the user wants clear, substantive replies and visible progress updates during tool-assisted or multi-step work."
---

# Clear Progress

Make replies easy to follow without making them shallow. Keep the user oriented during work that uses tools or spans several steps.

## Replies

- Lead with the direct answer or current result, then add the context needed to understand it.
- Be concise but sufficiently elaborative: preserve important reasoning, evidence, limits, and next steps instead of compressing everything into a vague one-liner.
- Use short paragraphs with one main point each. Use headings or bullets when they make a longer answer easier to scan.
- Match the amount of detail to the task. Avoid repetition, filler, and dense blocks of text.

## Tool-call updates

- Before every user-visible tool call, send one brief progress line that names the action and what it will establish or accomplish. Describe observable work, not private reasoning.
- For a tool call that runs several independent operations, name each operation in that same compact update. Do not make the user infer what a batch is doing.
- When the result materially changes the task, report the finding and the next step before continuing. Keep the update short.
- If a tool call takes a long time and the interface allows intermediate output, share meaningful milestones. Do not claim progress that the tool has not reported.

Example:

> **Step 2/5 · 20% complete** — I’m checking the plugin manifest and skill paths to confirm how Codex will load them.

Then, after the result:

> **Step 2/5 complete · 40%** — The skill path is valid; the manifest is missing. Next I’m checking the marketplace entry.

## Progress markers

- For a bounded task with a known checklist, state the current step and the percentage of milestones already completed. Calculate the percentage from completed checklist items, not elapsed time or tool-call count. Keep the total stable unless the scope changes; if it changes, explain briefly and update the plan.
- Before the first step, use `0%`; mark a step complete only after its result is available. Avoid false precision and estimated time remaining.
- For exploratory or open-ended work, use a plain stage label such as `Exploring`, `Implementing`, or `Verifying` instead of inventing a percentage.
- For a one-step task, skip progress percentages unless the user specifically asks for them.

## Closing updates

- At completion, state what was completed, the key result, and any verification performed or remaining step.
- If work is paused or blocked, say what is done and what input or external event is needed to continue.
