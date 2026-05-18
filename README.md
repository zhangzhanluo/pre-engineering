# PRE Engineering Skill / 臭皮匠工程 Skill

[English](#english) | [中文](#chinese)

---

<a id="english"></a>

## English

"Three humble cobblers surpass one Zhuge Liang" (三个臭皮匠，顶个诸葛亮) — A Chinese proverb reminding us that multiple ordinary agents, working together, can outperform a single genius. PRE Engineering is the embodiment of this wisdom.

The three agent roles — **P**lan, **R**eview, **E**xecute — form the acronym **PRE**. This also echoes "preparation": this skill provides the essential materials for a project to take flight.

### What It Does

When triggered, this skill detects the user's language (Chinese or English), confirms with the user, then guides through a 2-step interactive process to collect project requirements, generating 5 core documents:

1. **Project Goals Document** — Requirements and constraints (only humans can modify)
2. **Collaboration Log** — Agent communication medium with initial PLN_WAIT entry
3. **Planner Guide** — Planner role behavior specification
4. **Executor Guide** — Executor role behavior specification
5. **Reviewer Guide** — Reviewer role behavior specification

Document names adapt to the selected language.

### Installation

**Recommended** — use `npx skills add`:

```bash
npx skills add zhangzhanluo/pre-engineering
```

Or manually: place `skills/pre-engineering/` into your Claude Code skills directory.

### Trigger Conditions

- Initialize a multi-agent collaborative project
- Set up PRE system / Plan-Review-Execute workflow
- Create Planner/Executor/Reviewer guide documents
- Start a collaboration log-driven multi-agent workflow
- Express multi-agent collaboration intent (even without explicitly mentioning PRE)

### File Structure

```
skills/pre-engineering/
├── SKILL.md                          ← Skill definition
├── README.md                         ← This file (bilingual)
└── references/
    ├── en/                           ← English templates
    │   ├── planner-guide-template.md
    │   ├── executor-guide-template.md
    │   ├── reviewer-guide-template.md
    │   ├── collaboration-log-format-reference.md
    │   └── state-system-reference.md
    └── zh/                           ← Chinese templates (中文模板)
        ├── 规划者指导模板.md
        ├── 执行者指导模板.md
        ├── 审核者指导模板.md
        ├── 协作日志格式参考.md
        └── 状态体系参考.md
```

### How to Use

1. **Install**: `npx skills add zhangzhanluo/pre-engineering` (recommended) or copy the directory manually
2. **Trigger**: Express multi-agent collaboration intent in Claude Code
3. **Language detection**: Auto-detects your language and confirms with you
4. **Requirement collection**: 2-step interactive process
5. **Document generation**: 5 `.pre/{PROJECT_NAME}/` collaboration documents generated (with project-specific absolute paths)
6. **Launch agents**: Start three agents with `/loop` commands (using absolute paths — no directory switching needed)
7. **Job IDs**: Agents automatically record their loop job IDs in the collaboration log

### Key Mechanisms

- **Language Detection**: Auto-detects Chinese/English from user input
- **Loop Prevention**: 3 consecutive rejections trigger blockage → PLN_WAIT
- **Version Recording**: Reviewer manages git commit after execution reviews (no stash — direct commit)
- **Code Conciseness**: Reviewer enforces strict quality standards

### Acknowledgements

Thanks to [@import-wang](https://github.com/import-wang) for the creative inspiration and suggestions during development.

### Author

张战罗 (zhangzhanluo) — zhangzhanluo@outlook.com

---

<a id="chinese"></a>

## 中文

"三个臭皮匠，顶个诸葛亮" — 多个平凡智能体协作，能胜过单一天才智能体。臭皮匠工程正是这一中国谚语的实践。

三个角色的英文名——**P**lan（规划）、**R**eview（审核）、**E**xecute（执行）——首字母组成了 **PRE**。同时，PRE 也是 preparation（准备）的缩写，暗含本 skill 的定位：为项目起飞提供必要的准备材料。

### 功能说明

触发后，本 skill 自动检测用户语言（中文或英文）并与用户确认，通过2步交互流程收集项目需求，生成5份核心文档：

1. **项目目标文档** — 功能需求与技术约束（仅人工可修改）
2. **协作日志** — 智能体间通信媒介，含初始 PLN_WAIT 条目
3. **规划者指导** — 规划者角色行为规范
4. **执行者指导** — 执行者角色行为规范
5. **审核者指导** — 审核者角色行为规范

文档名称根据所选语言自动适配。

### 安装

**推荐方式** — 使用 `npx skills add` 安装：

```bash
npx skills add zhangzhanluo/pre-engineering
```

或手动将 `skills/pre-engineering/` 目录放入 Claude Code skills 目录中。

### 触发条件

- 初始化多智能体协同项目
- 设置 PRE 系统 / 规划-审核-执行工作流
- 创建规划者/执行者/审核者指导文档
- 启动协作日志驱动的多智能体工作流
- 表达多智能体协同意图（即使未明确提到 PRE）

### 文件结构

```
skills/pre-engineering/
├── SKILL.md                          ← Skill 定义
├── README.md                         ← 本文件（中英双语）
└── references/
    ├── en/                           ← 英文模板
    │   ├── planner-guide-template.md
    │   ├── executor-guide-template.md
    │   ├── reviewer-guide-template.md
    │   ├── collaboration-log-format-reference.md
    │   └── state-system-reference.md
    └── zh/                           ← 中文模板
        ├── 规划者指导模板.md
        ├── 执行者指导模板.md
        ├── 审核者指导模板.md
        ├── 协作日志格式参考.md
        └── 状态体系参考.md
```

### 使用方法

1. **安装**：`npx skills add zhangzhanluo/pre-engineering`（推荐）或手动复制目录
2. **触发**：在 Claude Code 中输入多智能体协同意图
3. **语言检测**：自动检测你的语言并与你确认
4. **需求收集**：2步交互流程
5. **文档生成**：生成5份 `.pre/{PROJECT_NAME}/` 协作文档（含项目专属绝对路径）
6. **启动智能体**：用 `/loop` 命令启动三个智能体（使用绝对路径，无需切换目录）
7. **Job ID**：智能体自动将循环任务 job ID 记录到协作日志

### 核心机制

- **语言检测**：从用户输入自动检测中/英文
- **循环阻断**：连续驳回3次触发阻断 → PLN_WAIT
- **版本记录**：审核者审核通过后直接 git commit（不使用 stash）
- **代码简洁性**：审核者严格审核，大胆驳回冗余和膨胀

### 致谢

感谢 [@import-wang](https://github.com/import-wang) 提供的创意启发和过程中的建议。

### 作者

张战罗 (zhangzhanluo) — zhangzhanluo@outlook.com