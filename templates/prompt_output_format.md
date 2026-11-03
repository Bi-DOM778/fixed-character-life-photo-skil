# Prompt Output Format — v1.3

## 0. Intent / Shot Brief

先记录 [Shot Brief](shot_brief.md) 的 intent_gate、关键字段来源、授权补全范围和冲突。NEEDS-INPUT 时可以设计方案，但不得实际调用生成。READY 后的实际提示必须包含目标差量与五类锚点。

## 1. Run Card

```yaml
skill_version: "1.4.0"
character_id: my-character
anchor_version: "1.0"
preset: BEDROOM_LAZY_HOME_DAYLIGHT
mode: text-only-first # 或 reference-assisted
identity_lock: unavailable # available | unavailable | conflict
primary_identity: null
support_refs: []
selection_reason: no approved images supplied
fallback: null
stage_a: NOT-RUN # generated | reuse | NOT-RUN
stage_b: NOT-RUN # edited | regeneration | NOT-RUN
aspect_ratio: "3:4"
anchor_status: {hair: explicit, pose: explicit, composition: inferred, environment: explicit, light: missing}
generation_context: {tool: null, model_version: null, seed: null, reference_controls: null}
retry_budget: {total_generation_calls: 6, same_defect_retries: 2}
```

## 2. Reference Roles

所有模式列实际输入序号、ref id、role、允许/禁止继承项、阶段及实际 approval；没有输入图写 none。仅定义提示词时序号标 planned，不能伪称已经上传。

## 3. Stage Prompts

每阶段一个可复制英文块：BASE / KEEP / CHANGE / AVOID / SUCCESS，可编译为连贯文本。Stage A 保证身份；Stage B 描述完整目标场景差量与五类锚点。若 A 复用写明 ref 与验收证据。

## 4. Negative Constraints

按本次失败风险选取；工具支持 negative 参数才输出独立字段，否则合入 AVOID。

## 5. QA / Retry

列三轴可观察目标、每项缺陷、PASS / FAIL / REVISE / NOT-RUN；实际未生成时全部 NOT-RUN。记录比较身份图、每次 delta、工具配置与调用次数；不要填写虚构 seed。

## 6. Revision / Library Status

返修输出 KEEP / CHANGE / AVOID / SUCCESS 和退出条件。记录 candidate / approved / rejected；人工批准者与日期未知时不能填 approved。

## 7. Facial Realism Decision

```yaml
realism_mode: preserve # preserve | targeted | off
observed_defect: null
texture_keep: original softness, natural sheen, identity skin baseline
realism_delta: null
texture_regression_check: NOT-RUN
user_texture_preference: pending
```

preserve 不自动追加纹理增强词；targeted 输出一个主要缺陷与最小 delta。不默认附加镜头、胶片颗粒、CFG 或重绘幅度。

## 8. 4K Delivery

按 [分辨率规则](../docs/output_resolution.md) 记录 requested_dimensions、actual_dimensions、source_dimensions、provenance 与 resolution_status。所有最终照片默认长边 3840；未生成时 NOT-RUN，能力不足时 UNMET。交付说明区分原生与放大。
