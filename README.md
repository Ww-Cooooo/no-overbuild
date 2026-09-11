**English** | [简体中文](README.zh-CN.md)

# No Overbuild

> Think broadly. Build the product well. Cut needless process, not quality.

Codex can identify many risks, edge cases, and future possibilities. The problem is not thinking too much. The problem begins when every possibility becomes a framework, field, gate, approval step, or large regression suite—until a straightforward project is expensive, brittle, and difficult to change.

No Overbuild is an open Codex Skill. It helps Codex make four balanced decisions while designing, coding, repairing, refactoring, testing, or carrying out technical workflows:

- **Keep local faults local:** recover safely or isolate the affected part while preserving user work.
- **Design comprehensively and deliver quality:** fulfill the agreed functionality, visual design, motion, interaction, and other relevant requirements—not a stripped-down substitute.
- **Verify precisely and keep process practical:** remove low-value tests, unchanged repeat checks, and unnecessary approvals or reports; preserve checks that protect real behavior and data.
- **Do not turn thinking into control:** use risks to make decisions, not to create a global gate for every possible issue.

Simplify avoidable burden, not product quality or completeness. Choose tools, dependencies, and abstractions for their real benefit and maintenance cost. A useful framework is not overengineering merely because it adds code; an elaborate process is not valuable merely because it looks rigorous.

For example, if Markdown export occasionally fails in a local tool used by five people, No Overbuild favors fixing the real fault, preserving user work, and containing the failed export. It does not automatically add a message queue, separate database service, event bus, and full observability platform. If the work instead involves orders, permissions, or irreversible data migration, it keeps the transactions, rollback, and validation justified by those risks.

Likewise, when the agreed interface needs polished visuals and meaningful motion, "keep it lightweight" is not permission to deliver a static placeholder. The Skill guides Codex's decisions; it is not an automatic guarantee of the result.

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

No Overbuild does not prescribe a technology stack or require a separate architecture report. It guides decisions throughout the work:

1. identify the real outcome, users, scale, risks, and existing structure;
2. think through necessary boundaries without implementing every possibility;
3. reuse suitable parts and choose additional tools or structure when their benefit justifies the cost;
4. make failures recoverable, visible, and as local as possible;
5. check the affected behavior and real risks; reuse passing evidence while the relevant work remains unchanged, expanding only for a change, failure, or unresolved doubt.

Relevant domain-specific Skills still apply. No Overbuild must not become an excuse to ignore their valid quality requirements. Hashes establish byte identity, not usability; test counts and repeated reports are not proof of a better product.

## Boundaries

- It does not expand the permissions granted to Codex.
- It does not weaken protections for user data, secrets, identity, permissions, or irreversible operations.
- Only safely recoverable local failures may continue or degrade. Actions that could corrupt state, break correctness, or cause irreversible harm must stop and report the issue.
- It does not remove necessary features or validation in the name of simplicity.
- It does not automatically access the network, install dependencies, or modify unrelated projects.
- This repository contains Skill instructions, display metadata, and five evaluation fixtures made of prompts and expected outcomes. It contains no executable scripts or evaluation runner; the fixtures alone are not evidence of passed behavioral tests.

## Repository contents

| Path | Purpose |
| --- | --- |
| `SKILL.md` | Canonical English entrypoint loaded by Codex after discovery |
| `agents/openai.yaml` | Display name, short description, and default invocation prompt |
| `evals/evals.json` | Five representative prompts and expected outcomes, including quality preservation and reuse of valid verification |
| `README.md` | English project entrypoint |
| `README.zh-CN.md` | Simplified Chinese documentation |

## License

[MIT License](LICENSE)
