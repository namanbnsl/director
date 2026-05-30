# Beautiful Motion Direction

Use this alongside `anti-slop-gate.md` when a video needs to feel genuinely crafted. This is not a request for more effects. It is a request for better staging, timing, rhythm, and custom visual ideas.

Research basis:

- Apple Human Interface Guidelines, Motion: motion should be purposeful, fluid, contextual, and should not distract or disorient. https://developer.apple.com/design/human-interface-guidelines/motion
- Material Design, Duration and easing: transitions should be fast enough to avoid waiting, slow enough to understand, and durations should adapt to distance and velocity. https://m1.material.io/motion/duration-easing.html
- Material Design, Choreography: motion should guide focus through shared elements and spatial relationships. https://m1.material.io/motion/choreography.html
- GSAP Easing docs: changing the ease changes the feel and personality of an animation. https://gsap.com/docs/v3/Eases/
- LottieFiles motion design guide: motion design combines graphic design, animation, filmmaking, visual communication, and sound. https://lottiefiles.com/blog/tips-and-tutorials/guide-to-motion-design
- Rive State Machine docs: state-based animation lets visuals transition between meaningful states rather than only play isolated clips. https://rive.app/docs/editor/state-machine

## Direction Test

Before writing HTML, describe the piece in one sentence using a physical or cinematic verb:

- "A system unfolds from a single signal into a living architecture."
- "Metrics build like pressure until the chart snaps into a new regime."
- "A product UI assembles itself from real interactions, then the camera dives into the decisive moment."

If the sentence is "slides explain X," redesign.

## The Four-Part Motion Recipe

Every major beat needs all four parts:

1. **Anticipation:** a small pre-motion before the main action. Examples: object compresses 3%, line retracts 20px before drawing forward, camera drifts opposite the coming push, cursor pauses before typing.
2. **Primary action:** the thing the viewer must understand. Examples: node connects, chart grows, interface state changes, 3D layer unfolds, headline slams in.
3. **Follow-through:** secondary elements settle after the main action. Examples: labels lag by 80ms, connector pulses after drawing, shadow catches up, particles continue, value overshoots then corrects.
4. **Continuing life:** something evolves during the hold. Examples: camera push, chart shimmer tied to data, orbiting markers, typed line, path trace, image parallax, subtle state changes.

A beat with only part 2 is mechanical. A beat with parts 1-4 feels directed.

## Custom Visual Systems

For every non-trivial video, build or use at least one custom visual system that belongs to the subject. Choose the system before choosing colors.

Examples:

- **Architecture:** packet flow, layer stack, dependency graph, service map, transformer block, queue, circuit board, data plane/control plane split.
- **Data:** animated proportional bars, slope line, morphing area, scrolling timeline, force graph, radial gauge, stream graph, map sweep, before/after comparison.
- **Product:** composed UI state machine, command palette typing, drag-and-drop board, notification cascade, file tree expansion, device fly-through.
- **Conceptual:** particle field, kinetic typography rig, SVG path drawing system, 3D object assembly, Lottie/Rive-style authored state change.

Do not start with background treatment. Start with the visual system.

## Choreography Rules

- Use shared-element transitions when one idea becomes another: the same node, card, word, or chart mark should carry the viewer across the cut.
- Stage the eye path. The first movement gets attention, the largest movement confirms hierarchy, and the final movement should hand off to the next beat.
- Use arcs and curves for natural travel. Straight-line motion is fine for mechanical systems, but organic or premium pieces need curved paths, orbit, sweep, or camera motion.
- Layer timing. Foreground leads, midground follows, background reacts; do not move all layers on the same frame.
- Use silence/stillness only as contrast after motion, not because the scene has nothing to do.

## Timing And Easing

Use durations by intent:

- **Snap:** 0.12-0.25s for hits, cursor blips, tiny state changes.
- **Read:** 0.3-0.55s for normal entrances, labels, UI state changes.
- **Weight:** 0.6-0.9s for large panels, diagrams, charts, or camera moves.
- **Cinema:** 1.0-2.5s for atmospheric pushes, reveals, 3D fly-throughs, or footage treatments.

Use easing by meaning:

- `expo.out`, `power4.out`: confident reveal.
- `back.out(1.2-1.8)`: tactile overshoot, playful or product-like.
- `sine.inOut`: elegant camera drift or calm continuous motion.
- `power2.in` or `power3.in`: exits and throws.
- `steps(1)` or stepped eases: terminals, counters, pixel or mechanical beats.
- CustomEase or MotionPath when the movement should feel authored, not generic.

Never use one ease family for a whole scene. Ease choice is part of the art direction.

## Beauty Killers

These usually make HyperFrames output look like AI-generated presentation art:

- Gradient background plus centered headline.
- Identical rounded cards with identical entrance tweens.
- Text sitting still after a reveal.
- Diagrams that appear already complete.
- Abstract blobs that do not react to the content.
- A camera that never moves.
- Motion that starts without anticipation and stops without follow-through.
- Effects that are not tied to the subject: glow, blur, particles, noise, or chromatic aberration with no story role.

## Implementation Pattern

When building a beat, write this before the code:

```text
Beat:
Shot:
Primary visual system:
Anticipation:
Primary action:
Follow-through:
Continuing life:
Shared element / transition handoff:
Custom asset/catalog/library used:
Why this is not a slide:
```

Then implement exactly that. If the code drifts into static layout, revise the plan or the implementation.
