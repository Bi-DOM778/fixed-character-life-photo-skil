# Example: Bedroom Daylight

## Request

保持主身份参考中的同一成年角色。灰色拉链卫衣、白色背心，坐在自己的卧室床上，一膝靠近镜头，一手抓头发。房间有蓝色床品、照片墙、零食架；白天自然光，慵懒但不要精修棚拍感。

## Run Card

```yaml
preset: BEDROOM_LAZY_HOME_DAYLIGHT
mode: text-only-first
identity_lock: available
aspect_ratio: "3:4"
anchor_status: {hair: explicit, pose: explicit, composition: preset, environment: explicit, light: explicit}
```

## Positive Prompt

> Use the uploaded master face reference as the only identity reference. Preserve the same adult character's face shape, eye shape and spacing, eyelids, nose structure, lip proportions, jawline, age impression, subtle asymmetry, and realistic skin texture. Identity has higher priority than styling. Create a natural vertical 3:4 bedroom lifestyle snapshot in soft daylight. They sit casually on their bed with one knee closer to the camera, one hand resting in their hair, and the other arm relaxed forward. They wear a loose light-gray zip hoodie over a white tank top. Their long dark hair is slightly lived-in with loose strands, and their expression is calm, soft, slightly distant, and gently tired. Show low-saturation blue bedding, wall photos, a small snack shelf, drinks, and personal objects. Soft window daylight must affect their face, hair, clothes, bed, and room consistently, with natural indoor shadow, shared grain and depth. They should feel like they live here, not like a polished portrait composited into a bedroom.

## Negative Prompt

> identity drift, different person, generic influencer face, altered facial proportions, plastic skin, excessive smoothing, separate studio face lighting, salon-perfect hair, showroom bedroom, floating subject, inconsistent depth of field, CGI, anime, 3D render

## QA Targets

- 同一身份，年龄与五官结构不漂移。
- 近膝透视成立，手与头发接触自然。
- 蓝色床品和生活物件可见但不抢主体。
- 面部与房间共享窗光，不存在“贴脸感”。

## Example Revision Delta

```text
KEEP: identity, gray hoodie, white tank top, room layout, 3:4 framing
CHANGE: lower camera slightly; enlarge the near knee by about 12%; reduce facial fill by 0.5 stop
AVOID: changing facial proportions or adding new decor
SUCCESS: the casual perspective is clearer and the face shares the room exposure
```

## v1.3 使用说明

以上为保留的 v1.2 完整场景示例，不代表本次已生成。实际使用按 [v1.3 输出格式](../templates/prompt_output_format.md) 增加 Selector、Router、阶段与预算；将身份固定句替换为实际路由，场景作为 Stage B 差量。
