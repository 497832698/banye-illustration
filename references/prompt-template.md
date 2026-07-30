# Prompt Template（组装器）

> 本文件只定义组装逻辑。风格词从 `styles/quirky-sketch.md` 获取，
> IP 从 `ip/banye/ip.md` 获取。不硬编码任何风格/IP 词。

每张图单独生成，不要把多张图拼在一张里。

---

## 组装顺序

```
{REF_IMAGE}
{IP_DESC}              ← 紧接参考图，先于风格段
{STYLE_DNA}
{WHITESPACE_DESC}
{STYLE_ADAPT}          ← 来自 styles/quirky-sketch.md，通用层
{IP_STYLE_ADAPT}       ← 来自 ip/banye/ip.md
{COMPOSITION_DESC}
{MESSAGE_DESC}
{SUBJECT_DESC}
{TITLE_DESC}
{MOOD_DESC}
{RATIO_DESC}
{OUTPUT_SIZE_DESC}
{LABEL_DESC}
{NEGATIVE_DESC}
```

---

## 变量来源

| 变量 | 来源文件 | 说明 |
|------|----------|------|
| `{REF_IMAGE}` | `assets/ip/banye/` | 作为 image reference 附件传入（见下方） |
| `{STYLE_DNA}` | `styles/quirky-sketch.md` → "Prompt 风格段" | 纯风格描述，不含 IP |
| `{WHITESPACE_DESC}` | `styles/quirky-sketch.md` → "留白指令" | 留白比例约束 |
| `{STYLE_ADAPT}` | `styles/quirky-sketch.md` → "风格适配指令" | 通用层，不写死具体锚点 |
| `{IP_STYLE_ADAPT}` | `ip/banye/ip.md` → "填入 `{IP_STYLE_ADAPT}`" | 般叶专属锁色 |
| `{IP_DESC}` | `ip/banye/ip.md` → "填入 `{IP_DESC}`" | 般叶外貌描述 |
| `{COMPOSITION_DESC}` | `shot-config.md` → Shot「构图」 | 从构图库选择或自定义 |
| `{MESSAGE_DESC}` | `shot-config.md` → Shot「核心信息」 | 先定义内容表意，再决定画面 |
| `{SUBJECT_DESC}` | `shot-config.md` → Shot「隐喻」 | 具象物件 + 结构；见下方填法 |
| `{MOOD_DESC}` | 可选 | 如不确定留空 |
| `{RATIO_DESC}` | 见下方 | 按 `$RATIO` 填入，**核心比例约束** |
| `{OUTPUT_SIZE_DESC}` | 见下方 | **可选**；仅 `$OUTPUT_SIZE` 有值时填入 |
| `{TITLE_DESC}` | 见下方 | 有标题时填 |
| `{LABEL_DESC}` | 见下方 | 文字标注（颜色从 style 文件读取） |
| `{NEGATIVE_DESC}` | `styles/quirky-sketch.md` → "绝对不要" + 般叶负向约束 | 合并输出 |

---

## 各变量填法

### `{REF_IMAGE}`

**般叶（固定角色）· `ref_mode: dual`：**

1. **必传** `assets/ip/banye/reference-character.png`（全身身份锚：银发、不对称耳环、项链、白西装、Q版比例）
2. **必传** `assets/ip/banye/examples/quirky-sketch/banye-sample.png`（校准图：锁怪诞手绘里的般叶线稿质感）
3. 两张都进上下文后再生图；prompt 开头强调 Match BOTH references + 般叶锚点关键词
4. 校准图缺失 → **当次按 single 处理**（仅设定图），并提示补回校准图

**`ref_mode: single`（仅设定图）：** 只传 `reference-character.png`；prompt 开头 Match character sheet（无 BOTH）。

**分工**：设定图 + 校准图 → 般叶身份与线稿质感；风格词 → 场景线稿与色纪律。禁止在 dual 下只传一张却声称完成。

### `{IP_DESC}`

- 读 `ip/banye/ip.md`「填入 `{IP_DESC}`」（般叶外貌描述）

### `{IP_STYLE_ADAPT}`

- 读 `ip/banye/ip.md`「填入 `{IP_STYLE_ADAPT}`」— 般叶专属锁色（银发、不对称耳环、项链、白西装、比例）
- 锚点优先：外貌/配饰/比例以参考图为准；`{STYLE_ADAPT}` 管线稿质感；`{IP_STYLE_ADAPT}` 管般叶专属锁色

### `{COMPOSITION_DESC}`

从 `composition-patterns.md` 构图库选择（或根据核心信息自定义），转英文：

