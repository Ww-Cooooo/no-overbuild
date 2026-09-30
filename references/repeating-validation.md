# repeating validation

This is an illustrative scenario expanded from the existing repository's narrow-change evaluation prompt, not a completed test. The earlier passing checks and unchanged conditions are assumptions of the example; verify those assumptions in the current task.

### Situation

Within an existing technical task, a local tool's functionality and data protections were checked yesterday. Today, only two explanatory sentences in a detail dialog change. The logic, dependencies, permissions, and data format remain unchanged, and the earlier verification record is available.

This is a narrow decision about validation scope inside that task. It does not make ordinary prose editing a new trigger for the Skill.

### Decision and follow-through

Confirm that the change is limited to those sentences. Check that the revised meaning is accurate and that the real dialog still presents the text legibly without hiding an action. The fact that a sentence is correct in the source file does not establish that it is readable in the interface.

Reuse the relevant earlier functional evidence while its assumptions remain true. Reinstalling the tool, rehearsing a data migration, rerunning unrelated suites, or comparing the entire workspace's hashes would not normally answer a new question about these sentences.

Suppose the longer text now pushes the close button out of reach. That observation changes the scope: repair the affected layout and check the dialog again under the relevant conditions. It still does not, by itself, create a reason to retest unrelated data migration code.

### When another check is justified

Repeat or broaden verification when a relevant artifact or condition changed, a check failed, or an unresolved question remains. An earlier pass that covered a different build or different conditions may not establish the needed behavior. Conversely, an unchanged passing result does not become useless merely because it was produced in a previous turn.

Do not create a new failure exercise solely to demonstrate that testing occurred. Finish when the evidence addresses the actual change and material open questions, subject to the project's required checks.
