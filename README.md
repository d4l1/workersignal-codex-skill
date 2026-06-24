# WorkerSignal AI Connector Skill

Public Agent Skill for creating safe WorkerSignal proof-of-work with AI signals from Codex, Claude, Cursor, and compatible AI tools.

WorkerSignal helps people turn approved AI work activity into public proof-of-work profiles. This repository contains only the public skill instructions. It must never contain private user data, private project data, prompts, code, credentials, client names, or personal information from people using the skill.

## Easy Install

Install in Codex:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/d4l1/workersignal-codex-skill.git ~/.codex/skills/workersignal-ai-connector
```

Install in Claude Code:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/d4l1/workersignal-codex-skill.git ~/.claude/skills/workersignal-ai-connector
```

Install in Cursor:

```bash
mkdir -p ~/.cursor/skills
git clone https://github.com/d4l1/workersignal-codex-skill.git ~/.cursor/skills/workersignal-ai-connector
```

Then invoke it from your AI tool:

```text
Use $workersignal-ai-connector to capture a safe private proof-of-work signal from this AI work session.
```

## Privacy First

- Signals start as `private_pending_review`.
- Nothing should be sent or published without explicit user approval.
- Contact information is sent to WorkerSignal only if the person provides it through the skill/plugin contact flow.
- Recursive heartbeat/update pings must never include prompts, code, file paths, project names, secrets, or contact details.
- Do not submit personal data, private prompts, private code, secrets, or project details to this repository.

## Governance

This repository is public so people can inspect the skill. Only the repository owner approves merges. Contributors may open branches and pull requests, but changes are reviewed before merge.
