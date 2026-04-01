# Output Templates

Use these templates when you want consistent, low-friction outputs.

Keep them compact. Adapt them to the user's context instead of copying mechanically.

## Template A: Guided Discovery Turn

```markdown
Idea Restatement

[1-2 sentence summary of the user's current idea]

Focus Questions

1. [highest-impact question]
2. [second highest-impact question]
3. [optional third question]
```

## Template B: Interim Synthesis

```markdown
Current Direction

- Decided: [short summary]
- Assumptions: [short summary]
- Still open: [only if important]

[Either ask the next small batch of questions, or say you have enough to draft the final prompt.]
```

## Template C: Prompt Strengthening

```markdown
Strengths

- [what should be preserved]

Gaps

- [ambiguities, missing constraints, likely failure points]

Optimized Prompt

[rewritten final prompt]
```

## Template D: Final Output From Rough Idea

```markdown
Assumptions

- [only include if still-open low-risk details were chosen by default]

Final Development Prompt

Please implement [product/feature] with the following requirements:

1. [product goal and scope]
2. [inputs, outputs, and success conditions]
3. [trigger and state flow]
4. [core logic or workflow rules]
5. [data/content structure, if relevant]
6. [UI/UX behavior, if relevant]
7. [integration or model/API behavior, if relevant]
8. [permissions/privacy/security constraints, if relevant]
9. [edge-case handling and guardrails]
10. [settings/persistence, if relevant]
11. [testing/evaluation/acceptance criteria, if relevant]
12. [build, packaging, deployment, or delivery constraints, if relevant]

Why This Is Execution-Ready

- [optional short explanation]
```

Only keep the sections that matter for the user's domain.

## Template E: Assumption Style

Good assumption phrasing:

- Assume the default language is Simplified Chinese unless the user asks for multilingual onboarding.
- Assume the app should remember the last selected mode in local settings.
- Assume native system components are preferred unless a custom UI is necessary.

Avoid vague assumption phrasing:

- I made some reasonable assumptions.
- Missing details were filled in as needed.
- I expanded the spec to make it more complete.
