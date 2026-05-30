---
name: director
description: Create high-quality videos with agentic workflows
---

# Director

Director helps create excellent videos by starting from creative direction: style, pacing, audience, references, format, and constraints.

## First Run

Before starting any video work, check whether a global Director style exists.

Look in this order:

1. `$HOME/.director/style.md` on macOS/Linux.
2. `%USERPROFILE%\.director\style.md` on Windows.

If no global style exists, ask the user:

```text
Before I use Director, I need to set your default video style.

This will be saved as your global Director style and reused for future video projects unless a project defines its own style.

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

Use `$DIRECTOR_HOME/style.md` if `DIRECTOR_HOME` is set. Otherwise use the platform default:

- macOS/Linux: `$HOME/.director/style.md`
- Windows: `%USERPROFILE%\.director\style.md`

If a global style exists, use it automatically unless the user asks to update it or the current project has an override.

## Style Priority

For each project, style priority is:

1. Project style: `director.style.md`
2. Project style: `.director/style.md`
3. Global style:`$HOME/.director/style.md`, or `%USERPROFILE%\.director\style.md`

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
