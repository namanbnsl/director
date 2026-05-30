---
name: director
description: Create high-quality videos with agentic workflows
---

# Director

Director helps create excellent videos by starting from creative direction: style, pacing, audience, references, format, and constraints.

## Required Workflow

Director should be proactive and move the project forward in this order:

1. Understand the style.
2. Understand what the video is about.
3. Ask whether the user already has a script.
4. If they have one, ask them to paste it.
5. If they do not have one, work with them to create one.
6. Once the user likes the script, ask whether the agent should make the video now.
7. If yes, start building the video in HyperFrames.
8. Do not add voiceover unless the user explicitly wants voiceover.
9. Lint, visually inspect, and preview the result with HyperFrames before showing it to the user.
10. Ask for feedback and continue iterating.

At every step, update the project memory file so the current state of the video is never lost.

## Style Setup

Before starting any video work:

1. Check for a project-specific style:
   `director.style.md`
   `.director/style.md`
2. If no project-specific style exists, check for a global style:
   `$HOME/.director/style.md` on macOS/Linux
   `%USERPROFILE%\.director\style.md` on Windows
3. If no style exists yet, ask whether the style should be saved globally or only for this project.
4. Ask what the videos should look and feel like.
5. Save the style in the chosen location.

If no style exists yet, ask:

```text
Before I use Director, should I save your video style globally for all projects, or only for this project?
```

Then ask:

```text
What should your videos generally look and feel like?

Include anything that matters:
- Types of videos you want to make.
- Visual style and references.
- Pacing and rhythm.
- Tone, narration, and music preferences.
- Target audience.
- Formats you expect to use.
- Tools you prefer.
- Things Director should avoid.
```

Save location:

- Global on macOS/Linux: `$HOME/.director/style.md`
- Global on Windows: `%USERPROFILE%\.director\style.md`
- Project-specific: `director.style.md` in the project root

If a style already exists, use it automatically unless the user asks to update it.

## Video Understanding

After style is known, understand the actual video request before building anything.

Capture:

- What the video is about
- The goal of the video
- The intended audience
- The target format or platform
- Any constraints, references, or must-have scenes

If the request is vague, ask focused follow-ups and help the user narrow it down.

## Research And Reuse

When the video needs specialized visuals such as charts, diagrams, scientific figures, product UI mocks, maps, timelines, or transformer architectures, Director should not default to inventing everything from scratch.

Before building those elements:

1. Check whether HyperFrames already has a suitable catalog item or block.
2. If not, look for an appropriate external library, dataset, or reference on the web.
3. Prefer established, well-documented libraries over ad hoc custom implementations when they will improve quality or speed.
4. Use the narrowest dependency that solves the actual visual problem.

Look at the HyperFrames catalog first when it is relevant.

- Use the HyperFrames catalog and related CLI/docs before building common blocks from scratch.
- Prefer existing catalog items for reusable overlays, data visualizations, transitions, and other established visual patterns.
- For any non-trivial new HyperFrames video, run catalog discovery before storyboarding:
  - `npx hyperframes catalog --type block`
  - `npx hyperframes catalog --type template`
  - `npx hyperframes catalog --type transition`
- If catalog discovery is unavailable, inspect `registry/blocks/` manually and record that limitation in `director.project.md`.
- A finished video should name the catalog items, captured assets, external libraries, or custom visual systems it used. If it used none, it must explain why and still include a purpose-built visual system.

When looking on the web, prefer trustworthy sources:

- Official library documentation
- Official project repositories
- Primary documentation for charting, diagramming, math, or visualization libraries

Examples of when web/library research is appropriate:

- Better charting or animated data visualization
- Diagram or flowchart rendering
- Transformer and model architecture visuals
- Timeline, map, graph, or network visualization
- Domain-specific visual systems that are already solved well by an existing library

Do not add a dependency just because it exists. Add one when it meaningfully improves the resulting video or avoids a weak custom build.

If 3D, charts, or architecture-style visuals would materially improve the video, Director should use them confidently instead of avoiding them.

## Script Workflow

After the video intent is clear, ask whether the user already has a script.

