# Dev Requirement Prompt Optimizer

> A Codex skill that turns rough product ideas and incomplete software requests into implementation-ready development prompts.

Dev Requirement Prompt Optimizer 是一个面向 Codex/AI coding workflow 的本地 skill。它通过多轮澄清、需求结构化、UI 交互补全和执行提示词生成，将“粗略想法”转化为可以直接交给 coding agent 实现的高质量开发任务描述。

## Highlights

- **Prompt-to-spec workflow**: 将模糊需求整理为目标、范围、约束、接口、测试和验收标准。
- **Guided clarification**: 针对缺失信息进行多轮追问，避免 agent 过早实现。
- **Implementation-ready output**: 输出可直接用于 Codex/Claude/Cursor 等 coding agent 的开发提示词。
- **UI-aware refinement**: 对前端体验、交互状态、布局和验收场景给出结构化补充。
- **Reusable skill package**: 可安装到 `~/.codex/skills/` 中作为本地 Codex skill 使用。

## How It Works

```text
Rough idea / incomplete request
        |
        v
Skill instructions
        |
        +--> clarify missing intent
        +--> normalize feature scope
        +--> enrich UI / API / data details
        +--> add tests and acceptance criteria
        |
        v
Implementation-ready prompt
```

## Features

| Module | Description |
|---|---|
| **Clarification Flow** | 从目标、用户、范围、约束、数据流和边界条件补齐需求。 |
| **Prompt Improvement** | 对已有草稿做结构化增强，而不是重写成固定模板。 |
| **UI Spec Patterns** | 补充页面布局、状态、交互反馈和前端验收标准。 |
| **Question Maps** | 根据需求类型选择高价值问题，减少无效追问。 |
| **Output Templates** | 生成适合 coding agent 执行的最终 prompt。 |

## Tech Stack

- **Runtime**: Codex local skill system
- **Format**: Markdown instructions, references, examples
- **Install Target**: `~/.codex/skills/dev-requirement-prompt-optimizer`

## Install

使用 Codex skill installer：

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo m4rklee/dev-requirement-prompt-optimizer \
  --path dev-requirement-prompt-optimizer
```

或手动复制目录：

```bash
cp -R dev-requirement-prompt-optimizer ~/.codex/skills/
```

安装后重启 Codex，使 skill 列表重新加载。

## Usage

触发方式示例：

```text
帮我把这个粗略需求整理成可执行的开发 prompt：我要做一个能上传 PDF 并自动生成 PPT 的网页工具。
```

或：

```text
用 dev-requirement-prompt-optimizer 优化下面这个需求，让 coding agent 可以直接实现。
```

## Project Structure

```text
dev-requirement-prompt-optimizer/
  SKILL.md                       # Main skill instructions
  agents/openai.yaml             # Agent config example
  references/
    output-templates.md          # Final prompt templates
    question-maps.md             # Clarification question maps
    ui-spec-patterns.md          # UI and interaction patterns
VERSION
INSTALL.md
RELEASE_NOTES.md
README.md
```

## Notes

- 该仓库是 Codex skill，不是独立 Web 服务。
- 输出质量依赖输入需求的清晰度；对于高风险或高成本需求，仍建议人工确认关键决策。
- Skill 会帮助补全工程细节，但不会替代产品负责人对业务目标的判断。

## Roadmap

- Add more examples for backend, frontend and agent projects.
- Add domain-specific question maps.
- Add before/after prompt comparison samples.
- Add automated validation checklist for final prompts.
