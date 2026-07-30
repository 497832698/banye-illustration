# IP · 般叶（Banye）

> ref_mode: dual（校准图已入库：`examples/quirky-sketch/banye-sample.png`）
> 气质：痞帅的设计师
> 设定图：全身正面（`reference-character.png`）+ 多穿搭参考（`reference-outfits.png`）
> 描述「长什么样 · 动作怎么选 · 序列图怎么带读」。画风见 `styles/quirky-sketch.md`。

---

## 参考图（生图必传）

| 图 | 路径 | 作用 |
|----|------|------|
| **设定图** | `assets/ip/banye/reference-character.png` | 身份锚（全身三面视图）；跨风格复用 |
| **穿搭参考** | `assets/ip/banye/reference-outfits.png` | 多套穿搭（白西装/礼服/牛仔/和风/牛仔帽）配色与造型 |
| **校准图** | `assets/ip/banye/examples/quirky-sketch/banye-sample.png` | 该 IP 在 quirky-sketch 里的风格样板（Step 0.4 已入库，QA 5/5 通过） |

**双参考协议（校准图补完后生效 $IP=banye）：**

1. 每次生图传 **设定图 + 校准图 1 张**（共 2 张）
2. 设定图管锚点色（银发、耳环、项链、比例）；校准图管「手绘线稿里仍像同一人」
3. 校准图**不**承担构图/标注示范——那些由 shot-config 当次决定
4. prompt 开头：`Match Banye to BOTH references — silver-white flowing hair, NO glasses, asymmetric silver hoops (left ear ONE, right ear FOUR), silver chain necklace, big-head chibi ~1:1.3, default white suit.`

---

## 锚点（6 个，丢任一个就不算般叶）

1. **银白飘逸中长发**：蓬松、微卷、飘逸感强，刘海偏分（非直硬短发、非金发）
2. **多套穿搭**：默认白西装套装 / 礼服装 / 牛仔装（三视图与周边图可辨）
3. **不对称银环 + 项链**：**不戴眼镜**；左耳 **1 枚**小银环、右耳 **4 枚**小银环（左右不对称是核心识别点）；银色链条项链
4. **Q 版大头比例**：头身比约 **1:1.3**（约 2–3 头身），非成人正常比例
5. **黑色眼线**：上挑黑色眼线，强化「瘾帅」冷感
6. **双模式表情**：有时夸张戏剧化、有时安静冷感

**比例：** Q 版大头，头身约 1:1.3，与设定图一致；**不因 sketch 风格拉长身体或改正常比例。**

---

## 填入 `{IP_DESC}`

```
[Match reference-character.png AND reference-outfits.png for Banye's appearance]
Banye: chibi/cartoon character, head-to-body ratio about 1:1.3 (big-head proportion, roughly 2-3 heads tall, NOT normal adult proportion);
silver-white long flowing hair, voluminous and wispy (NOT stiff, NOT short, NOT gold/yellow, NOT gray-washed);
NO glasses;
black winged eyeliner on upper lids, cool roguish "bad-boy handsome" look;
gray/silver eyes;
LEFT ear: exactly ONE small silver hoop; RIGHT ear: exactly FOUR small silver hoops (ASYMMETRIC — core identity signal, must be preserved);
silver chain necklace on neck;
outfits (multiple): default white suit set, plus formal dress and denim outfit;
expressions alternate between exaggerated/dramatic and calm/quiet.
Keep exact hairstyle, earring count and placement, necklace, and proportions from reference; only outlines become sketchy.
```

---

## 填入 `{IP_STYLE_ADAPT}`

> quirky-sketch 下、$IP=banye 时追加在 `{STYLE_ADAPT}` 之后。其它 IP 若无此节则留空。

```
Banye-specific identity lock:
- Silver-white FLOWING hair (NOT yellow, NOT gold, NOT gray-washed, NOT stiff/short)
- LEFT ear ONE silver hoop + RIGHT ear FOUR silver hoops — ASYMMETRY must be preserved exactly
- Silver chain necklace must be present
- Default outfit = white suit; scene accent colors must NOT tint, replace, or bleed into hair / suit / necklace
- Head-to-body ratio ~1:1.3 big-head chibi — do NOT draw as normal adult proportion
- NO glasses (character is specified without glasses)
```

---

## QA · 走形失败信号（$IP=banye）

**锚点走形**

- 头发变黄 / 金 / 灰白，或变短变直失去飘逸感
- 耳环数量或位置错（尤其「左 1 右 4」不对称被破坏、数量减少）
- 项链缺失 / 银链变金链
- 头身比画成正常成人比例（非 Q 版大头 1:1.3）
- 戴了眼镜（设定为不戴）
- 表情固定单一（缺少夸张↔安静双模式）

**配色走形**

- 场景软蓝 / 软橙渗入银发或白西装（最常见：背景蓝染白发、橙点缀染西装）

**流程**

- 双参考未传入即声称已走 banye 流程

---

## 动作库（选与锚定句匹配的，禁默认放大镜）

拉、指、观察、按按钮、思考、托腮

---

## 序列图导游（结构轴 = 路径序列时）

> 管「站在动线哪、怎么带读」，不管长什么样（见锚点）或动作词表（见动作库）。

- 全图 **1 个般叶**，沿故事动线参与：指路 / 按按钮 / 托腮思考 / 拉物件
- 站在**步骤之间或动线侧面**，不遮挡编号圈与关键物件
- shot-config「故事动线」须写明般叶站位与引导动作

**禁止：** 每站复制多个般叶、角落站桩装饰、与锚定句无关的动作、身体挡住主路径节点

**非序列图**（单点澄清、物件特写、对比并置等）：般叶可不存在；存在时按信息分工即可，不适用本节

---

`v1.1` · 2026-07-30 · 怪诞手绘校准图入库（QA 5/5），ref_mode = dual，随 banye-illustration Skill 内置。
