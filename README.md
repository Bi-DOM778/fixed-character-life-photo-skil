# Fixed Character Life Photo Skill

> v1.4.0 · Public Character Atlas Edition

为用户选定的同一成年角色组织生活照提示词与定向返修：分清身份、场景、姿势和光线参考，通过图集选图、分阶段生成及质量检查减少换脸、场景错位和反复返工。

A reusable, tool-agnostic skill for consistent adult-character lifestyle photo prompting and revision. Bring your own authorized references; no personal face assets are included.

## 适合什么需求

- 给同一成年角色持续制作生活照，切换穿搭、表情、机位与环境。
- 参考某张图的动作或场景，同时保持用户指定角色的身份。
- 修正光线、表情或姿态，保留已经满意的画面部分。
- 为虚拟角色、数字人或虚拟模特组织可复用的提示与验收流程。

## 快速开始

将整个仓库作为 `fixed-character-life-photo-skill` 安装到支持SKILL.md的环境，或直接让智能体读取 [SKILL.md](SKILL.md)。图像生成与编辑依赖当前环境实际提供的工具；无图像工具时可交付可复制提示词。

Codex（Bash）：

```bash
git clone https://github.com/Bi-DOM778/fixed-character-life-photo-skil.git ~/.codex/skills/fixed-character-life-photo-skill
```

Codex（PowerShell）：

```powershell
git clone https://github.com/Bi-DOM778/fixed-character-life-photo-skil.git "$env:USERPROFILE/.codex/skills/fixed-character-life-photo-skill"
```

目标目录已存在时先检查，不覆盖自己的私有版本。也可下载仓库ZIP，将目录命名为 `fixed-character-life-photo-skill` 后放入技能目录。

提供自己有权使用的成年角色参考，明确目标场景和需要保留的部分。首次可以直接提供当前对话中的身份图；需要跨次复用时，按 [Atlas说明](docs/character_atlas.md) 把空 [sample](character_atlas/sample/identity.md) 复制为自己的私有角色目录，再填写identity与manifest。示例没有照片，也没有approved身份。

```text
使用 $fixed-character-life-photo-skill。
以我提供的成年角色身份参考为唯一身份来源，场景图仅提供构图和光线。
目标：日间咖啡馆门口，全身，轻松微笑，朋友手机抓拍感。
服装与发型采用我本次指定的方案，不把示例造型锁成身份特征。
先输出参考图职责与两阶段提示；没有实际生成时，将QA标为NOT-RUN。
```

## 工作流

用户目标 → 同角色身份Anchor → 最近批准视图选择 → 参考图职责路由 → 五类场景锚点 → BASE / KEEP / CHANGE / AVOID / SUCCESS → Stage A身份检查 → Stage B场景与融合检查 → 人工确认。

- **身份与场景解耦**：场景人物不能提供角色脸、年龄或身体身份。
- **变化可控**：身份基础结构与表情、发型、服装、姿势和光线分开处理。
- **定向返修**：保留成功部分，每轮处理具体缺陷，避免沿失败图无限重绘。
- **按证据验收**：身份、场景、人物环境融合分别检查；静态检查不代表模型效果保证。

## 文档与模板

| 内容 | 入口 |
|---|---|
| 默认执行入口 | [SKILL.md](SKILL.md) |
| 图集与身份字段 | [Atlas](docs/character_atlas.md)、[Identity](templates/character_identity_schema.md)、[Manifest](templates/atlas_manifest_schema.md) |
| 最近参考选择与职责 | [Selector](templates/reference_selection_rules.md)、[Router](docs/reference_router.md) |
| 生成前画面契约 | [Requirements](docs/generation_requirements.md)、[Shot Brief](templates/shot_brief.md) |
| 分阶段与返修 | [Two-stage](docs/two_stage_pipeline.md)、[Delta](docs/delta_prompting.md)、[Revision](docs/revision_delta_mode.md) |
| 表情与质感 | [Expression](docs/expression_deformation.md)、[Realism](docs/facial_realism.md) |
| 验收与输出 | [QA](templates/qa_checklists.md)、[Output](templates/prompt_output_format.md)、[Resolution](docs/output_resolution.md) |
| 使用示例 | [Atlas routing](examples/example_atlas_routing.md)、[Bedroom](examples/example_bedroom_daylight.md)、[Café](examples/example_cafe_ccd.md)、[Street](examples/example_street_flash.md) |

保留卧室、街头、咖啡馆三类共9个 [Preset](presets/)。示例服装、发型和摄影条件是可覆盖的场景变量，不预设人物身份。`Status: validated`仅指文档结构与约束的静态状态。

## 私有素材与能力边界

公开包只包含文字规范、通用模板和空示例图集，不含人脸图片、个人身份描述、预置批准记录、密钥或私人生成结果。自建角色放在被.gitignore排除的私有目录；不要直接把sample填成个人图集后提交。

实际身份一致性依赖参考覆盖与图像工具能力，未提供参考时不能承诺锁脸。所有人物按成年人处理；使用者应确认图像使用与发布权限，仓库MIT许可不授予第三方人物肖像或照片权利。

默认最终照片目标为长边3840像素，保留画幅；以实际文件核验，放大须标注来源，工具不支持时如实报告UNMET。没有真实生图或视觉检查时，相关结果保持NOT-RUN。

## 许可与版本

本仓库沿用 [MIT License](LICENSE)。版本说明见 [CHANGELOG](CHANGELOG.md)。
