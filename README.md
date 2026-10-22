# AI 信息核验三步法

一个包含三个能力的 Agent Skill：**启动核验 → 核对引用 → 围绕证据追问**。

适合检查网络主张、核对 AI 引用和改进证据不足的回答。核验过程中遇到过于专业的解释，也可要求按读者水平重述，并保留来源、条件和未知。

> 非官方实现。方法来源于 Mike Caulfield 的视频及配套文章；本项目不代表原作者认可、背书或授权。来源与第三方许可范围见 [SOURCES.md](SOURCES.md)、[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

## 最快开始

安装完整文件夹后，直接在支持技能的工具中说：

```text
用 ai-verification-three-moves 核查这段内容：
[粘贴待查主张、截图文字或链接]
请找对应依据，指出哪些能确认，哪些还不能。
```

只核对 AI 回答时：

```text
用 ai-verification-three-moves 检查下面的回答和引用：
[粘贴 AI 回答及来源]
请核对原文是否支持每项结论，不要只确认链接存在。
```

继续追问时：

```text
这份核验回答的来源不够合适。
请用 ai-verification-three-moves 帮我追问更直接的证据，
再解释给初中生，保留来源、适用条件和不确定性。
```

## 安装到 Codex

本仓库根目录就是一个完整技能。下载仓库 ZIP 后，将解压后的文件夹命名为 `ai-verification-three-moves`，保留 `SKILL.md` 和整个 `references/`。

按使用范围选择一个位置：

| 范围 | 完整技能文件夹的位置 |
|---|---|
| 个人使用 | `~/.agents/skills/ai-verification-three-moves/` |
| 当前项目 | `<项目根目录>/.agents/skills/ai-verification-three-moves/` |

已有同名目录时，先保留旧版，避免把两版内容合并。安装后可以直接点名调用；CLI / IDE 中也可使用 `$ai-verification-three-moves`。如果没有出现，重启 Codex。

路径、调用方式和重新发现行为依据 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。其他 Agent 工具的安装路径请按其文档设置；本项目未逐一测试兼容性。

## 三个能力

| 你想做什么 | 技能怎样处理 |
|---|---|
| 不知道从哪里开始核查 | 直接使用原主张或可读图片准备初次查询，保留未确认项 |
| 引用似乎支持不了结论 | 打开来源、定位候选段落，再核对对象、时期、单位及条件 |
| 回答证据不足或太难 | 准备证据导向的追问，或按所给材料完成保留限定条件的重述 |

没有联网、来源打不开或没有实际提交查询时，会区分“仅准备”“仅核对所给摘录”和实际执行。不会用模型认同、关键词命中或机构名气代替证据。

## 范围与已知限制

- 视频依据为一份未经音画校对的英文自动字幕；末句不完整，视频发布日期未知。只覆盖所提供正文，不保证覆盖完整视频。
- 示例描述的是讲者的口述演示。普利茅斯岩、登月舱脚垫案例中的数字、物理解释、具体论文及来源真实性没有在本项目中逐项独立核实。
- 输出字段、状态、缺输入分支、提示模板以及简化时保留证据的规则，是本项目的实现约定。
- 不提供专业事实裁决、统一证据评分、复杂冲突裁决或通用停止阈值。
- 已完成主流程自测，尚未完成独立盲测；不宣称比未加载技能更准确。详见 [VALIDATION.md](VALIDATION.md)。

## 仓库内容

```text
ai-verification-three-moves/
├── SKILL.md
├── references/
│   ├── capabilities/
│   ├── capability-index.md
│   ├── cheatsheet.md
│   ├── glossary.md
│   └── overview.md
├── README.md
├── SOURCES.md
├── VALIDATION.md
├── LICENSE
├── LICENSE.md
├── THIRD_PARTY_NOTICES.md
└── LICENSES/
    └── cangjie-skill-MIT.txt
```

不包含完整视频转写、原始截图、开发过程、测试输出、个人路径、运行清单或历史备份。技能本身是说明文档，不包含需要执行的脚本；联网及模型能力由宿主提供。

## 许可

本项目新增的技能编排和模板中，发布者有权授权的部分采用 [MIT License](LICENSE)。具体边界见 [许可范围](LICENSE.md)。cangjie 的相应 MIT 声明单独保留；原视频、文章和第三方引文不因本项目采用 MIT 而被重新授权。
