# Modern Web UI Skill

面向 Codex 的中文网页 UI 设计 skill，将视觉参考转化为布局、排版、色彩、材质和组件规则，并指导界面实现与验证。

## 适用场景

- 设计新页面，或改善已有网页的视觉表现。
- 从截图、参考页面或设计作品中提炼可执行的设计规范。
- 实现摄影与编辑排版、深色玻璃质感、柔和浅色应用界面等视觉方向。
- 检查响应式布局、中文断行、内容溢出与关键交互。

遵循项目已有的技术栈与组件体系。仅涉及业务逻辑或后端的任务无需启用。

## 安装到 Codex

在支持内置 `skill-installer` 的 Codex 中发送：

```text
$skill-installer 请从 https://github.com/hsjv-Chai/modern-web-ui-skill 安装 skills/modern-web-ui
```

也可以直接提供 skill 的完整目录链接：

```text
$skill-installer https://github.com/hsjv-Chai/modern-web-ui-skill/tree/main/skills/modern-web-ui
```

安装后，在下一轮对话中查看是否可用；如果没有出现，重启 Codex。

### 手动安装（macOS / Linux）

需要 Git。在终端执行以下命令，将整个 skill 文件夹安装到个人技能目录；目标已存在时会停止，避免覆盖已有版本。

```sh
(
  set -eu
  skill_dest="$HOME/.agents/skills/modern-web-ui"
  if [ -e "$skill_dest" ] || [ -L "$skill_dest" ]; then
    echo "目标已存在，请先检查已有版本：$skill_dest" >&2
    exit 1
  fi
  skill_tmp=$(mktemp -d)
  trap 'rm -rf "$skill_tmp"' EXIT
  git clone --depth 1 https://github.com/hsjv-Chai/modern-web-ui-skill.git "$skill_tmp/repo"
  mkdir -p "$HOME/.agents/skills"
  cp -R "$skill_tmp/repo/skills/modern-web-ui" "$skill_dest"
)
```

只想在某个项目使用时，将完整的 `skills/modern-web-ui/` 文件夹复制到该项目的 `.agents/skills/modern-web-ui/`。请同时保留 `references/` 和 `agents/`，不要只复制 `SKILL.md`。

技能目录及安装行为参考 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 使用

在 Codex 对话中明确调用：

```text
$modern-web-ui 帮我优化当前页面的视觉层次，保留现有技术栈，并检查桌面和移动端布局。
```

```text
$modern-web-ui 根据这张参考图，为博客首页整理设计规范并实现页面，重点处理排版、留白和中文可读性。
```

也可直接描述网页设计任务，由 Codex 根据 skill 的描述决定是否启用。提供页面文件、截图、参考链接或品牌约束，有助于确定具体方向。

## 文件结构

```text
skills/modern-web-ui/
├── SKILL.md                       # 技能说明与工作流程
├── agents/openai.yaml             # Codex 展示名称与简介
└── references/design-language.md  # 视觉语言、参数建议与参考边界
```

本 skill 为说明与参考资料，无需额外安装运行依赖。页面实现和浏览器验证使用所在项目及当前环境提供的工具。
