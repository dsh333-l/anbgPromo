# 整屋风格预设库 (room-style-presets.md)

> 版本：v1.0 | 用途：门窗设计师 Step 7 整屋风格延展时调用。
> 说明：每个风格预设都包含吊顶/地面/墙面/窗套/窗台板/窗帘/家具 7 项，"一键成片"时整套套用。

---

## 预设结构

每个风格预设的字段：

```
吊顶：[造型 + 材质]
地面：[材质 + 颜色]
墙面：[处理 + 颜色]
窗套：[样式 + 颜色]
窗台板：[材质 + 颜色 / 无窗台]
窗帘：[材质 + 样式 + 颜色]
家具大件：[沙发/床/桌椅风格描述]
推荐门窗色：[关联 color-palette.md 编号]
prompt 关键词：[整段英文/中文关键词，用于 7 层结构 prompt]
```

---

## R01 简中风（新中式简约版）

- **吊顶**：石膏平顶 + 局部木纹梁 / 浅米色乳胶漆
- **地面**：深胡桃木地板 / 木纹瓷砖
- **墙面**：浅米色乳胶漆 + 局部木饰面或竹编装饰
- **窗套**：深胡桃木窗套，宽 80mm
- **窗台板**：胡桃木窗台板
- **窗帘**：双层棉麻帘 + 纱帘，米白或浅灰，落地款
- **家具大件**：胡桃木实木家具、布艺沙发、圆几、屏风
- **推荐门窗色**：C09 深胡桃木纹 / C16 外古铜内深木
- **prompt 关键词**：
  ```
  modern Chinese minimalist interior, walnut wood floor, cream wall with bamboo decor, dark walnut window casing, linen curtains, solid wood furniture, warm ambient light
  ```

## R02 现代简约

- **吊顶**：石膏平顶 + 隐藏式灯带 / 纯白
- **地面**：浅灰大理石纹瓷砖 / 浅色木地板
- **墙面**：纯白或浅灰乳胶漆，局部艺术涂料
- **窗套**：极窄黑色金属窗套或无窗套
- **窗台板**：石材薄板或无窗台
- **窗帘**：纯色亚麻帘，灰白或浅灰，简约罗马帘
- **家具大件**：直线条沙发、玻璃茶几、金属边几
- **推荐门窗色**：C01 哑光纯黑 / C03 哑光中灰
- **prompt 关键词**：
  ```
  modern minimalist interior, light grey marble floor, pure white walls, hidden ceiling light strips, ultra-thin black window frames, linen roman blinds, clean line furniture, natural daylight
  ```

## R03 轻奢

- **吊顶**：石膏造型顶 + 金属线条收边 / 微弧形
- **地面**：米黄大理石 / 鱼骨拼木地板
- **墙面**：浅米色硬包 + 金属线条
- **窗套**：香槟金或古铜金属窗套
- **窗台板**：米黄大理石窗台板
- **窗帘**：双层丝绒帘 + 纱帘，浅金或浅咖
- **家具大件**：丝绒沙发、大理石餐桌、金属脚椅
- **推荐门窗色**：C11 香槟金 / C16 外古铜内深木
- **prompt 关键词**：
  ```
  light luxury interior, beige marble floor, ivory fabric wall panels with gold trim, champagne gold window casing, velvet curtains, brass detail furniture, soft warm lighting
  ```

## R04 侘寂（Wabi-Sabi）

- **吊顶**：微水泥平顶 / 原色
- **地面**：微水泥地面 / 大板灰色瓷砖
- **墙面**：稻草漆 / 微水泥 / 自然原色
- **窗套**：原木色窄窗套或无窗套
- **窗台板**：原木板或无窗台
- **窗帘**：粗麻帘，米白或自然色，落地款
- **家具大件**：原木低矮家具、棉麻软装、陶器
- **推荐门窗色**：C08 浅橡木纹 / C03 哑光中灰
- **prompt 关键词**：
  ```
  wabi-sabi interior, micro-cement floor and walls, natural light wood window casing, raw linen curtains, low wooden furniture, ceramic objects, soft diffused natural light
  ```

## R05 法式

