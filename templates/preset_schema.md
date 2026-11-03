# Preset Schema

每个 Preset 必须使用以下结构。标题即 `PRESET_ID`，采用大写蛇形命名：`[SCENE]_[CAPTURE/LIGHT/MOOD]_[POSE/FEATURE]`。

```markdown
# PRESET_ID

Status: validated
Version: 1.4.0

## Purpose
适用与不适用场景。

## Identity Policy
该场景特有的身份保护要求。

## Scene Fidelity Anchors
### Hair state
### Pose anchor
### Composition anchor
### Architecture / environment anchor
### Light behavior

## Scene Integration
人物和环境共享的成像逻辑。

## Prompt Skeleton
可直接复制、保留可替换槽位的英文主提示词。

## Negative Prompt
只列高价值失败模式。

## QA Checklist
可观察的通过条件。

## Revision Deltas
常见失败对应的最小修改。
```

## 验证规则

`validated` 仅在字段齐全、五类锚点无内在冲突、身份来源隔离、包含 Integration/Negative/QA/Delta 时使用。若仅是草案，标记 `draft`。

## v1.3 Atlas Binding

新增 Preset 应写明 Selector/Router 接入；Skeleton 是完整场景骨架，正式编译须替换身份固定句并输出差量，不绑定某个角色图片路径。
