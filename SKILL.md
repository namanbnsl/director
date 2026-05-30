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
6. Check whether `ffmpeg` is installed before continuing.

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