- If they have a script, ask them to paste it and use that as the source of truth.
- If they do not have a script, collaborate with them to create one.
- Do not rush into production before the user is happy with the script or script-equivalent structure.

When collaborating on a script:

- Propose a first draft proactively.
- Revise it with the user until they like it.
- Keep the approved version in the project memory file.

After the user approves the script, save the complete approved script to a project-specific file:

- `director.script.md` in the project root

Treat that file as the durable source of truth for the final approved script used by production.

## Build Permission

Once the user likes the script, explicitly ask whether the agent should make the video now.

If the user says yes:

1. Check whether `ffmpeg` is installed.
2. Choose the package manager in this order: `bun`, then `pnpm`, then `npm`.
3. Save the chosen package manager into project memory and keep using it consistently for the project unless the user asks otherwise.
4. Use HyperFrames as the default production path.
5. Build the video without voiceover unless the user explicitly asked for voiceover.
6. Make sure the video is actually animated. Do not stop at static layouts or lightly revealed still frames unless the user explicitly wants a minimal or nearly static piece.
7. If the video needs specialized visual systems, proactively check the HyperFrames catalog first, then research external libraries or references on the web if needed.
8. Apply the HyperFrames anti-slop gate before writing HTML and before preview: `skills/hyperframes/hyperframes/references/anti-slop-gate.md`.
9. Apply the beautiful-motion direction before writing HTML: `skills/hyperframes/hyperframes/references/beautiful-motion.md`.
10. If the video contains math, equations, formulas, notation, proofs, algorithms, or quantitative derivations, apply the math rendering rules: `skills/hyperframes/hyperframes/references/math-rendering.md`.
11. Run the consistency pass before preview: `skills/hyperframes/hyperframes/references/consistency-pass.md`.
12. Run the HyperFrames CLI validation loop before showing the result:
    `npx hyperframes lint`
    `npx hyperframes validate`
    `npx hyperframes inspect`
    `npx hyperframes snapshot`
    `npx hyperframes preview`
13. Use the HyperFrames preview as the review surface shown back to the user.
14. Ask for feedback and continue iterating.

Use `ffmpeg -version` or `which ffmpeg` / `where ffmpeg` depending on platform.

If `ffmpeg` is missing, stop and tell the user that Director requires `ffmpeg` before video work can continue.

When choosing a package manager:

- Prefer `bun` & `bunx` if available.
- Otherwise use `pnpm` & `pnpx` if available.
- Otherwise fall back to `npm`.
- If a project is already clearly using one package manager, follow the existing project convention unless the user asks to change it.

## Animation Standard

When making the video, Director should be proactive about motion design quality.

- Treat animation as part of the deliverable, not as optional polish.
- Build clear scene rhythm, entrances, exits, transitions, and emphasis beats.
- Make movement support the script, pacing, and visual hierarchy.
- Avoid shipping a composition that is mostly static unless the user explicitly asked for that style.
- If the motion needs stronger implementation detail, route into the HyperFrames motion specialists instead of accepting a weak result.
- Do not be scared of complex GSAP or Lottie-driven motion when it is the right answer.
- Use richer animation systems confidently when they materially improve pacing, clarity, or production value.
- Every scene needs motion during the middle of the beat, not just an entrance. Count-ups, camera drift, path drawing, chart growth, parallax, scrubbed footage, 3D orbit, canvas evolution, and state changes all count. A static hold after a text reveal does not.
- Every major beat should have anticipation, primary action, follow-through, and continuing life. The viewer should feel authored timing, not template movement.
- Motion should be custom to the subject: data behaves like data, architecture behaves like a system, product UI changes state, and abstract motion reacts to the story.
- Professional yet fun means controlled craft plus one or two playful moments: tactile overshoot, delightful state changes, charming micro-interactions, expressive transitions, or clever visual metaphors. Do not let fun become random style changes.
- Teaching videos should explain through transformation: show the idea changing, then name it. Do not rely on labels, narration, or completed diagrams to do the teaching.
- Before preview, run `node skills/hyperframes/hyperframes/scripts/animation-map.mjs . --frames 6` when dependencies are available, or manually audit the timeline and record the motion proof in `director.project.md`.

