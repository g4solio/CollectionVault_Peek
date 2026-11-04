# CollectionVault_Peek

A peek at how CollectionVault is built.

CollectionVault is a private project: a personal catalog for books and comics, in everyday use since 29 October 2026, taken from an agreed scope to production in two weeks with AI agents writing most of the code. This repository publishes the part of it that isn't the product: the operating model that let that happen without the code going feral.

Nothing here is product code, data, prompts or the product's own rules. Those stay private. What's here is the shape of the work: the documents an agent reads before it writes, the checks a pull request has to pass, and the habits around them.

## The model in one paragraph

Agents do most of the typing. I own the product spec, the domain glossary, the architecture decisions, the coding standards, the review, and the CI that enforces whatever a script can check. Every rule has its reason written next to it, usually the incident that caused it. Work reaches an agent as a fully specified issue and comes back as a pull request that runs the whole test suite with warnings as errors, plus guards for the rules a script can check. I review the diff, not the chat.

## Who does what

**The agents:** implementation, the first draft of tests and docs, refactors, visual iteration, and the retro that turns a broken rule into a check.

**Me:** the product spec (`PRODUCT.md`), the glossary (`GLOSSARY.md`), the architecture decisions (`docs/adr/`), the coding standards (`CODING_STANDARDS.md`), the review, and what "done" means.

**The machinery:** the test suite on every pull request with warnings as errors; CI guards for rules a script can check; ADRs that cite the issue that made them; triage labels that say which issues an agent may take alone.

## The loop

1. **Decide in writing.** A product decision goes in `PRODUCT.md`, a term in `GLOSSARY.md`, an architecture decision in an ADR that links the issue where it was decided.
2. **Cut the work into issues**, labelled as in `docs/agents/triage-labels.md`. `ready-for-agent` means fully specified; `ready-for-human` means it needs me first.
3. **One agent, one branch, one issue.** The agent reads `AGENTS.md` before anything else: repo language, how to run the app without touching real data or paid services, where the domain docs are.
4. **Pull request.** CI runs the tests with warnings as errors and the guards. I read the diff against `CODING_STANDARDS.md`. Titles are full sentences that say what changed.
5. **Retro.** A rule that was broken becomes a CI guard if a script can check it, or a standard with its *Why* if only a reader can.

## What is in this repository

| Path | What it is |
|---|---|
| `PRODUCT.md` | The product document template, as used, with CollectionVault's specifics removed. |
| `GLOSSARY.md` | The glossary rules (one name per thing, Avoid lists, stored keys) with example entries from a stand-in domain. |
| `AGENTS.md` | What an agent reads before touching the repo. |
| `CODING_STANDARDS.md` | The judgement calls a review checks, each with its reason. |
| `docs/adr/` | The ADR convention and template. |
| `docs/agents/` | Issue tracker conventions and triage labels. |
| `.github/workflows/guards.yml` | This repository's own guards. A model that says "rules a script can check run in CI" should run in CI, so this one checks its own ADRs, standards and glossary. |
| `templates/dotnet-guards.yml` | The .NET guards from CollectionVault's pipeline, with project names as placeholders. |

## Figures from the private repository

Main branch, 16 October to 3 November 2026.

| | |
|---|---|
| Scope agreed | 16 October 2026 |
| In everyday use | 29 October 2026 |
| Commits | 357 |
| Pull requests | 77 |
| CI guards | tests with warnings as errors · the core may not read a clock, a file, the network or the console · start-up work must finish before the app reports started · every page script must parse |

## The tooling underneath

[Claude Code](https://claude.com/claude-code) with these plugins: [impeccable](https://github.com/pbakaus/impeccable) for the product document schema and design critique, [ponytail](https://github.com/DietrichGebert/ponytail), [mattpocock/skills](https://github.com/mattpocock/skills) for triage, wayfinding and grilling a spec against the docs, and [dotnet-skills](https://github.com/Aaronontheweb/dotnet-skills). The conventions in `docs/agents/` follow the shape those skills expect. The rules and their reasons are mine.

## Who

[Davide Gozzi](https://g4solio.github.io/portfolio/), senior software engineer in Modena, Italy. Software that has to keep working, shipped with AI agents; architecture, review and verification stay mine. [LinkedIn](https://www.linkedin.com/in/davide-gozzi5/) · [CV](https://g4solio.github.io/portfolio/Davide_Gozzi_CV.pdf)
