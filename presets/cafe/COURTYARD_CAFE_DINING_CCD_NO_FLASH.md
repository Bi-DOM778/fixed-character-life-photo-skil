# COURTYARD_CAFE_DINING_CCD_NO_FLASH

Status: validated  
Version: 1.4.0

## Purpose

庭院咖啡馆用餐的无闪光 CCD/卡片机照片，依赖遮阴自然光和环境反射，氛围轻松而非商业餐饮摄影。

## Identity Policy

遮阴和高反差不得造成一侧五官消失；保持肤色与年龄感，不用强降噪抹平身份纹理。

## Scene Fidelity Anchors

- **Hair state**：自然披散或简单束发，可有庭院微风。
- **Pose anchor**：坐餐桌旁，手与餐具/杯子互动，肩臂有真实支撑。
- **Composition anchor**：4:3 横版优先，中景含桌面前景和庭院背景。
- **Architecture / environment anchor**：庭院桌椅、植物、墙面/拱门、餐盘与杯具。
- **Light behavior**：无闪光；遮阴天光为主，植物与墙面反射补光，亮处可能轻微溢出。

## Scene Integration

皮肤、食物、桌面和植物共享自然遮阴色温与有限动态范围；桌面遮挡、餐具投影和人物坐姿支撑一致。

## Prompt Skeleton

> Preserve the exact adult identity from the master face reference. Create a candid 4:3 courtyard-café dining photo captured with a small early-digital compact camera and no flash. They sit naturally at an outdoor table, one hand interacting with a cup, fork, or plate while their shoulders and forearms rest believably. Include tabletop foreground, simple food and drink, courtyard chairs, plants, and a textured wall or archway. Use open-shade daylight with soft directional modeling and subtle green or warm wall bounce, slightly limited highlight latitude, modest compact-camera sharpness, and restrained digital noise. Apply the same ambient color and exposure behavior to face, food, table, and courtyard. Keep the scene lived-in and spontaneous, not a restaurant advertisement.

## Negative Prompt

> identity drift, direct flash, studio food lighting, extreme background blur, luxury restaurant campaign, oversaturated greenery, smoothed face, floating utensils, duplicated tableware, impossible arm support, CGI

## QA Checklist

- [ ] 无直闪高光或闪光硬阴影。
- [ ] 遮阴天光仍能辨认五官结构。
- [ ] 手、餐具、杯盘接触可信。
- [ ] 桌面前景与庭院背景建立空间层次。
- [ ] 全图具有统一卡片机动态范围和噪点。

## Revision Deltas

- 面部发灰：增加墙面暖反射或中性天光，不加入直闪。
- 餐饮广告感：减少食物完美摆盘，放松姿势并保留生活痕迹。
- 环境过绿：降低植物反射对肤色的污染，保持背景自然。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
