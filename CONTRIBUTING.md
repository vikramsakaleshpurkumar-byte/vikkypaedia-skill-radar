# Contributing

Thanks for helping improve Vikkypaedia Skill Radar.

Good contributions include:

- Better routing heuristics.
- Examples for different LLM platforms.
- Safer rules for high-stakes domains.
- Shorter, clearer wording.
- Compatibility notes for new skill formats.

Please keep the core skill small. The point of Skill Radar is to route to other skills without becoming a giant catalog itself.

## Design Principles

- Prefer metadata inspection over hard-coded skill lists.
- Recommend at most three candidate skills.
- Ask before using a skill when the match is uncertain.
- Use the most specific matching skill.
- Do not invent unavailable skill names.
- Treat medical, legal, financial, and clinical tasks as high-stakes.
