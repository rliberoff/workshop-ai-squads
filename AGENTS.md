# Agent instructions

Guidance for any AI coding assistant working in this repository, like for example GitHub Copilot.

## Purpose

This is a technical workshop about AI agentic development using [Squads](https://github.com/bradygaster/squad) and GitHub Copilot.

## Order of precedence

Apply the first source that resolves the question, and never silently override a higher one.

| Priority | Source | What it governs |
| :--- | :--- | :--- |
| 1 | A direct, explicit user directive | Overrides everything below, by rule 1 of the Copilot instructions |
| 3 | [`.github/copilot-instructions.md`](.github/copilot-instructions.md) | Interaction style, language policy, code generation and modification philosophy |
| 4 | [`.github/instructions/`](.github/instructions/) | Scoped rules, applied according to their `applyTo` glob |
| 5 | `.agents/skills/<skill_name>/SKILL.md` | Domain conventions, applied when the skill description matches the task |
| 6 | This file | Orientation and repository facts only |

If two applicable sources conflict, or one cannot be loaded, stop the affected work and ask the user to resolve it

## Repository map

## Prerequisites

| Requirement | Check |
| :--- | :--- |
| Squads 1.1.0 or later | `squad --version` |
| GitHub Copilot CLI 1.0.105 | `copilot --version` |

## Rules that apply to every change

- Ask before you build. [`wow-follow-up-question.instructions.md`](.github/instructions/wow-follow-up-question.instructions.md) requires at least 95% confidence before making changes, and requires you to state your confidence percentage in every exchange.
- Never emit placeholders. [`wow-no-dummy-no-placholder-code.instructions.md`](.github/instructions/wow-no-dummy-no-placholder-code.instructions.md) forbids `TODO` markers, pseudo-code markers, dummy defaults and non-functional stubs. Use real values, or the idiomatic parametric form for the language.
- Change the minimum. Preserve existing structure, style and logic; extend rather than replace; do not refactor or reformat code the request did not target.
- Declare intent before each tool call, in one concise sentence.

## Language policy

- Code, Infrastructure as Code (IaC), scripts, executable configuration, identifiers and every code comment are always in English. This includes Terraform descriptions and validation messages, XML documentation comments, log and event names, and exception messages.
- Instruction files, prompt files, custom agents and skills are always in English.
- Standalone documentation may be Spanish or English according to its audience.
- Reply to the user in the language the user writes in.
- User interface in the frontend must be in Spanish.

## Commits and pull requests

- Update the `CHANGELOG.md` with a summary of the changes made before creating a pull request. If in doubt, ask the human for guidance on how to document the change, including the version number or date.
- Every commit message and pull request title, always and without exception, follows the [`wow-conventional-commits`](.agents/skills/wow-conventional-commits/SKILL.md) skill. Load the skill before you write the message and take the format from it; never improvise one, and never take it from this file.
- The integration branch is `dev`. Work on a topic branch named after the pattern already used in the remote, `@<user>/<topic>`.
- One commit is one logical change.
- All integration happens through pull requests in Azure Repos. Direct commits to the integration branch and self-merges are prohibited.
- Attach the evidence the constitution requires when the change touches security, tests, coverage, performance or observability.

## Things not to do

- Do not put a secret, token or personally identifiable information in code, configuration, logs or telemetry.
- Do not claim a validation ran when it did not.

## Important references

- [Squads Documentation](https://bradygaster.github.io/squad/)
- [Squads GitHub Repository](https://github.com/bradygaster/squad)
