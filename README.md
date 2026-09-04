**English** | [简体中文](README.zh-CN.md)

# No Overbuild

> Think broadly. Build only what earns its weight. Keep local faults local.

Codex can identify many risks, edge cases, and future possibilities. The problem is not thinking too much. The problem begins when every possibility becomes a framework, field, gate, approval step, or large regression suite—until a straightforward project is expensive, brittle, and difficult to change.

No Overbuild is an open Codex Skill. It helps Codex make four balanced decisions while designing, coding, repairing, refactoring, testing, or carrying out technical workflows:

- consider real users, future change, compatibility, recovery, privacy, and failure modes;
- converge on the smallest complete solution that fits the actual scale and risk;
- keep recoverable local failures from taking down the whole product or task;
- preserve necessary safety and validation without turning comprehensive thinking into comprehensive control.

It does not mean thinking less or omitting required work. When a high-risk or large-scale system genuinely needs more structure, that complexity should remain—as long as each part owns a concrete responsibility.

For example, if Markdown export occasionally fails in a local tool used by five people, No Overbuild favors fixing the real fault, preserving user work, and containing the failed export. It does not automatically add a message queue, separate database service, event bus, and full observability platform. If the work instead involves orders, permissions, or irreversible data migration, it keeps the transactions, rollback, and validation justified by those risks.

## Language

The canonical [SKILL.md](SKILL.md) is written in English and is the entrypoint Codex loads after the Skill is installed and discovered. The repository provides both English and Chinese READMEs so that one instruction source remains authoritative while users can understand and install the Skill in either language.

No Overbuild currently targets Codex. Other Agent Skill-compatible hosts may be able to read the same structure, but cross-host compatibility is not claimed until it has been verified.

## When to use it

Use No Overbuild when Codex is:

- adding or refactoring a software feature;
- fixing a bug while the proposed solution keeps expanding;
- designing an agent, automation, or multi-step technical workflow;
- deciding whether a new framework, service, protocol, schema, dependency, or state machine is justified;
- designing failure handling, upgrades, migrations, tests, or releases;
- dealing with a local problem that is blocking the whole program or task.

It is not intended for simple factual answers, translation, or ordinary prose editing.

## Install

If you want Codex to perform the installation, send it this request:

```text
Inspect and install this Codex Skill: https://github.com/Ww-Cooooo/no-overbuild
Only inspect and copy this repository into my personal Skill directory. Do not install dependencies, modify projects, or overwrite, delete, or update an existing Skill. If the target already exists, stop and report its path and source.
After installation, report the actual path and what was copied. I will open a new task separately to verify discovery.
```

This request authorizes inspection and copying of this repository into the personal Skill directory. It does not authorize dependency installation, project changes, or overwriting an existing Skill.

You can also clone it manually into your personal Skill directory.

Manual installation requires Git, and the target `no-overbuild` directory must not already exist. If it already exists, stop and report its path and source instead of cloning over, deleting, or blindly updating it.

### Windows PowerShell 7

```powershell
$skillRoot = Join-Path $env:USERPROFILE ".agents\skills"
New-Item -ItemType Directory -Force -Path $skillRoot | Out-Null
git clone https://github.com/Ww-Cooooo/no-overbuild.git (Join-Path $skillRoot "no-overbuild")
```

### macOS or Linux

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Ww-Cooooo/no-overbuild.git "$HOME/.agents/skills/no-overbuild"
```

After installation, verify the local entrypoint without changing it.

Windows PowerShell 7:

```powershell
$skillRoot = Join-Path $env:USERPROFILE ".agents\skills"
$skillEntry = Join-Path $skillRoot "no-overbuild\SKILL.md"
Test-Path -LiteralPath $skillEntry
Select-String -LiteralPath $skillEntry -Pattern '^name: no-overbuild$'
```

macOS or Linux:

```bash
skill_entry="$HOME/.agents/skills/no-overbuild/SKILL.md"
test -f "$skill_entry" && grep -Fx 'name: no-overbuild' "$skill_entry"
```

Once the file exists and the name matches, open a new Codex task so the Skill list is loaded again:

```text
Confirm that no-overbuild appears in the available Skill list for this task. Then read it and report the resolved SKILL.md path without modifying any project files.
```

Codex must report both the available Skill and its resolved entrypoint before discovery is considered verified. Use `$no-overbuild` explicitly when you want to guarantee invocation for a task; implicit selection depends on whether the request matches the Skill description.

## Use

Invoke it explicitly:

```text
Use $no-overbuild to fix this problem. Think through the real impact and failure handling, but do not add a heavyweight framework for a local fault.
```

You can also describe the development task normally. Codex may select the Skill automatically when the request matches its design, implementation, repair, refactoring, testing, migration, or fault-containment scope.

## How it changes the work

No Overbuild does not prescribe a technology stack or require a separate architecture report. It changes the order of decisions:

1. identify the real outcome, users, scale, risks, and existing structure;
2. think through necessary boundaries without implementing every possibility;
3. prefer repair and reuse, adding structure only for a real new responsibility;
4. make failures recoverable, visible, and as local as possible;
5. validate with high-information scenarios, scaling the depth of testing to the actual impact and risk.

## Boundaries

- It does not expand the permissions granted to Codex.
- It does not weaken protections for user data, secrets, identity, permissions, or irreversible operations.
- Only safely recoverable local failures may continue or degrade. Actions that could corrupt state, break correctness, or cause irreversible harm must stop and report the issue.
- It does not remove necessary features or validation in the name of simplicity.
- It does not automatically access the network, install dependencies, or modify unrelated projects.
- This repository contains Skill instructions, display metadata, and three evaluation fixtures made of prompts and expected outcomes. It contains no executable scripts or evaluation runner.

## Repository contents

| Path | Purpose |
| --- | --- |
| `SKILL.md` | Canonical English entrypoint loaded by Codex after discovery |
| `agents/openai.yaml` | Display name, short description, and default invocation prompt |
| `evals/evals.json` | Three representative prompts and expected outcomes for evaluating both overbuilding and underbuilding |
| `README.md` | English project entrypoint |
| `README.zh-CN.md` | Simplified Chinese documentation |

## License

[MIT License](LICENSE)
