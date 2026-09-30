---
name: no-overbuild
description: Use when Codex designs, implements, repairs, refactors, reviews, tests, migrates, or publishes software or multi-step technical workflows where unnecessary architecture, process, validation, or failure handling could make the result heavier or more brittle than the real problem requires. Think comprehensively, deliver the agreed quality, remove avoidable burden, and keep recoverable faults local. Do not use for simple factual answers, translation, or ordinary prose editing.
---

# No Overbuild

Think comprehensively. Deliver the agreed quality. Keep process proportionate and local faults local.

Use this skill as a decision lens while doing the work. Do not turn it into a new ceremony, report, framework, or approval layer.

Here, "overbuild" means architecture, process, checks, or failure handling whose burden is not justified by the actual job. Work does not become unnecessary merely because it takes effort: a requested interaction may warrant a library, and a risky migration may warrant substantial verification. Judge the purpose and benefit of the work before removing it.

## Start from the real job

Before changing anything, identify the intended result, actual users, current owner of the behavior, existing structure, realistic scale, and consequences of failure. Distinguish a demonstrated need from a hypothetical future possibility.

Think beyond the first implementation idea. Consider the user journey, maintenance, compatibility, recovery, privacy, security, and likely future change. Thinking broadly improves the decision; it does not require implementing every possibility.

## Design comprehensively and build the product well

Within the agreed scope, deliver the required functionality, visual quality, motion, interaction, performance, compatibility, maintainability, and user guidance where relevant. Do not use "lightweight," "minimum implementation," fewer lines, or fewer dependencies to justify missing capabilities or unfinished polish. Do not expand the product beyond the user's goal either.

Reuse suitable existing parts. Choose new tools, frameworks, dependencies, or abstractions by their concrete benefit to the goal and their maintenance cost—not by an automatic preference for adding or avoiding them. Keep useful module boundaries; fewer files or a giant function do not make a design simpler. Cut avoidable burden, not product quality or completeness.

## Keep failures proportional

Do not let a recoverable local fault become an unrelated global failure.

- If one safe repair is evident, apply it and tell the user what happened.
- Otherwise, use a bounded retry or an in-scope fallback when it has a clear stopping condition.
- If recovery is uncertain, preserve useful state and isolate only the affected step, component, or capability.
- Stop the corresponding risky action when identity, user data, secrets, permissions, ownership, irreversible changes, or an untrusted source are uncertain. Unrelated safe work may continue.
- Never hide an error, invent success, or silently discard user work.

This is a reasoning order, not a required runtime state machine.

## Validate for information, not volume

Choose checks for the changed behavior and real risk, not a preset count. Consider:

- the main user journey affected by the work;
- realistic failure or recovery paths actually introduced or changed;
- any data, privacy, security, compatibility, or authorization boundary actually at risk.

Reuse suitable checks and their passing results while the relevant code, artifact, and conditions remain unchanged. After relevant checks pass, expand or repeat only for a new change, failure, or unresolved doubt. Do not invent a failure exercise for a change that introduces none. High-risk work may need substantial verification; neither fewer nor more tests is a success metric.

Remove redundant approvals, reports, evidence packages, and unrelated full-suite runs. Hashes can establish byte identity or delivery integrity, not whether a feature works; do not add hash comparisons to ordinary work without that need. Preserve meaningful assertions and required protections, and explain proposed changes to established checks rather than silently bypassing them.

## Do not turn comprehensive thinking into comprehensive control

Reconsider the design when it starts to show these signs:

- the same truth is maintained in several places;
- one edge case creates a general framework or permanent workflow;
- exact wording, timestamps, counts, or rebuildable projections become global health gates;
- an optional component failure blocks the whole product or task;
- many similar tests repeat the same evidence;
- a routine tool or connection problem grows into a separate engineering project;
- documentation and approval steps become larger than the change they protect.

## Preserve intent and authority

The user's explicit request and the project's established constraints take precedence. Apply relevant domain-specific Skills and their valid requirements; merely reading them is not adoption. This skill never grants permission, weakens necessary safety, or overrides those requirements with a generic preference for simplicity. Surface a real conflict or tradeoff instead of silently lowering the agreed quality.

Finish with the real outcome: what changed, what remained intact, what was verified, any local fault or recovery that occurred, and the next useful action. Keep that explanation proportional to the work.

## Read the case that matches the current situation

The guidance above stands on its own. Use the task and observed feedback to select a case below; do not wait until you personally feel confused. Each case is a separate local file. Read only the matching cases, and reuse a case already read while the relevant situation remains unchanged.

| Current situation | Read |
| --- | --- |
| A request to simplify is being used to reduce agreed capabilities or finish, or feedback says the product fell short despite completed checks. | [Quality and process](references/quality-and-process.md) |
| A failure in one operation may interrupt other work, or a proposed repair introduces infrastructure beyond the observed cause. | [A local export failure](references/local-export-failure.md) |
| Safeguards are being simplified for a change involving live data, access boundaries, or hard-to-reverse state. | [A consequential migration](references/consequential-migration.md) |
| Broad checks are proposed after a narrow change, or it is unclear whether earlier results still cover the current conditions. | [Repeating validation](references/repeating-validation.md) |

These cases explain decisions; they are not mandatory task templates. If the reference is unavailable, use the core guidance above and state the missing context only if it affects the decision. No original development chat or other Skill is needed to understand this one.
