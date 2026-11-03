# IXUS_CAFE_BENCH_CCD

Status: validated  
Version: 1.4.0

## Purpose

复古卡片机/IXUS 感的咖啡馆长椅生活照：小传感器、适度锐利、轻微暖偏色与真实动态范围，而非强滤镜怀旧。

## Identity Policy

“CCD 感”只改变成像质地，不改变五官比例或肤色身份基准。禁止以低清模糊掩盖漂脸。

## Scene Fidelity Anchors

- **Hair state**：自然整理但不精修，可有靠背压发。
- **Pose anchor**：坐长椅，躯干轻靠或前倾，一手持杯/放桌边，重心松弛。
- **Composition anchor**：横版 4:3 或竖版 3:4，中景，轻微广角卡片机视角。
- **Architecture / environment anchor**：木质/皮质长椅、小桌、杯具、菜单或墙面装饰。
- **Light behavior**：咖啡馆环境光或轻微机顶闪；高光较直接、暗部细节有限但不死黑。

## Scene Integration

卡片机式锐度、轻微噪点、白平衡偏移和有限动态范围必须作用于整张图，不只覆盖人物；杯子、桌面与手有真实接触。

## Prompt Skeleton

> Use the master face reference as the only identity source and keep the same adult character's facial structure, age impression, asymmetry, and real skin detail. Create a casual café bench snapshot with a compact Canon IXUS / early digital CCD visual character, framed in 4:3 landscape or 3:4 vertical medium shot. They sit naturally on a wooden or leather bench, lightly leaning back or forward, with one hand holding a cup or resting near the table. Include a small table, drinkware, menu or wall details, and believable café depth. Render modest compact-camera sharpness, slightly warm imperfect white balance, restrained digital noise, limited but plausible highlight latitude, and mild wide-angle perspective. Apply the same capture texture to the character, the table, and the room; keep it candid rather than filtered or nostalgic cosplay.

## Negative Prompt

> identity drift, blurry face hiding identity, extreme vintage filter, heavy film scratches, modern full-frame commercial look, extreme bokeh, creamy studio lighting, plastic skin, floating cup, showroom café, CGI

## QA Checklist

- [ ] CCD/卡片机感来自成像行为而非重滤镜。
- [ ] 人脸清楚到足以核对身份。
- [ ] 手与杯、身体与长椅接触合理。
- [ ] 人物和环境共享噪点、锐度和白平衡。
- [ ] 咖啡馆空间可辨识但不抢主体。

## Revision Deltas

- 太现代：减少极浅景深，提高全图卡片机锐度与有限高光宽容度。
- 太“复古滤镜”：降低偏色和划痕，只保留轻微白平衡与数字噪点。
- 杯子悬浮：明确手指握持和杯底/桌面位置。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
