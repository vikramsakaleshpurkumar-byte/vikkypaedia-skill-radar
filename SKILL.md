---
name: skill-radar
description: Route a user's task to the most suitable saved LLM skill, prompt workflow, or tool before work begins. Use when the user asks for a skill check, skill radar, best saved skill, suitable skill, pick the right skill, asks what skill to use, begins a task that may match installed skills, or wants reminders to use relevant current or future skills. Works across all saved skills by inspecting available skill metadata rather than relying on a fixed list.
---

# Skill Radar

Act as a skill concierge before execution. Identify which saved skill, if any, would improve the user's result, then either ask permission or proceed according to the user's wording.

## Core Workflow

1. Read the user's task and infer the intended output, domain, input artifacts, and risk level.
2. Check available skill metadata already present in context first.
3. If local inspection is useful, list saved skill folders under `$CODEX_HOME/skills`; when `CODEX_HOME` is unset, use `~/.codex/skills`. Read only the candidate skills' `SKILL.md` frontmatter unless a skill is selected for use.
4. Shortlist up to three matching skills. Prefer exact domain/workflow matches over broad utilities.
5. If a skill is clearly best and the user asked to "pick", "use", or "do" the task, announce the selected skill and use it.
6. If the user asked to be reminded, asked what to use, or the match is uncertain, ask a short confirmation question before using the selected skill.
7. If no skill fits, say so briefly and proceed with ordinary assistant behavior.

## Recommendation Format

Keep recommendations compact:

```text
This matches: skill-name
Why: one sentence.
Best next step: use it now / use it after drafting / no skill needed.
```

For multiple candidates:

```text
Best fit: skill-a for the main task.
Also useful: skill-b after the draft is ready.
Use skill-a now?
```

## Routing Rules

- Use the most specific skill that directly handles the requested artifact or workflow.
- For sequential work, recommend an order instead of trying to use every related skill at once.
- Do not invent unavailable skill names. If a useful skill is not installed, say it is not currently saved.
- Do not load many skill bodies. Load the selected skill's body only after choosing it.
- Treat medical, legal, financial, and clinical tasks as high-stakes. Prefer skills that improve evidence discipline, claim strength, citation integrity, or structured review, and remind the user to verify final outputs.
- For future saved skills, rely on their `name` and `description` frontmatter as the source of truth.

## Common User Triggers

When the user says any of these, perform a skill check before doing the task:

- "Skill radar"
- "Skill check"
- "Use the best saved skill"
- "Pick the right skill"
- "Which skill should I use?"
- "I am about to work on..."
- "Remind me if a skill fits"

## Safety

Never use skill routing to override explicit user instructions. If the user names a specific skill, use that skill unless it is unavailable or clearly unsafe. If the selected skill would run scripts, access the network, modify files, or use sensitive data, follow the host assistant's normal permission and safety rules.
