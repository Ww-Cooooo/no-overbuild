# Clarification and bounded changes

Read this when the user's wording supports different outcomes, or when a repair may reach outside the original change. These are teaching examples, not observations from a real project or a fixed questionnaire.

## Identify the missing decision

Use the user's actual words and accepted constraints. Inspect relevant evidence first; do not scan an entire repository just to avoid one simple question.

| Situation | Appropriate next action | Mistake to avoid |
| --- | --- | --- |
| A setting, implementation, or supplied document can settle a fact | Inspect it and state any remaining limitation. | Asking the user to do the investigation, or inventing a plausible answer. |
| Different readings would change behavior, meaning, scope, or an accepted tradeoff | Explain the difference and ask before dependent work. | Choosing silently because an edit is reversible. |
| The result is clear and only implementation remains uncertain | Use engineering judgment or a targeted experiment. | Asking the user to choose routine implementation details. |
| The user explicitly delegates a choice or requests alternatives | Explore within that boundary and label proposals as proposals. | Treating exploration as acceptance or permission to change fixed requirements. |

A useful question identifies the decision: “By keeping old records, do you mean they must remain visible in the app, or only recoverable from an archive? That changes what cleanup may remove.” The user may give a different answer. While waiting, locate the cleanup entrypoint or inspect ownership; do not change retention behavior on an assumed answer. Once resolved, retain the decision for this task and continue without requesting the same approval again.

## A small change can still alter the user's meaning

Request: “Make cancellation automatic.” The UI distinguishes cancelling a queued job from stopping a running job.

- Wrong: wire cancellation to stop all running jobs because the code is easy to undo.
- Better: inspect the current behavior, explain the distinction, and ask which behavior is intended. Leave the dependent change pending.
- Independent work: examine the affected handler and existing checks; a separately authorized, unrelated typo correction may proceed.

Contrast: “Disable download while its request is pending, then enable it after either success or failure.” With an existing request-state pattern, the outcome is clear. Reuse that pattern and check the two completion paths; do not ask the user to select a state-management library or repeat the stated failure behavior.

## Necessary related work is different from opportunistic cleanup

For each proposed edit, identify why the requested result needs it. Keep this as a working explanation; no separate ledger is required.

### References that must move together

Request: rename an internal response field and update the corresponding page. The producer, typed consumer, and documented example all reference the old field.

- Updating all three is related work: omitting one breaks the behavior or its explanation. A required generated file can also change; check its relation to the intended source change rather than requiring the user to name every generated line.
- Replacing the whole request layer or reformatting adjacent pages is unrelated unless separately authorized.
- If the field is actually public and the migration boundary is undecided, clarify that dependency before making a breaking interpretation.

### New unused code versus pre-existing dead code

Request: replace a parser call with an existing helper. This makes its old private import and local adapter unused; a different legacy parser was already unused before the task.

- Check references and any external or dynamic use. Remove the import and adapter only when this change made them unnecessary and that conclusion is supported.
- Leave the pre-existing legacy parser alone. Mention it if useful, without turning its cleanup into a condition for finishing the requested change.
- If a symbol's role is uncertain, investigate its contract or clarify the consequential ambiguity. Do not delete it merely to make the diff look cleaner.

### Broad authorization remains broad

Request: “Reorganize this module completely while preserving its public behavior.” Restructuring that module is authorized; a narrow patch need not be sufficient. Preserve the stated behavior and inspect affected consumers, without extending the rewrite to neighboring modules for style consistency.

Existing local modifications are part of the starting state. If their intended outcome conflicts with the rewrite and cannot be determined, resolve that conflict before overwriting them. Revert only accidental unrelated edits introduced by this task, not another person's work.

## Finish the actual task

Review the actual diff and relevant behavior, then report the result and material unresolved findings proportionately. An unrelated issue does not require fixing it or blocking the requested delivery. Source-code cleanup is not a blanket deletion rule for user assets, recordings, previous deliverables, or failure evidence.

Related reading: the third-party [Karpathy Guidelines](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/skills/karpathy-guidelines/SKILL.md) separates focused code edits and newly unused code from pre-existing dead code. This Skill adapts that idea while preserving necessary related repairs and agreed quality; it does not adopt a universal line-count target or stop every independent action for every unknown.
