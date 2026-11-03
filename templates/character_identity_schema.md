# Character Identity Schema

复制为角色 identity.md。字段内容应由 master 与人工确认建立，不能默认套用示例脸。

```yaml
schema_version: "1.0"
character_id: my-character
anchor_version: "1.0"
adult: true
master_ref_id: master-front
approval: unavailable  # unavailable | candidate | approved | rejected
approved_by: null
approved_at: null
immutable:
  face_shape_jaw: unknown
  eyes_spacing_eyelids: unknown
  nose_structure: unknown
  lips_proportions: unknown
  adult_age_impression: unknown
  asymmetry_marks: unknown
  skin_texture_baseline: unknown
  body_proportions: unknown
  hairline_natural_color: unknown
mutable:
  - expression
  - hairstyle_state
  - makeup
  - outfit
  - pose
  - scene
  - camera
  - lighting
evidence: []
```

每项 immutable 的正式值包含 description、source_ref_ids、confidence（high/medium/low）。unknown 不进入正向 prompt。体型未知时不从另一人物全身图学习体型。

immutable 指基础身份结构，不是不同表情下的像素轮廓。mutable.expression 允许合理的眼睑闭合、脸颊位移、唇部拉伸/前突和下颌开合；按 [表情形变规则](../docs/expression_deformation.md) 评估，不能把平静表情写成身份不变量。

master_ref_id 必须指向 manifest 中同角色 approved 记录，才可声明 anchor approved。修改骨骼、年龄基准或身份标记视为 anchor 新版本；写明修改理由及用户确认，不把普通返修当身份升级。
