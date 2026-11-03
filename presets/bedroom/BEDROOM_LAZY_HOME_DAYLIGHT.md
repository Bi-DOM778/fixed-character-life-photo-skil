# BEDROOM_LAZY_HOME_DAYLIGHT

Status: validated  
Version: 1.4.0

## Purpose

白天卧室生活照：清冷、安静、轻微慵懒。适合床上坐姿、抱膝或抓头发；不适合正式棚拍或豪华样板间。

## Identity Policy

主身份参考是唯一身份来源。保留脸型、眼距、鼻唇比例、下颌、年龄印象和真实皮肤；不因“韩系”改成模板甜妹脸。

## Scene Fidelity Anchors

- **Hair state**：长发自然披散，少量碎发和轻微凌乱，非沙龙造型。
- **Pose anchor**：坐在床上，一膝靠近镜头；一手入发或扶头，另一手自然放松。
- **Composition anchor**：竖版 3:4，中景；保留床和生活背景，近膝形成温和透视。
- **Architecture / environment anchor**：低饱和蓝色床品、照片墙、小置物架、零食饮料与个人物件，真实但不脏乱。
- **Light behavior**：柔和窗光为主；面部与房间共享光向和动态范围，允许自然眼下色调。

## Scene Integration

人物和床品具有一致白平衡、阴影软度、噪点与景深。头发接触肩部、手接触头发、身体压住床垫的关系应可信。

## Prompt Skeleton

> Use the uploaded master face reference as the only identity reference. Preserve the same adult character's facial structure, eye shape and spacing, eyelids, nose, lips, jawline, age impression, subtle asymmetry, and realistic skin texture; identity takes priority over styling. Create a natural vertical 3:4 bedroom lifestyle snapshot in soft daylight. They sit casually on their own bed, one knee closer to the camera, one hand resting in their hair and the other arm relaxed. They wear a loose light-gray zip hoodie over a white tank top. Their long dark hair is slightly lived-in with loose strands; their expression is calm, soft, slightly distant, and gently tired. Show blue low-saturation bedding, wall photos, a small shelf, snacks, drinks, and a few personal objects. Use soft window daylight across both the character and the room, with believable indoor shadows, consistent grain, depth, and color. They should feel as if they live here, not like a polished portrait placed over a bedroom.

## Negative Prompt

> identity drift, different person, generic influencer face, altered facial proportions, plastic skin, excessive smoothing, separate studio face lighting, salon-perfect hair, showroom bedroom, person-background mismatch, CGI, anime, 3D render

## QA Checklist

- [ ] 身份结构与主参考一致。
- [ ] 近膝透视明显但不过度变形。
- [ ] 房间有人居住的痕迹且不似样板间。
- [ ] 面部没有比房间更“精修”或更亮。
- [ ] 身体与床垫、手与头发接触可信。

## Revision Deltas

- 人像感过强：降低独立面部补光与磨皮，保持身份结构。
- 慵懒感不足：放松肩部、降低下巴、增加轻微不对称重心。
- 近景关系不足：镜头略靠近并降低，增大近膝尺度，不改变脸。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
