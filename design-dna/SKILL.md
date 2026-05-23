---
name: design-dna
description: >
  Reverse-engineer the complete UI design system from any web page — HTML/CSS source code,
  Tailwind classes, React components, or screenshots — and generate a production-ready
  Markdown design system document (Design Tokens, component specs, motion, layout, responsive).
  Use this skill when the user asks to extract, analyze, reverse-engineer, generate, or clone
  a UI design system / design spec / design tokens / visual style guide from a website,
  screenshot, or code source. Triggers include: extract design spec, reverse-engineer UI style,
  generate design system, analyze visual design, extract Design Tokens, clone interface style,
  UI spec document generation, 提取设计规范, 逆向UI风格, 生成设计系统, 分析视觉设计,
  提取Design Tokens, 复刻界面风格, UI规范文档生成, 设计规范逆向.
allowed-tools: Read, Bash, Write
---

# DesignDNA — UI Design System Reverse-Engineering

Extract the complete visual design system from any web page source or screenshot, and output a
production-ready Markdown design system document that lets any frontend developer replicate the
original visual quality, component behavior, and layout system.

---

## Workflow

When this skill is activated, follow these steps in order:

### 1. Accept Input

The user will provide one or more of:

| Input Type | Format |
|------------|--------|
| HTML/CSS source code | Pasted code, file path, or URL |
| Tailwind classes | Component markup with utility classes |
| React component code | JSX/TSX source |
| Screenshot / image | File path or pasted image |

If the input is a **URL**, use WebFetch to retrieve the page source first.

### 2. Analyze the Source

Perform a thorough visual analysis of the provided material:

- **Colors**: Extract all hex/rgb/hsl values from CSS variables, inline styles, and class definitions. Identify primary, secondary, neutral, and semantic colors.
- **Typography**: Font family stack, font sizes, line heights, font weights.
- **Spacing**: Padding, margin, gap patterns. Identify the base spacing rhythm (4px / 8px / etc.).
- **Border radius**: All border-radius values used across components.
- **Shadows**: Box-shadow definitions, including card shadows, hover shadows, glow effects.
- **Backgrounds**: Solid colors, gradients, blur/backdrop-filter, noise textures.
- **Components**: Identify every distinct UI component present (buttons, cards, inputs, modals, etc.).
- **Motion**: transition durations, easing curves, animation definitions.
- **Layout**: Grid/flex patterns, max-widths, container padding, content density.
- **Responsive**: Media queries, breakpoint behavior, mobile adaptations.
- **Icons**: Style (outline/filled), stroke width, size conventions.

### 3. Generate Output Document

Produce the design system document following the format defined in
[output-format.md](references/output-format.md).

Use the template in [assets/template.md](assets/template.md) as the document skeleton.

### 4. Validate Before Delivery

Before delivering, check:

- [ ] All CSS variable values are syntactically correct and directly copy-pasteable
- [ ] Every component extracted from the source is documented (no omissions)
- [ ] Inferred values are marked with `（推断值）`
- [ ] Unidentifiable values are marked with `未定义`
- [ ] No fabricated values that contradict the source's visual style
- [ ] No placeholder or pseudo-code — all CSS must be production-ready
- [ ] Markdown structure follows the 13-chapter format exactly

---

## Missing Value Rules

When a value cannot be extracted from the source:

1. **Prefer real values** — extract from source code or visually measure from screenshots
2. **If missing** — infer based on overall style consistency, mark as `（推断值）`
3. **If uninferrable** — mark as `未定义`

**Never**:
- Fabricate values that contradict the visual style
- Fill in design language elements that don't exist in the source
- Output placeholder comments like `/* add your value here */`

---

## Component Extraction Rules

Only document components that **actually exist** in the source:

- Do NOT invent components not present in the source
- For each component, document only the states that are visually evidenced
- Missing states should be marked `（推断值）` or `未定义`
- Include interactive states: default, hover, focus, active, disabled (where applicable)

---

## Technology Stack Inference

Only infer the tech stack when there is clear evidence:

| Evidence | Valid Inference |
|----------|-----------------|
| 8px spacing rhythm, utility classes | TailwindCSS |
| Radix-compatible component structure | Radix UI / shadcn/ui |
| `framer-motion` imports / spring easing | Framer Motion |
| `gsap` / ScrollTrigger | GSAP |
| File-based routing, `next/image` | Next.js |

If no clear evidence exists, output `无法确定`. Never force an association.

---

## Output Quality Checklist

- All code is directly copy-pasteable — no explanations, no pseudo-code
- CSS is complete and syntactically valid
- Markdown structure is clean and scannable
- Output reads like a real enterprise-grade Design System
- Avoids "AI-sounding" descriptions — be precise and technical
- Every component's critical states are covered

---

## Extended Reference

For the complete 13-chapter output format specification with detailed templates,
CSS variable structures, component checklists, and examples, read:

**[references/output-format.md](references/output-format.md)** — Full output format spec

For common pitfalls and error handling patterns in reverse-engineering, read:

**[references/gotchas.md](references/gotchas.md)** — Gotchas and edge cases

For the output document template skeleton, use:

**[assets/template.md](assets/template.md)** — Copy-ready output template
