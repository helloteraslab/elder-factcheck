# Elder-FactCheck

[简体中文说明](./README.zh-CN.md)

`Elder-FactCheck` is a reusable skill for agents such as Codex, OpenClaw, or similar prompt-driven assistants. It helps users review suspicious content shared by older family members, then craft a respectful reply that preserves dignity while reducing misinformation risk.

## What It Does

- reviews links, screenshots, pasted text, and forwarded article summaries
- classifies the content into common misinformation-prone categories
- evaluates credibility, factual quality, manipulation risk, and hidden incentives
- optionally verifies important claims with trustworthy sources
- writes a gentle reply the user can send to a parent or grandparent

This project is designed for a very specific but common use case:

family elders often forward content out of care, not bad intent. A useful agent should check the content without turning the conversation into a fight.

## Who This Is For

- people helping parents or grandparents navigate forwarded articles
- agent builders who want a socially aware fact-checking skill
- prompt and skill authors looking for a concrete family-safety workflow

## Files

- [`SKILL.md`](./SKILL.md): the main skill definition
- [`examples/example-inputs.md`](./examples/example-inputs.md): example requests and outputs
- [`LICENSE`](./LICENSE): project license
- [`.gitignore`](./.gitignore): recommended ignores for a clean repo

## Highlights

- built for real family communication, not just raw claim classification
- balances fact-checking with tone and relationship preservation
- works even when the original content is incomplete or only available as a screenshot
- includes fallback behavior for partial verification

## Recommended Usage

Call the skill when a user:

- explicitly asks for `elder-factcheck`
- shares a suspicious article or screenshot from a family elder
- wants help replying politely to their mother, father, grandmother, or grandfather

## Install

Copy or register [`SKILL.md`](./SKILL.md) in the skill directory used by your agent platform.

If your platform supports per-skill metadata:

- use `elder-factcheck` as the skill name
- keep the long-form description so the runner can match family fact-checking requests
- preserve the execution and safety sections, since they define the behavior more than the header does

## Example Scenarios

1. A grandmother shares a health article claiming that one food "feeds cancer cells."
2. A father forwards a screenshot saying a new national policy takes effect tomorrow.
3. A mother sends a family-ethics article that uses guilt and absolutist language.
4. A grandfather shares a warning about banking fraud with no official source.

## Output Shape

The skill is designed to produce:

- target person
- content type
- 3 core claims
- structured assessment
- conclusion
- short reasoning
- verification notes
- suggested reply

## Design Goals

- preserve dignity
- avoid confrontation-first language
- support partial evidence and honest uncertainty
- prefer primary or authoritative sources
- keep results actionable for everyday users

## Limitations

- not a replacement for doctors, lawyers, regulators, or banks
- depends on source accessibility and the agent's browsing abilities
- should not make overconfident claims when verification is weak

## Adapting For Your Agent

You may want to customize:

- the default target person
- source preferences by region
- supported language or locale
- reply tone for different family relationships
- output verbosity

## License

MIT
