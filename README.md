# Agent-Bell

**让 AI 继续干活，回合结束时手机响一声。**

Agent-Bell 为 Codex 和 Pi 提供回合结束提醒，通过 [WxPusher](https://wxpusher.zjiecode.com/) 把消息发到微信。把任务交给 agent 后，你可以切去做别的事，或暂时离开电脑，不用反复回来查看它有没有回复。

[![MIT License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

[快速开始](#快速开始) · [使用指南](docs/guide.md) · [配置说明](docs/configuration.md)

## 能帮你做什么

- **少盯一个窗口**：让 agent 改代码、排查问题或整理资料，一轮回复结束后自动提醒你回来查看。
- **一眼认出是哪项任务**：通知带有简短摘要，不用先打开会话才能知道这次在说什么。
- **分清是哪台机器**：每条消息标明机器名和 agent，多台电脑同时工作时也能辨认来源。
- **同时照顾 Codex 和 Pi**：可以只接入其中一个，也可以两个都用，统一在微信接收提醒。

## 你会收到什么

例如，让笔记本上的 Codex 修复登录页后，你会收到这样的消息：

```text
[laptop · Codex]
修复登录页的表单验证
任务已完成
时间：2026-10-08 15:30:00
```

有可用的摘要模型时，会根据本轮请求和最后回复生成简短摘要；没有可用模型时，仍可用最后回复的首行发送提醒。

这里的“任务已完成”表示 **agent 的这一轮回复已经结束**，不代表代码、测试或整个任务一定成功。具体结果仍需回到原会话查看。

## 快速开始

需要 Node.js 18+，以及支持 `Stop` hook 的 Codex 或支持 `agent_settled` 的 Pi。

**1. 获取接收通知的令牌**

按 [WxPusher SPT 指南](https://wxpusher.zjiecode.com/docs/spt.html) 扫码获取自己的 SPT。

**2. 安装并选择要接入的 agent**

```sh
git clone https://github.com/ch-z-hc/Agent-Bell.git
cd Agent-Bell
node install.mjs
```

按提示选择 `codex`、`pi` 或 `both`，输入 SPT 和机器名。安装结束时可以选择发送测试通知。

**3. 启用提醒**

- **Codex**：打开 `/hooks`，审阅、信任并启用通知 hook。
- **Pi**：运行 `/reload` 或重开会话。

让 agent 完成一轮回复，确认微信收到提醒，就可以开始使用了。

## 更多用法

- [验证通知、更新与常见问题](docs/guide.md)
- [自定义机器名、摘要与代理](docs/configuration.md)
- [开发与离线测试](docs/guide.md#开发)

## 数据与隐私

通知正文会发送给 WxPusher；生成模型摘要时，本轮用户请求和最后回复还会发送给所选模型端点。SPT 是推送凭据，请妥善保管，不要放进公开仓库、日志或截图。

## 许可证

[MIT](LICENSE)
