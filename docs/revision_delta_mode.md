# Revision Delta Mode

Revision Delta Mode 用于在保留成功部分的前提下，做可验证的定向返修。

## 基本格式

```text
KEEP: identity, outfit, room layout, aspect ratio
CHANGE: camera 20 cm lower; raised knee 15% larger in frame; lamp warmth visible on camera-right cheek
AVOID: changing facial proportions or adding new props
SUCCESS: knee perspective is obvious and face shares the room light
```

## 模糊反馈的机制化翻译

| 用户反馈 | 优先检查的 delta |
|---|---|
| “再明显一点” | 镜头距离、尺度差、关节角度、道具相对位置 |
| “不像参考图” | 五类锚点逐项比对，找首个结构偏差 |
| “变化太小” | 提高几何差值，而非加强情绪形容词 |
| “脸像贴上去的” | 光向、色温、曝光、锐度、噪点、接触阴影 |
| “再自然一点” | 重心、手部受力、视线、微表情与生活痕迹 |

## 修改优先级

1. Camera geometry
2. Expression mechanics
3. Pose geometry
4. Light behavior
5. Prop placement

每轮优先修改 1–3 项。若同时更换身份、姿势、环境和光线，就无法判断哪项带来改善。

## 身份保护

返修说明必须显式列出身份保持项。不要为了“更自然”而改变脸型、眼距、鼻部结构、年龄印象或皮肤基准。

## 退出条件

达到目标、连续两轮相同 delta 无改善、或生成系统能力不足时停止叠加词汇，报告限制并建议更换参考/控制方式。

## v1.3 基准与预算

修订底图不自动变成身份来源。始终保留当前 anchor 与 approved primary；身份失败返回 Stage A。遵守 [QA Retry policy](../templates/qa_checklists.md) 的调用预算与同缺陷停止条件。

## 质感返修

应用 [Facial Realism](facial_realism.md)：声明原有柔润度、光泽与肤色为 KEEP；仅修具体人工痕迹。新增黑眼圈、皱纹或粗糙感不算默认改善。质感退化时回退，不继续叠加真实感词。
