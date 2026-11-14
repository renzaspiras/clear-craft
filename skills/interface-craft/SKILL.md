---
name: interface-craft
description: Use when building or changing a user interface, frontend page, component, or responsive layout and the rendered visual result matters.
---

# Interface Craft

Create interfaces that feel intentional, fit their product, and work at the sizes and states people actually use. Treat the rendered browser UI as the deliverable: code review alone cannot establish visual quality.

## Before implementation

- Identify the user's main task, the page's information hierarchy, and the primary action. Keep the composition focused on those needs.
- Inspect the existing product, design tokens, components, and neighboring screens. Reuse established patterns when they are coherent; do not mistake reuse for a reason to skip design judgment.
- Set a specific visual direction that fits the product: density, typography, color, spacing, and layout. Use relevant references when the direction is unclear or the domain is unfamiliar.
- Choose the structure for the use case: top bar, sidebar, split pane, table, dashboard, editor, form, or other pattern as appropriate. Use Flexbox for one-dimensional alignment and Grid for two-dimensional relationships; let rows wrap or reflow when space is constrained.

## Avoid generic or AI-slop results

- Do not reach automatically for the same centered hero, gradient wash, oversized rounded cards, repeated KPI tiles, decorative blobs, or uniform card grid. Use these only when they serve this product and task.
- Give the page a clear hierarchy and a few deliberate visual decisions. Prefer useful real content, realistic labels and data, meaningful empty/loading/error states, and restrained decoration over placeholder copy and surface effects.
- Avoid arbitrary iconography, excessive badges, inconsistent spacing, low-contrast text, tiny controls, and unexplained color. Make actions and status legible without relying on color alone.
- Do not redesign unrelated screens or replace a coherent design system just to make the result look novel. Make the smallest intentional changes that fulfill the brief.

## Required browser and visual review

For any task that creates or changes rendered UI, use Playwright to inspect the running result before reporting completion. A source diff, successful build, static mockup, or single screenshot supplied by someone else does not substitute for this review.

1. Start the app using the repository's documented development command and confirm the page is reachable. Read the available `playwright` skill before using its CLI when that skill is installed; otherwise use the repo's existing Playwright setup or an available Playwright browser tool.
2. Open the changed route in a real browser. Inspect the rendered page and capture a screenshot. Use the screenshot to check hierarchy, alignment, spacing, typography, contrast, clipping, and whether the result looks like this product rather than a generic template.
3. Check a wide desktop viewport and a narrow phone viewport. Also check an intermediate width when the layout has a meaningful tablet or collapsed-navigation transition. Resize the browser; do not infer responsiveness from CSS alone.
4. Exercise the main changed interaction in the browser: for example navigation, opening a menu or dialog, submitting a form, filtering/sorting, or selecting an item. Check focus and keyboard operation for changed interactive controls where applicable.
5. Fix visible defects and repeat the relevant browser checks. Check the browser console or app output for errors caused by the changed UI when available.
6. Report what viewports and interaction you inspected. Link or name screenshots when captured. State clearly if Playwright could not run, why, and what remains visually unverified; never say the UI was visually verified when you did not see it rendered.

Prefer the project's existing Playwright workflow. When the `playwright` skill is available, use its documented CLI workflow rather than adding a new test framework just for a visual check. If the app cannot start or Playwright is unavailable, make reasonable setup/diagnostic attempts, then state the blocker and limit the completion claim. Do not silently downgrade to code-only review.

## Final quality pass

Confirm that:

- The main task and primary action are obvious without competing decoration.
- Navigation and content structure fit the use case; sidebars, toolbars, rows, and panels collapse or move appropriately.
- The page remains readable and usable at checked sizes, with no accidental horizontal overflow or clipped key actions.
- Loading, empty, error, and success states touched by the change are coherent.
- The visual review reflects the actual running UI, not a guess from source code.
