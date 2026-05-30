---
name: data-visual-storytelling
description: Turn data, metrics, charts, and quantitative comparisons into animated video sequences that feel cinematic and clear instead of slide-based.
---

# Data Visual Storytelling

Use this skill when the video depends on charts, metrics, dashboards, timelines, maps, graphs, or other quantitative visuals.

## Outcome

Produce a data-visual plan that covers:

- What data matters
- What the viewer should understand
- Best chart or diagram forms
- Animation strategy
- Scene sequencing
- Labels, callouts, and emphasis

## Workflow

1. Read `director.project.md` first.
2. Identify the data story, not just the dataset.
3. Choose visual forms that fit the message.
4. Prefer animated progression over static chart screenshots.
5. Look for HyperFrames catalog items or external libraries when useful.
6. Specify how values change over time: count-up, proportional fill, path draw, morph, camera move, comparison reveal, or state transition.
7. Save the chosen plan back into `director.project.md`.

## Guidance

- Avoid “dashboard as slide” output.
- Emphasize change, comparison, sequence, and insight.
- Let animation reveal the story progressively.
- Route to HyperFrames specialists for implementation once the visual logic is chosen.
- Do not use generic cards plus numbers as the whole visualization. Pair every number with a moving visual form that makes the quantity tangible.
- Prefer SVG, Canvas, CSS shapes, or a catalog visualization block over static chart screenshots.
- If the data story includes formulas, statistical notation, equations, or derivations, route through `skills/hyperframes/hyperframes/references/math-rendering.md` and render math with KaTeX/SVG/Canvas/Three.js rather than plain text.
