# DesignDNA

> Extract the DNA of any UI.
> 将任意 UI 界面逆向为可复用设计系统。

---

[English](#english) | [中文](#中文)

---

# English

## Overview

DesignDNA is an AI-powered UI reverse engineering prompt, packaged as a standard [Agent Skill](https://agentskills.io) for cross-platform compatibility with 40+ AI coding agents (Claude Code, Cursor, VS Code Copilot, Gemini CLI, etc.).

It extracts complete design systems from:

- Screenshots
- HTML/CSS source code
- Tailwind projects
- React components
- SaaS dashboards
- Modern web interfaces

And transforms them into reusable engineering specifications.

---

## What It Generates

- Design Tokens
- CSS Variables
- Typography Systems
- Component Specifications
- Responsive Rules
- Motion Guidelines
- Layout Systems
- Interaction States
- Technical Stack Inference

---

## Core Features

### UI Reverse Engineering

Analyze and reconstruct:

- Visual language
- UI patterns
- Shadows
- Radius systems
- Layout rhythm
- Motion behavior
- Responsive structures

---

### Smart Style Inference

When the original source is incomplete:

- Infer missing styles based on surrounding UI language
- Mark inferred values clearly
- Avoid hallucinated patterns

---

### Production-Ready Output

Generate:

- Reusable Markdown specs
- Engineering-friendly CSS
- Component state definitions
- Real-world Design System structures

---

## Project Structure

```
design-dna/
├── SKILL.md                    # Core: metadata + reverse-engineering workflow
├── references/
│   ├── output-format.md        # Complete 13-chapter output format specification
│   └── gotchas.md              # Common pitfalls and edge cases
├── assets/
│   └── template.md             # Copy-ready output document template
└── scripts/                    # (Reserved for future validation scripts)
```

---

## Quick Start

### Option 1: Agent Skill (Recommended)

Copy the `design-dna/` folder to your agent's skills directory:

```bash
# Claude Code / Gemini CLI / Roo Code
cp -r design-dna/ .agents/skills/

# Or to user-level (works across all projects)
cp -r design-dna/ ~/.workbuddy/skills/
```

Then in your agent, provide a screenshot or source code and ask:

> "Extract the design system from this page"

### Option 2: Direct Prompt

The original prompt is preserved in `DesignDNA.md` at the project root.
Copy its contents and use directly with any AI assistant.

---

## Example Workflow

### Step 1

Provide:

- A screenshot
- HTML/CSS
- Tailwind code
- React component source

### Step 2

Use the DesignDNA skill or prompt.

### Step 3

Generate:

- Complete Design System docs
- CSS variable systems
- Component specifications
- Responsive guidelines

---

## Example Output

```css
:root {

  --color-primary: #7c5cff;

  --color-surface:
    rgba(255,255,255,0.08);

  --radius-lg: 20px;

  --shadow-glow:
    0 0 24px rgba(124,92,255,0.35);

}
```

---

## Philosophy

DesignDNA is not just a prompt.

It is a workflow for turning interfaces into reusable engineering systems.

---

## Future Plans

- Figma Token Export
- Tailwind Config Generator
- shadcn/ui Theme Generator
- Cursor Rules
- Chrome Extension
- MCP Integration
- AI Agent Automation

---

## License

MIT License

---

# 中文

## 项目简介

DesignDNA 是一个基于 AI 的 UI 逆向工程 Prompt，按 [AgentSkills 开放标准](https://agentskills.io) 封装为标准 Skill，兼容 Claude Code、Cursor、VS Code Copilot、Gemini CLI 等 40+ AI 编码助手。

它可以从以下内容中自动提取完整设计系统：

- 网页截图
- HTML / CSS 源码
- Tailwind 项目
- React 组件
- SaaS 后台
- 现代 Web UI

并自动生成结构化、可复用、工程化的设计规范文档。

---

## 可生成内容

- Design Tokens
- CSS Variables
- 字体系统
- 组件规范
- 响应式规则
- 动效规范
- 布局系统
- 交互状态
- 技术栈推断

---

## 核心特性

### UI 逆向工程

自动分析并重建设计语言：

- 视觉风格
- UI 模式
- 阴影体系
- 圆角体系
- 布局节奏
- 动效行为
- 响应式结构

---

### 智能风格推断

当源码不完整时：

- 基于整体 UI 风格推断缺失值
- 自动标记"推断值"
- 避免 AI 胡乱补全

---

### 工程化输出

自动生成：

- Markdown 设计规范
- 可复用 CSS
- 组件状态定义
- 企业级 Design System 结构

---

## 项目结构

```
design-dna/
├── SKILL.md                    # 核心文件：元数据 + 逆向分析工作流
├── references/
│   ├── output-format.md        # 完整 13 章输出格式规范
│   └── gotchas.md              # 常见陷阱与边缘情况
├── assets/
│   └── template.md             # 可复用的输出文档模板
└── scripts/                    # （预留）校验脚本
```

---

## 快速上手

### 方式一：Agent Skill（推荐）

将 `design-dna/` 文件夹复制到你的 Agent 技能目录：

```bash
# Claude Code / Gemini CLI / Roo Code
cp -r design-dna/ .agents/skills/

# 或复制到用户级目录（跨项目通用）
cp -r design-dna/ ~/.workbuddy/skills/
```

然后在 Agent 中提供截图或源码，输入：

> "提取这个页面的设计系统"

### 方式二：直接使用 Prompt

原始 Prompt 保留在项目根目录的 `DesignDNA.md` 中。
复制内容后可直接用于任何 AI 助手。

---

## 使用流程

### 第一步

输入：

- 网页截图
- HTML/CSS
- Tailwind 代码
- React 组件源码

### 第二步

使用 DesignDNA Skill 或 Prompt。

### 第三步

自动生成：

- 完整 Design System 文档
- CSS 变量系统
- 组件规范
- 响应式规范

---

## 输出示例

```css
:root {

  --color-primary: #7c5cff;

  --color-surface:
    rgba(255,255,255,0.08);

  --radius-lg: 20px;

  --shadow-glow:
    0 0 24px rgba(124,92,255,0.35);

}
```

---

## 项目理念

DesignDNA 不只是一个 Prompt。

它真正想做的是：

> 将 UI 界面逆向为可复用的工程化设计系统。

---

## 后续计划

- Figma Token 导出
- Tailwind Config Generator
- shadcn/ui Theme Generator
- Cursor Rules
- Chrome 插件
- MCP 集成
- AI Agent 自动化

---

## License

MIT License

---

# Tagline

> Extract the DNA of any UI.
> 提取任意 UI 的设计基因。
