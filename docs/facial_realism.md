# Facial Realism — 克制的真实感修正

目标是可信的摄影感与原有角色质感协调。先保护身份与用户认可的美感，再修正明确的人工痕迹；不以增加瑕疵证明真实。

## 模式与触发

- preserve（默认）：保留参考中的柔润皮肤、自然光泽、已有纹理与不对称。参考无明显缺陷时，不额外添加真实感词包。
- targeted：出现可观察的蜡感、塑料感、厚重涂抹、全脸均匀色块、不合理高光或眼睛玻璃感时启用。记录具体缺陷，只修最小相关变量。
- off：用户明确不需要真实感修正时使用；仍保持身份与场景目标。

不因出现“漂亮”“柔润”“皮肤光滑”就自动判为失败。真实感强度不是越高越好。

## 修正策略

| 缺陷 | 可用 delta | 保持项 |
|---|---|---|
| 皮肤厚重涂抹 | 适量恢复细微、不均匀的皮肤纹理与自然明暗过渡 | 原有柔润程度、肤色基准、五官结构 |
| 瓷白均匀色块 | 恢复符合身份与受光的局部色调变化 | 不随机制造红斑、黑眼圈或晒伤 |
| 蜡状高光 | 调整高光面积、强度与衰减，使皮肤有合理反射 | 不将正常鼻尖/唇部光泽全部去掉 |
| 眼睛过度玻璃感 | 修正与光源一致的反光和虹膜成像细节 | 眼形、眼距、虹膜颜色与表情 |
| 脸与全图质感脱节 | 匹配清晰度、受光、曝光与噪点 | 不单独把脸锐化或加颗粒 |

毛孔、绒毛、唇纹只在当前景别、分辨率和光线能够表现时适量保留。全身远景不要求可见毛孔。保留已有稳定特征，不新增痣、疤、痘、明显皱纹、黑眼圈或眉眼不对称；用户明确请求新增时作为单独变化记录，不默认为身份事实。

85mm、f/1.4、浅景深、胶片颗粒不是全局默认。手机、CCD、直闪与窗光分别遵守所选 Preset 的摄影逻辑。不统一指定 CFG 或重绘幅度；仅使用工具实际支持的参数，记录实际值，不把某模型经验区间迁移到所有工具。

## Pipeline 接入

Stage A 默认 preserve，不把纹理增强当作身份建立步骤。Stage B 保留成功质感与五类锚点；缺陷明确时启用 targeted。返修以原有用户认可图为比较基准，并保留该图；失败修正版不进入 approved Atlas。

每轮一个主修正目标。若细节变干、变杂、显老、过锐或用户偏好原图，停止追加真实感词，回到认可版本，并撤去造成退化的 delta。身份漂移仍按身份硬门处理。

## 可复制的最小返修示例

```text
BASE: the user-approved portrait; retain its identity and photographic character.
KEEP: facial geometry, age impression, expression, skin softness, existing marks,
hair, clothes, composition and lighting direction.
CHANGE: reduce the visible waxy highlight transition on the cheeks;
retain only subtle skin texture appropriate to this framing and light.
AVOID: added blemishes, dark circles, wrinkles, gritty pores, extra sharpening,
matte lifeless skin or a new facial identity.
SUCCESS: the highlight looks more photographic while the original soft skin
quality and whole-image coherence remain intact.
```

仅在确有上述高光缺陷时使用该示例，不作为每次生图固定追加文本。
