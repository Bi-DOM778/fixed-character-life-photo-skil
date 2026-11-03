# IPHONE_DAYLIGHT_FLASH_STREET_FULLBODY

Status: validated  
Version: 1.4.0

## Purpose

日间街头全身抓拍，以手机近距离直闪制造轻微反常、鲜活的生活感；不追求长焦时尚大片。

## Identity Policy

全身小脸占比下仍应维持可辨识结构；不得用过度锐化或换脸式美化弥补分辨率。

## Scene Fidelity Anchors

- **Hair state**：自然披发或轻微风动，边缘不做广告式完美飞扬。
- **Pose anchor**：站立或一步行走，重心明确，一手可持包/手机，手臂不僵直。
- **Composition anchor**：竖版 3:4，全身含脚，手机视角略低或胸口高度，背景保留街道纵深。
- **Architecture / environment anchor**：人行道、店面/墙面、路缘与少量行人或车辆线索。
- **Light behavior**：白天环境曝光成立，近距离直闪在皮肤和衣物产生克制高光及短阴影，背景不被闪光照亮。

## Scene Integration

直闪遵循距离衰减：主体略亮、背景仍由日光决定；脚底接触阴影、路面色彩反射和透视必须一致。

## Prompt Skeleton

> Preserve the exact adult identity from the master face reference. Create a candid vertical 3:4 full-body iPhone-style street photo in daylight, with both feet visible and a believable walking or standing weight shift. Use a close phone-camera perspective at chest or slightly lower height, with mild wide-angle spatial depth rather than fashion-lens compression. Add subtle daylight fill-flash behavior: crisp restrained highlights on nearby skin and clothing, a short local shadow, and natural daylight exposure in the background. Show a real sidewalk, storefront or textured wall, curb, and modest street activity. Keep hair naturally loose with slight breeze, anatomy and ground contact credible, and identity stable without beauty-campaign retouching.

## Negative Prompt

> identity drift, cropped feet, floating feet, stiff mannequin pose, telephoto fashion compression, studio key light, dark night background, excessive flash blowout, plastic skin, empty showroom street, CGI, extra limbs

## QA Checklist

- [ ] 全身与双脚完整，承重可信。
- [ ] 手机广角透视温和且非畸变。
- [ ] 闪光只明显作用于近处主体。
- [ ] 背景保持日间环境曝光。
- [ ] 小尺寸面部仍保持身份特征。

## Revision Deltas

- 不像直闪：增加近处短阴影与局部高光，不压暗整个背景。
- 像棚拍：降低背景虚化，加入真实街道纵深和轻微曝光不完美。
- 姿势僵硬：明确前后脚承重、髋肩反向微转与摆臂。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
