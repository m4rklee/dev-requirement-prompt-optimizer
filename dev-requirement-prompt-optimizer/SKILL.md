---
name: dev-requirement-prompt-optimizer
description: Turn rough product ideas or incomplete build requests into implementation-ready development prompts through guided multi-turn clarification, sensible defaults, and structured prompt rewriting.
---

# Development Requirement Prompt Optimizer

Use this skill when the user has any of these needs:

- a vague product or feature idea that needs to become a build-ready prompt
- an existing development prompt that needs to be strengthened
- a request to identify missing constraints, edge cases, or delivery requirements
- a request to make a prompt more executable for coding agents or engineers

This skill is designed for real conversations where the user may start with only a half-formed idea.

## Main Objective

Turn the user's current idea into a prompt that is:

- clear enough to implement
- constrained enough to avoid drift
- flexible enough to preserve user intent
- structured enough to be reused as an execution prompt

Do not optimize for length. Optimize for execution quality.

## Generality Rule

This skill must remain domain-general.

- Do not overfit the workflow to the last example task.
- Treat examples in this skill as illustrative patterns, not default product assumptions.
- Only include UI, model, API, data, deployment, or packaging sections if they are relevant to the user's request.
- Adapt the final prompt structure to the domain instead of forcing one universal section order.
- Prefer reusable requirement language over domain-specific wording unless the user explicitly wants domain-specific language.

## Operating Modes

Choose one mode quickly based on the user's input.

### Mode 1: Guided Discovery

Use when the user starts with a rough idea, partial concept, or incomplete brief.

Goal: progressively discover the missing requirements through short question rounds, then produce the final implementation-ready prompt.

### Mode 2: Prompt Strengthening

Use when the user already has a prompt or requirement draft.

Goal: preserve what is strong, identify the implementation gaps, and rewrite it into a sharper execution prompt.

### Mode 3: Hybrid

Use when the user has a draft prompt, but it is still too incomplete to rewrite confidently in one pass.

Goal: critique what exists, ask a few targeted questions, then produce the final prompt.

## Default Assumption

Assume the user does not have a polished specification unless they clearly do.

Your role is to help the user think, not to wait for them to think everything through alone.

## High-Level Workflow

Follow this workflow in order:

1. Classify the maturity of the input.
2. Restate the idea briefly to confirm understanding.
3. Identify the highest-impact unknowns.
4. Ask at most 3 targeted questions in one round.
5. After each user reply, synthesize what is decided, assumed, and still open.
6. Stop discovery once the implementation direction is stable.
7. Produce the final optimized development prompt.
8. Optionally include a short note on assumptions or remaining risks.

## Maturity Classification

Internally classify the input into one of these buckets:

- Seed idea: the user has only a general concept
- Shaped idea: the user knows the product and flow, but many constraints are missing
- Draft prompt: the user already has a requirements draft
- Near-final prompt: only refinement or gap-checking is needed

This classification is for your own steering. You do not need to announce it every time.

## Guided Discovery Rules

In guided discovery, your job is to ask the fewest questions that unlock the most implementation clarity.

### Questioning Rules

- Ask at most 3 questions per round.
- Ask only questions that materially change implementation direction, scope, or architecture.
- Prefer concrete framing over broad brainstorming.
- When useful, offer 2-3 likely options instead of an empty question.
- Allow the user to answer with "you decide".
- If a detail is low-risk, choose a sensible assumption and label it clearly.
- If the user is unsure, recommend a default instead of stalling the conversation.
- Do not force exhaustive specification gathering before drafting.
- Stop asking once the next implementation step is obvious enough to draft against.

### Priority Order

Ask about missing details in roughly this order:

1. Product target: what are we building, for whom, and on which platform?
2. Core interaction: what starts the flow, what happens during it, and what ends it?
3. Success outcome: what should the user end up with?
4. Important constraints: OS version, framework, privacy, latency, online/offline, API dependencies, deployment environment.
5. Settings and persistence: what needs to be configurable or remembered?
6. UX detail with engineering impact: layout, animation, visibility, real-time feedback, transitions, accessibility.
7. Delivery constraints: build method, packaging, runtime target, deployment, signing, install/run expectations.

### Recommended Defaults

When the user is early-stage and undecided, prefer to recommend defaults such as:

- a sensible target platform based on the idea
- an explicit first-run default behavior
- minimal but sufficient configuration
- conservative post-processing instead of aggressive AI rewriting
- platform-native implementation when feasible
- a short list of supported variants instead of wide-open customization

## Prompt Strengthening Rules

When the user already has a prompt, improve it using these rules:

