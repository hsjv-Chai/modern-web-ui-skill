# Modern Web UI Skill

面向 Codex 的中文网页 UI 设计 skill，将视觉参考转化为布局、排版、色彩、材质和组件规则，并指导界面实现与验证。

## 适用场景

- 设计新页面，或改善已有网页的视觉表现。
- 从截图、参考页面或设计作品中提炼可执行的设计规范。
- 实现平面图文、纯排版和轻量应用界面，结合透明与磨砂玻璃表达导航、浮层和面板的层次。
- 检查响应式布局、中文断行、内容溢出与关键交互。

遵循项目已有的技术栈与组件体系。仅涉及业务逻辑或后端的任务无需启用。

## 设计原则与流程

- **整体设计前必须查看范例的实际画面。** 优先使用用户提供的范例；未提供时选择相关参考。文字描述、搜索摘要和历史分析不能替代查看。
- 查看后先简述观察结果与借鉴方向，再确定风格、布局和整体视觉实现。没有任何可见的相关范例时，说明阻塞并获取可访问的参考；需求与项目检查可以继续。
- 默认平面化，通过排版、比例、留白、色块与细线建立层级；主动考虑局部透明与磨砂玻璃，整体立体和拟真材质按明确的视觉选择使用。
- 透明与磨砂效果可用于吸顶导航、悬浮工具栏、菜单和轻量面板，保持文字与操作清晰，并提供背景模糊不可用时的稳定表面。
- 内容主题与视觉气质分别确定。字体、配色、插画和文案依据当前项目选择，避免将个人博客固定套成田园慢生活风格。
- 装饰承担明确作用，减少重复的星芒、手绘线、英文副标、编号与标语。博客首页优先让读者找到可阅读的文章。

局部微调按需要查看参考，无需重复整个整体设计流程。完成页面后检查实际的桌面、移动端布局与适用交互，并说明验证范围。

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

如果安装时遇到 Python HTTPS 证书错误，可让安装器改用 Git 下载：

```text
$skill-installer 请从 hsjv-Chai/modern-web-ui-skill 安装 skills/modern-web-ui，使用 Git 方式（--method git）。
```

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
