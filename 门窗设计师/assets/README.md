# 门窗设计师素材目录

这个目录用来存放门窗设计师 skill 需要用到的真实素材。
门窗设计师 skill 在工作时，会从这里读取产品资料、风格模板图、色卡、品牌物料等。

---

## 目录结构

```
assets/
├── product-series/      ← 安贝格产品系列资料
├── style-templates/     ← 门窗风格模板图
├── color-swatches/      ← 颜色色卡和实物图
└── brand/               ← 品牌 logo、署名水印、方案封面背景
```

---

## product-series/ — 产品系列资料

放置安贝格官方产品系列的资料文件。

**建议子目录结构**：

```
product-series/
├── 75系列断桥铝/
│   ├── 参数表.pdf
│   ├── 剖面图.jpg
│   └── 应用案例/
├── 108系列推拉门/
│   ├── 参数表.pdf
│   └── ...
└── ...
```

**上传后操作**：
更新 `references/product-series.md`，把新系列按结构化字段追加到列表，并去掉占位说明。

---

## style-templates/ — 风格模板图

放置门窗风格的参考图和模板图，用于客户在 Step 4 选择风格时浏览。

**建议命名格式**：`[风格归类]-[编号]-[简述].jpg`

例：

- `S01-极简极窄-01-黑框落地.jpg`
- `S03-中式万字格-01-胡桃色井字.jpg`
- `S05-工业窄边-01-黑框密集分格.jpg`

**上传后操作**：
更新 `references/style-templates.md` 的"安贝格官方模板"段。

---

## color-swatches/ — 颜色色卡

放置色卡实物图、官方色号对照图。

**建议命名格式**：`[色号]-[色名].jpg`

例：

- `C01-哑光纯黑.jpg`
- `C09-深胡桃木纹.jpg`

**上传后操作**：
更新 `references/color-palette.md` 的"安贝格官方色卡"段。

---

## brand/ — 品牌物料

放置品牌相关的物料：

- `logo.png` — 品牌标准 logo
- `logo-white.png` — 反白 logo
- `cover-bg.jpg` — 方案封面背景图
- `signature.png` — 设计师署名水印
- `brand-info.md` — 品牌一句话定调、官网、电话、地址

**上传后操作**：
更新 `references/export-template.md` 末尾的"品牌信息"段，把占位变量替换为真实信息。

---

## 上传规范

1. 文件名用中文或英文都可以，但建议同一类别保持一致风格
2. 图片优先 JPG，文档优先 PDF
3. 单个文件不超过 20 MB
4. 上传完成后，**记得回头更新对应的 `references/*.md` 文件**，否则 skill 不会读取
