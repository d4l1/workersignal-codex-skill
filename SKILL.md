---
name: workersignal-codex-connector
description: Capture, redact, preview, and optionally send WorkerSignal work signals from Codex sessions or local AI work summaries. Use when a user asks to create a WorkerSignal signal, prepare a Codex connector signal, or summarize AI work activity without exposing private prompts, code, credentials, client names, project names, or sensitive personal data.
---

# WorkerSignal Codex Connector

## Core Rule

Create safe work signals, not transcripts. Never send private prompts, private code, credentials, internal project names, client names, third-party personal data, or NDA material. Every signal must be previewed before sending, and every send requires explicit user approval.

## Workflow

1. Identify a candidate work signal from a user-approved summary.
2. Redact secrets, emails, phones, tokens, private domains, client names, and internal names.
3. Convert the work into a compact signal with title, summary, source, AI tools, technical tools, categories, and `private_pending_review` visibility.
4. Show the preview to the user.
5. Send only when the user explicitly approves.
6. Leave publication to the WorkerSignal web approval flow.

## Signal Shape

```json
{
  "title": "CRM workflow automation",
  "summary": "Built and debugged an approved CRM workflow involving stage updates, notifications, and backend validation.",
  "source": "codex",
  "ai_tools": ["Codex"],
  "technical_tools": ["CRM", "Notifications", "REST API"],
  "categories": ["CRM automation", "Backend integrations"],
  "visibility": "private_pending_review"
}
```

## Capture Guidance

- Prefer a user-written or user-confirmed summary over raw session text.
- Use `source: "codex"` for Codex work and include other AI tools only if the user confirms them.
- Keep summaries outcome-focused: problem type, tools, technical area, complexity, and result.
- Generalize client/project references, for example "a private CRM migration" instead of a real client or internal project name.
- Do not claim verification. Use private pending review unless the WorkerSignal web flow later marks evidence public.

## References

Read `references/signal-policy.md` when deciding whether content is safe to capture or whether a preview should be blocked.
