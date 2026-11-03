# Multi-face Test Record

每目标复制一份；结果来自真实图像观察和用户反馈。

```yaml
test_id: null
round: R1
skill_version: "1.4.0"
character_id: null
anchor_version: null
primary_identity: null
support_refs: []
reference_roles: []
selection_reason: null
fallback: null
target: {angle: null, expression: null, framing: null, scene: null, preset: null}
realism: {mode: preserve, observed_defect: null, delta: null}
tool: null
model_version: null
parameters_supported: {}
parameters_used: {}
baseline_path: null
edited_path: null
stage_a: NOT-RUN
stage_b: NOT-RUN
generation_call_count: 0
identity: NOT-RUN
scene_fidelity: NOT-RUN
scene_integration: NOT-RUN
quality_regression: NOT-RUN
user_texture_preference: pending # original | edited | equal | pending
unrequested_marks_or_aging: NOT-RUN
overall: NOT-RUN
library_status: candidate
reviewer: null
review_date: null
```

## 观察证据

逐项说明：身份结构、肤色/纹理基准、目标缺陷、全图一致性、新增瑕疵或老化、质感是否干杂过锐；分别给 PASS / FAIL / REVISE / NOT-RUN，跳过项写 N/A 与原因。用户偏好未取得时写 pending，不替用户确认审美验收。

## 下一步

保留原图 / 接受候选 / 回退 / 最小 delta / 工具或参考覆盖限制。正式 approved 仍须人工确认身份与最终输出。
