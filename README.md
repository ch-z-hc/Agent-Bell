# Agent-Bell

Codex / Pi 的回合结束通知工具。每轮回复结束后，通过 [WxPusher](https://wxpusher.zjiecode.com/) 发送通知，可在 WxPusher 手机或桌面客户端接收。

适合需要等 agent 处理较长任务，或同时在几台机器上运行 agent 的情况。

[![MIT License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## 功能

- 支持 Codex 和 Pi，可单独安装，也可同时使用。
- 通知包含机器名、agent 名称、回复摘要和时间。
- 有可用的摘要模型时生成简短摘要；否则使用最后回复的首行。

## 通知示例

```text
[laptop · Codex]
修复登录页的表单验证
任务已完成
时间：2026-10-08 15:30:00
```

“任务已完成”是通知中的固定文案，只表示本轮回复结束。实际执行结果需要查看原会话。

## 使用

先按 [WxPusher SPT 指南](https://wxpusher.zjiecode.com/docs/spt.html) 获取推送令牌，然后安装：

```sh
git clone https://github.com/ch-z-hc/Agent-Bell.git
cd Agent-Bell
node install.mjs
```

需要 Node.js 18+。按提示选择 `codex`、`pi` 或 `both`，填写 SPT 和机器名。

- Codex 需要支持 `Stop` hook，安装后在 `/hooks` 中审阅、信任并启用。
- Pi 需要支持 `agent_settled`，安装后运行 `/reload` 或重开会话。

安装时可以发送测试通知，在 WxPusher 客户端确认是否收到。

## 文档

- [安装、更新与常见问题](docs/guide.md)
- [机器名、摘要、代理等配置](docs/configuration.md)

## 数据说明

通知正文会发送给 WxPusher。生成模型摘要时，本轮请求和最后回复还会发送给所选模型端点。请勿公开 SPT 或 API key。

## 许可证

[MIT](LICENSE)