1. Preserve the user's intent and strong constraints.
2. Do not flatten distinctive product thinking into generic spec language.
3. Replace vague adjectives with observable behavior.
4. Convert implied workflow into explicit state transitions.
5. Add defaults where omission creates ambiguity.
6. Separate hard constraints from preferences when useful.
7. Name preferred technical approaches only where that reduces drift.
8. Add predictable platform-specific edge-case handling.
9. Tighten LLM or automation instructions so they do not overreach.
10. End with build, packaging, or delivery constraints.
11. Include explicit assumptions for unresolved low-risk details.

## What Strong Development Prompts Usually Get Right

Strong prompts usually do most of the following:

1. State the product in one concrete sentence.
2. Break the work into numbered requirements.
3. Specify trigger, intermediate, and completion behavior.
4. Define default behavior so the feature works on first run.
5. Include only the implementation anchors that matter architecturally.
6. Describe UI behavior in engineering-relevant terms when needed.
7. Define settings, persistence, and menu/configuration surfaces.
8. Call out dangerous edge cases and state restoration behavior.
9. Constrain AI-assisted behavior so it improves accuracy without changing intent.
10. Include delivery requirements such as build, package, signing, or deployment.

## Common Weaknesses To Fix

Look for these gaps in weak prompts:

- no concrete product goal
- no platform or runtime scope
- no user flow or event order
- no default settings
- no persistence rules
- no distinction between real-time state and final state
- no failure prevention or edge-case handling
- no integration boundary definition
- no delivery or acceptance constraints
- overly broad instructions like "make it better" or "optimize the text"

## Conversation State

Maintain this lightweight internal model while guiding the user:

- Confirmed: what the user has clearly chosen
- Open: what is still ambiguous and important
- Assumptions: what you are choosing to keep momentum

Do not dump this state every turn unless it helps the user.

## When To Stop Asking Questions

Stop discovery and draft the final prompt once these are sufficiently clear:

- the product or feature goal
- the main user flow
- the target platform or runtime
- the key integrations or constraints
- the expected output or delivery form

If only minor details remain open, proceed with explicit assumptions.

Do not keep asking questions after the implementation path is already stable.

## Do Not Over-Interview

Do not turn this skill into a generic discovery questionnaire.

Avoid extra question rounds when:

- the remaining unknowns are low-risk
- the user has already signaled "you decide"
- the likely answers would not change architecture or scope
- a reasonable default is clearly better than another round of clarification
- the user is asking for momentum rather than perfect specification

When in doubt, draft with labeled assumptions instead of blocking.

## Domain Adaptation

Adapt your questions and final prompt structure to the type of build request.

If needed, read [question-maps.md](references/question-maps.md) for domain-specific question priorities.
If the request has meaningful UI or interaction complexity, also read [ui-spec-patterns.md](references/ui-spec-patterns.md).

Typical domains:

- web app or website
- mobile app
- desktop app
- backend service or API
- AI feature or agent workflow
- automation or internal tool
- data workflow or evaluation pipeline

## Output Contracts

Use the output contract that matches the mode.

### Contract A: Guided Discovery

Use this structure during the conversation:

1. Idea Restatement
2. Focus Questions
3. Interim Synthesis
4. Final Prompt

### Contract B: Prompt Strengthening

Use this structure:

1. Strengths
2. Gaps
3. Optimized Prompt

If needed, read [output-templates.md](references/output-templates.md) for example phrasing and reusable structures.

## Section Selection Rule

Build the final prompt from relevant sections rather than forcing the same outline every time.

Common section candidates include:

- product goal and scope
- inputs, outputs, and success conditions
- trigger and state flow
- core logic or workflow rules
- data model or content structure
- UI/UX behavior
- integrations, APIs, or model behavior
- permissions, privacy, or security constraints
- edge cases and guardrails
- settings and persistence
- testing, evaluation, or acceptance criteria
- build, packaging, deployment, or delivery constraints

Pick the smallest set of sections that makes the prompt executable.

## Final Prompt Requirements

The final optimized development prompt should usually:

- open with one-sentence product intent
- use numbered requirements
- define the core user flow
- include first-run defaults
- define persistence, integrations, and guardrails where relevant
- specify critical UX behavior when it changes implementation
- call out known platform or domain edge cases
- end with build, packaging, deployment, or delivery constraints

Not every prompt needs every section above. Keep only the sections that materially affect execution.

If UI or interaction quality materially affects the product, the final prompt should also specify:

- the main screen or page structure
- the key interaction loop, including trigger, in-progress, success, and failure states
- what feedback is visible to the user at each important state
- whether animations are functional, decorative, or signal-driven
- any important sizing, placement, hierarchy, or responsiveness constraints
- what should happen after the primary action completes

## Compression Rule

