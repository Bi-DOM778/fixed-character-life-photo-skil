# Scene Fidelity Anchors

五类锚点把抽象感觉转换为可执行画面关系。

## 状态词

- `explicit`：用户文字明确给出。
- `inferred`：从参考图保守推断。
- `missing`：未提供，可由 Preset 给默认值。
- `conflict`：来源互相矛盾，组装前必须裁决。

## 1. Hair state

描述长度、落向、束缚方式、碎发、潮湿或风动状态，以及头发与耳机、手、衣领的接触。避免只写“漂亮长发”。

## 2. Pose anchor

描述承重、关节方向、手的位置、腿的前后关系、躯干倾斜与视线。优先使用几何关系，如“一膝更靠近镜头”，而非“自然坐着”。

## 3. Composition anchor

包括画幅、景别、机位高度、拍摄距离、主体占比、裁切位置、留白与前后景关系。构图必须和姿势、镜头透视兼容。

## 4. Architecture / environment anchor

描述空间类型、材质、固定结构、关键道具及生活痕迹。挑选 3–6 个高辨识元素即可，避免把背景写成无重点的物品清单。

## 5. Light behavior

描述主光来源与方向、色温、软硬、闪光衰减、阴影、环境曝光与人脸响应。“暖光”必须说明它如何同时影响人物与房间。

## 锚点完整性示例

| Anchor | Status | Value |
|---|---|---|
| Hair | explicit | long dark hair, loose strands, lightly lived-in |
| Pose | explicit | seated, raised knee near camera, right hand in hair |
| Composition | inferred | vertical 3:4, medium shot, mild near-knee perspective |
| Environment | explicit | blue bedding, photo wall, snack shelf, floor lamp |
| Light | missing | preset default: soft window daylight |

## 冲突示例

“正午窗光”与“仅由床头暖灯照明”不能同时作为唯一主光。应选定主光，并把另一光源降级为环境补光，而不是把冲突原样塞入 prompt。
