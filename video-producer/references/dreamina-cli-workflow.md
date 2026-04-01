# 即梦 CLI 操作流程 (dreamina-cli-workflow.md)

> 版本：v1.0
> 用途：video-producer 读取此文件，统一通过即梦 CLI 完成图片和视频生成。
> 方法来源：用户提供的《即梦 CLI 体验指南》。
> 重要说明：CLI 品牌名是即梦，但命令名统一使用 `dreamina`。

---

## Agent 总原则

- 所有视频生成任务统一使用 `dreamina` CLI，不再使用网页工具或 Kling。
- 提交任务前，先确认 CLI 已安装、已登录、余额查询正常。
- 默认复用现有登录态，不要每次任务都重新执行 `dreamina login`。
- 默认优先使用 `--poll=30`，先等待一轮结果；超时后再用 `query_result` 追结果。
- 如果任务依赖本地图片，必须先确认文件路径真实存在，再执行命令。
- 如果文档方法和其他旧说明冲突，以本文件为准。

---

## 安装与帮助

推荐安装命令：

```bash
curl -fsSL https://jimeng.jianying.com/cli | bash
```

安装完成后先执行：

```bash
dreamina -h
```

用于确认命令可用，并阅读当前环境支持的全部功能。

---

## 登录与自检

### 登录

```bash
dreamina login
```

- 该命令会自动拉起默认浏览器完成授权。
- 如果当前机器没有浏览器，CLI 会引导你手动导入登录态。
- 这不是每次都要执行的命令。只有首次登录、账号切换、登录态失效时才需要。

### 登录排障

```bash
dreamina login --debug
```

- 当浏览器没有自动拉起，或登录卡住时使用。
- 终端会打印回调地址和调试信息，便于排查。

### 登录成功自检

```bash
dreamina user_credit
```

- 如果能返回包含余额信息的 JSON，说明登录状态和环境配置正常。
- 如果这一步失败，不要继续提交生成任务，应先处理登录或配置问题。

### 推荐检查顺序

每次开始生成任务时，按这个顺序：

1. `dreamina -h`
2. `dreamina user_credit`
3. 只有在 `user_credit` 失败时，才执行 `dreamina login`
4. 登录后再次执行 `dreamina user_credit`

---

## 视频任务命令

### 文生视频

```bash
dreamina text2video \
  --prompt="镜头推进，一只橘猫从沙发上跳下来" \
  --duration=5 \
  --ratio=16:9 \
  --video_resolution=720P \
  --poll=30
```

适用：
- 没有首帧素材，直接根据镜头描述生成视频。
- 默认是 video-producer 的首选模式。

### 图生视频

```bash
dreamina image2video \
  --image ./first_frame.png \
  --prompt="镜头慢慢推近" \
  --duration=5 \
  --poll=30
```

适用：
- 已有首帧、参考图、产品图或场景图。
- 需要保持主体、构图或品牌元素一致时优先使用。

注意：
- `--image` 必须指向本地真实文件路径。

---

## 图片任务命令

### 文生图

```bash
dreamina text2image \
  --prompt="一只戴墨镜的橘猫" \
  --ratio=1:1 \
  --resolution_type=2k \
  --poll=30
```

适用：
- 封面图、图文页配图、首帧草图生成。

### 图生图

```bash
dreamina image2image \
  --images ./input.png \
  --prompt="改成水彩风格" \
  --resolution_type=2k \
  --poll=30
```

适用：
- 已有原图，需要做风格改写、结构微调或统一视觉风格。

注意：
- `--images` 必须指向本地真实文件路径。

---

## 异步任务处理

### 使用 `--poll`

在提交命令中加入 `--poll=<秒数>`，例如：

```bash
--poll=30
```

行为：
- 工具提交任务后，会以每秒 1 次的频率轮询状态。
- 如果在等待时间内完成，终端直接输出最终结果。
- 如果等待超时，终端先返回 `querying` 状态和 `submit_id`。

### 查询任务结果

```bash
dreamina query_result --submit_id=<你的_submit_id>
```

直接下载到指定目录：

```bash
dreamina query_result --submit_id=<你的_submit_id> --download_dir=./downloads
```

### 查看历史任务