| 构图 | 填入内容 |
|------|---------|
| 单主体居中 | `single centered subject, generous negative space on all sides` |
| 对比并置 | `two contrasting elements side by side, visual tension` |
| 行动中人物 | `character in mid-action, dynamic pose` |
| 物件特写 | `close-up single object, exaggerated scale` |
| 环境暗示 | `tiny figure in vast environment, scale contrast` |
| 图标级单主体 | `ultra-simple visual symbol, large whitespace, room for sparse labels` |
| 隐喻场景 mini | `minimal scene with 3 elements or fewer, one complete metaphor` |
| 序列逻辑 | `2-4 numbered main steps in left-to-right order; failure/rollback nested inside the last step, not as an extra equal station; rollback arrow from broken state to save point or clean file` |
| 信息聚焦 | `one clear visual focus, supporting elements are smaller and only serve the main message` |
| 情绪面孔 | `expressive face close-up, exaggerated emotion` |

### `{MESSAGE_DESC}`

`Reader takeaway: <one sentence describing the key idea this image must communicate>.`

### `{SUBJECT_DESC}`

从 shot-config「物件表意」+「隐喻」填入，包一层英文引导：

```
Draw these specific named objects from the source text: <物件表意>.
Scene layout: <隐喻内容，含信息分工>.
Clear story flow: <故事动线>, connected by arrows or path in reading order.
Each main object has a clear information role (problem source / action entry / result / state).
Allow 4-6 named objects when needed; use size and line weight for hierarchy, not extra color fills.
For sequential diagrams: exactly N numbered main steps if title says N steps;
nest failure/broken state inside the last step (before → action → after), not as a fourth equal station;
rollback arrow must go from broken state or rollback button TO save box or clean file, never back to broken state.
Viewer can name 2-3 concrete objects in 3 seconds.
Do not use magnifying glass, lightbulb, or generic file icons unless listed in source nouns.
Use soft blue as main scene accent on at most 1-4 objects.
Soft orange on at most 2 small highlights only (not object fills).
Show changes with line marks, not red-green color fills.
No colored sticky notes or label background fills.
```

### `{COMPOSITION_DESC}` 补充

序列逻辑构图时，在 `{COMPOSITION_DESC}` 末尾加：`numbered main steps with clear left-to-right story flow; failure state nested inside final step`

### `{RATIO_DESC}`

按 `$RATIO` 填入（**默认 16:9**）：

| `$RATIO` | 填入内容 |
|----------|---------|
| 16:9 | `aspect ratio 16:9, horizontal composition, landscape orientation, wide frame, NOT portrait, NOT square` |
| 3:4 | `aspect ratio 3:4, vertical composition, portrait orientation, tall frame, NOT landscape` |
| 1:1 | `aspect ratio 1:1, square composition, balanced framing` |
| 9:16 | `aspect ratio 9:16, vertical composition, tall mobile frame` |
| 其它 | 按用户给定比例动态生成，写明 `aspect ratio W:H` 及横/竖/方构图方向 |

推荐像素（16:9 → 1920×1080；3:4 → 1080×1440）**仅作参考**，不写入 `{RATIO_DESC}`，除非用户同时指定了 `$OUTPUT_SIZE`。

### `{OUTPUT_SIZE_DESC}`（可选）

**仅当用户明确要求具体像素（`$OUTPUT_SIZE` 有值）时填入，否则整段留空。**

示例（16:9 + 1920×1080）：
```
CRITICAL: target output 1920x1080 pixels, landscape 16:9 frame
```

示例（3:4 + 1080×1440）：
```
CRITICAL: target output 1080x1440 pixels, portrait 3:4 frame
```

### `{TITLE_DESC}`

- 有标题 → `centered handwritten Chinese title at top: "标题内容"`
- 无标题 → 留空

### `{LABEL_DESC}`

- 默认：`sparse handwritten Chinese labels only, 2-5 labels total: "锚点词1", "锚点词2"; exact labels from shot-config; black text and black arrows only; {LABEL_COLOR}; no English except product names`
- `{LABEL_COLOR}` 从 `styles/quirky-sketch.md` → "标注颜色指令" 读取
- 用户明确不要文字时：`no text, no letters, no words, no watermark`

### `{NEGATIVE_DESC}`

从 `styles/quirky-sketch.md`「绝对不要」段落提取，加上般叶负向约束。默认附加：

```
avoid equal-weight process diagrams unless the core idea is truly a process;
avoid formal workflow chart or dense tutorial page;
do not optimize for fewer words at the expense of meaning;
no colored sticky notes, no label background fills, no red-green diff color blocks;
soft blue main scene accent; soft orange at most 2 small highlights only; no orange object fills or label backgrounds
```

**般叶专属负向约束（来自 `ip/banye/ip.md`）：**

```
NOT yellow / gold / gray-washed hair for Banye; keep silver-white flowing hair;
NOT symmetric earrings — Banye is LEFT ear ONE hoop + RIGHT ear FOUR hoops (asymmetric);
NOT missing the silver chain necklace;
NOT normal adult body proportion — keep chibi big-head ~1:1.3;
NOT glasses on Banye (character is without glasses);
scene accent colors must NOT tint, replace, or bleed into hair / suit / necklace
```

---

`v1.0` · 2026-07-30 · 自 gimi-illustration prompt-template v1.7 派生；固定 IP=般叶，去除 Gimi/none 专属示例。
