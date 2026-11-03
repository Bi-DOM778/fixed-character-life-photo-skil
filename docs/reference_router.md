# Reference Role Router

对所有图像输入建立角色表，Text-only First 也包括身份图与编辑底图。角色必须显式指定；一图可以承担多个非身份职责，但范围不能隐式扩张。

| Role | 允许继承 | 禁止继承 |
|---|---|---|
| Identity | anchor、同角色视角/表情/身体比例证据 | 强制服装背景和拍摄风格 |
| Scene | 空间、建筑、道具、布局、构图 | 人物脸、年龄、体型身份 |
| Pose | 动作、关节关系、视线、承重 | 脸与身体身份、妆容 |
| Lighting | 光向、软硬、色温、曝光、闪光衰减 | 人脸与皮肤身份基准 |
| Style | 全图色彩/噪点/锐度/景深行为 | 五官、年龄、体型改造 |

编辑底图 Base 是载体而非第六种身份授权：列出保持范围和允许编辑区域；未批准底图不能变为 Identity。Stage A 身份通过结果可作 Stage B 临时底图，不能直接加入 Atlas。

## 编译前检查

为每项记录 ref_id、实际文件/输入序号、roles、allowed、forbidden、approval、stage。序号以本次工具真正上传顺序为准，不沿用上一轮 Image 1 标签。

身份冲突先停下合并；场景冲突按用户最新明确目标、显式锚点、选定 Preset 顺序裁决。多角色引用的矛盾必须选定主来源，例如灯光只归 Lighting 图，不同时继承 Scene 图另一套主光。

传给工具的约束必须包含实际图片角色：

```text
Image 1: Identity only; retain the approved character anchor.
Image 2: Scene and Pose only; use layout, framing and joint relationships.
Ignore the depicted person's face, age, body identity and styling.
Image 3: Lighting only; use its light direction and falloff across the whole scene.
```

不支持独立角色权重时仍写清职责，但不承诺完全隔离。参考身份侵入时优先移除非身份人物图、改用文字锚点或裁掉无关人脸（需工具支持），而非无限增强“same person”。