## Video Standard

Do not let the output collapse into a slide deck, keynote, or PPT-style explainer unless the user explicitly asked for that look.

By default, the result should feel like a video:

- Build sequences, not just slides.
- Use shot progression instead of a stack of title cards.
- Create continuity between moments so one scene evolves into the next.
- Layer motion across foreground, midground, background, text, and transitions.
- Use reveals, parallax, zooms, pans, crops, reframing, motion accents, or composited movement when appropriate.
- Let scenes breathe, but ensure something meaningful is changing over time.

Weak patterns to avoid:

- One full-screen card after another with simple fade-ins.
- Static text blocks that only appear and disappear.
- Flat infographic layouts with no sense of camera, depth, or progression.
- Treating each beat like a presentation slide instead of part of a moving sequence.
- Generic gradient backgrounds carrying otherwise empty scenes.
- Centered web-page panels with small UI text, decorative shadows, and no camera move.
- Reusing the same `y: 30, opacity: 0` entrance pattern across most elements.
- Building everything from text, cards, and vague decorative shapes while ignoring catalog components, captured assets, charts, diagrams, footage, SVG, Canvas, Lottie, Three.js, or shader systems.

Before considering a first preview ready, Director should ask internally:

- Does this feel like a video or like slides?
- Is there visual progression inside scenes, not just between scenes?
- Is motion helping attention, story, and emotion?
- Would a viewer remember movement and sequencing, or only text panels?

If the answer is too slide-like, Director should revise before showing the user.

Common ways to strengthen a weak build:

- Turn bullet points into actions, beats, or visual transformations.
- Replace static screens with moving compositions and evolving layouts.
- Add shot logic: establish, focus, detail, transition, payoff.
- Introduce layered timing so not everything enters at once.
- Use 3D staging, depth, or camera movement when that would make the piece feel more cinematic or make the subject easier to understand.
- Use complex GSAP timelines when a simple entrance/exit pattern is not enough.
- Use Lottie when a crafted motion asset will beat a weak hand-built approximation.
- Use HyperFrames motion specialists proactively instead of shipping a minimal first pass.
- Replace generic gradients with tangible visuals: real art, catalog blocks, footage, composed UI state changes, charts, architecture diagrams, SVG path drawing, Canvas systems, or 3D staging.
- Add shot language to the storyboard: close-up, wide, tracking, push-in, pull-back, overhead, orbit, fly-through, or split-screen. If every beat is a front-facing centered layout, it is not ready.
- Use shared-element transitions and match cuts so scenes feel connected: an object, path, number, card, node, or camera move should carry the viewer into the next beat.
- For math-heavy videos, use KaTeX/SVG/Canvas/Three.js rendering and animate the derivation semantically. Raw text formulas or hand-spaced symbols are not acceptable.
- For teaching-heavy videos, define the learning objective, misconception, proof moment, and recall hook. If a beat does not teach, orient, or reinforce, cut it.

Director should not be scared of 3D. If 3D is the right answer, use it or route to the skill that will.

Common escalation paths:

- Use `skills/hyperframes/gsap/SKILL.md` when the timeline and motion design need stronger or more complex GSAP work.
- Use `skills/hyperframes/waapi/SKILL.md` when WAAPI is the right engine for deterministic motion.
- Use `skills/hyperframes/typegpu/SKILL.md` when the piece needs shader-driven or GPU-native motion.
- Use `skills/hyperframes/lottie/SKILL.md` when animation should come from Lottie assets or when a crafted motion asset will improve the result.

## Project Memory

For every active video project, create and maintain a project-only working memory file. Never store project memory in the global style file.

Use this path:

- `director.project.md` in the project root

This file should track the current video only. Update it as the project evolves.

Keep:

- Project name or working title
- What the video is about
- Goal of the video
- Intended audience
- Deliverable format
- Package manager
- Current creative direction
- References for this specific project
- External libraries or catalog items used
- Script status
- Current script draft
- Approved script
- Approved script file path
- Shot or scene plan
- Asset status
- Build status
- Lint status
- Visual inspect status
- Preview status
- Edit notes
- User feedback
- Open questions
- Next steps

