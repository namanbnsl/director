# Math Rendering

Use this whenever a video contains formulas, equations, proofs, symbols, derivations, geometric notation, statistical expressions, matrix/vector notation, or algorithmic math.

Math is not normal text. It needs special rendering, special pacing, and special animation.

## Rendering Standard

Prefer one of these paths:

1. **KaTeX for formulas and inline math** when the expression is textual/symbolic.
2. **SVG for diagrams, geometry, graphs, vectors, paths, and annotated derivations.**
3. **Canvas or Three.js** when the math is spatial, dynamic, simulated, or needs continuous motion.

Do not typeset math by hand with plain HTML spans unless it is a tiny symbol such as `x`, `n`, or `O(n)`.

## KaTeX Pattern

Use KaTeX for crisp equation rendering:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/katex@0.16.22/dist/katex.min.css"
  crossorigin="anonymous"
/>
<script
  defer
  src="https://cdn.jsdelivr.net/npm/katex@0.16.22/dist/katex.min.js"
  crossorigin="anonymous"
></script>

<div id="eq-main" class="equation"></div>

<script>
  katex.render(String.raw`L(\theta)=\frac{1}{N}\sum_{i=1}^{N}(y_i-f_\theta(x_i))^2`, document.getElementById("eq-main"), {
    displayMode: true,
    throwOnError: false,
    strict: "ignore",
  });
</script>
```

If the project must render offline or avoid CDN dependencies, install/copy KaTeX assets into the project and reference local files. Do not fall back to ugly plain text math.

## Motion For Math

Animate math like a derivation, not like a title card.

- Reveal equations by semantic units: term, operator, numerator, denominator, vector, matrix row, constraint, result.
- Use highlighting to track the viewer's attention: color one term, draw a brace, circle a variable, or connect a symbol to a diagram.
- Transform meaningfully: duplicate a term, move it across the equals sign, collapse a sum into a mean, expand a vector into components.
- Pair formula with a visual system when possible: graph curve, geometry diagram, loss surface, probability distribution, matrix grid, token flow, or number line.
- Keep the current equation stable while animating emphasis on top. Do not make the viewer reread an equation after every tween.

## Layout Rules

- Equations need more breathing room than body text.
- Large display equations should occupy 45-80% of frame width.
- Inline math inside paragraphs must be noticeably better rendered than normal text and must not change line height unpredictably.
- Use `font-variant-numeric: tabular-nums` for numeric tables and calculations.
- For matrix/grid math, align cells exactly. Uneven math grids look broken immediately.
- Avoid tiny subscripts in video. If a subscript matters, zoom in or split the equation into a close-up beat.

## Consistency

Math has its own visual grammar across the whole video:

- One equation type style.
- One highlight color for "current focus."
- One secondary color for "previous/result."
- One diagram line style.
- One notation scale: do not jump between tiny academic notation and giant marketing numbers without a shot reason.

## Pre-Preview Checks

Before showing a math video:

- Snapshot at every equation's hero frame.
- Check that all symbols are crisp, not clipped, and not rendered as raw LaTeX.
- Check that fractions, radicals, matrices, summations, integrals, and subscripts are readable at 1920x1080.
- Confirm the animation reveals mathematical meaning, not just opacity.
- If an equation is too dense, split it into multiple beats.
