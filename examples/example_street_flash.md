# Example: Street Flash

## Request

同一成年角色夜晚在街边蹲下，一只手搭膝，手机直闪抓拍。要真实的闪光距离衰减、路面和店灯，不要棚拍或时尚广告。

## Run Card

```yaml
preset: NIGHT_STREET_FLASH_CROUCH_CANDID
mode: reference-assisted
identity_lock: available
aspect_ratio: "3:4"
anchor_status: {hair: inferred, pose: explicit, composition: inferred, environment: explicit, light: explicit}
```

## Reference Roles

```text
Identity reference: identity only.
Scene reference: crouch geometry, framing, pavement, storefront depth, and flash behavior only; ignore the depicted person's identity.
```

## Positive Prompt

> Use the master face reference as the only identity source and preserve the same adult character's facial structure, eye spacing, nose, lips, jawline, age impression, asymmetry, and natural skin. Use the scene reference only for crouch geometry, framing, street layout, and lighting. Create a candid vertical 3:4 night-street phone snapshot. They hold a stable low crouch with both feet grounded, knees and hips anatomically coherent, and one elbow resting naturally on a knee. Keep visible pavement, storefront light, street fixtures, and distant colored light. Direct on-camera flash makes the nearby face, clothes, hands, and pavement crisp and brighter, produces a believable short hard shadow, and falls off rapidly with distance. Background lights remain darker and independently exposed. Their hair follows gravity with slight breeze, and realistic high-ISO texture appears across both subject and background.

## Negative Prompt

> identity drift, scene-reference face, childlike proportions, broken crouch, floating heels, fused knees, extra fingers, soft studio key light, evenly lit background, black cutout background, glossy fashion campaign, plastic skin, CGI

## QA Targets

- 身份仅来自主身份图，未继承场景图人物。
- 脚—膝—髋几何和承重成立。
- 近处闪亮、远处快速衰减，且有合理硬阴影。
- 店灯、路面和高 ISO 质感属于同一张照片。

## Example Revision Delta

```text
KEEP: identity, crouch, outfit, storefront positions
CHANGE: place both heels firmly on pavement; move the right knee 8% outward; add a short flash shadow behind the left arm
AVOID: relighting the background with flash or changing the face
SUCCESS: the crouch is physically stable and the flash direction is obvious
```

## v1.3 使用说明

以上为保留的 v1.2 完整场景示例，不代表本次已生成。实际使用按 [v1.3 输出格式](../templates/prompt_output_format.md) 增加 Selector、Router、阶段与预算；将身份固定句替换为实际路由，场景作为 Stage B 差量。
