# Atlas Manifest Schema

manifest.json 使用 UTF-8；schema_version 与 skill 版本独立。顶层字段：schema_version、character_id、anchor_version、angle_convention、references。references 可以为空，但此时身份锁定 unavailable。

单条 reference 的 JSON 形状：

```json
{
  "id": "left-45",
  "slot": "left-45",
  "path": "refs/face-left-45.png",
  "sha256": null,
  "character_id": "my-character",
  "anchor_version": "1.0",
  "approval": "candidate",
  "approved_by": null,
  "approved_at": null,
  "source": {"kind": "generated", "parent_ref_ids": ["master-front"]},
  "view": {"yaw_deg": -45, "pitch_deg": 0, "visible_cheek": "left", "framing": "headshot"},
  "expression": "neutral",
  "allowed_roles": ["Identity"],
  "quality": {"identity": "NOT-RUN", "face_readable": false, "occlusion": "unknown"},
  "qa_record": null,
  "notes": "Unapproved example record; not an actual image"
}
```

## 字段与约束

- id 唯一；slot 为 master-front / left-45 / right-45 / profile / fullbody / expression 或具体子类。
- path 相对该角色目录，必须指向实际图片，不能越出目录。sha256 正式批准时为 64 位小写十六进制摘要。
- yaw_deg：0 正脸；负值角色左颊可见，正值右颊可见；范围 -180..180。pitch_deg：正值低头，负值抬头，范围 -90..90。不可混用相机俯仰。
- framing：headshot / bust / halfbody / fullbody；expression 为规范化标签，未知用 unknown。
- approval：candidate / approved / rejected / unavailable。approved 必须有批准者、日期、身份 PASS 和可读性 true；fullbody 可用身体 QA，但不能单独承担不可读脸的身份核对。
- source.kind：user-master / user-reference / generated；generated 必填 parent_ref_ids，父引用真实存在，谱系不循环。
- anchor_version 与当前 identity 一致；旧 anchor 图不自动参与当前路由。
- quality.identity：PASS / FAIL / NOT-RUN；遮挡为 none / partial / severe / unknown。
- qa_record 指向本角色目录内的验收 Markdown，记录比较对象与具体缺陷。approved 不等于模型生成成功。

校验先排除 candidate、rejected、unavailable、缺文件、摘要不符、anchor 不匹配和身份冲突，再做排序。
