# Anti-Slop Production Gate

Use this gate before writing a multi-scene HyperFrames video and again before showing the preview. If a composition fails this gate, revise it; do not present it as ready.

For craft direction, pair this with `beautiful-motion.md`. The anti-slop gate rejects weak work; beautiful-motion explains how to make the replacement feel authored.

## The Bar

The output must feel like directed motion, not a styled slide deck.

Reject a build when:

- Scenes are mostly centered title cards, cards, or panels with simple fades.
- A beat has one entrance sequence and then sits still.
- Gradients carry the visual identity instead of assets, components, diagrams, footage, charts, typography, or camera motion.
- The video invents generic UI instead of using the project's catalog items, captured assets, brand components, or a purpose-built visualization.
- Text and panels are scaled like a web page rather than a video frame.
- The camera never pans, pushes, reframes, tracks, zooms, or creates depth.
- Motion has no anticipation, follow-through, shared-element handoff, or subject-specific visual system.

## Pre-Build Discovery

Before writing storyboard beats or HTML, run the available local discovery commands for the project:

```bash
npx hyperframes catalog --type block
npx hyperframes catalog --type template
npx hyperframes catalog --type transition
```

If a command is unavailable in the installed HyperFrames version, record that in the project notes and inspect `registry/blocks/` manually if it exists:

```bash
find registry/blocks -maxdepth 2 -type f 2>/dev/null
```

Then decide what to use:

- Pick at least one catalog block, transition, template, or documented reusable pattern for any non-trivial video.
- For data, architecture, timelines, maps, graphs, product UI, or model diagrams, pick a visual system before writing layout CSS.
- If no catalog item fits, name the external library or custom visualization approach and explain why.

## Beat Requirements

Each beat in the storyboard must include:

- **Shot type:** extreme close-up, close-up, medium, wide, overhead, tracking shot, push-in, pull-back, orbit, fly-through, or split-screen.
- **Primary visual:** real asset, catalog component, composed UI interaction, chart/diagram, footage, 3D scene, canvas/SVG visualization, or kinetic type system.
- **Motion throughout:** at least one build motion, one mid-beat evolution, and one transition/camera handoff.
- **Depth:** foreground, midground, and background. A flat text block over a background is not enough.
- **Technique stack:** 2-4 named techniques from `references/techniques.md`, transitions catalog, catalog blocks, Three.js, Lottie, Canvas, SVG, WAAPI, or TypeGPU.
- **Gradient justification:** if using a gradient, name why it exists. Valid uses include a brand-owned asset, optical light effect, shader transition, heatmap/data encoding, or localized glow. Invalid use: making an empty frame look designed.
- **Beauty recipe:** anticipation, primary action, follow-through, and continuing life. Missing any part requires a deliberate reason.

## Gradient Rules

Gradients are not a default style.

- Do not use full-screen decorative linear gradients as the primary background unless they are a captured brand asset or a deliberate light/energy effect.
- Do not use gradient text.
- Do not stack multiple generic glows across every scene.
- Prefer solid fields with grain, photographic/video texture, SVG marks, diagram lines, grids, shapes, real product art, and component motion.
- If a gradient is necessary, keep it localized and paired with tangible content.

## Motion Proof

A ready preview needs evidence of motion, not just a clean lint result.

For each scene, confirm:

- At least 5 independently animated elements or one complex procedural/3D/canvas system plus supporting text motion.
- At least 3 easing families across the scene.
- No repeated `y: 30, opacity: 0` pattern as the dominant choreography.
- No dead hold longer than 1.5 seconds unless something meaningful is evolving: camera, count-up, path draw, scrubbed footage, chart growth, parallax, shader, or ambient object motion.
- Multi-scene videos use intentional transitions, not only fades.
- At least one transition uses a shared element, camera move, match cut, shader, or subject-specific transformation rather than a generic opacity crossfade.

Run the animation map helper when the project has the dependencies available:

```bash
node skills/hyperframes/hyperframes/scripts/animation-map.mjs . --frames 6
```

Use the report to look for long dead zones, repeated movement, collisions, missing targets, and too few mapped tweens. If the helper cannot run because dependencies are missing, do a manual timeline audit and write the finding into `director.project.md`.

## Visual Component Requirement

Every non-trivial video must include at least one of:

- a real captured or supplied asset used as a primary visual,
- a HyperFrames catalog block or template,
- a custom chart/diagram/architecture visualization,
- a Three.js, Canvas, SVG, Lottie, shader, or typed text system,
- a composed product interaction that changes state over time.

If the video contains only decorative backgrounds, text, and cards, it fails.

The visual component must be custom to the topic. A generic stat card, generic blob background, or generic browser window does not satisfy this requirement unless it has a subject-specific state change or visualization behavior.

## Final Readiness

Before showing the user a preview:

- `npx hyperframes lint` passes.
- `npx hyperframes validate` passes, including contrast.
- `npx hyperframes inspect` passes or every intentional overflow is marked.
- Catalog/components/visual systems used are recorded in `director.project.md`.
- The storyboard or notes include why the video is not a slide deck.
- The final scan contains no generic gradient-first scenes.
