---
name: fixed-character-life-photo-skill
description: 为同一成年角色生成和返修生活照提示词；使用 Character Atlas、参考职责分离和差量提示，检查身份一致、场景还原与人物环境融合。
metadata:
  version: "1.4.0"
---

# Fixed Character Life Photo — Character Atlas Edition

身份一致性优先于造型、场景装饰与风格强化。默认输出可复制提示词；用户要求生成时，使用当前环境可用的图像工具。不得编造工具参数、读取权限或已生成结果。

## 使用者提供的身份输入

本公开版没有默认人物、人脸代号或预置身份照片。每次使用用户明确选择的成年角色及其有权使用的参考图；只读取该角色的 identity 与 manifest，不混合不同人的身份。姓名、职业、性格、服装和场景由用户的本次需求决定。

需要复用时按 [Character Atlas](docs/character_atlas.md) 自建私有图集。包内 [sample](character_atlas/sample/identity.md) 只演示字段，manifest为空且未获批准，不能作为可用身份来源。没有可访问参考时可以输出文字方案，身份锁定须标为 unavailable；不凭空读取用户图库。

## 生成前硬性要求

实际生成前必须执行 [Generation Requirements](docs/generation_requirements.md)，完成 [Shot Brief](templates/shot_brief.md)。关键画面意图缺失且未授权自动补全时，先集中补齐，不自行开批量生成。当前指令、已确认上下文或明确授权预设可以满足要求；不增加重复确认。身份 Anchor 与表情、发型、动作、机位等 Shot Variables 分离。

## 执行流程

1. 确认成年角色、目标与身份来源。读取角色 identity 和 manifest，核对图片真实可访问及 approval 状态。没有身份参考时可设计文字提示，但标记身份锁定 unavailable。
2. 按 [Character Atlas](docs/character_atlas.md) 建立 Immutable Character Anchor，未知特征保持 unknown，不从场景人物补齐。
3. 归一化 Hair、Pose、Composition、Environment、Light [五类锚点](docs/scene_fidelity_anchors.md)。保留 explicit / inferred / missing / conflict 状态；先解决冲突。
4. 默认 Text-only First：场景优先由文字建立，身份图仍可输入。用户要求还原场景参考或关键空间关系难以文字化时走 Reference-assisted。
5. 按 [选择规则](templates/reference_selection_rules.md) 自动选最近的已批准身份参考，并用 [Router](docs/reference_router.md) 为每张输入图声明职责和禁止继承项。不得只因上一张生成得较新就把它当身份来源。
6. 选择单一最接近的 v1.2 Preset 骨架，按 [Delta-only](docs/delta_prompting.md) 编译 BASE / KEEP / CHANGE / AVOID / SUCCESS。删除已有参考中的重复描述，不删除必要场景目标和身份约束。
7. 默认采用 [Two-stage pipeline](docs/two_stage_pipeline.md)：Stage A 通过身份门，再执行 Stage B。已有适用且身份通过的批准图可复用 Stage A；记录 reuse，不伪称重新生成。
8. 按 [输出格式](templates/prompt_output_format.md) 提供路由、阶段提示与可观察 QA 目标；实际生成后执行 [三轴 QA 与 Retry](templates/qa_checklists.md)。未看见图像时 QA 为 NOT-RUN。
9. 返修使用 [Revision Delta Mode](docs/revision_delta_mode.md)。反复漂移按 [一致性阶梯](docs/consistency_ladder.md) 升级；生成候选不能自动进入 approved 库。

## 必须保持

- 身份来源属于同一角色；不同人的身份不得合并。Anchor 改版需要用户明确确认，并保留旧版本。
- 场景图人物的脸、年龄、体型身份不得迁移。Style 不得覆盖身份结构。
- 光线允许改变肤色的画面呈现，表情与透视允许改变投影；不可把这些变化当作身份结构改写。
- 身份锁定保护基础结构，不冻结表情。按 [表情形变规则](docs/expression_deformation.md) 允许眼睑、脸颊、嘴形和下颌开合随目标情绪合理联动；身份和表情分别验收，不用增加皮肤细节补救僵硬。
- 发型状态、服装、动作、光线可变；角色明确锁定的发际线、发色基准或体型比例仍须保留。
- 人物与环境共享受光、曝光、锐度、噪点、景深与接触关系。设备名须转译为可观察的成像行为。
- 不支持多图/编辑时输出工具限制与降级方案；不承诺 prompt 能提供像素锁定。
- validated 仅表示静态规范检查，不代表生图或身份验收成功。

## 按需读取

- 身份定义：[identity schema](templates/character_identity_schema.md)、[身份策略](docs/identity_policy.md)
- 图集字段：[manifest schema](templates/atlas_manifest_schema.md)
- 总体设计：[architecture](docs/architecture.md)、[workflow](docs/workflow.md)
- Preset 扩展：[preset schema](templates/preset_schema.md)、[negative library](templates/negative_prompt_library.md)
- 完整例子：[atlas routing](examples/example_atlas_routing.md)

## 克制的真实感修正

默认 realism: preserve；先保护身份和原有美感，只有发现具体蜡感、涂抹感或全图质感不一致时才启用 targeted。按 [Facial Realism](docs/facial_realism.md) 接入 Stage B 和返修，不默认加瑕疵、放大毛孔或改用人像镜头。多脸验证见 [测试方案](docs/multi_face_testing.md)。

## 4K 输出要求

每次照片交付默认要求 4K，按 [4K 交付规则](docs/output_resolution.md) 设置与核验像素尺寸。优先原生输出；不支持时明确实际尺寸，必要时使用可用的高质量放大流程，并标注 upscaled。不得仅在 prompt 写“4K”就宣称交付 4K。
