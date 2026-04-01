# Install

This release installs the `dev-requirement-prompt-optimizer` skill into a Codex skills directory.

## Quick Install

Run:

```bash
bash install.sh
```

This copies the bundled `dev-requirement-prompt-optimizer/` folder into:

```bash
$HOME/.codex/skills/
```

## Manual Install

1. Extract the release archive.
2. Copy `dev-requirement-prompt-optimizer/` into your Codex skills directory.
3. Confirm the final path is:

```bash
$HOME/.codex/skills/dev-requirement-prompt-optimizer/
```

## Included Files

- `SKILL.md`
- `agents/openai.yaml`
- `references/output-templates.md`
- `references/question-maps.md`
- `references/ui-spec-patterns.md`

## Notes

- This release is designed to be reusable across multiple project types.
- The UI reference is optional and should only be used when the task has meaningful interaction or interface complexity.
