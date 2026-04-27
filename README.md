# 今晚打不打球

一个可直接部署到 GitHub Pages 的单 HTML AI 角色聊天 WebApp。

项目目标：做一个“直男体育生兄弟群”风格的 IM + 场景体验。用户可以在群聊、单人私聊、场景模式之间切换，也可以通过入口向导生成本次场景配置。

## 当前推荐入口

### 场景模式 + 向导页

当前最新场景入口：

```text
scenes-v06.html
```

GitHub Pages：

```text
https://tyu-mint.github.io/sports-bros-ai/scenes-v06.html?v=06
```

特点：

- 第一页输入 Endpoint / API Key / Model
- 圆形箭头进入入口向导
- 下方保留“直接进入场景”
- 向导 Agent 使用“您”称呼用户
- 语气平淡、克制、服务型
- 向导会生成“本次规则包”
- 配置卡可点击修改
- 确认后进入场景
- 进入后复用 `scenes-v04.html` 的场景 + IM 内核

### 稳定 IM 入口

当前稳定 IM：

```text
index-v063.html
```

GitHub Pages：

```text
https://tyu-mint.github.io/sports-bros-ai/index-v063.html?v=063
```

特点：

- 真多 agent 群聊
- Router Model 先选择发言人
- 每个体育生独立 prompt
- 时间作为系统元数据传入，避免模型复读时间戳
- 长按自己的消息可编辑
- 编辑模式下可修改任意消息上下文
- 备注名、个人资料、备份、导入
- 主动消息
- 自动 `safe / coarse / suggestive / nsfw` 状态
- Router Model / Deep Model 字段
- 三层记忆结构

## 推荐配置

```text
Endpoint: https://api.deepseek.com
Main Model: deepseek-chat
Router Model: deepseek-chat
Deep Model: 可留空，或填写支持深思的模型
Key: 你的 API Key
```

`Router Model` 用来判断：

- 群聊由谁发言
- 是否触发教练
- 是否进入深思
- 是否切换内容模式
- 是否进入粗口 / 暗示 / NSFW 状态

`Deep Model` 用来处理更复杂的关系判断、边界判断和场景推演。留空时会回退到 Main Model。

## 角色设定

当前五个体育生 agent：

| Agent | 年龄 | 方向 |
| --- | ---: | --- |
| 周野 | 18 | 篮球队，外向主心骨，行动号召型 |
| 陈骁 | 18 | 足球队，嘴欠损友，起哄接梗快 |
| 林川 | 18 | 田径队，话少行动派，关心不解释 |
| 赵恺 | 18 | 健身，自律，催饭催睡催动起来 |
| 阿航 | 18 | 游泳队，阳光话痨，气氛组 |

所有角色均设定为 18 岁成年人。

## 主要版本

### `index-v063.html`

当前 IM 稳定版。

核心修复：

- 群聊改成真多 agent 架构
- Router 选择发言人
- 每个 agent 单独生成自己的回复
- 时间元数据从聊天文本中移出
- 输出前清洗时间戳和角色名前缀

### `scenes-v04.html`

场景模式稳定内核。

功能：

- 场景选择
- Scene Agent 场景描写
- 快捷行为按钮
- 动作格式 `(动作)台词`
- 手机端 IM 浮层
- IM 面板接入 `v0.6.3` 核心能力

### `scenes-v05.html`

第一版入口向导。

功能：

- API key 后进入极简输入页
- 向导 Agent 生成场景配置
- 确认后进入场景

### `scenes-v06.html`

当前最新入口向导。

新增：

- 高级服务型向导 Agent
- 使用“您”称呼用户
- 生成“本次规则包”
- 显示可编辑配置卡
- 支持修改配置项后再进入场景

## 场景配置卡字段

`scenes-v06.html` 的向导会生成：

```json
{
  "title": "夜里宿舍",
  "scene": "宿舍",
  "mode": "safe | coarse | suggestive | nsfw",
  "intensity": "soft | medium | explicit",
  "relationshipTone": "brother | rough_bro | teasing | direct",
  "atmosphere": ["夜晚", "直接", "粗粝"],
  "participants": ["zhouye", "chenxiao", "linchuan", "zhaokai", "ahang"],
  "intro": "开场描写",
  "scenePrompt": "Scene Agent 补充提示",
  "agentOverrides": {
    "zhouye": "本场行为倾向",
    "chenxiao": "本场行为倾向"
  },
  "quick": ["(动作)快捷行为"],
  "boundaries": ["本次边界"]
}
```

用户可以在进入前点击卡片里的任意项目修改。

## 已实现能力

- 单 HTML 部署
- 手机端适配
- API Key 本地保存
- IM 首页
- 群聊 / 私聊
- 真多 agent 群聊
- Router 发言人选择
- Scene Agent
- 入口向导 Agent
- 配置卡编辑
- 动作格式 `(动作)台词`
- 5 分钟时间分隔
- 时间元数据修复
- 长按编辑消息
- 编辑上下文
- 备注名
- 个人资料
- 备份 / 导入
- 主动消息
- 浏览器通知权限入口
- 教练 Agent
- 自动内容状态切换
- 三层记忆数据结构

## 规划中

- 正式版统一存储 key，升级后保留旧对话记录
- 动态角色档案提取器
- 场景模式和 IM 更深层互通
- PWA / Telegram 推送
- API Proxy，解决浏览器 CORS 和 Key 暴露问题
- 将单 HTML 拆分为 `index.html + app.js + style.css`

## 使用方式

推荐通过 GitHub Pages 打开：

```text
https://tyu-mint.github.io/sports-bros-ai/scenes-v06.html?v=06
```

或者直接测试 IM：

```text
https://tyu-mint.github.io/sports-bros-ai/index-v063.html?v=063
```

## 常见问题

### `failed to fetch`

常见原因：

1. API 服务限制浏览器 CORS
2. 网络无法访问 Endpoint
3. 直接从 `file://` 打开 HTML
4. Endpoint 填写缺少 `/v1` 或服务不兼容 OpenAI Chat Completions 格式

稳定方案是后续加 API Proxy：

```text
手机网页 -> /api/chat -> 模型 API
```

### 为什么每次新版本记录会空？

当前每个测试版本使用独立 `localStorage` key，方便避免旧数据污染新版本。正式版会改成稳定 key + schema migration，用来保留历史对话、备注、设置和记忆。

## 当前建议

优先测试：

```text
scenes-v06.html
```

确认入口向导、配置卡、场景进入、手机 IM 浮层稳定后，再把它设为默认场景入口。
