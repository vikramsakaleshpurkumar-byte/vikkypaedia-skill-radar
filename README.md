# Vikkypaedia Skill Radar

Vikkypaedia Skill Radar is a lightweight meta-skill that helps an AI assistant choose the best saved skill, prompt pack, workflow, or tool before starting a task.

It is designed for people who collect many skills and then forget which one to use. Instead of memorizing names, the user can ask for a quick skill check:

```text
Skill radar:
I am writing the discussion section for my manuscript.
```

The assistant should respond with a short recommendation:

```text
Best fit: discussion-composer
Also useful later: claim-strength-calibrator
Use discussion-composer now?
```

## What It Does

- Routes a task to the most suitable saved skill.
- Works with current and future skills by reading skill metadata.
- Recommends a sequence when multiple skills are useful.
- Asks before switching workflows unless the user has already asked it to proceed.
- Helps structure growing personal skill libraries.

## Who It Is For

- Researchers managing many writing, analysis, and review skills.
- Developers using reusable agent workflows.
- Students and clinicians who want a reminder layer before drafting or analyzing.
- Anyone building a personal LLM skill library.

## Install For Codex

Copy the skill folder into your Codex skills directory:

```text
~/.codex/skills/skill-radar
```

On Windows, this is usually:

```text
C:\Users\<you>\.codex\skills\skill-radar
```

Then restart Codex so the skill is discovered.

## Basic Usage

Ask directly:

```text
Use skill-radar to recommend the best saved skill for this task:
[paste your task]
```

Or use a short habit phrase:

```text
Skill check:
I am about to polish a journal manuscript paragraph.
```

Or let it proceed automatically:

```text
Pick the right saved skill and use it for this:
[paste your task]
```

## Cross-LLM Adaptation

This repository is written as a Codex skill, but the pattern is platform-neutral. For other assistants, adapt the core rule:

1. Inspect available workflow/tool/skill descriptions.
2. Match the user's task to the most specific workflow.
3. Recommend at most three candidates.
4. Ask before using a workflow unless the user explicitly says to proceed.
5. If no workflow fits, continue normally.

## Repository Layout

```text
vikkypaedia-skill-radar/
├── README.md
├── LICENSE
└── skill-radar/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

## License

MIT License.
