# UI Spec Patterns

Use this reference when the product's quality depends on interface behavior, interaction flow, dynamic feedback, or state visibility.

The goal is to help turn vague UI wishes into implementation-ready prompt language.

This file is optional and domain-specific. Do not use it when the request has no meaningful user interface.

## Core Principle

A strong UI section does not just describe how the interface should look.

It describes:

- what the user sees
- when they see it
- why it changes
- what system state it represents
- what they can do next

## The Five Layers Of Good UI Prompting

When UI matters, try to cover these layers in the final prompt.

### 1. Screen Structure

Specify the major screens, panels, or regions.

Examples:

- landing page with scenario selection
- practice page with a single active prompt and recording CTA
- results panel with transcript and coaching feedback
- bottom floating panel during voice capture
- admin table with filter controls and bulk actions
- job status page with queue state and retry controls

Weak:

- "create a nice page"

Strong:

- "use a two-column practice layout with the current prompt on the left and transcript/feedback on the right"

### 2. Interaction Loop

Describe the full loop around the main user action.

Examples:

- tap record -> recording state -> stop -> transcribing -> feedback ready
- choose scenario -> study sample dialogue -> start speaking practice -> review results
- hold key -> capture audio -> release -> refine text -> inject result
- submit form -> validating -> saving -> success banner -> return to list
- start job -> queued -> running -> completed or failed -> retry or inspect logs

If there is one thing to preserve from strong UI prompts, preserve the loop.

### 3. State Visibility

Specify what the user can observe at each important state.

Common state categories:

- idle
- active/in progress
- loading/processing
- success/ready
- partial failure
- retry

Examples:

- "show a visible recording state while the microphone is active"
- "display the recognized transcript before feedback appears"
- "show a refining status while the LLM response is pending"
- "show validation errors inline before allowing submission"
- "display job status and last updated time while processing continues"

### 4. Dynamic Behavior

When the interface moves or changes over time, specify whether the behavior is:

- signal-driven
- content-driven
- transition-driven

Signal-driven examples:

- waveform size reflects real audio input
- progress indicator reflects actual generation progress
- status chip reflects actual backend job state

Content-driven examples:

- transcript area grows as text becomes longer
- result card expands when detailed feedback is shown
- table height expands when filters reveal more rows

Transition-driven examples:

- panel enters with a short spring animation
- results reveal after transcription completes
- confirmation drawer opens after a destructive action is requested

Avoid asking for animation without purpose.

### 5. Failure Experience

A usable interface specifies what happens when something goes wrong.

Common failure states to define:

- permission denied
- network delay
- empty input
- malformed model output
- unsupported browser/device capability

Examples:

- "preserve the user's transcript if feedback generation fails"
- "show a retry action if recording permission is denied"
- "show a non-blocking error state if transcription fails"
- "preserve form input if save fails"
- "show retry or inspect-log actions if a background job fails"

## When To Add Concrete Measurements

Concrete measurements are worth adding when they prevent drift or matter to usability.

Good cases:

- floating overlays
- compact panels
- controls that must stay visible
- content areas that resize with text
- animation timings that define responsiveness

Do not over-measure ordinary pages unless the layout is genuinely important to product quality.

## When To Name Specific UI Primitives

Name a concrete UI primitive when:

- platform behavior matters
- implementation choice changes user experience
- the component solves a known system-level problem

Examples:

- nonactivating floating panel
- capsule-shaped bottom overlay
- browser microphone permission flow
- transcript review card
- multi-step setup wizard
- server-side paginated table

Do not name low-value implementation details that do not affect UX outcomes.

## Writing Moves That Upgrade Weak UI Prompts

Replace these:

- "modern UI"
- "nice animations"
- "intuitive experience"
- "real-time feel"

With these:

- "clearly separate study mode from practice mode"
- "show explicit states: idle, recording, transcribing, feedback ready"
- "use animation only for entering practice mode and revealing feedback"
- "keep the primary action visually dominant on the practice screen"

## Reusable UI Question Prompts

Use these when you need to sharpen UI requirements in guided discovery.

- What are the 2 to 4 main screens or states the user moves through?
- What is the single primary action on the most important screen?
- What should the user see while the system is listening, processing, or waiting?
- After the core action completes, should the product continue the flow or switch into review mode?
- Are there any interface details that must be precise, such as placement, resizing, motion, or responsiveness?
- Should dynamic visuals reflect real user/system state, or are mock visuals acceptable for the prototype?
- If this is an internal tool, what must remain visible to support trust, auditability, or operator control?

## Reusable UI Requirement Snippets

Use or adapt snippets like these in final prompts.

### Screen Separation

- "Clearly separate learning mode from active practice mode."
- "Keep the practice screen focused on one primary task at a time."

### State Visibility

- "Display explicit user-visible states: idle, recording, processing, ready, and retry."
- "Show the recognized transcript before or alongside the generated feedback."

### Post-Action Experience

- "After each answer, switch to a review-oriented results view instead of immediately continuing the conversation."
- "After submission, preserve the user's answer and reveal structured feedback in place."

### Dynamic Feedback

- "Use real input-driven feedback where possible rather than decorative placeholder animation."
- "Expand or collapse content areas smoothly as transcript and feedback length change."

### Error Handling

- "Provide clear retry actions for microphone, transcription, and feedback failures."
- "Preserve the user's current attempt whenever possible instead of resetting the flow."
- "Preserve unsaved form state whenever possible if submission fails."
- "Show operators what failed, what succeeded, and what action is available next."
