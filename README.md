# dev-handoff-orchestrator

一个供 Codex 开发流程使用的全局 Skill：管理 ChatGPT 顾问协作、关键决策审批、双层进度和会话交接。默认不介入简单的一次性任务。

## 安装

在 Windows PowerShell 中，将仓库克隆到 Codex 用户级 Skill 目录：

```powershell
git clone https://github.com/Zeno-wistom/dev-handoff-orchestrator.git "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator"
```

Codex 也支持其他用户级 Skill 路径；请按当前版本的 Skill 文档配置。不要把 `.dev-handoff.local.json` 放入或提交到此共享仓库。新项目的首次绑定须由用户明确指定准确的 Project 和会话。

ChatGPT 项目指令模板位于 [`ChatGPT 项目级指令.md`](ChatGPT%20项目级指令.md)，用户手动复制到指定 Project。

## 更新与后续发布

此用户请求指定的仓库也是安装目录的 Git 工作副本。修改 Skill 后先运行内置结构校验：

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator"
```

然后检查 `git -C "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator" diff` 和状态；只提交本 Skill 的文件，不提交具体项目配置、密钥、token、日志或个人验证报告。完成提交并推送到 `origin/main`，记录 commit 与推送结果。除非用户要求仅本地保存，已授权的本 Skill 更新应同步推送至这个仓库，不代表可上传其他项目文件。

## 文件结构

- `SKILL.md`：简洁的启用条件和协作规则。
- `references/workflow.md`：Project 绑定、浏览器检查、咨询边界和会话恢复。
- `references/templates.md`：双层进度、审批、咨询与一次复制六项交接模板。
- `references/binding.example.json`：无绑定的示例结构。
- `ChatGPT 项目级指令.md`：供用户复制到 ChatGPT Project 的项目指令。

## 许可证

此仓库目前未附加许可证。仓库公开后，任何人可以在 GitHub 上查看和 fork；未附加许可证时，公开仓库不表示授予通用的复制、再分发或制作衍生作品的权利。若要开源再利用，请先选择适当许可证后再添加。

参考：[GitHub 关于为仓库选择许可证的说明](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)。
