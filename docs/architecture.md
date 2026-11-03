# Architecture

## 目标

系统优化三个相互独立、需要同时过关的维度：

1. **Identity Fidelity**：是否仍是同一位成年角色。
2. **Scene Fidelity**：姿势、构图、环境、设备感与光线是否符合目标。
3. **Scene Integration**：人物是否真的属于该环境，而非“精修头像贴背景”。

Identity 是硬门槛；Scene Fidelity 与 Integration 不能通过牺牲身份来换取。

## 分层模型

```text
User intent / references
        ↓
Identity contract ── Scene anchor map
        ↓                 ↓
        Prompt composer + selected preset
                     ↓
          Positive / Negative / QA
                     ↓
              Generated image
                     ↓
          QA or Revision Delta
```

### Identity Layer

定义不可漂移项：脸型、眼形与间距、眼睑结构、鼻部结构、唇部比例、下颌、年龄印象、可辨识的不对称与真实皮肤特征。

### Scene Layer

用五类锚点表达可观察目标，不把“韩系”“氛围感”等风格词当作场景事实。

### Capture Layer

把 iPhone、CCD、直闪等标签转译为成像行为，包括视角、距离、透视、闪光衰减、白平衡、动态范围、颗粒和清晰度。

### Integration Layer

统一人物与环境的光源方向、色温、曝光、噪点、锐度、景深和接触关系。该层决定照片是否像同一次曝光。

### QA Layer

按 Identity → Scene → Integration 的顺序检查。身份失败时不应只修背景；融合失败时不应重设计面部。

## Preset 继承规则

Preset 是可覆盖的基线，不是不可修改的完整咒语。优先继承稳定骨架，再覆盖用户明确变量。不同 Preset 发生冲突时，按身份策略、用户明确要求、单一基线的顺序裁决。

## v1.3 Production Flow

Master Identity → Immutable Anchor → Atlas Selector → Reference Role Router → Five Anchors + Preset → Delta Compiler → Stage A / Identity QA → Stage B / Three-axis QA → Human Approval → Approved Library。参考选择与阶段规则见 [工作流](workflow.md)。
