# Output Format Specification

This document defines the complete 13-chapter output format for the DesignDNA design system document.
Follow this structure exactly when generating the output.

---

## Chapter 1: Document Naming

Auto-name the document based on the core visual characteristics.

**Format**: `[Visual Style] + [UI Type] + 规范`

### Examples

- 深色毛玻璃科技风 UI 规范
- 极简白色卡片式后台规范
- 高级渐变霓虹风 Design System
- 苹果风半透明界面规范

Naming must convey:
- Visual style
- Interface personality
- UI type

---

## Chapter 2: Visual Style Summary

Prioritize analysis of:

- Design language
- Style keywords
- UI personality
- Brand feel
- Light and shadow characteristics
- Color tendency
- Motion tendency
- Spatial density
- Reference styles

### Output Format

```markdown
风格关键词：
glassmorphism / minimal / soft-shadow / neon

视觉特征：
大面积留白 + 微弱描边 + 半透明模糊

参考风格：
Apple / Linear / Vercel
```

---

## Chapter 3: Design Tokens (CSS Variables)

Output the complete CSS variable system. All values must be directly copy-pasteable with correct CSS syntax and a unified naming convention.

### Structure Template

```css
:root {
  /* Colors */
  --color-primary: #000000;
  --color-primary-hover: #111111;
  --color-primary-active: #222222;

  --color-secondary: #666666;

  --color-bg: #ffffff;
  --color-surface: #f5f5f5;
  --color-surface-hover: #eeeeee;

  --color-border: #e0e0e0;

  --color-text: #1a1a1a;
  --color-text-muted: #888888;

  --color-success: #22c55e;
  --color-warning: #f59e0b;
  --color-danger: #ef4444;

  --color-disabled: #cccccc;

  /* Radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.07);
  --shadow-lg: 0 10px 25px rgba(0, 0, 0, 0.1);
  --shadow-glow: 0 0 20px rgba(0, 0, 0, 0.15);

  /* Spacing */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 24px;
  --space-6: 32px;

  /* Opacity */
  --opacity-hover: 0.8;
  --opacity-disabled: 0.5;

  /* Blur */
  --blur-glass: blur(12px);

  /* Transition */
  --transition-base: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}
```

### Required Sub-systems

#### Color System
- Primary, secondary, neutral, semantic (success/warning/danger)
- Hover, active, disabled variants

#### Shadow System
- Card shadow, overlay shadow, hover shadow, inset shadow

#### Border Radius System
- Small / Medium / Large / Extra-large

#### Spacing System
Based on actual analysis — identify the base rhythm (commonly 4px or 8px):
- 4px, 8px, 12px, 16px, 24px, 32px, etc.

#### Background System
Analyze:
- Gradients (linear, radial, conic)
- Noise textures
- Glassmorphism (backdrop-filter, blur)
- Glow effects
- Pattern overlays

---

## Chapter 4: Missing Value Handling Rules

Priority order (strictly enforced):

1. **Extract from source** — prefer real values from code/screenshots
2. **Infer from style** — if missing, infer based on overall style consistency
3. **Mark inferred** — label as `（推断值）`
4. **Mark unknown** — if uninferrable, label as `未定义`

### Forbidden

- Fabricating values that contradict the visual style
- Filling in design language elements not present in the source
- Using placeholder comments

---

## Chapter 5: Base Styles

Output base element styles for:

- `body`
- `h1` through `h6`
- `p`
- `a`
- `button`
- `input`
- `textarea`
- `select`

### Required for each element

- Font family stack
- Line height
- Font weight
- Font size (for headings)
- Hover state (if applicable)
- Focus state (if applicable)
- Active state (if applicable)

### Example

```css
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  color: var(--color-text);
  background: var(--color-bg);
}

h1 {
  font-size: 2.5rem;
  font-weight: 700;
  line-height: 1.2;
  letter-spacing: -0.02em;
}
```

---

## Chapter 6: Component Specifications (Core)

Extract every component that **actually exists** in the source.

### For each component, document:

1. **Purpose** — what the component does
2. **HTML structure** — semantic markup
3. **CSS** — complete, production-ready styles
4. **State variations** — default, hover, focus, active, disabled
5. **Motion** — transitions and animations
6. **Responsive behavior** — breakpoint adaptations

