# Shot Brief — 单张生成契约

生成前按 [硬性要求](../docs/generation_requirements.md) 填写。critical 字段的 proposed/missing 使 intent_gate 为 NEEDS-INPUT；明确授权补全的字段可标 delegated。用户已明确的内容直接继承，不重复确认。

```yaml
skill_version: "1.4.0"
intent_gate: NEEDS-INPUT # READY | NEEDS-INPUT
character_id: null
primary_identity: null
approval_evidence: null
identity_invariants: []
unknown_identity_features: []
request_count: null
shot_id: null
scene_and_activity: {value: null, source: missing}
expression_and_gaze: {value: null, source: missing}
expression_deformation: {intensity: null, eyes_screen_left: null, eyes_screen_right: null, cheeks_and_mouth: null, head_body_coordination: null} # fill relevant observable cues; no arbitrary numeric thresholds
hair: {value: null, source: missing}
outfit: {value: null, source: missing}
pose: {value: null, source: missing}
composition: {framing: null, camera_height: null, subject_angle: null, capture: null, source: missing}
environment: {value: null, source: missing}
light: {direction: null, softness: null, environment_spill: null, source: missing}
texture_preference: {reference: null, realism_mode: preserve, source: missing}
aspect_ratio: "3:4"
resolution_long_edge: 3840
series_variation: null
delegated_choices: []
unresolved_conflicts: []
stage_a: NOT-RUN # reuse only when view/expression are suitable and identity passes
reference_roles: []
```

## 工具提示编译

```text
BASE: 实际输入图和职责；阶段与目标。
KEEP: 不可变身份和本次明确保留项。
CHANGE: 完整场景差量与五类锚点；未要求锁定的表情/发型/机位放这里。
AVOID: 本次身份/质感/接触关系的主要失败风险。
SUCCESS: 可观察的身份、场景、融合与像素要求。
```

工具发送后保存真实 prompt、参考映射及实际尺寸；未运行项保持 NOT-RUN。不支持的参数省略并说明限制。
