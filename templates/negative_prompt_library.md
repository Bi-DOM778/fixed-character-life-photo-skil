# Negative Prompt Library

按实际失败风险选取，通常每次 8–16 项足够。负面提示词不能替代正向结构描述。

## Identity

```text
identity drift, different person, generic influencer face, altered facial proportions, changed eye spacing, changed nose structure, age regression, excessive beautification
```

## Skin / face rendering

```text
plastic skin, porcelain skin, waxy face, excessive smoothing, over-sharpened facial details, glam beauty retouching, separate portrait lighting
```

## Anatomy / pose

```text
extra fingers, fused fingers, broken wrist, impossible limb angle, duplicated limbs, floating hand, unstable body weight, pose mismatch
```

## Scene / integration

```text
person-background mismatch, inconsistent light direction, mismatched color temperature, floating subject, missing contact shadow, showroom interior, excessive staged decor, inconsistent depth of field
```

## Capture style

```text
CGI, anime, 3D render, artificial HDR, cinematic teal-orange grade, studio fashion campaign, fake lens blur, uniformly sharp background
```

## 场景附加项

- 卧室：`commercial bedroom set, spotless showroom, salon-perfect hair`
- 街头直闪：`soft studio key light, flashless flat lighting, empty sterile street`
- CCD 咖啡馆：`modern full-frame commercial look, extreme bokeh, pristine digital sharpness`

先删除与目标矛盾的项。例如目标本身是商业广告时，不应加入 `studio fashion campaign`。

## Facial Realism 按需负面约束

只有对应风险确实存在时选择 waxy highlight transitions、painted skin smoothing、oversharpened pores、added blemishes、unrequested aging。不要全局排除 smooth skin 或 soft focus，以免破坏自然柔润皮肤与正常光学虚化。正向保持项与定向修正优先于长负面词表。
