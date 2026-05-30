# Consistency Pass

Run this before preview for every multi-scene video. Inconsistency is one of the fastest ways for a video to feel generated instead of directed.

## Lock The System

Before writing or revising scenes, define:

- **Palette:** one canvas color, one text color, one muted text color, one accent, one warning/emphasis color if needed.
- **Typography:** one display face, one body face, one mono/math face if needed, and exact weight roles.
- **Shape language:** corner radius, border thickness, line cap style, icon/stroke style.
- **Depth language:** flat, shadowed, glass, 3D, or layered. Do not mix all of them.
- **Motion language:** 2-3 recurring eases, standard transition duration range, standard ambient motion style.
- **Shot language:** recurring camera moves and framing scale.
- **Visual motif:** a repeated line, grid, marker, path, particle behavior, device angle, or diagram convention.

Write those decisions into `director.project.md` or the storyboard before implementation.

## Scene-To-Scene Continuity

Every scene should feel like part of the same film unless the script explicitly changes worlds.

Check:

- Same background/canvas logic across scenes.
- Same border radius and stroke widths.
- Same label style, casing, spacing, and placement.
- Same data label grammar and number formatting.
- Same math/equation style if math appears.
- Same shadow/depth model.
- Same transition family, with only 1-2 deliberate hero exceptions.
- Same treatment for captured assets: all flat, all framed, all parallax, or all integrated with a stated reason.

## Variation Without Randomness

Variation is good; inconsistency is not.

Use controlled variation:

- Change shot size, not the whole style.
- Change emphasis color intensity, not the palette.
- Change camera direction, not motion physics.
- Change chart form when the data story changes, not because a scene looks empty.
- Use one "hero" transition as a set piece; keep connective transitions quieter.

## Snapshot Review

When snapshots are available, compare the contact sheet mentally as if it were a film strip:

- Could these frames come from the same video?
- Does one scene suddenly look like a different template?
- Are type sizes jumping without a shot reason?
- Are gradients, shadows, radii, or borders inconsistent?
- Does the visual density stay intentional?
- Is the fun/professional balance consistent, or does one scene become corporate while another becomes toy-like?

Fix inconsistency before polishing individual scenes.
