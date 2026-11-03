# Delta-only Prompting

默认相对 Selector 选出的最近身份参考写变化，最近指目标视觉距离，非文件时间。返修则相对上一张已验收底图；保留 approved identity reference 作为校验来源。完整 anchor 存在 identity.md，不在每轮复制冗长脸部清单。

## 编译契约

```text
BASE: Image 1, approved left-45 identity reference; anchor v1.0.
KEEP: character identity, facial structure, age impression and asymmetry.
CHANGE: full-body walking shot; gray cardigan over white tank; daylight sidewalk;
phone camera at chest height; mild direct fill flash; relaxed small smile.
AVOID: inheriting the scene reference person's face or body identity.
SUCCESS: readable same identity; both feet grounded; flash fades with distance.
```

BASE、KEEP 与职责约束仍是必要信息，delta-only 不等于只写几个形容词。比较参考与目标后，仅写不同或无法从参考继承的 shot variables；新场景首次生成应包含完整五类目标锚点。支持独立 negative 参数才单独输出，否则将关键避让约束整合到主提示。

## 两个基准

- Stage A：相对 approved closest identity；只改目标视角、景别、表情和必要可辨识受光。
- Stage B：相对通过身份门的 Stage A 底图；改场景、服装、镜头和光线，重新核对身份。
- Revision：相对最近成功图；保留成功的 pose、场景与取景，只改缺陷。失败图可以当修复底图，不可当新身份源。

Preset 的 Prompt Skeleton 是场景骨架。删掉旧的“master only”固定句，换成本次实际路由与简短 KEEP；保留其空间几何、成像行为和融合条件。工具只能接受文字时可提供完整重建 prompt，标记 fallback: full-text；不要声称仍有视觉身份条件。

避免把侧脸透视修成正面五官、把笑容压回中性表情或把暖灯肤色纠成白光肤色。修正结构漂移，允许自然投影与受光变化。
