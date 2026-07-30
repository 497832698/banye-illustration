---
name: banye-illustration
description: >
  单一角色配图 Skill —— 只能生成「般叶（Banye）」形象的怪诞手绘风格配图。
  输入中文文章正文，自动产出 16:9（可指定任意比例）的怪诞手绘插画，
  主角固定为般叶（银白普通短发、不对称银环、银项链、Q版大头、白西装、痞帅设计师）。
  使用触发词：配图 / 给我般叶配图 / 帮我配图 / illustration。
---

# banye-illustration · 般叶专属配图 Skill

> **v1.0** · 从 `gimi-illustration`（Public 2.0 / 内部 4.7）派生  
> **本 Skill 只生成「般叶（Banye）」一个角色**，已内置其设定图、多穿搭参考与怪诞手绘校准图。

输入文章内容，生成怪诞手绘风格配图。单风格 `quirky-sketch`，**固定角色 = 般叶（Banye）**，默认 16:9。

---

## 角色锁定说明（重要）

本 Skill **只能**生成般叶形象，不使用任何其它角色 IP：

- 角色：般叶（Banye），「痞帅的设计师」，Q 版大头（头身比约 1:1.3）
- 银白普通短发（不飘逸）、不戴眼镜、黑色上挑眼线
- 左耳 1 枚银环 + 右耳 4 枚银环（不对称核心识别点）+ 银色链条项链
- 默认白色西装套装；多套穿搭（白西装 / 礼服 / 牛仔）
- 全部锚点、锁色、动作库见 `references/ip/banye/ip.md`

每次生图都会自动加载般叶的设定图 + 校准图 + 锚点，**无需指定角色**。

---

## 换装路由（按关键词自动选服装）

般叶**身份锚（银白发/左1右4银环/银项链/无眼镜/黑眼线/圆润少年脸/Q版大头）永远不变，权重最高**；只有衣服随关键词切换。

| 你说的话 | 自动选用服装 | 服装参考图（生成后入库才生效） |
|----------|--------------|-------------------------------|
| 不指定 / 白西装 | 白西装（默认） | `outfits/white_suit/reference.png` |
| 般叶穿短袖 | 短袖 | `outfits/short_sleeve/reference.png` |
| 般叶穿背心 | 背心 | `outfits/vest/reference.png` |
| 般叶穿黑西装 | 黑西装 | `outfits/black_suit/reference.png` |
| 般叶穿礼服 | 礼服 | `outfits/tuxedo/reference.png` |
| 般叶牛仔风 | 牛仔 | `outfits/denim/reference.png` |
| 般叶潮流/流行 | 流行 | `outfits/street/reference.png` |
| 般叶韩系 | 韩系 | `outfits/korean/reference.png` |
| 般叶杀马特 | 杀马特/视觉系 | `outfits/visual/reference.png` |

> 完整关键词映射与服装描述见 `references/ip/banye/ip.md`「衣橱库」。服装参考图由用户按提示词自生成并发回，我存入 `outfits/{id}/` 后，换装可靠性拉满。

---

## 触发词

`配图` / `给我般叶配图` / `帮我配图` / `illustration`

> 无需说「用般叶」——本 Skill 生出来的图主角永远是般叶。

---

## 参考文件（按需加载）

| 文件 | 何时加载 |
|------|---------|
| `references/styles/quirky-sketch.md` | 生图时（风格定义 + 色纪律 + QA） |
| `references/composition-patterns.md` | 出策略时 |
| `references/shot-config.md` | 出策略时（配图策略单落盘格式） |
| `references/prompt-template.md` | 组装 prompt 时 |
| `references/qa-checklist.md` | 质检时 |
| `references/ip/banye/ip.md` | 般叶全部锚点 / 锁色 / 动作库 / 序列图导游 |

---

## 生图能力

调用当前 AI 软件**内置的生图工具**（如 WorkBuddy ImageGen / Codex `@Image Gen` / Cursor `GenerateImage` 等）。Skill 负责策略、prompt 组装、参考图附件、QA；生图由平台工具执行。接口语义：文本 prompt + 可选图片附件。

平台适配优先级：

1. 支持显式图片附件的平台：把般叶参考图作为 image reference 附件传入（见 `prompt-template.md`「参考图」）。
2. 不支持图片输入且无法把图片放入上下文时，暂停说明原因；只有用户接受降级时，才使用 `ip/banye/ip.md` 文字锚点描述。

---

## 核心变量

| 变量 | 默认值 | 说明 |
|------|--------|------|
| `$STYLE` | `quirky-sketch` | v1.0 固定，不切换 |
| `$RATIO` | `16:9` | 宽高比；用户可指定任意比例 |
| `$IP` | `banye` | **固定**；本 Skill 仅此一个角色 |
| `$TITLE` | 无 | 用户要求时顶部手写标题 |
| `$COUNT` | 自动推断 | 配图张数 |
| `$OUTPUT_SIZE` | 无 | **可选**；仅用户明确要求具体像素时记录 |

**推荐像素（非强制）：** 16:9 → 建议 1920×1080；3:4 → 建议 1080×1440。

---

## 工作流

### Quick Mode

用户已给正文且变量可推断 → 不多问，直接生图。以下情况才确认：用户说「先别生图」、变量冲突、比例不明确。

### Step 1 · 意图确认

记录：`$RATIO` · `$TITLE` · `$COUNT` ·（可选）`$OUTPUT_SIZE`

Quick Mode 推断：竖版/小红书 → 3:4；否则 → 16:9。

### Step 2 · 消化内容 + 出策略

> 策略细节以 `composition-patterns.md` 为准；落盘格式以 `shot-config.md` 为准。

1. 加载上述两文件
2. 按 `composition-patterns.md` 的 **Step 2 决策流程** 执行（二轴 → 创意生成法六步 → 构图库 → Shot Config）
3. Quick Mode：默认直接落盘并进入 Step 3；用户说「先看策略」时先展示摘要

### Step 3 · 组装 Prompt + 生图

1. 加载 `styles/quirky-sketch.md`、`prompt-template.md`、`ip/banye/ip.md`
2. 读 `ip/banye/ip.md` 的 `ref_mode`（当前为 `dual`）：
   - `dual` → 设定图 `reference-character.png` + 校准图 `examples/quirky-sketch/banye-sample.png` 一并传入
   - 参考图未进上下文，不得声称已执行般叶流程
3. 填充变量槽，调用生图工具（`IP_DESC` 在 `STYLE_DNA` 之前，见 `prompt-template.md`）

### Step 4 · QA 质检

加载 `qa-checklist.md`。`$OUTPUT_SIZE` 有值时 → 等比缩放 + 白底留白，禁止裁切。不通过 → 重试，最多 2 次。
> 般叶专属走形信号见 `ip/banye/ip.md`「QA · 走形失败信号」。

### Step 5 · 交付

```
outputs/{YYYYMMDD}-{slug}/
  shot-config.md      ← 配图策略 + 插入位置（与图片同时交付）
  01-{slug}.png
  02-{slug}.png       ← 多张时继续编号
```

---

## 版本

`v1.0` · 2026-07-30 · 自 gimi-illustration Public 2.0 派生；锁定单一角色般叶（Banye），去除 Gimi / none / 自定义 IP 录入流程。
