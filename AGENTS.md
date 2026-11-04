# Project

What to read and respect before changing anything in this repository.

## Language

The repo language is English: identifiers, comments, test names, exception messages, docs, tool and file names, stored keys and allowed values, issue and pull request text. Domain concepts use the English terms in `GLOSSARY.md`, never the words the interface shows. The one exception is text that describes documents saved in older versions (schema steps, fixtures): it stays as saved, because translating it would break loading.

## Before you write

- `PRODUCT.md`: who it is for and what it must stay true to.
- `GLOSSARY.md`, then the ADRs in `docs/adr/` for the area you are about to touch. If your change contradicts an ADR, say so in the pull request instead of silently overriding it.
- `CODING_STANDARDS.md`: what the review will check that no script does.

## Issues and pull requests

- Issues and specs live in GitHub Issues, worked with the `gh` CLI. Conventions in `docs/agents/issue-tracker.md`; labels in `docs/agents/triage-labels.md`.
- One issue, one branch, one agent. Take only issues labelled `ready-for-agent`; everything else needs a human first.
- A pull request title is a full sentence that says what changed, not what was done: "The store keeps the parsed catalog while its file is unchanged", not "Cache catalog".
- Every pull request runs the full test suite with warnings as errors and the guards in `.github/workflows/`. Green means this code passed. Never skip, disable or quarantine a test to get there.

## Local data

Real data lives in a git-ignored folder that only the main checkout has. Tests and CI never see it. After a change to a stored document's schema, run the loader tool against the real data from your worktree before opening the pull request.

## Running the app

The development launch profile uses scratch folders, its own port and no API keys, so a trial run reaches no real data and no paid service. The real app is the published one. Start-up work must finish before the app reports started, so a test host sees it done.
