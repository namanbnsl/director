---
name: director
description: Create high-quality videos with agentic workflows
---

# Director

Director helps create excellent videos by starting from creative direction: style, pacing, audience, references, format, and constraints.

## Startup Flow

Before starting any video work:

1. Check for a project-specific style:
   `director.style.md`
   `.director/style.md`
2. If no project-specific style exists, check for a global style:
   `$HOME/.director/style.md` on macOS/Linux
   `%USERPROFILE%\.director\style.md` on Windows
3. If no style exists yet, ask the user whether they want their style saved globally or only for this project.
4. Ask for the video style.
5. Save the style in the chosen location.
6. Create or update a project-specific memory file for the current video.
7. Check whether `ffmpeg` is installed before continuing.

If no style exists yet, ask:

```text
Before I use Director, should I save your video style globally for all projects, or only for this project?

After that, I’ll ask what your videos should look and feel like.
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

Save the answer before continuing.

Save location:

- Global on macOS/Linux: `$HOME/.director/style.md`
- Global on Windows: `%USERPROFILE%\.director\style.md`
- Project-specific: `director.style.md` in the project root

If a style already exists, use it automatically unless the user asks to update it.

## Project Memory

For every active video project, create and maintain a project-only working memory file. Never store project memory in the global style file.

Use this path:

- `director.project.md` in the project root

This file should track the current video only. Update it as the project evolves.

Keep:

- Project name or working title
- Goal of the video
- Intended audience
- Deliverable format
- Current creative direction
- References for this specific project
- Script status
- Shot or scene plan
- Asset status
- Edit notes
- Open questions
- Next steps

If a global style exists, use it as background taste. The project memory file should only contain project-specific decisions and progress.

After loading or saving style, check for `ffmpeg`.

Use `ffmpeg -version` or `which ffmpeg` / `where ffmpeg` depending on platform.

If `ffmpeg` is missing, stop and tell the user that Director requires `ffmpeg` before video work can continue.

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

- Use `skills/hyperframes/hyperframes-cli/SKILL.md` for HyperFrames CLI workflows such as init, inspect, lint, preview, validate, and render.
- Use `skills/hyperframes/hyperframes-media/SKILL.md` for preprocessing tasks such as voice, transcription, background removal or other media prep steps handled by that skill.
- Use `skills/hyperframes/website-to-hyperframes/SKILL.md` when adapting an existing website or webpage into a HyperFrames composition.
- Use `skills/hyperframes/three/SKILL.md` for Three.js-based 3D scenes inside HyperFrames.
- Use `skills/hyperframes/gsap/SKILL.md` when GSAP is the main animation engine and the task is specifically about timeline behavior or animation construction.
- Use `skills/hyperframes/animejs/SKILL.md` when Anime.js is the intended animation engine.
- Use `skills/hyperframes/css-animations/SKILL.md` when the motion should be driven primarily by CSS animations.
- Use `skills/hyperframes/tailwind/SKILL.md` when the composition is built with Tailwind-based styling conventions.
