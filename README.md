# banye-illustration · 般叶专属配图 Skill

> 单一角色怪诞手绘配图 Skill —— **只能生成「般叶（Banye）」形象**。

## 这是什么

从 `gimi-illustration`（Public 2.0 / 内部 4.7）派生出的**精简版**：去掉了原版的 Gimi 角色、none 无角色模式、以及「自定义 IP 录入」流程，只保留一个固定角色 **般叶（Banye）** 和完整的怪诞手绘配图管线。

- 输入：中文文章正文
- 输出：怪诞手绘风格插画（默认 16:9，可指定任意比例）
- 主角：永远是般叶（银白普通短发、左耳1枚+右耳4枚不对称银环、银项链、白西装、Q版大头、痞帅设计师）

## 怎么用

对话里发：

```
配图

[粘贴你的文章正文]
```

- 触发词：`配图` / `给我般叶配图` / `帮我配图` / `illustration`
- 无需指定角色，生出来的图主角固定为般叶
- 支持选项：比例（如「3:4 竖版」）、张数（「配 3 张」）、标题（「顶部加手写标题」）

## 目录结构

```
banye-illustration/
├── SKILL.md                      入口与工作流
├── IP-NOTICE.md                  般叶角色归属说明
├── LICENSE                       MIT
├── references/
│   ├── prompt-template.md         Prompt 组装器
│   ├── composition-patterns.md   构图模式库
│   ├── shot-config.md            配图策略单格式
│   ├── qa-checklist.md           质检清单
│   ├── styles/
│   │   └── quirky-sketch.md      怪诞手绘风格定义
│   └── ip/
│       └── banye/
│           └── ip.md             般叶全部锚点 / 锁色 / 动作库
└── assets/
    └── ip/
        └── banye/
            ├── reference-character.png      设定图（身份锚）
            ├── reference-outfits.png        多套穿搭参考
            └── examples/quirky-sketch/
                └── banye-sample.png         怪诞手绘校准样板
```

## 想改般叶形象？

直接编辑 `references/ip/banye/ip.md`（锚点、锁色、动作库、序列图导游）。改完下次配图即生效。

## 许可

代码与文档：MIT（见 `LICENSE`）。般叶角色归用户自有。
