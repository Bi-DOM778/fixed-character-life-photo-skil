# Character Atlas

Atlas 是经过验收的同一角色身份视图库，不是任意生成图集。master-front 是身份裁决基准；其他视图帮助呈现该身份在不同投影和表情下的形态，不替代 master。

## 目录约定

```text
character_atlas/<character-id>/
  identity.md
  manifest.json
  refs/              仅放实际可用的身份图
  candidates/        未批准的扩展图
  approved_dataset/  通过三轴 QA 且人工确认的生活照
```

建议 slots：master-front、left-45、right-45、profile-left、profile-right、fullbody、expression-neutral、expression-smile、expression-pout。profile 和 expression 是类别，可按需要扩展。无需凑齐所有 slot 才开始；缺图必须记录 unavailable。

left/right 按角色自身解剖方向：left-45 表示角色左颊朝向相机。记录可見 cheek 与 yaw；不要自动镜像，避免痣和不对称换边。机位俯仰与头部转向分开标注。

## 建立与扩展

1. 用户指定 master，记录来源与批准者。读取真实图片后填写 identity schema，无法确认的项用 unknown。
2. 从 master 生成目标视角候选；Stage A 只改变角度、景别或表情，尽量采用中性背景与可辨识光线。
3. 核对骨骼、五官、年龄感、左右不对称及身体比例。新视角不能仅以“看起来好看”批准。
4. QA 后仍保持 candidate；用户确认身份后才设 approved，并记录日期、父参考和验收证据。不能由 skill 自己替用户批准身份。
5. 将实际图片放入 refs，填写相对路径及 SHA-256。图片修改后更新记录并重新验收。

## Immutable Character Anchor

锁定脸型与下颌、眼形/间距/眼睑、鼻梁/鼻翼/鼻尖、唇形与比例、成年年龄印象、自然不对称、稳定标记；有证据时锁定体型比例、发际线与天然发色。皮肤纹理基准保留，不要求毛孔逐像素一致。

不锁死每次曝光下的像素颜色、表情产生的肌肉形变、透视投影或头发风动。衣服、妆容、发型状态属于 shot variables，但不能暗中改变身份。

随包 sample 是空清单，不包含任何真实人物或固定角色的身份图，也不代表任何角色已经通过验收。使用者自行提供有权使用的参考，并在私有工作区保存身份材料。
