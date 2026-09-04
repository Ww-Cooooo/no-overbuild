---
name: no-overbuild
description: Use when Codex designs, implements, repairs, refactors, reviews, tests, migrates, or publishes software or multi-step technical workflows where unnecessary architecture, process, validation, or failure handling could make the result heavier or more brittle than the real problem requires. Think comprehensively, choose the smallest complete solution, keep recoverable faults local, and preserve necessary safety and correctness. Do not use for simple factual answers, translation, or ordinary prose editing.
---

# No Overbuild

Think comprehensively. Build only what earns its weight. Keep local faults local.

Use this skill as a decision lens while doing the work. Do not turn it into a new ceremony, report, framework, or approval layer.

## Start from the real job

Before changing anything, identify the intended result, actual users, current owner of the behavior, existing structure, realistic scale, and consequences of failure. Distinguish a demonstrated need from a hypothetical future possibility.

Think beyond the first implementation idea. Consider the user journey, maintenance, compatibility, recovery, privacy, security, and likely future change. Thinking broadly improves the decision; it does not require implementing every possibility.

## Converge on the smallest complete solution

Prefer repairing, reusing, combining, or removing existing parts before adding a new abstraction. Add a service, framework, protocol, state machine, registry, schema field, dependency, or permanent process only when it owns a real responsibility that the current design cannot carry cleanly.

Smallest complete does not mean fewest lines. Keep everything required for the feature to work well, remain understandable, preserve user data, and survive realistic faults. When the real scale or risk justifies greater complexity, use it and explain what concrete responsibility earns that weight.

## Keep failures proportional

Do not let a recoverable local fault become an unrelated global failure.

- If one safe repair is evident, apply it and tell the user what happened.
- Otherwise, use a bounded retry or an in-scope fallback when it has a clear stopping condition.
- If recovery is uncertain, preserve useful state and isolate only the affected step, component, or capability.
- Stop the corresponding risky action when identity, user data, secrets, permissions, ownership, irreversible changes, or an untrusted source are uncertain. Unrelated safe work may continue.
- Never hide an error, invent success, or silently discard user work.

This is a reasoning order, not a required runtime state machine.

## Validate for information, not volume

Choose checks for information, not a preset count. Cover:

- the main user journey affected by the work;
- one realistic failure or recovery path introduced or changed;
- any data, privacy, security, compatibility, or authorization boundary actually at risk.

Reuse existing checks when they answer these questions. A narrow change may need only a few high-information checks; a broad or high-risk change may need substantially more. Let the actual impact determine the depth, and add broader regression coverage when the change or evidence shows a wider risk.

## Watch for overengineering

Reconsider the design when it starts to show these signs:

- the same truth is maintained in several places;
- one edge case creates a general framework or permanent workflow;
- exact wording, timestamps, counts, or rebuildable projections become global health gates;
- an optional component failure blocks the whole product or task;
- many similar tests repeat the same evidence;
- a routine tool or connection problem grows into a separate engineering project;
- documentation and approval steps become larger than the change they protect.

## Preserve intent and authority

The user's explicit request and the project's established constraints take precedence. This skill shapes how authorized work is completed; it never expands permission, weakens necessary safety, or replaces a domain-specific requirement with a generic preference for simplicity.

Finish with the real outcome: what changed, what remained intact, what was verified, any local fault or recovery that occurred, and the next useful action. Keep that explanation proportional to the work.
