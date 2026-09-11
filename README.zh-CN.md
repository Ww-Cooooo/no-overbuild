[English](README.md) | **简体中文**

# No Overbuild

> 想得全面，把产品做好；精简无效负担，不降低品质。

Codex 很容易想到许多风险和未来可能性。问题不在于想得多，而在于把想到的每一种情况都做成框架、字段、门禁、审批和大规模回归，最后让一个本来不复杂的项目变得昂贵、脆弱又难以修改。

No Overbuild 是一个面向 Codex 的公开 Skill。它让 Codex 在设计、编程、修复、重构、测试和技术工作流中保持四件事：

- **小故障不能拖死整体：**能安全恢复就修复，否则隔离受影响的部分，保留用户工作。
- **全面思考，把产品做好：**认真实现已确认的功能、视觉、动效、交互等要求，不交付缩水替代品。
- **验证精准，流程务实：**去掉无价值测试、无变化的重复验证和冗余审批、文档，保留保护实际功能与数据的检查。
- **全面思考不等于全面管控：**用风险帮助判断，不把每种可能性都做成全局门禁。

精简的是无效负担，不是产品品质和完成度。工具、依赖和抽象按实际收益与维护成本取舍：有价值的框架，不会因为增加代码就变成过度工程化；复杂的流程，也不会因为看起来严谨就自动有价值。

例如，一个五人使用的本地工具出现单项导出错误时，它会先修复真实故障、保留用户工作并隔离导出失败，而不是顺手增加消息队列、独立服务和完整监控平台；如果任务本身涉及订单、权限或不可逆数据迁移，它仍会保留与风险相称的事务、回退和验证。

同样，用户已经要求精致的界面和有意义的动效，“做得轻量”不是交付静态占位页面的理由。Skill 用这些指令引导 Codex 做决定，不代表自动保证每次结果。

## 为什么实际 Skill 使用英文

安装并被发现后，Codex 加载的正式入口 [SKILL.md](SKILL.md) 使用英文；仓库同时提供中英文 README。这样只维护一份正式指令，避免两种语言分别修改后产生规则漂移，也方便不同地区的开发者和工具共同审阅。

这不代表 Codex 不能理解中文。No Overbuild 当前仍以 Codex 为正式目标；其他兼容 Agent Skill 结构的宿主可能能够读取相同的 `SKILL.md`，但尚未作为本版本的兼容承诺。

## 什么时候使用

适合让 Codex 在这些工作中采用：

- 新增或重构软件功能；
- 修复一个错误却发现方案正在不断膨胀；
- 设计 Agent、自动化或多步骤技术工作流；
- 决定是否需要新框架、服务、协议、Schema、依赖或状态机；
- 设计容错、升级、迁移、测试和发布方式；
- 一个局部问题正在阻塞整个程序或整项任务。

简单问答、翻译和普通文字修改不需要使用它。

## 安装

如果希望 Codex 直接执行安装，可以把下面这段请求发给它：

```text
请检查并安装这个 Codex Skill：https://github.com/Ww-Cooooo/no-overbuild
只授权检查并把这个仓库复制到我的个人 Skill 目录；不要安装依赖、修改项目，也不要覆盖、删除或更新已经存在的 Skill。如果目标已经存在，停止并报告它的路径和来源。
安装完成后告诉我实际位置和复制了什么。我会另外打开一个新任务验证是否发现 $no-overbuild。
```

这段请求只授权检查并把当前仓库复制到个人 Skill 目录，不授权安装依赖、修改项目或覆盖已经存在的 Skill。

也可以手动克隆到 Codex 的个人 Skill 目录。

手动方式需要本机已有 Git，并且目标 `no-overbuild` 目录尚不存在；如果已经存在，先停止并报告实际路径与来源，不得二次克隆、删除、覆盖或盲目更新。

### Windows PowerShell 7

```powershell
$skillRoot = Join-Path $env:USERPROFILE ".agents\skills"
New-Item -ItemType Directory -Force -Path $skillRoot | Out-Null
git clone https://github.com/Ww-Cooooo/no-overbuild.git (Join-Path $skillRoot "no-overbuild")
```

### macOS 或 Linux

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Ww-Cooooo/no-overbuild.git "$HOME/.agents/skills/no-overbuild"
```

安装后可以先在终端只读核对实际文件。

Windows PowerShell 7：

```powershell
$skillRoot = Join-Path $env:USERPROFILE ".agents\skills"
$skillEntry = Join-Path $skillRoot "no-overbuild\SKILL.md"
Test-Path -LiteralPath $skillEntry
Select-String -LiteralPath $skillEntry -Pattern '^name: no-overbuild$'
```

macOS 或 Linux：

```bash
skill_entry="$HOME/.agents/skills/no-overbuild/SKILL.md"
test -f "$skill_entry" && grep -Fx 'name: no-overbuild' "$skill_entry"
```

文件存在且能找到名称后，再打开一个新的 Codex 任务，让 Skill 列表重新加载：

```text
请先确认 no-overbuild 出现在当前任务的可用 Skill 列表中，再读取它，并告诉我实际解析到的 SKILL.md 路径；先不要修改任何项目文件。
```

Codex 能报告可用 Skill 和实际入口路径，才说明当前新任务已经发现了它。若希望某次工作确定使用该 Skill，请显式写出 `$no-overbuild`；自动采用取决于当前任务与 Skill 描述是否匹配。

## 使用

可以显式调用：

```text
使用 $no-overbuild 修复这个问题。先想全影响和容错，但不要为了一个局部错误引入新的重型框架。
```

也可以直接描述开发任务。匹配到设计、实现、修复、重构、测试、迁移或故障范围问题时，Codex 可以自动采用这套判断方式。

## 它会怎样影响工作

No Overbuild 不规定固定技术栈，也不要求输出一份额外的架构报告。它在工作过程中引导 Codex 做决定：

1. 先判断真实目标、实际用户、规模、风险和现有结构；
2. 把必要边界想全，但不把所有可能性都实现；
3. 复用适合的部分，新增工具或结构看收益是否值得成本；
4. 让故障可恢复、对用户可见并明确说明，并尽量停在发生的位置；
5. 检查受影响的行为与真实风险；相关内容和条件未变，就复用已通过的证据，只因新改动、失败或未解决疑点扩大验证。

相关专业 Skill 仍需落实，不能借 No Overbuild 省略它们有效的质量要求。哈希能证明字节一致，不能证明好用；测试数量多、报告重复写，也不代表产品更好。

## 边界

- 不会扩大用户授予 Codex 的权限；
- 不会降低用户数据、秘密、身份、权限和不可逆操作所需的保护；
- 只有可以安全恢复的局部错误才继续或降级；可能污染状态、破坏正确性或造成不可逆结果时，停止对应动作并明确报告；
- 不会因为追求精简而删除必要功能或验证；
- 不会自动执行网络操作、安装依赖或修改其他项目；
- 当前仓库包含 Skill 指令、展示元数据，以及由提示和预期结果组成的五个评测用例；不包含可执行脚本或评测执行器，用例本身不代表行为测试已经通过。

## 仓库内容

| 路径 | 用途 |
| --- | --- |
| `SKILL.md` | 安装并被发现后由 Codex 加载的英文正式入口 |
| `agents/openai.yaml` | Skill 的显示名称、简介和默认调用提示 |
| `evals/evals.json` | 五个代表性提示与预期结果，包含品质不能缩水、有效验证可以复用 |
| `README.md` | 英文项目入口 |
| `README.zh-CN.md` | 当前中文说明 |

## 许可证

[MIT License](LICENSE)
