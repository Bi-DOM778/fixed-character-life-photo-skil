# IPHONE_SHADED_CAFE_DAYLIGHT_FLASH_SEATED_WINK

Status: validated  
Version: 1.4.0

## Purpose

遮阴咖啡馆的手机日间补闪坐姿眨眼照：活泼但仍是同一成年角色，避免夸张幼态表情。

## Identity Policy

眨眼只改变一侧眼睑和少量颊部肌肉；另一眼、鼻唇、脸型和年龄印象保持稳定。不得把眨眼变成新身份。

## Scene Fidelity Anchors

- **Hair state**：整洁自然，少量碎发，可受轻风影响。
- **Pose anchor**：坐椅上，躯干微前倾或侧转；单眼自然闭合，一手可托腮/扶杯。
- **Composition anchor**：竖版 3:4，腰上中景，手机眼平近拍，保留桌椅与遮阴空间。
- **Architecture / environment anchor**：遮阳棚/树荫、咖啡桌椅、杯子与街边背景。
- **Light behavior**：遮阴日光为底，手机轻补闪提亮眼窝和面部；背景仍保持日间层次。

## Scene Integration

补闪在皮肤、杯子和近处桌面产生一致的轻微高光；远处不受闪光影响。眨眼伴随真实的单侧颊部和嘴角微变化，不挤压整张脸。

## Prompt Skeleton

> Use the master face reference as the only identity reference. Preserve the same adult character's face shape, open eye, eye spacing, nose, lips, jawline, age impression, and natural skin. Create a vertical 3:4 iPhone-style shaded café snapshot. They are seated and turn or lean slightly toward the camera, giving a natural one-eye wink with only subtle cheek and mouth-corner movement, while one hand rests near their cheek or cup. Include café chairs, a small table, a drink, overhead shade or tree shade, and readable daylight street depth. Use shaded daylight as the ambient exposure with restrained phone fill flash on the nearby face, cup, and table; keep the background naturally lit and slightly darker. Match sharpness, color, and depth across the whole frame for a playful candid moment, not a beauty advertisement.

## Negative Prompt

> identity drift, both eyes closed, distorted open eye, childlike face, exaggerated cartoon wink, altered jawline, hard night flash, evenly flashed background, beauty campaign, plastic skin, extra fingers, floating cup, CGI

## QA Checklist

- [ ] 只闭合一眼，另一眼和眼距保持身份。
- [ ] 眨眼肌肉变化自然且不过度幼态。
- [ ] 坐姿与手部支撑合理。
- [ ] 补闪只影响近处，背景保持遮阴日光。
- [ ] 杯子、桌面和皮肤高光强度相容。

## Revision Deltas

- 眨眼带偏脸：恢复脸型和开放眼，仅缩小闭眼侧眼睑间距。
- 表情太夸张：减少嘴角牵拉和面颊挤压，保留轻微不对称。
- 像夜间直闪：提高背景日光曝光并降低正面闪光强度。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
