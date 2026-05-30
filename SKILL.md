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

## Script Workflow

After the video intent is clear, ask whether the user already has a script.

- If they have a script, ask them to paste it and use that as the source of truth.
- If they do not have a script, collaborate with them to create one.
- Do not rush into production before the user is happy with the script or script-equivalent structure.

When collaborating on a script:

- Propose a first draft proactively.
- Revise it with the user until they like it.
- Keep the approved version in the project memory file.

## Build Permission

Once the user likes the script, explicitly ask whether the agent should make the video now.

If the user says yes:

1. Check whether `ffmpeg` is installed.
2. Use HyperFrames as the default production path.
3. Build the video without voiceover unless the user explicitly asked for voiceover.
4. Make sure the video is actually animated. Do not stop at static layouts or lightly revealed still frames unless the user explicitly wants a minimal or nearly static piece.
5. Run the HyperFrames CLI validation loop before showing the result:
   `npx hyperframes lint`
   `npx hyperframes inspect`
   `npx hyperframes preview`
6. Use the HyperFrames preview as the review surface shown back to the user.
7. Ask for feedback and continue iterating.

Use `ffmpeg -version` or `which ffmpeg` / `where ffmpeg` depending on platform.

If `ffmpeg` is missing, stop and tell the user that Director requires `ffmpeg` before video work can continue.

## Animation Standard

When making the video, Director should be proactive about motion design quality.

- Treat animation as part of the deliverable, not as optional polish.
- Build clear scene rhythm, entrances, exits, transitions, and emphasis beats.
- Make movement support the script, pacing, and visual hierarchy.
- Avoid shipping a composition that is mostly static unless the user explicitly asked for that style.
- If the motion needs stronger implementation detail, route into the HyperFrames motion specialists instead of accepting a weak result.

Common escalation paths:

- Use `skills/hyperframes/gsap/SKILL.md` when the timeline and motion design need stronger GSAP work.
- Use `skills/hyperframes/waapi/SKILL.md` when WAAPI is the right engine for deterministic motion.
- Use `skills/hyperframes/typegpu/SKILL.md` when the piece needs shader-driven or GPU-native motion.
- Use `skills/hyperframes/lottie/SKILL.md` when animation should come from Lottie assets.

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
- Current creative direction
- References for this specific project
- Script status
- Current script draft
- Approved script
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
- approval to build
- production progress
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

Route to HyperFrames when the work is HTML-video composition or animation:

- Use `skills/hyperframes/hyperframes/SKILL.md` for overall HyperFrames composition work: scenes, overlays, captions, transitions, voiceover-driven visuals, and general HTML video assembly.
- Use `skills/hyperframes/typegpu/SKILL.md` when the composition needs shaders, WebGPU, TypeGPU, particle systems, liquid-glass effects, or other GPU-driven rendering.
- Use `skills/hyperframes/waapi/SKILL.md` when the motion is best expressed with the Web Animations API and needs deterministic seeking inside HyperFrames.
- Use `skills/hyperframes/lottie/SKILL.md` when the composition depends on Lottie or dotLottie assets.

Use other HyperFrames specialists when the implementation path is already clear:

- Use `skills/hyperframes/hyperframes-cli/SKILL.md` for HyperFrames CLI workflows such as init, inspect, lint, preview, validate, and render. Use this skill before showing any HyperFrames build to the user.
- Use `skills/hyperframes/hyperframes-media/SKILL.md` for preprocessing tasks such as voice, transcription, background removal or other media prep steps handled by that skill.
- Use `skills/hyperframes/website-to-hyperframes/SKILL.md` when adapting an existing website or webpage into a HyperFrames composition.
- Use `skills/hyperframes/three/SKILL.md` for Three.js-based 3D scenes inside HyperFrames.
- Use `skills/hyperframes/gsap/SKILL.md` when GSAP is the main animation engine and the task is specifically about timeline behavior or animation construction.
- Use `skills/hyperframes/animejs/SKILL.md` when Anime.js is the intended animation engine.
- Use `skills/hyperframes/css-animations/SKILL.md` when the motion should be driven primarily by CSS animations.
- Use `skills/hyperframes/tailwind/SKILL.md` when the composition is built with Tailwind-based styling conventions.
