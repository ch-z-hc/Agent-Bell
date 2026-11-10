# Agent-Bell

Codex / Pi 回合结束通知工具，通过 [WxPusher](https://wxpusher.zjiecode.com/) 在手机或桌面客户端接收通知。

- 支持 Codex 和 Pi，可分别安装或同时使用。
- 通知包含机器名、agent 名称、回复摘要和时间。
- 支持模型摘要；未配置摘要模型时使用最后回复的首行。

## 通知示例

```text
[laptop · Codex]
修复登录页的表单验证
任务已完成
时间：2026-10-08 15:30:00
```

“任务已完成”是固定文案，仅表示本轮回复结束。

## 使用

[安装指南](docs/guide.md) · [配置说明](docs/configuration.md)

通知正文发送至 WxPusher。启用模型摘要时，本轮请求和最后回复会发送至所选模型服务。

[MIT License](LICENSE)
