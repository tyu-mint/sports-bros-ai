# 今晚打不打球

AI 体育生兄弟群 IM WebApp。当前版本是单 HTML，可直接部署到静态托管平台。

## 当前版本

`v0.4-editable-context`

功能：

- 首次打开输入 Endpoint / API Key / Model
- IM 首页：置顶群聊 + 5 个独立体育生 agent
- 群聊多 agent 回复
- 单人私聊独立 prompt
- 兄弟相处教练，仅在需要时显示
- 每个体育生独立后台长期记忆
- 全局用户偏好、边界、社交观察
- 可编辑用户消息和体育生消息，修改上下文
- 可删除消息
- 手机端适配

## 使用

直接打开 `index.html`。

推荐部署到 HTTPS 静态托管：

- Cloudflare Pages
- Netlify
- Vercel
- GitHub Pages

配置：

```text
Endpoint: https://api.deepseek.com
Model: deepseek-chat
Key: 你的 DeepSeek API Key
```

## 常见问题

`failed to fetch` 常见原因：

1. 直接从手机本地 `file://` 打开 HTML
2. API 服务限制浏览器 CORS
3. 网络无法访问 Endpoint

稳定方案是加一个 API Proxy：

```text
手机网页 -> /api/chat -> DeepSeek API
```
