# WorkerSignal Codex Skill

Public Codex skill for creating safe WorkerSignal proof-of-work signals.

WorkerSignal helps people turn approved AI work activity into public proof-of-work profiles. This repository contains only the public skill instructions. It must never contain private user data, private project data, prompts, code, credentials, client names, or personal information from people using the skill.

## Install

Copy this folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/d4l1/workersignal-codex-skill.git ~/.codex/skills/workersignal-codex-connector
```

Then invoke it in Codex:

```text
Use $workersignal-codex-connector to capture a safe private work signal from this AI work session.
```

## Privacy First

- Signals start as `private_pending_review`.
- Nothing should be sent or published without explicit user approval.
- Contact information is sent to WorkerSignal only if the person provides it through the skill/plugin contact flow.
- Do not submit personal data, private prompts, private code, secrets, or project details to this repository.

## Governance

This repository is public so people can inspect the skill. Only the repository owner approves merges. Contributors may open branches and pull requests, but changes are reviewed before merge.