- **吊顶**：石膏线造型顶 + 中央吊灯 / 米白
- **地面**：人字拼或鱼骨拼木地板，中色调
- **墙面**：米色护墙板 + 石膏线 + 浅米乳胶漆
- **窗套**：白色或米色宽窗套，带石膏线收边
- **窗台板**：白色石材或木质窗台板
- **窗帘**：双层绸缎帘 + 蕾丝纱帘，落地米白或浅金
- **家具大件**：弧形沙发、雕花边几、复古吊灯
- **推荐门窗色**：C05 哑光纯白 / C06 米白
- **prompt 关键词**：
  ```
  french classic interior, herringbone wood floor, ivory wainscoting walls with crown molding, white window casing with profile, satin curtains with lace, curved fabric sofa, vintage chandelier
  ```

## R06 北欧

- **吊顶**：纯白平顶 / 局部原木梁
- **地面**：浅橡木地板
- **墙面**：纯白乳胶漆，局部跳色（莫兰迪色）
- **窗套**：白色或浅木窄窗套
- **窗台板**：白色石材或浅木窗台板
- **窗帘**：纯色棉麻帘，白或浅灰
- **家具大件**：曲木椅、布艺沙发、圆形茶几
- **推荐门窗色**：C05 哑光纯白 / C08 浅橡木纹
- **prompt 关键词**：
  ```
  scandinavian nordic interior, light oak floor, white walls with single accent color, white window casing, cotton curtains, bentwood chairs, fabric sofa, bright natural daylight
  ```

## R07 中古

- **吊顶**：浅灰平顶 / 局部木格栅
- **地面**：深色木地板 / 复古花砖
- **墙面**：深绿、酒红或深蓝乳胶漆 + 黄铜装饰
- **窗套**：深木色或黑色窗套
- **窗台板**：深木窗台板
- **窗帘**：天鹅绒帘，深绿/酒红/驼色
- **家具大件**：复古真皮沙发、黄铜茶几、皮质单椅
- **推荐门窗色**：C01 哑光纯黑 / C09 深胡桃木纹 / C12 古铜
- **prompt 关键词**：
  ```
  mid-century modern interior, dark walnut floor, deep green walls with brass accents, dark wood window casing, velvet curtains, vintage leather sofa, brass coffee table, warm tungsten light
  ```

## R08 工业风

- **吊顶**：水泥裸顶 + 黑色管道线
- **地面**：水泥自流平 / 深灰瓷砖
- **墙面**：裸砖墙 / 微水泥 / 深灰乳胶漆
- **窗套**：黑色金属窄窗套
- **窗台板**：黑色金属或无窗台
- **窗帘**：粗麻帘 + 黑色金属轨道，深灰或棕
- **家具大件**：皮沙发、铁艺茶几、金属灯具
- **推荐门窗色**：C01 哑光纯黑 / C04 砂面铁灰
- **prompt 关键词**：
  ```
  industrial loft interior, polished concrete floor, exposed brick wall, raw concrete ceiling with black pipes, black steel window frames, leather sofa, metal furniture, dramatic spot lighting
  ```

---

## 一键成片调用方式

整屋出图时调用 `dreamina image2image`，输入图为 Step 6 的分格效果图，prompt 中的 7 层结构这样组装：

```text
【风格锚定】[风格名]室内空间，建筑级渲染图，写实摄影质感
【光影色调】[根据风格选择，例如自然日光柔和均匀 / 暖色调灯光]
【视角构图】室内正对窗的构图，能完整看到窗、墙、地面、吊顶
【门窗规格】[沿用 Step 6 的门窗规格描述]
【室内陈设】
  吊顶：[预设吊顶]
  地面：[预设地面]
  墙面：[预设墙面]
  窗套：[预设窗套]
  窗台板：[预设窗台板]
  窗帘：[预设窗帘]
  家具：[预设家具大件]
【场景环境】[房间类型 + 楼层 + 朝向]
【整体氛围】[一句话定调]
```

---

## 客户没指定风格时的引导

按这个顺序提问：

1. 你家客厅最后想要什么感觉？放松/温暖/高级/通透/安静？
2. 看了哪些案例觉得喜欢？
3. 沙发是布艺还是真皮？地板是木的还是石材？
4. 偏冷色还是暖色？
5. 木色想要浅木还是深胡桃？

把回答映射到 R01-R08，给客户 1-2 个推荐选项。
