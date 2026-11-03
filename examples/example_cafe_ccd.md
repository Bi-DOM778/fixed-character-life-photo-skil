# Example: Café CCD

## Request

同一成年角色坐在咖啡馆长椅上，手拿杯子，像朋友用旧款 IXUS 卡片机随手拍。画面 4:3，不要强复古滤镜，也不要全画幅商业人像感。

## Run Card

```yaml
preset: IXUS_CAFE_BENCH_CCD
mode: text-only-first
identity_lock: available
aspect_ratio: "4:3"
anchor_status: {hair: preset, pose: explicit, composition: explicit, environment: explicit, light: preset}
```

## Positive Prompt

> Use the master face reference as the only identity source and preserve the same adult character's facial geometry, age impression, asymmetry, and real skin texture. Create a candid 4:3 café bench snapshot with an early compact Canon IXUS / CCD visual character. They sit naturally on a wooden bench, lightly leaning back, one hand holding a cup with believable finger contact while the other rests near the table. Include a small table, drinkware, a menu, wall details, and modest café depth. Use a mild compact-camera wide perspective, slightly warm imperfect white balance, restrained digital noise, modest sharpness, and limited but plausible highlight latitude. Apply the same capture texture to their face, cup, bench, and background. Keep it spontaneous and contemporary, not a heavy retro filter or commercial portrait.

## Negative Prompt

> identity drift, blurry face hiding identity, heavy vintage filter, film scratches, extreme bokeh, modern full-frame campaign, creamy studio lighting, plastic skin, floating cup, extra fingers, CGI

## QA Targets

- 身份可辨，低清质感不掩盖五官。
- 手指确实握住杯子，身体受长椅支撑。
- 全图共享卡片机锐度、噪点和白平衡。
- 不出现重滤镜、划痕或夸张怀旧色。

## Example Revision Delta

```text
KEEP: identity, bench pose, cup, café layout
CHANGE: increase depth of field; reduce background blur; add restrained compact-camera noise across the full frame
AVOID: lowering face resolution or adding film scratches
SUCCESS: the image reads as an older compact digital snapshot rather than a modern full-frame portrait
```

## v1.3 使用说明

以上为保留的 v1.2 完整场景示例，不代表本次已生成。实际使用按 [v1.3 输出格式](../templates/prompt_output_format.md) 增加 Selector、Router、阶段与预算；将身份固定句替换为实际路由，场景作为 Stage B 差量。
