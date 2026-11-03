# Workflow — v1.3

1. Intake：成年角色、identity/manifest、目标角度/表情/景别、穿搭、场景、设备感、画幅与预算。缺身份仍可设计 prompt，但锁定 unavailable。
2. 模式：Text-only First 优先文字化场景；复杂参考还原走 Reference-assisted。两者都可使用身份 Atlas。
3. 提取 [五类锚点](scene_fidelity_anchors.md)，处理冲突；从 presets 选单一场景骨架。
4. 用 [Selector](../templates/reference_selection_rules.md) 过滤并排序真实 approved 图；生成 [角色表](reference_router.md)。
5. 读取 [Delta compiler](delta_prompting.md)；按角色身份约束和目标差量编译提示，替换旧 Preset master 固定句。
6. 执行或输出 [A/B pipeline](two_stage_pipeline.md)。Stage A 身份不通过不继续 B；B 后三轴重新检查。
7. 保存真实运行信息、QA、调用次数与最小返修 delta。使用 [输出格式](../templates/prompt_output_format.md)。
8. 遵守 [Retry](../templates/qa_checklists.md) 预算；人工确认后更新库与 manifest。覆盖不足走 [一致性阶梯](consistency_ladder.md)。

优先级：Immutable Anchor → 用户最新明确 shot variables → 显式锚点 → 职责正确的参考 → Preset 默认。用户明确要修改身份时先版本化 anchor，不能将其当普通场景覆盖。

## 质感与测试

Stage B 前记录 preserve / targeted / off 与具体缺陷；默认 preserve。生成后使用 [真实感规则](facial_realism.md) 做退化比较。多角色迭代按 [测试方案](multi_face_testing.md) 分轮推进，不用未运行测试宣称泛化通过。

## 最终输出尺寸

交付前执行 [4K 文件核验](output_resolution.md)。目标长边 3840 且保持画幅；原生优先，放大必须标注，能力不足如实报 UNMET。
