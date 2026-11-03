# BEDROOM_LAZY_HOME_WARM_LAMP

Status: validated  
Version: 1.4.0

## Purpose

夜晚卧室的睡前、发呆或安静陪伴感。暖灯是空间光源，不是夜店或电影式强色光。

## Identity Policy

低照度不得抹掉身份结构；保留真实年龄与皮肤层次。不要以过曝面部换取“好看”。

## Scene Fidelity Anchors

- **Hair state**：居家披发，轻微压乱和碎发。
- **Pose anchor**：靠床头、坐床边或抱膝；可托腮、拿杯子或放下手机。
- **Composition anchor**：竖版 3:4，半身至中景，保留较多暗部空间。
- **Architecture / environment anchor**：床、毯子、床头/落地灯和少量个人物件。
- **Light behavior**：暖灯为主光或明显实景光；面部不过曝，背光侧自然变暗，环境仍保留细节。

## Scene Integration

暖色溢光必须同时落在皮肤、头发、床品和邻近墙面；阴影方向与画面中的灯位置一致，暗部保留轻微噪点。

## Prompt Skeleton

> Use the master face reference as the only identity source and preserve the same adult character's facial proportions, age impression, asymmetry, and natural skin. Create a vertical 3:4 intimate bedroom snapshot at night. They sit quietly against the headboard or at the edge of the bed, shoulders relaxed, wearing simple homewear, with naturally loose slightly messy hair and a soft sleepy expression. Include bedding, a warm bedside or floor lamp, a blanket, and a few personal objects. Let the practical lamp genuinely illuminate both the character and the room: warm spill on the lamp-facing cheek and hair, soft falloff across the face, realistic darker areas, and matching warmth on nearby bedding and wall. Keep the low-light texture believable and avoid a separately lit beauty portrait.

## Negative Prompt

> identity drift, overexposed face, harsh frontal flash, nightclub lighting, beauty dish lighting, plastic skin, glamorous makeup, cinematic teal-orange grade, showroom bedroom, crushed black background, CGI, anime

## QA Checklist

- [ ] 暖灯位置与阴影方向一致。
- [ ] 人脸可辨识但没有独立提亮。
- [ ] 暖光同时影响人物和至少两个环境表面。
- [ ] 姿势有睡前收敛感。
- [ ] 暗部有细节而非纯黑抠图感。

## Revision Deltas

- 假夜景：降低面部曝光 0.5–1 档，扩大灯光对床品和墙面的影响。
- 太像夜店：降低饱和度，改为单一暖色实景灯和中性暗部。
- 表情过度摆拍：放松眼睑与嘴角，视线略偏离镜头。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