```bash
dreamina list_task
dreamina list_task --gen_status=success
dreamina list_task --submit_id=<你的_submit_id>
```

---

## Agent 执行约定

### 默认生成策略

- F1 15 秒短视频：默认整段生成 1 条视频任务，不先拆镜头。
- F2 90 秒案例拆解：按段落拆成多个 5 秒或 10 秒镜头，再逐段生成。
- F3 30 秒情绪钩子：优先评估整段生成；效果不稳时再拆成 2-3 段。
- F4 图文长帖：统一使用 `text2image` 或 `image2image` 生成封面图和配图，不调用视频命令。

### 15 秒整段 Prompt 模板

推荐结构：

```text
[主体] 在 [场景] 中进行 [连续动作]，镜头 [镜头运动]，重点表现 [单一卖点/单一感受]，整体风格 [风格描述]，光线 [光线描述]，9:16 竖屏，15 秒。
```

写法要求：

- 只保留 1 个核心卖点，不把 3 个卖点塞进同一条 15 秒视频。
- 动作写成连续过程，不要写成 3 次跳切。
- 优先写用户能感知的结果，例如“安静下来”“不再西晒发烫”“开窗更安心”。
- 少写抽象词，多写可拍到的动作、表情、环境变化。
- 如果是前后对比，也尽量放在同一场景里完成，不要跨太多空间。

适合的 15 秒模板类型：

- 场景演示型：先有问题，后有改善。
- 前后对比型：同一空间里出现明显变化。
- 单点说明型：只展示一个判断标准或一个动作。
- 情绪钩子型：先给情绪，再给一个结论。

示例 1：

```text
临街卧室里，一位年轻女生先被窗外车声吵得皱眉，随后起身关上窗，房间立刻安静下来，她放松坐回床边，镜头从室内中景慢慢推进到窗边和人物表情，重点表现关窗前后噪音差异，整体风格真实居家、自然生活感、干净明亮，自然日光，9:16 竖屏，15 秒。
```

示例 2：

```text
西晒客厅里，下午阳光强烈照进室内，人物先抬手挡光感到闷热，随后画面转到窗边玻璃细节和更柔和稳定的室内状态，镜头缓慢推进并停留在人物感受和窗边细节，重点表现隔热后的舒适感，整体风格现代住宅、生活化、有质感，柔和自然光，9:16 竖屏，15 秒。
```

### 命令选择规则

- 15 秒默认整段视频：优先 1 条 `text2video` 或 `image2video` 命令。
- 没有参考图：优先 `text2video`。
- 有首帧或产品实拍：优先 `image2video`。
- 只做封面和图文：使用 `text2image` / `image2image`。
- 需要查历史、补下载、补拉结果：使用 `list_task` / `query_result`。

### 结果落盘

- 生成结果默认下载到项目内 `output/videos/YYYY-MM-DD-[topic]/raw/`
- 成片候选、封面候选、任务 JSON、submit_id 记录都要保留，便于 review-ops 复核。

---

## 常见问题

### 登录后仍提示无权限或失败

先检查两项：

1. `~/.dreamina_cli/config.toml` 是否存在且内容正常。
2. `dreamina user_credit` 是否能成功返回信息。

如果 `user_credit` 失败，说明登录或环境配置异常，不要继续测试生成命令。

### 登录流程卡住

执行：

```bash
dreamina login --debug
```

把终端里的调试信息作为排障依据。

### 异步任务迟迟没有最终结果

- 优先用带 `--poll=30` 的命令提交。
- 超时后记录 `submit_id`，稍后执行：

```bash
dreamina query_result --submit_id=<你的_submit_id>
```

### 切换账号

```bash
dreamina relogin
```

### 清空本地登录信息

```bash
dreamina logout
```

注意：
- 该命令只清除 `credential.json` 中的登录凭证。
- 不会删除 `config.toml` 和 `tasks.db`。

---

## 本地文件说明

- `~/.dreamina_cli/config.toml`：环境配置文件。
- `~/.dreamina_cli/credential.json`：本地登录凭证。
- `~/.dreamina_cli/tasks.db`：任务提交记录数据库。
- `~/.dreamina_cli/logs/`：工具运行日志目录。
