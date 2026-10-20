# dev-handoff-orchestrator

用于中大型、多阶段开发的 ChatGPT × Codex 顾问交接 Skill：在两端讨论、实现、核验、审批和继续开发时，提供一致的工作流、双层进度和上下文交接格式。

## 安装

Windows PowerShell：

```powershell
git clone https://github.com/Zeno-wistom/dev-handoff-orchestrator.git "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator"
```

已安装的工作副本可在检查工作区干净且远端正确后，运行：

```powershell
git -C "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator" pull --ff-only
```

遇到本地未提交更改或冲突时先核对，不强制覆盖。

## 使用

- 在 ChatGPT 中讨论产品方向，复制可执行 Prompt 给 Codex。
- Codex 开发并完成必要测试后，提供简洁的成果报告、证据和下一步。
- 将报告交给 ChatGPT 解释和审查，需要时再由用户审批重要取舍。
- 切换新会话或跨重要阶段时，生成包含六项当前上下文的一次复制交接 Prompt。
- 项目有明确阶段时持续展示双层进度；缺少可靠验收数据则标为未知。

[ChatGPT 项目级指令.md](ChatGPT%20项目级指令.md) 可用于希望在某个 ChatGPT Project 内统一顾问行为的项目。

## 文件

- `SKILL.md`：角色、开发流程、进度、审批与会话管理
- `agents/openai.yaml`：Skill 名称与入口说明
- `references/workflow.md`：执行及会话恢复细则
- `references/templates.md`：日常汇报、完整交接与执行 Prompt
- `ChatGPT 项目级指令.md`：ChatGPT 项目指令模板

## 修改与发布

仅在核对仓库身份与工作区状态后修改 Skill。提交前审阅变更及敏感信息，并校验结构：

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator"
```

更新后提交并推送至本仓库 `main`；这个授权只适用于本 Skill，不扩展至其他项目。

## 许可证

当前未附加许可证。公开仓库可供查看，但不代表授予通用的复制或再分发许可。需要对外开源复用时再选择许可证。
