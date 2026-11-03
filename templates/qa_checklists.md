# QA Checklists

## Generation Intent Gate

- [ ] 单张 Shot Brief 为 READY；关键意图来自明确指令、确认上下文或授权补全。
- [ ] 表情、发型和机位未被无故写入不可变身份；多图差异符合用户方案。
- [ ] 已将参考职责、KEEP/CHANGE/AVOID 和五类锚点写入真实工具提示。

## Hard Gates

- [ ] 所有人物均被设定为成年人。
- [ ] 主身份来源唯一且无冲突。
- [ ] 没有身份参考时，输出未承诺身份锁定。
- [ ] 场景参考人物的脸部特征未迁移。
- [ ] 没有明显的肢体结构错误或不可能接触关系。

任一 Hard Gate 失败即返修，不进入主观评分。

## Identity Fidelity（0–2 每项）

- 脸型与下颌
- 眼形、眼距与眼睑
- 鼻部和唇部比例
- 年龄印象与自然不对称
- 皮肤纹理与非模板化气质

建议通过线：8/10，且无单项 0。

## Scene Fidelity（0–2 每项）

表情目标按 [表情形变规则](../docs/expression_deformation.md) 独立检查，再纳入 Pose anchor：左右眼状态、嘴形、脸颊联动、情绪幅度和头颈/身体配合。明确目标未达到即 REVISE，不能被其他项目总分抵消。身份相似但表情僵硬不算整体 PASS；身份漂移也不能因表情生动而放行。

- Hair state
- Pose anchor
- Composition anchor
- Environment anchor
- Light behavior

建议通过线：8/10。

## Scene Integration（0–2 每项）

- 人物与环境光向一致
- 色温与曝光属于同一次拍摄
- 锐度、噪点与景深一致
- 接触阴影和遮挡可信
- 人物状态与空间叙事一致

建议通过线：8/10。

## 结论格式

```text
Identity: 9/10 — PASS
Scene: 8/10 — PASS
Integration: 7/10 — REVISE
Primary defect: face is 0.5–1 stop brighter than the room and lacks warm spill
Next delta: lower facial fill; add subtle lamp warmth on camera-right cheek; keep identity and pose
```

分数用于定位，不是跨模型的绝对基准。最终以可观察缺陷和下一步 delta 为核心。


## v1.3 Atlas 与阶段门

- [ ] primary 为同角色同 anchor 的可用 approved 图；角色表与实际输入一致。
- [ ] 未把 candidate、失败返修图或场景人物当作身份源。
- [ ] Stage A 身份先通过；Stage B 再独立检查三轴。
- [ ] 稳定不对称、标记左右和已知身体比例正确；未知不能凭空评分。
- [ ] 表情肌肉、透视投影和场景受光变化未被误判为身份改变。
- [ ] 未把主图的平静眼裂、嘴宽、唇部投影或下颌位置冻结到不同表情；鼻部、唇部比例和下颌等结构证据已结合视角与表情判断。
- [ ] 闭眼等状态使眼形不可判断时，该项标 NOT-RUN，补充同身份适当视角的可辨识证据；不因闭眼遮蔽而给身份满分。
- [ ] 未靠新增毛孔、瑕疵、黑眼圈或锐化补救表情僵硬；现场感检查关注动作、受光和纹理尺度的整体协调。

评分沿用 v1.2 的每轴 0–2 五项、建议 8/10。任何已确认不可变结构漂移是 Identity FAIL，不可由总分抵消。无法看清的关键结构标 NOT-RUN，不能自动给满分；身份 QA 只要关键项不可判断，就不能出身份 PASS。未知 anchor 项记录 N/A，分母与观察范围写清，不声称全身份已验证。

## Retry Policy

默认每个目标最多 6 次生成调用（A/B 初次及全部返修合计）；同一主缺陷最多再试 2 次。用户给出预算时优先使用用户预算。每次先写 defect 与单一主要 delta；必要时联动 1–3 个可验证变量。

| 失败轴 | 下一步 |
|---|---|
| Identity | 停止 B；检查角色图侵入、角度覆盖与 primary；修 A 后再做 B |
| Scene Fidelity | 保持身份，只修首个几何/布局/光线偏差 |
| Integration | 保持结构与场景，修全图受光、曝光、接触、噪点或景深 |
| 同缺陷两次无改善 | 停止叠词；提出更合适参考/Atlas 扩展或工具控制 |
| 工具失败或预算用尽 | 停止；报告已通过版本、未解决缺陷与需要的下一步 |

三轴通过后记录 QA，但正式加入 Atlas/approved_dataset 仍需人工确认。用户拒绝的图保留 rejected 状态，不参与后续身份路由。

## Facial Realism / Texture Preservation

作为 Scene Integration 的补充检查，不新增可抵消身份硬失败的评分轴。

- [ ] 保留参考中原有柔润度、自然光泽和稳定肤色；未无故改变年龄印象。
- [ ] 仅在观察到缺陷时修正；没有随机新增痣、痘、疤、皱纹、黑眼圈或不对称。
- [ ] 纹理尺度符合景别与受光，不强求全身照能看见毛孔。
- [ ] 脸部锐度、曝光、噪点与头发、服装、环境协调。
- [ ] 与认可底图比较，未出现变干、变杂、过锐或光泽被完全抹除。
- [ ] 用户质感偏好独立记录；pending 不能伪填用户认可。

明确质感退化标 REVISE，并保留/回退原图；身份漂移或新增稳定身份标记按硬失败处理。没有实际图像仍为 NOT-RUN。测试记录见 [多脸模板](multi_face_test_record.md)。

## Final Resolution Gate

- [ ] 已读取实际交付文件宽高，达到所选画幅的 4K 目标。
- [ ] 原生/放大来源与放大前尺寸如实记录；没有仅凭 prompt 判定 4K。
- [ ] 保持画幅、身份、表情、肤色与光泽；放大无假毛孔、光晕或过锐。

像素不足时 resolution_status: UNMET，即使三轴 QA 通过也不能称为完整 4K 交付。仅提示词输出为 NOT-RUN。