### Standard Component Checklist

Only include components present in the source:

- [ ] Button
- [ ] Card
- [ ] Navbar
- [ ] Sidebar
- [ ] Modal
- [ ] Dialog
- [ ] Tooltip
- [ ] Badge
- [ ] Tabs
- [ ] Dropdown
- [ ] Input
- [ ] Switch
- [ ] Table
- [ ] Toast
- [ ] Loading
- [ ] Skeleton
- [ ] (Add any additional components found in source)

### State Documentation Rules

For each component, only document states that are visually evidenced:

| State | If evidenced | If not evidenced |
|-------|-------------|-----------------|
| Default | Document with real CSS | N/A |
| Hover | Document with real CSS | Infer and mark `（推断值）` |
| Focus | Document with real CSS | Mark `未定义` if unclear |
| Active | Document with real CSS | Mark `未定义` if unclear |
| Disabled | Document with real CSS | Mark `未定义` if unclear |

---

## Chapter 7: Motion Specification

Extract:

- `transition` timing
- `easing` curves
- Hover animations
- Modal enter/exit animations
- Page transition style

### Output Format

```css
transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
```

### Analysis Notes

Additionally analyze and describe:

- Whether motion feels soft/rapid
- Whether it leans Apple-style
- Whether it has gaming feel
- Whether it emphasizes micro-interactions

---

## Chapter 8: Icon Specification

Analyze:

- Outline vs filled style
- Recommended icon library
- Size conventions
- Stroke width rules
- Color inheritance behavior

### Output Format

```markdown
风格：outline
推荐图标库：
- Lucide Icons
- Heroicons
- Phosphor Icons

尺寸规则：16px / 20px / 24px
Stroke 宽度：1.5px
颜色继承：currentColor
```

---

## Chapter 9: Layout System

Extract:

- Grid system (CSS Grid / Flexbox)
- Max-width values
- Content density
- Whitespace rhythm
- Container padding
- Card arrangement pattern

### Classification

Identify which layout pattern the design follows:

- Dashboard style
- Bento Grid style
- Editorial style
- Apple style
- Custom (describe)

---

## Chapter 10: Responsive Adaptation

Output media queries and breakpoint behavior:

```css
@media (max-width: 768px) { /* tablet */
  /* adaptations */
}

@media (max-width: 480px) { /* mobile */
  /* adaptations */
}
```

### Required Coverage

- Tablet adaptation
- Mobile adaptation
- Grid/column changes
- Font size scaling
- Navbar changes (hamburger menu, collapse)
- Drawer/sheet behavior

---

## Chapter 11: Technology Stack Inference

Infer the likely tech stack, but **only when clear evidence exists**.

### Evidence Table

| Evidence | Valid Inference |
|----------|-----------------|
| 8px spacing rhythm, utility-only classes | TailwindCSS |
| `data-radix-*` attributes, Radix component structure | Radix UI |
| `cn()` utility, `variants()` pattern | shadcn/ui |
| `motion.*` API, spring configs | Framer Motion |
| `gsap.to()`, ScrollTrigger | GSAP |
| `next/image`, App Router file structure | Next.js |
| `.module.css` or CSS Modules import pattern | CSS Modules |
| Styled Components / Emotion imports | CSS-in-JS |

### If no clear evidence: output `无法确定`

---

## Chapter 12: Output Quality Requirements (Strict)

All output MUST satisfy:

- Markdown format throughout
- No explanatory filler text — be direct and technical
- All CSS code is directly copy-pasteable
- Clean, scannable document structure
- Enterprise-grade Design System quality
- No "AI-sounding" descriptions
- Prefer production-ready code over explanations
- No missing component states
- No pseudo-code
- No incomplete CSS blocks

---

## Chapter 13: Final Verification

The generated document must satisfy this criterion:

> Any frontend developer who copies this document can reproduce the original
> interface's visual quality, component behavior, and layout system in a new project
> with high fidelity.

Before delivering, verify:

- [ ] All 13 chapters are present
- [ ] CSS is syntactically correct
- [ ] No placeholder values
- [ ] Inferred values are marked
- [ ] Components match the source (no invented ones)
- [ ] No generic AI descriptions — all analysis is specific to the source