Do not add detail just to sound smart or comprehensive.

Add detail only when it improves:

- implementation clarity
- scope control
- risk reduction
- testability
- delivery quality

## Style Rules For Guided Questions

- Ask in plain language, not spec jargon.
- Prefer "Which is closer?" over "What do you want?" when the user is early-stage.
- One question should unlock multiple downstream decisions when possible.
- Offer recommended defaults when the user seems undecided.
- Keep momentum and reduce decision fatigue.
- Avoid asking for preference when the tradeoff is weak and a default will do.

## Style Rules For Final Prompts

- Prefer direct verbs: implement, detect, store, restore, display, inject, refine, validate, package.
- Prefer exact nouns over abstractions.
- Prefer measurable behavior over adjectives.
- Prefer explicit before/after behavior around side effects.
- Prefer concise numbered sections over dense prose.
- Use "must" for hard constraints and "preferred" for directional guidance.

## UI And Interaction Writing Rules

When the product has a meaningful interface, do not stop at visual adjectives like "clean", "modern", or "intuitive".

Write UI and interaction requirements in a way that an engineer or designer could directly act on.

### What To Capture

Capture the highest-value interaction details such as:

- the primary screens or panels
- the order in which the user moves through them
- the primary call to action on each screen
- the system states the user can observe
- how transitions reveal progress or completion
- how failure, waiting, and retry states appear
- which UI details are critical enough to constrain

### Strong UI Spec Patterns

Prefer writing things like:

- "show a results view after submission"
- "separate learning mode from practice mode"
- "display recording states: idle, recording, transcribing, feedback ready"
- "expand the panel width as transcript length grows"
- "show retry guidance if microphone permission is denied"

Avoid weak UI language like:

- "make the interface modern"
- "add a nice animation"
- "show a beautiful dashboard"
- "make it user-friendly"

### State-Driven Interaction Rule

When there is a core user action, describe the full state loop whenever possible:

- what starts the action
- what the user sees while it is in progress
- what indicates success
- what indicates failure
- what happens next

### Real Feedback Rule

If the UI includes dynamic feedback, specify whether it must reflect real system state or real user input.

Examples:

- real waveform driven by audio level
- actual transcript updates from speech recognition
- explicit loading state while AI feedback is pending

Do not allow placeholder or fake dynamic behavior unless the user explicitly wants a mock-only prototype.

### Constraint Rule

Only specify measurements, component types, motion timings, or layout constraints when they materially improve reproducibility or reduce implementation drift.

Good reasons to constrain:

- platform-native behavior matters
- visual placement affects usability
- animation timing affects perceived responsiveness
- panel sizing changes with content
- a component must avoid known platform quirks

### Progressive Disclosure Rule

For complex products, prefer revealing the next action at the right time instead of putting every control on screen at once.

If this matters for the product, say so explicitly in the final prompt.

## Quality Bar

Before finalizing, sanity-check the resulting prompt:

- Could an engineer start implementation without guessing the core flow?
- Are the most dangerous ambiguities removed?
- Are defaults defined where first-run behavior matters?
- Are integrations and post-processing behaviors constrained appropriately?
- Does the prompt preserve the user's intent instead of replacing it?
- Is the prompt specific enough to build, but not bloated with low-value detail?

## Final Self-Check

Before using the final prompt, quickly check:

- Did I choose the right mode: guided discovery, strengthening, or hybrid?
- Did I ask only the minimum useful questions?
- Did I keep the prompt domain-appropriate instead of forcing a template?
- Did I label assumptions clearly where I moved forward without more input?
- Did I include UI, data, security, testing, or deployment sections only when relevant?
- Would a builder know what to implement first without another clarification round?

## Good Behavior Patterns

When a source prompt is already good, preserve and emulate patterns like:

- clear end-to-end user loop
- architecture-relevant technical preferences without overprescribing everything
- explicit defaults and supported variants
- UI details that are specific enough to reproduce
- distinction between real signal-driven behavior and placeholder behavior
- edge-case handling around platform quirks
- conservative AI correction policies
- delivery constraints at the end

## Default Final Prompt Skeleton

Use this as a section bank, not a mandatory fixed outline:

```markdown
Please implement [product/feature] with the following requirements:

1. Product goal and scope
2. Inputs, outputs, and success conditions
3. Trigger and state flow
4. Core logic or workflow rules
5. Data model or content structure
6. UI/UX behavior
7. Integration, API, or model behavior
8. Permissions, privacy, or security constraints
9. Edge-case handling and guardrails
10. Settings and persistence
11. Testing, evaluation, or acceptance criteria
12. Build, packaging, deployment, or delivery constraints
```

Only keep the sections that matter for the user's domain.