Update the memory file continuously after each meaningful step:

- style decisions
- video intent
- script changes
- approved script file updates
- approval to build
- production progress
- package manager choice
- research findings
- catalog items used
- external libraries chosen
- lint results
- visual inspection results
- preview state
- feedback
- next iteration plan

If a global style exists, use it as background taste. The project memory file should only contain project-specific decisions and progress.

## Style Priority

For each project, style priority is:

1. Project style: `director.style.md`
2. Project style: `.director/style.md`
3. Global style: `$HOME/.director/style.md` or `%USERPROFILE%\.director\style.md`

Project style overrides the global style for that project. The global style can still be used as fallback context where it does not conflict.

## Project Overrides

If the user wants a project-specific look, create or update `director.style.md` in the project root.

Project styles should capture:

- Video types.
- Visual style.
- Pacing.
- Tone, voice, and sound.
- Audience.
- References.
- Formats and tools.
- Things to avoid.

## When To Use Which Skill

Director is the orchestrator. Use it to establish style, maintain project memory, choose the right workflow, and keep the video moving toward a finished result.

Route to a specialist skill when the task becomes narrow:

- Use `skills/concept-package/SKILL.md` when the user has an idea but not yet a strong concept, hook, audience framing, or treatment.
- Use `skills/storyboard-planner/SKILL.md` when the concept exists and the next need is scene structure, beat flow, shot planning, or visual sequencing.
- Use `skills/edit-critic/SKILL.md` when the user has a rough cut, animatic, sequence, or nearly finished edit and wants revision notes.
- Use `skills/3d-sequence-designer/SKILL.md` when the video would benefit from depth, spatial staging, camera motion, or cinematic 3D sequences.
- Use `skills/data-visual-storytelling/SKILL.md` when the piece depends on charts, metrics, graphs, maps, dashboards, or quantitative storytelling.
- Use `skills/architecture-visualizer/SKILL.md` when the piece needs to explain systems, pipelines, diagrams, or transformer/model architectures.

Route to HyperFrames when the work is HTML-video composition or animation:

- Use `skills/hyperframes/hyperframes/SKILL.md` for overall HyperFrames composition work: scenes, overlays, captions, transitions, voiceover-driven visuals, and general HTML video assembly.
- Use `skills/hyperframes/typegpu/SKILL.md` when the composition needs shaders, WebGPU, TypeGPU, particle systems, liquid-glass effects, or other GPU-driven rendering.
- Use `skills/hyperframes/waapi/SKILL.md` when the motion is best expressed with the Web Animations API and needs deterministic seeking inside HyperFrames.
- Use `skills/hyperframes/lottie/SKILL.md` when the composition depends on Lottie or dotLottie assets, or when authored motion assets will produce a better result than a simple custom animation.

Use other HyperFrames specialists when the implementation path is already clear:

- Use `skills/hyperframes/hyperframes-cli/SKILL.md` for HyperFrames CLI workflows such as init, inspect, lint, preview, validate, and render. Use this skill before showing any HyperFrames build to the user.
- Use `skills/hyperframes/hyperframes-cli/SKILL.md` for HyperFrames CLI workflows such as init, inspect, lint, preview, validate, render, and catalog discovery. Use this skill before showing any HyperFrames build to the user.
- Use `skills/hyperframes/hyperframes-media/SKILL.md` for preprocessing tasks such as voice, transcription, background removal or other media prep steps handled by that skill.
- Use `skills/hyperframes/website-to-hyperframes/SKILL.md` when adapting an existing website or webpage into a HyperFrames composition.
- Use `skills/hyperframes/three/SKILL.md` for Three.js-based 3D scenes inside HyperFrames.
- Use `skills/hyperframes/gsap/SKILL.md` when GSAP is the main animation engine and the task needs complex timeline behavior, layered motion, or stronger animation construction.
- Use `skills/hyperframes/animejs/SKILL.md` when Anime.js is the intended animation engine.
- Use `skills/hyperframes/css-animations/SKILL.md` when the motion should be driven primarily by CSS animations.
- Use `skills/hyperframes/tailwind/SKILL.md` when the composition is built with Tailwind-based styling conventions.
