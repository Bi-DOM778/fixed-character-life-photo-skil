# BEDROOM_LAZY_HOME_HEADPHONE

Status: validated  
Version: 1.4.0

## Purpose

卧室戴头戴式耳机的听歌、放空或轻微俏皮生活照；避免商业耳机广告感。

## Identity Policy

耳机和被压住的头发不得改变头宽、额头比例或面部轮廓。可轻微嘟嘴，但不得幼态化。

## Scene Fidelity Anchors

- **Hair state**：耳机压住头顶发丝，长发自然落在肩胸，保留少量碎发。
- **Pose anchor**：坐床上或床边；双手轻扶耳罩，或一手调耳机、一手落在腿上。
- **Composition anchor**：竖版 3:4，中近景至中景，完整保留耳机、双手与部分床。
- **Architecture / environment anchor**：蓝灰床品、照片墙、置物架、台灯或吉他等少量个人物件。
- **Light behavior**：窗光、黄昏环境光或柔和暖灯；不使用产品广告轮廓光。

## Scene Integration

耳罩应真实遮挡部分头发与耳部，手指正确接触耳罩；人物、耳机和房间共享色温、反光与清晰度。

## Prompt Skeleton

> Use the master face reference as the only identity reference. Preserve the same adult character's facial geometry, age impression, subtle asymmetry, and realistic skin. Create a vertical 3:4 bedroom lifestyle snapshot of the character sitting casually on a bed while wearing over-ear headphones. Their long dark hair is naturally compressed beneath the headband and falls around their shoulders with loose strands. They gently adjust both earcups, or adjust one while the other hand rests on their leg. Their expression is calm, dreamy, slightly pouty, or quietly playful without becoming childlike. They wear a gray hoodie over a white tank top. Show blue-gray bedding, wall photos, a small shelf, and a few personal objects. Use soft room-consistent window or lamp light, believable hand-to-headphone contact, and matching texture across face, headphones, and room. Keep it candid, not a commercial audio campaign.

## Negative Prompt

> identity drift, enlarged head, altered jawline, childlike face, generic cute influencer, floating headphones, hands not touching earcups, extra fingers, commercial headphone advertisement, rim-light campaign, plastic skin, CGI

## QA Checklist

- [ ] 耳机没有改变身份轮廓。
- [ ] 头带压发和手扶耳罩关系真实。
- [ ] 双手清晰且无结构错误。
- [ ] 房间信息足以证明生活场景。
- [ ] 光线不像产品海报。

## Revision Deltas

- 耳机悬浮：明确耳罩贴合、头带压发与手指接触点。
- 广告感过强：去掉轮廓光，扩大环境可见范围并降低产品锐度。
- 可爱感带偏身份：保持脸部几何，缩小嘟嘴幅度，仅调整嘴角和眼睑。

## v1.3 Atlas Binding

本文件保留 v1.2 场景成功骨架。运行时按 [Selector](../../templates/reference_selection_rules.md) 选 approved identity；Prompt Skeleton 的 master-only 句由实际 [Router](../../docs/reference_router.md) 与 KEEP 替换，不原样执行。完整场景转成 Stage B 差量；Status: validated 仅为静态规范状态。
