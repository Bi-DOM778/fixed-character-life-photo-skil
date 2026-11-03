# Example — Left-45 Café / Full-body / Smile

示范输入假设：同角色 master-front、left-45、fullbody 已真实批准，expression-smile 缺失。此示例不提供实际图像，也不构成验收。

目标：左颊 45°，全身，微笑，日间咖啡馆门口；灰开衫、白背心；朋友手机 1x 拍摄。用户另给一张场景人物图。

Selector：left-45 primary（角度最近）；fullbody support（身体比例）；expression 缺失回退文字描述。若工具最多三图，A 用前两图，B 按支持容量用 A、left-45、场景图；不将未上传 fullbody 声称为 B 输入。

角色表：A Image 1=left-45 Identity，Image 2=fullbody Identity/body only。B Image 1=A Base，Image 2=left-45 Identity，Image 3=Scene+Pose+Lighting；忽略其中人物脸/年龄/体型。

Stage A planned prompt：

```text
BASE: Image 1, approved left-45 identity; Image 2 supplies only the same character's body proportions.
KEEP: immutable facial structure, adult age impression, asymmetry and body proportions.
CHANGE: full-body standing view, left cheek toward camera at about 45 degrees;
a small relaxed smile, readable face, plain background with soft daylight.
AVOID: mirrored identity marks or a redesigned jaw.
SUCCESS: same readable identity, coherent proportions and grounded feet.
```

A 身份通过才执行 B：

```text
BASE: Image 1, identity-passed Stage A base. Image 2 is identity only.
Image 3 supplies café layout, pose, framing and daylight only; ignore its person's identity.
KEEP: the approved character anchor and successful left-45 face orientation.
CHANGE: gray cardigan and white tank; relaxed step outside the café;
loose wind-touched hair; vertical 3:4 full-body framing with both feet visible;
phone 1x perspective at chest height; storefront, café chairs and readable street depth;
daylight with restrained fill flash fading into the distance.
Apply consistent exposure, noise and sharpness to face, clothes, pavement and background.
AVOID: a scene-reference face, floating feet, separately lit portrait skin.
SUCCESS: same identity; café anchors match; plausible flash, occlusion and ground contact.
```

QA：Identity / Scene / Integration = NOT-RUN（尚未生成）。若 B 眼距漂移：Identity FAIL，先移除场景图脸部干扰并返回 A；不能以场景漂亮为由批准入库。
