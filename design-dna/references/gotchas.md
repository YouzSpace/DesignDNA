# Gotchas and Edge Cases

Common pitfalls when reverse-engineering UI design systems, and how to handle them.

---

## Color Extraction

### Dark Mode Ambiguity
Some websites use `prefers-color-scheme` or JavaScript-toggled dark mode. Only document the
theme that is visible in the provided source/screenshot. If both themes are present, document
each as a separate section.

### CSS Custom Properties vs Hardcoded Values
Many sites define design tokens in `:root` but also hardcode colors inline or in component CSS.
Extract BOTH — the token name and the actual value — and note where hardcoding occurs.

### Gradient Color Stops
When extracting gradients, record the exact color stop positions (e.g., `0%`, `50%`, `100%`),
not just the colors. A `linear-gradient(to right, #000, #fff)` is very different from
`linear-gradient(to right, #000 10%, #fff 90%)`.

### Transparent / Semi-transparent Colors
`rgba()` and `hsla()` values are common in overlays, shadows, and borders. Always preserve
the alpha channel — do not round or approximate opacity values.

---

## Typography

### System Font Stack Approximation
`-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, ...` is a system font stack, not a
single font. Document the full stack, not just the first entry.

### Responsive Font Sizes
Font sizes often change at breakpoints. If `clamp()` or media-query-based sizing is used,
document both the mobile and desktop values, plus the breakpoint where they change.

### `rem` vs `px` vs `em`
Preserve the unit system used in the source. Do not convert between units — this introduces
rounding errors and breaks the design's mathematical relationships.

---

## Spacing and Layout

### Inconsistent Spacing Rhythm
Not all designs follow a perfect 4px or 8px rhythm. If the source uses irregular spacing
(5px, 13px, 17px), document the actual values faithfully. Do NOT round to the nearest power of 2.

### Negative Margins
Some layouts use negative margins for overlapping elements or edge-to-edge containers. Document
these explicitly — they are easy to overlook but critical for replication.

### `gap` vs `margin` for Spacing
Modern CSS uses `gap` in flexbox/grid, while older patterns use `margin` on children. Identify
which pattern the source uses and document accordingly.

---

## Shadows

### Multi-layer Shadows
Professional designs often stack multiple `box-shadow` values:
```css
box-shadow: 0 1px 2px rgba(0,0,0,0.04), 0 4px 12px rgba(0,0,0,0.08);
```
Document each layer separately with its offset, blur, spread, and color.

### `inset` Shadows
Inner shadows (`inset 0 1px 0 rgba(...)`) are commonly used for inset borders, pressed states,
or depth effects. These are frequently missed — check for them explicitly.

---

## Components

### State Complexity
Real-world components can have many states beyond the basic five. Watch for:
- Loading state (spinner, skeleton, shimmer)
- Error state (red border, error message)
- Selected/checked state
- Expanded/collapsed state
- Truncated state (text overflow)

### Component Variants
Buttons often come in primary, secondary, ghost, outline, danger, link variants. Document
each variant separately with its distinct CSS.

### Tooltip / Popover Positioning
Tooltip positioning (top, right, bottom, left) often has different arrow styles and offsets.
If the source shows tooltips, document the positioning system.

---

## Motion and Animation

### `transition: all` Anti-pattern
Many production sites use `transition: all 0.2s ease` as a shorthand. While this works, it's
not best practice. Document what the source **actually uses**, not what it **should use**.

### GPU-Accelerated Properties
Properties like `transform` and `opacity` are GPU-accelerated, while `width`, `height`, `top`,
and `left` trigger layout reflow. If the source uses non-accelerated properties in animations,
note this as a potential performance concern.

### Reduced Motion
Check if the source has `prefers-reduced-motion: reduce` handling. If it does, document it.
If it doesn't, note it as `未定义`.

---

## Technology Stack Inference

### Tailwind vs Custom CSS
The presence of utility classes like `flex`, `p-4`, `text-lg` strongly suggests Tailwind.
However, some frameworks (e.g., Tachyons, Windi CSS) use similar naming. Only infer Tailwind
when there is clear evidence (e.g., `tailwind.config`, `@tailwind` directives).

### React vs Vue vs Vanilla
- React: `className`, `jsx`, `useState`, component file structure
- Vue: `class` binding, `v-if`/`v-for`, `.vue` single-file components
- Vanilla: plain HTML/CSS, no framework indicators
- If uncertain, mark as `无法确定`

### Framework Version Guessing
Do not guess framework versions unless there is explicit evidence (e.g., `package.json`,
`importmap`, CDN URL with version number). A component using hooks does NOT prove React 18+.

---

## Screenshot-Specific Issues

### Resolution and Scaling
Screenshots may be taken at different zoom levels and resolutions. If extracting pixel values
from a screenshot, be aware of potential scaling artifacts. Always prefer source code values
over visual measurements.

### Color Accuracy
Screenshot colors may differ from actual CSS values due to compression, color profile
mismatches, or display calibration. If a screenshot is the only source, note that color
values are approximate: `（截图推断值，可能存在色差）`.

### Dynamic Elements
Screenshots capture a single moment. Hover states, active states, animations, and transitions
cannot be directly observed. Mark these as `（推断值）` or `未定义` as appropriate.
