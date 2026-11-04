# Coding standards

The judgement calls a review checks a change against. Rules a script can check run in CI instead (`.github/workflows/`), and a rule moves there the moment someone writes the script.

Every rule carries its reason, usually the incident that produced it. A rule without a *Why* is a preference, and preferences don't survive the next agent.

## The core decides, the adapters word it

A page, an endpoint or a job sends the user's answer to the core as one event and words the core's refusal. A rule the core enforces is checked only in the core; the adapter shows the refusal next to what the user typed, with the input left in place.

Why: an adapter's copy of a core rule drifts. A page once checked an edited allocation's sum on its own, missed a flag the core read, and let through what the core would have refused, until a later change removed the copy.

## A retry pays only for what failed

Any path that repeats a paid call or a paid reading keeps what was already paid for, and its failure state, until the answer is complete. Its test runs several failures in a row, not one.

Why: a retry that reset a connector's state paid again for a call that had already answered, on every attempt, up to the monthly cap. The test ran one retry and passed.

## One name per thing

Names follow `GLOSSARY.md`: a stored value is its English label in snake_case, and a code name built on a glossary term uses the whole term and none of its _Avoid_ words. A naming test checks the parts a script can.

Why: a review reads this file, not the glossary, and every naming slip in one review came from exactly those two sources.

## How to add a rule

1. Write the rule as the review would state it.
2. Write the *Why*: the incident, the commit or the issue.
3. If a script can check it, write the script and put it in CI instead of here.
