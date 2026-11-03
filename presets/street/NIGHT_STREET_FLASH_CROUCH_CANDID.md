# NIGHT_STREET_FLASH_CROUCH_CANDID

Status: validated  
Version: 1.4.0

## Purpose

夜街蹲姿直闪抓拍：近处主体鲜明、远处环境昏暗但可读。适合俏皮、疲惫或临时停下的瞬间。

## Identity Policy

蹲姿、仰俯角和强闪不得改变脸宽、下颌或年龄。避免因夜景噪点把身份磨成模板脸。

## Scene Fidelity Anchors

- **Hair state**：自然下垂或轻微风乱，符合重力。
- **Pose anchor**：稳定蹲姿，双脚和膝髋结构可解释；一肘可搭膝，手不悬空。
- **Composition anchor**：竖版 3:4，机位接近眼睛或略高，人物占画面主要区域，保留地面。
- **Architecture / environment anchor**：夜街路面、店灯、护栏/墙体与远处光点。
- **Light behavior**：相机直闪照亮近处脸、衣物和地面；背景由店灯/路灯曝光，随距离明显衰减。

## Scene Integration

闪光在人物后方或地面形成合理短硬阴影；环境光在暗部留下色彩，噪点贯穿人物与背景，发丝遵守重力与风向。

## Prompt Skeleton

> Preserve the same adult identity from the master face reference, including facial geometry, age impression, and natural skin. Create a candid vertical 3:4 night-street snapshot of the character in a stable low crouch, both feet grounded, knees and hips anatomically coherent, one elbow optionally resting on a knee. Frame from a close phone-camera position while retaining visible pavement and dim street context. Use direct on-camera flash: the nearby face, clothes, hands, and pavement are crisp and brighter, with believable short hard shadows and rapid falloff; storefront and street lights remain darker, colorful, and independently exposed in the distance. Their hair falls naturally with gravity and slight street breeze. Keep realistic high-ISO texture across the whole image and avoid a staged fashion campaign.

## Negative Prompt

> identity drift, childlike proportions, broken crouch, floating heels, fused knees, extra fingers, soft studio lighting, evenly lit background, flash without shadow, black cutout background, glossy fashion campaign, plastic skin, CGI

## QA Checklist

- [ ] 蹲姿可实际维持，脚跟与地面关系合理。
- [ ] 手、膝、髋没有融合或多肢。
- [ ] 闪光随距离衰减并产生可信阴影。
- [ ] 远处夜街仍有可读环境线索。
- [ ] 噪点和锐度不只出现在背景。

## Revision Deltas

- 蹲姿失败：先修脚—膝—髋几何与承重，保持脸和环境。
- 背景全黑：提高环境曝光，不扩大闪光覆盖范围。
- 像时尚片：降低造型精致度、减少轮廓光并保留高 ISO 不完美。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
