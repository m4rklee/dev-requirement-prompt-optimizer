# Question Maps

Use this reference only when the project domain changes what questions matter most.

Ask at most 3 questions in one round. Choose the highest-impact questions first.

## Web App Or Website

Priority questions:

- Is this a marketing site, dashboard, content product, internal tool, or full web app?
- Should it be desktop-first, mobile-first, or equally responsive?
- Does it need authentication, persistence, admin roles, or external APIs?

Recommended defaults:

- responsive layout
- basic empty/loading/error states
- persistent settings only when they affect repeat usage

## Mobile App

Priority questions:

- iOS, Android, or cross-platform?
- What is the primary on-the-go interaction?
- Does the app need offline behavior, push notifications, background processing, or device permissions?

Recommended defaults:

- platform-native patterns
- explicit permission prompts only when required
- graceful offline fallback if the app depends on network access

## Desktop App

Priority questions:

- Which OS and minimum version?
- Is this a windowed app, menu-bar app, tray app, or background utility?
- What system integrations matter: keyboard hooks, clipboard, filesystem, notifications, mic, camera?

Recommended defaults:

- native UI components where possible
- explicit first-run permissions guidance
- remembered settings for user-visible preferences

## Backend Service Or API

Priority questions:

- Is this synchronous API, async worker, scheduled job, or event-driven service?
- What are the inputs, outputs, and consumers?
- What matters most: latency, reliability, cost, auditability, or throughput?

Recommended defaults:

- structured error responses
- configuration via env vars
- logging around external integrations and failures

## AI Feature Or Agent Workflow

Priority questions:

- Is the model generating, classifying, extracting, refining, or routing?
- What content must be preserved exactly, and what may be transformed?
- Which model/API/provider constraints matter: cost, latency, privacy, streaming, tool use?

Recommended defaults:

- conservative post-processing rules
- explicit system behavior boundaries
- fallback behavior when model output is missing, delayed, or malformed

## Automation Or Internal Tool

Priority questions:

- What manual workflow is this replacing or speeding up?
- Who runs it, how often, and in what environment?
- What errors are acceptable versus unacceptable?

Recommended defaults:

- minimize setup steps
- surface progress and failures clearly
- avoid adding configuration unless it directly affects repeated use

## Data Workflow Or Evaluation Pipeline

Priority questions:

- What are the data sources, formats, and expected outputs?
- Is this one-off analysis, recurring evaluation, or production pipeline?
- What matters most: reproducibility, speed, interpretability, or benchmark comparability?

Recommended defaults:

- explicit input/output paths or interfaces
- deterministic settings where possible
- saved artifacts for metrics, logs, and intermediate results when useful
