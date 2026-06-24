# WorkerSignal Signal Policy

Allowed signal content:

- General task title.
- Safe summary of the work outcome.
- AI tools used when user-approved.
- Technical tools, frameworks, and broad categories.
- Approximate complexity and evidence status.
- Public links only when the user explicitly approves them.
- Contact details only when the person explicitly provides them through the skill/plugin contact flow.

Blocked content:

- Full prompts or full conversations.
- Private code or proprietary implementation details.
- API keys, tokens, passwords, cookies, signing secrets, or credentials.
- Client names, private project names, private domains, and internal systems unless approved.
- Personal data about third parties.
- Financial, contractual, legal, HR, health, or NDA-protected details.

Required defaults:

- `visibility` must start as `private_pending_review`.
- Publication must happen only after explicit approval in WorkerSignal.
- Connector updates that change behavior, permissions, or data sent must be visible to the user.

Safe summary pattern:

`Built/debugged/designed <general system or workflow> involving <approved tools/categories> to solve <general problem>, with private details removed.`
