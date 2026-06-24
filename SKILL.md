---
name: workersignal-ai-connector
description: Capture, redact, preview, and optionally send WorkerSignal proof-of-work signals from Codex, Claude, Cursor, or local AI work summaries. Use when a user asks to create a WorkerSignal signal, use WorkerSignal capture/contact/preview/send/update/ping/disconnect flows, prepare an AI connector signal, or summarize AI work activity without exposing private prompts, code, credentials, client names, or sensitive project details.
---

# WorkerSignal AI Connector

## Core Rule

Create safe work signals, not transcripts. Never publish or send private prompts, private code, credentials, internal project names, client names, third-party personal data, or NDA material. Every signal and contact payload must be previewed before sending, and every send requires explicit user approval.

## Quick Workflow

1. Identify the candidate work signal from the user-approved session summary.
2. Redact secrets, emails, phones, tokens, private domains, client names, and internal names.
3. Convert the work into a compact signal with title, summary, source, AI tools, technical tools, categories, and `private_pending_review` visibility.
4. Show the preview to the user.
5. Ask whether the user wants to add public contact information for their WorkerSignal profile.
6. Send signals or contact details only when the user explicitly approves the exact preview.
7. Leave publication to the WorkerSignal web approval flow.

## Contact Workflow

Ask for contact information only after explaining that it is optional and user-controlled. The user can provide any combination of display name, headline, location, availability, email, website, LinkedIn, GitHub, WhatsApp, or calendar link.

Never infer contact information from the session. Never scrape it from files. Never send contact information without a contact preview and explicit approval.

```bash
npm run workersignal -- contact --name "Public Display Name" --headline "AI workflow builder" --email "public@example.invalid" --website "https://example.com"
npm run workersignal -- preview-contact
npm run workersignal -- send-contact --approve
```

## Recursive Sync

Use recursive pings to keep the connector alive and discover updates, not to stream work content. A ping/update loop may send connector name, version, event type, capabilities, timestamps, and safe counters only. It must not send prompts, transcripts, source code, file paths, private project names, secrets, or contact details.

```bash
npm run workersignal -- ping
npm run workersignal -- sync
npm run workersignal -- sync --watch --interval 300
```

## Local CLI

Run commands from the WorkerSignal.ai repo root.

```bash
npm run workersignal -- login --api-url https://workersignal.ai --token "$WORKERSIGNAL_TOKEN"
npm run workersignal -- capture "Built and debugged an approved AI workflow summary."
npm run workersignal -- preview
npm run workersignal -- send --approve
npm run workersignal -- contact --name "Public Display Name" --headline "AI workflow builder" --email "public@example.invalid"
npm run workersignal -- preview-contact
npm run workersignal -- send-contact --approve
npm run workersignal -- updates
npm run workersignal -- ping
npm run workersignal -- sync --watch --interval 300
npm run workersignal -- disconnect
```

Use `send --approve` only after the user has reviewed the exact preview. If the user has not approved, stop at `preview`.
Use `send-contact --approve` only after the user has reviewed the exact contact preview. If the user has not approved, stop at `preview-contact`.

## Signal Shape

```json
{
  "title": "CRM workflow automation",
  "summary": "Built and debugged an approved CRM workflow involving stage updates, notifications, and backend validation.",
  "source": "codex",
  "ai_tools": ["Codex"],
  "technical_tools": ["HubSpot", "Slack", "REST API"],
  "categories": ["CRM automation", "Backend integrations"],
  "visibility": "private_pending_review"
}
```

## When Capturing From Codex

- Prefer a user-written or user-confirmed summary over raw session text.
- Use `source: "codex"` for Codex work and include other AI tools only if the user confirms them.
- Keep summaries outcome-focused: problem type, tools, technical area, complexity, and result.
- Generalize client/project references, for example "a private CRM migration" instead of a real client or internal project name.
- Do not claim verification. Use private pending review unless the WorkerSignal web flow later marks evidence public.

## When Capturing From Claude or Cursor

- Claude Code skills are folders with `SKILL.md`; Cursor Agent Skills use the same portable `SKILL.md` pattern and can discover compatible skill folders.
- Use `source: "claude"` for Claude work and `source: "cursor"` for Cursor work only when the user confirms the tool.
- In Cursor, prefer Agent Skills or MCP configuration for installation. In Claude, prefer the user's Claude skill directory or custom skill upload flow.
- Keep the same privacy policy across tools: preview first, approval second, WorkerSignal publication last.

## References

Read `references/signal-policy.md` when deciding whether content is safe to capture or whether a preview should be blocked.
