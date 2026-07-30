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
4. prompt 开头：`Match Banye to BOTH references — silver-white short/medium regular hair (NOT long/flowing), NO glasses, asymmetric silver hoops (left ear ONE, right ear FOUR), silver chain necklace, big-head chibi ~1:1.3, default white suit.`

---

## 锚点（6 个，丢任一个就不算般叶）

1. **银白普通短发**：及耳/颌线的普通清爽短发，顺贴有轻微层次与刘海，不飘逸不炸毛（非长发、非蓬松飘逸、非金发）
2. **多套穿搭（衣橱库见下）**：白西装(默认)/短袖/背心/黑西装/礼服/牛仔/流行/韩系/杀马特；**仅衣服变化，发色与配饰(银发/不对称耳环/项链)永远不变**
3. **不对称银环 + 项链**：**不戴眼镜**；左耳 **1 枚**小银环、右耳 **4 枚**小银环（左右不对称是核心识别点）；银色链条项链
4. **Q 版大头比例**：头身比约 **1:1.3**（约 2–3 头身），非成人正常比例
5. **黑色眼线**：上挑黑色眼线，强化「瘾帅」冷感
6. **双模式表情**：有时夸张戏剧化、有时安静冷感

**比例：** Q 版大头，头身约 1:1.3，与设定图一致；**不因 sketch 风格拉长身体或改正常比例。**

---

## 衣橱库（OUTFIT_LIBRARY）

> **身份锚（银发 / 左1右4银环 / 银项链 / 黑眼线 / 无眼镜 / Q版大头 / 痞帅脸 / 圆润少年脸）全部锁定不变，权重最高；只换衣服/鞋。**
> 路由：用户提示词命中某关键词 → 选用对应服装 + 该服装的校准参考图；无关键词 → 默认白西装。

| id | 服装 | 触发关键词 | 服装段（进 prompt，中） | 参考图路径（用户生成后填入） | 状态 |
|----|------|-----------|------------------------|------------------------------|------|
| white_suit | 白西装（默认） | 白西装/西装/默认 | 米白/奶油色西装套装（外套+长裤）+白色内搭 | 设定图 reference-character.png（默认即白西装） | ✅ 默认已含 |
| short_sleeve | 短袖 | 短袖/半袖/T恤 | 宽松纯色短袖T恤（浅灰/黑/白）+休闲长裤或牛仔裤 | assets/ip/banye/outfits/short_sleeve/reference.png | ✅ 已入库 |
| vest | 背心 | 背心/无袖/坎肩 | 白色或黑色工字背心+运动短裤或阔腿裤 | assets/ip/banye/outfits/vest/reference.png | ✅ 已入库 |
| black_suit | 黑西装 | 黑西装/黑色西装/暗黑西装 | 全黑西装套装（黑外套+黑西裤）+黑或白内搭 | assets/ip/banye/outfits/black_suit/reference.png | ✅ 已入库 |
| tuxedo | 礼服 | 礼服/正装/燕尾服/晚礼服 | 黑色/藏青丝绒礼服套装+领结或领带+皮鞋 | assets/ip/banye/outfits/tuxedo/reference.png | ✅ 已入库 |
| denim | 牛仔 | 牛仔/丹宁/美式休闲 | 牛仔外套或牛仔衬衫+牛仔裤全牛仔（可做旧） | assets/ip/banye/outfits/denim/reference.png | ✅ 已入库 |
| street | 流行/潮流 | 流行/潮流/街头/hiphop/潮牌 | 宽松oversize卫衣+工装裤+运动鞋；可加棒球帽 | assets/ip/banye/outfits/street/reference.png | 待补 |
| korean | 韩系 | 韩系/韩风/清爽/温柔 | 米色针织开衫+白T+直筒休闲裤 | assets/ip/banye/outfits/korean/reference.png | ✅ 已入库 |
| visual | 杀马特/视觉系 | 杀马特/视觉系/视觉/夸张 | 发型保持普通银白短发不变（不炸毛不染色）+黑色铆钉皮衣或破洞卫衣+多层金属链+护腕+臂环；眼妆加重 | assets/ip/banye/outfits/visual/reference.png | ✅ 已入库 |

**杀马特特别约束**：发色绝不染色（仍银白），仅通过蓬乱层次 + 夸张服装/配饰 + 强烈姿态营造视觉冲击，以保般叶识别度。

**校准参考图（用户生成后）**：每套服装的 `reference.png` 由用户按本表提示词自生成并回传；入库后，配图时除设定图+校准图外，额外附上对应服装参考图，把「换装不认错人」的可靠性拉满。

---

## 填入 `{IP_DESC}`

```
[CRITICAL — IDENTITY LOCK: the 8 anchors below are NON-NEGOTIABLE and have the HIGHEST priority. They MUST be preserved exactly even when outfit/clothing changes and even over any style instruction. The character must remain recognizable as Banye regardless of clothing.]

[Match reference-character.png AND reference-outfits.png for Banye's appearance]
Banye: chibi/cartoon character, head-to-body ratio about 1:1.3 (big-head proportion, roughly 2-3 heads tall, NOT normal adult proportion);
silver-white short/medium regular hair, neat with slight layering (NOT long/flowing, NOT voluminous/wispy, NOT gold/yellow, NOT gray-washed);
NO glasses;
black winged eyeliner on upper lids, cool roguish "bad-boy handsome" look;
gray/silver eyes;
LEFT ear: exactly ONE small silver hoop; RIGHT ear: exactly FOUR small silver hoops (ASYMMETRIC — core identity signal, must be preserved);
silver chain necklace on neck;
face shape: round-soft boyish face;
outfits (multiple, see 衣橱库): white suit (default), short-sleeve tee, tank top, black suit, tuxedo, denim, streetwear, Korean-casual, shamate/scene; CURRENT OUTFIT is chosen by user keyword (default = white suit); ONLY the clothing differs — anchors above NEVER change;
expressions alternate between exaggerated/dramatic and calm/quiet.
Keep exact hairstyle, earring count and placement, necklace, face shape, and proportions from reference; only outlines become sketchy.
```

---

## 填入 `{IP_STYLE_ADAPT}`

> quirky-sketch 下、$IP=banye 时追加在 `{STYLE_ADAPT}` 之后。其它 IP 若无此节则留空。

```
Banye-specific identity lock (HIGHEST PRIORITY — apply before and above any outfit/clothing instruction):
- Silver-white SHORT/REGULAR hair (NOT long/flowing, NOT yellow, NOT gold, NOT gray-washed)
- LEFT ear ONE silver hoop + RIGHT ear FOUR silver hoops — ASYMMETRY must be preserved exactly
- Silver chain necklace must be present
- Round-soft boyish face shape must be preserved
- Default outfit = white suit; when user specifies an outfit keyword (see 衣橱库), use THAT outfit instead and state it explicitly; scene accent colors must NOT tint, replace, or bleed into hair / outfit / necklace
- Head-to-body ratio ~1:1.3 big-head chibi — do NOT draw as normal adult proportion
- NO glasses (character is specified without glasses)
- Black winged eyeliner on upper lids — keep
```

---

## QA · 走形失败信号（$IP=banye）

**锚点走形**

- 头发变黄 / 金 / 灰白，或变成飘逸长发/炸毛（应保持普通短发）
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
