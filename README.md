# dev-requirement-prompt-optimizer

A Codex skill for turning rough product ideas or incomplete software requests into implementation-ready development prompts.

## What It Does

This skill helps with:

- guided multi-turn clarification from rough idea to final execution prompt
- strengthening weak or incomplete development prompts
- hybrid prompt improvement when a draft exists but still needs key clarification
- domain-aware prompt structuring instead of forcing one rigid template
- optional UI and interaction specification refinement when interface quality matters

## Skill Path

Install this skill into:

```text
~/.codex/skills/dev-requirement-prompt-optimizer
```

## Repository Structure

```text
dev-requirement-prompt-optimizer/
  SKILL.md
  agents/openai.yaml
  references/
    output-templates.md
    question-maps.md
    ui-spec-patterns.md
VERSION
INSTALL.md
RELEASE_NOTES.md
```

## Install From GitHub

If your Codex environment includes the system skill installer, install with:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo m4rklee/dev-requirement-prompt-optimizer \
  --path dev-requirement-prompt-optimizer
```

After installation:

```text
Restart Codex to pick up new skills.
```

## Version

Current release: `1.0.0`
