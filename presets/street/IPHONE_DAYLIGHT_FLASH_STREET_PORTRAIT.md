# IPHONE_DAYLIGHT_FLASH_STREET_PORTRAIT

Status: validated  
Version: 1.4.0

## Purpose

日间街头中近景/半身手机直闪人像，强调身份与即时抓拍感，不做影棚外拍。

## Identity Policy

直闪高光不得抹平鼻唇和眼睑结构；保持毛孔、轻微不对称与年龄印象。

## Scene Fidelity Anchors

- **Hair state**：自然散发，可有风吹碎发掠过脸侧。
- **Pose anchor**：上身微转、回看镜头或停步；一手靠近衣领/包带。
- **Composition anchor**：竖版 3:4，腰上或胸上景别，手机眼平略近，背景可识别。
- **Architecture / environment anchor**：店面、街墙、标识和路人层次，避免纯色摄影背景。
- **Light behavior**：日光作环境光，手机直闪轻度填充眼窝和面部，皮肤高光克制。

## Scene Integration

头发边缘、肩部和背景遮挡关系自然；面部闪光与衣物反光强度匹配，背景保留日光色温和手机式动态范围。

## Prompt Skeleton

> Use the uploaded master face as the only identity source and preserve the same adult character's facial shape, eyes, nose, lips, jawline, age impression, asymmetry, and natural skin. Make a vertical 3:4 waist-up or chest-up iPhone-style street portrait in daylight. They pause or turn slightly toward the camera with a relaxed asymmetrical posture, one hand near a collar or bag strap, and naturally wind-touched hair. Keep storefronts, textured walls, street signs, and soft pedestrian depth recognizable behind the character. Use restrained phone fill flash in daylight: mild direct catchlights and local skin highlights, gentle filling of facial shadows, while the street remains naturally daylight-exposed. Match sharpness, white balance, and grain across subject and background for a spontaneous snapshot.

## Negative Prompt

> different person, generic influencer face, altered eye spacing, poreless skin, beauty dish, studio backdrop, extreme bokeh, night-flash look, blown forehead, haloed hair cutout, fashion campaign, CGI

## QA Checklist

- [ ] 眼睑、鼻唇和下颌未被直闪洗平。
- [ ] 背景仍能识别为真实街道。
- [ ] 闪光强度与衣物反光一致。
- [ ] 头发边缘没有抠图光晕。
- [ ] 姿势像停步抓拍而非证件照。

## Revision Deltas

- 证件照感：上身转 10–20°、视线略偏、加入手与包带互动。
- 直闪过猛：降低额头/鼻梁高光并恢复面部中间调。
- 背景脱节：减少虚化，统一白平衡和锐度。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
