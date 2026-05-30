---
name: architecture-visualizer
description: Turn systems, pipelines, transformer architectures, and technical diagrams into understandable animated video sequences and visual explanations.
---

# Architecture Visualizer

Use this skill when the video needs to explain a system, workflow, technical stack, model architecture, pipeline, or transformer-style diagram.

## Outcome

Produce an architecture visualization plan with:

- Core system narrative
- Main entities and connections
- Progressive reveal order
- Diagram style
- Motion and emphasis strategy
- Where 2D is enough and where 3D or depth may help

## Workflow

1. Read `director.project.md` first.
2. Identify the minimum structure needed for understanding.
3. Break the explanation into beats rather than dumping the whole architecture at once.
4. Research existing libraries or reference styles if they would improve clarity.
5. Specify the reveal mechanics: path drawing, packets moving, node activation, zoom/reframe, layer separation, 3D depth, or state transition.
6. Save the chosen explanation structure into `director.project.md`.

## Guidance

- Avoid giant static diagrams.
- Reveal systems progressively.
- Use motion to explain flow, dependency, and hierarchy.
- Do not be scared of transformer or model-architecture visuals; they are a first-class use case.
- Do not turn architecture into a labeled slide. Each beat should show a change in the system: data moves, layers unfold, dependencies light up, or the camera reframes from overview to detail.
- Use catalog blocks, SVG path drawing, Canvas, Three.js, or composed diagram components when they improve clarity.
