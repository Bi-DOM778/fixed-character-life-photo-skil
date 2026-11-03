# Closest Reference Selector

输入：character_id、anchor_version、目标 yaw/pitch、expression、framing、工具输入容量，以及已核对 manifest。输出：primary_identity、support_refs、fallback_reason、excluded_refs 和完整选择理由。

## 自动选择

1. 只保留同角色、同 anchor、approved、真实可访问且身份 PASS 的图；primary 必须脸可读。严重遮挡排除。验证 hash；未提供或无法验证时标记 unverified，不能假称已核验。
2. 目标角度未知时采用 master-front，不从场景脸猜身份。目标 ±30..60° 优先对应 left-45/right-45；±60..100° 优先相应侧 profile；近正面优先 master-front。其他角度使用最接近的可用图并记录覆盖不足。
3. 候选以如下代价升序排序（是确定性启发式，非生物识别置信度）：
   `cost = circular_yaw_distance/180 * 0.55 + abs(pitch_difference)/180 * 0.15 + expression_mismatch * 0.20 + framing_mismatch * 0.10`。
   yaw 距离取 min(abs(a-b), 360-abs(a-b))。未知候选角度对应距离项记 1；expression 不同或未知记 1，相同记 0；framing 不同或未知记 1。
4. 同代价依次优先无遮挡、master-front、id 字典序。选择一个 primary，避免把不同视图混成平均脸。
5. 全身目标增加 approved fullbody 作为身体比例支持；大笑/眨眼等复杂表情增加匹配 expression ref。支持图不替换 primary，且必须与 anchor 一致。最多各一张；不足容量时优先 primary，再身体，再表情，按本次风险调整并记录。
6. master 是裁决来源，不一定每次上传。工具容量允许且新角度风险高时可补 master；容量不足保留 primary 并记录限制。

## 缺失与降级

| 条件 | 行动 |
|---|---|
| 侧面 slot 缺失，master 可用 | 用最近角度或 master；标注低覆盖，Stage A 生成候选并验收 |
| expression 缺失 | 用最近角度身份图，文字描述表情肌肉变化，不伪造 ref |
| fullbody 缺失 | 保留脸参考；身体比例 unknown，不能借用场景人物体型 |
| 所有 approved 身份图不可用 | identity_lock unavailable；继续文字设计，生成依赖身份时先取得可用参考 |
| 单图工具 | primary 优先；场景/姿势转文字；无法承载所需控制时报告限制 |
| 左右方向不确定 | 标记 unknown，以 master 回退；不得自动镜像 |

示例：左颊 45°、全身、微笑 → left-45 primary + fullbody support + expression-smile support（均需实际 approved）；缺 expression 时删除该支持并写原因。
