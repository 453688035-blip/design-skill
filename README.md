# Design Skill

Google 设计系统与代码风格指南的本地参考资源库，涵盖 **Material Design 3 (M3)** 视觉设计系统和 **Google 代码风格指南**两大核心内容。

---

## 目录

- [概述](#概述)
- [目录结构](#目录结构)
- [Material Design 3 资源](#material-design-3-资源)
- [代码风格指南](#代码风格指南)
- [设计系统 Skill](#设计系统-skill)
- [IDE/编辑器配置](#ide编辑器配置)
- [许可证](#许可证)

---

## 概述

本仓库整合了以下资源：

| 资源 | 来源 | 用途 |
|---|---|---|
| Material Design 3 (M3) | [m3.material.io](https://m3.material.io/) | UI 视觉设计系统：色彩、排版、形状、动效、组件 |
| Google Style Guides | [google.github.io/styleguide](https://google.github.io/styleguide/) | 代码编写规范：HTML/CSS、JS/TS、Python、Go、Shell 等 |
| Google Design System Skill | 自定义 Claude Code Skill | 将 M3 + 代码规范融合为 AI 可用的技能文件 |

---

## 目录结构

```
design-skill/
├── google-design-system/
│   └── SKILL.md                    # Claude Code Skill：M3 设计系统 + 代码风格融合指南
│
├── DESIGN_SYSTEM_SUMMARY.md        # M3 设计系统完整摘要文档
├── google-design-system.zip        # Skill 文件打包
│
│  ── 代码风格指南 ──
│
├── javaguide.html                  # Java 风格指南
├── jsguide.html                    # JavaScript 风格指南
├── tsguide.html                    # TypeScript 风格指南
├── htmlcssguide.html               # HTML/CSS 风格指南
├── pyguide.md                      # Python 风格指南
├── cppguide.html                   # C++ 风格指南
├── csharp-style.md                 # C# 风格指南
├── objcguide.md                    # Objective-C 风格指南
├── shellguide.md                   # Shell/Bash 风格指南
├── angularjs-google-style.html     # AngularJS 风格指南
├── jsoncstyleguide.html/xml        # JSON/C 风格指南
├── xmlstyle.html                   # XML 文档格式指南
├── Rguide.md                       # R 语言风格指南
├── vimscriptguide.xml              # Vim Script 风格指南
├── lispguide.xml                   # Common Lisp 风格指南
│
│  ── IDE/编辑器配置 ──
│
├── intellij-java-google-style.xml  # IntelliJ IDEA Java 格式化配置
├── eclipse-java-google-style.xml   # Eclipse Java 格式化配置
├── eclipse-cpp-google-style.xml    # Eclipse C++ 格式化配置
├── google-c-style.el               # Emacs C 语言配置
├── google_python_style.vim         # Vim Python 格式化配置
├── pylintrc                        # Pylint Python 配置
│
│  ── 其他 ──
│
├── shopm3-improved.html            # M3 商店示例页面
├── styleguide.css                  # 通用样式
├── styleguide.xsl                  # XML 样式转换
├── shell.xsl                       # Shell 指南 XSL
├── LICENSE                         # CC-By 3.0 许可证
└── CODE_OF_CONDUCT.md              # 行为准则
```

---

## Material Design 3 资源

### 核心文档

| 文件 | 说明 |
|---|---|
| `DESIGN_SYSTEM_SUMMARY.md` | M3 完整摘要（700+ 行），涵盖色彩、排版、形状、动效、交互状态、设计 Token、组件规范 |
| `google-design-system/SKILL.md` | Skill 文件，将 M3 和代码规范融合为结构化指南 |

### M3 设计体系概要

**色彩系统** — 26+ 命名色彩角色，三层 Token 模型：

```
Reference Token → System Token → Component Token
(md.ref.*)        (md.sys.*)     (md.comp.*)
```

**排版系统** — 30 种文字样式（15 基础 + 15 强调），五大角色：

| 角色 | 用途 | 尺寸变体 |
|---|---|---|
| Display | 英雄区域 | Large / Medium / Small |
| Headline | 章节标题 | Large / Medium / Small |
| Title | 组件标题 | Large / Medium / Small |
| Body | 正文内容 | Large / Medium / Small |
| Label | UI 标签、按钮 | Large / Medium / Small |

**形状系统** — 圆角梯度（4dp → Full），支持形状变形动效。

**动效系统** — 基于物理弹簧的运动模型，Expressive / Standard 两种方案。

**交互状态** — Enabled / Disabled / Hover / Focused / Pressed / Dragged，每种状态要求双重视觉指示器。

---

## 代码风格指南

### 语言覆盖

| 语言 | 文件格式 | 指南 |
|---|---|---|
| Java | HTML | 类命名、Javadoc、格式化规则 |
| JavaScript | HTML | 模块化、Promise/async、编码约定 |
| TypeScript | HTML | 类型注解、接口设计、文件结构 |
| HTML/CSS | HTML | 语义化标签、选择器规范、属性顺序 |
| Python | Markdown | 命名约定、docstring、导入顺序 |
| C++ | HTML | 头文件管理、内存安全、命名 |
| C# | Markdown | PascalCase/camelCase、async 模式 |
| Objective-C | Markdown | Cocoa 命名、注释规范 |
| Shell/Bash | Markdown | 脚本结构、错误处理、命名 |
| JSON/C | HTML/XML | 缩进、注释、结构规范 |
| AngularJS | HTML | 组件模式、依赖注入 |
| R | Markdown | 函数命名、赋值风格 |
| Vim Script | XML | 脚本结构、函数命名 |
| Common Lisp | XML | 格式化、命名约定 |

### 通用规则

| 规则 | 约定 |
|---|---|
| 编码 | UTF-8，无 BOM |
| 缩进 | 2 空格（HTML/CSS/JS/TS/C#）/ 4 空格（Python/Shell） |
| 行宽 | 80 字符（Python/Shell/Go）/ 100 字符（C#） |
| 文件命名 | kebab-case（Web）/ snake_case（Python/Shell）/ PascalCase（C#） |
| TODO | 仅使用 `TODO:` 关键字 |
| 注释 | 解释"为什么"，而非"是什么" |

---

## 设计系统 Skill

`google-design-system/SKILL.md` 是为 **Claude Code** 定制的 Skill 文件，融合了：

1. **Material Design 3** 视觉设计规范（色彩、排版、形状、动效、组件）
2. **Google 代码风格指南**（HTML/CSS、JS/TS、Python、Go、Shell、C# 等）

### 使用场景

- 设计 UI 时：引用 M3 Token（`md.sys.color.primary`），而非硬编码色值
- 编写代码时：遵循对应语言的 Google 代码风格
- 审查代码时：对照代码风格规则检查一致性
- 构建组件时：参考 M3 组件规范（按钮、卡片、导航等）

---

## IDE/编辑器配置

| 文件 | 编辑器 | 语言 |
|---|---|---|
| `intellij-java-google-style.xml` | IntelliJ IDEA | Java |
| `eclipse-java-google-style.xml` | Eclipse | Java |
| `eclipse-cpp-google-style.xml` | Eclipse | C++ |
| `google-c-style.el` | Emacs | C |
| `google_python_style.vim` | Vim | Python |
| `pylintrc` | Pylint | Python |

导入对应配置文件即可在编辑器中自动格式化为 Google 风格。

---

## 许可证

- 代码风格指南：[CC-By 3.0](https://creativecommons.org/licenses/by/3.0/)
- Material Design：[Apache 2.0](https://github.com/material-components/material-components-android/blob/master/LICENSE)

---

## 参考链接

| 资源 | 链接 |
|---|---|
| Material Design 3 | https://m3.material.io/ |
| M3 色彩系统 | https://m3.material.io/styles/color/overview |
| M3 排版系统 | https://m3.material.io/styles/typography/overview |
| M3 组件库 | https://m3.material.io/components |
| M3 设计 Token | https://m3.material.io/foundations/design-tokens/overview |
| Google 代码风格 | https://google.github.io/styleguide/ |
| Material Theme Builder | https://material-foundation.github.io/material-theme-builder/ |
