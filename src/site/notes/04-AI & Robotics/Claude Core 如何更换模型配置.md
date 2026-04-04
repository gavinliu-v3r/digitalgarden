---
{"aliases":["Claude Core 模型切换","Claude Code 模型配置"],"created":"Saturday, April 4th 2026, 2:48:34 pm","modified":"Saturday, April 4th 2026, 2:51:06 pm","dg-publish":true,"tags":["domain/ai"],"related":"","author":"Gavin","permalink":"/04-AI & Robotics/Claude Core 如何更换模型配置/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":["Claude Core 模型切换","Claude Code 模型配置"],"created":"Saturday, April 4th 2026, 2:48:34 pm","modified":"Saturday, April 4th 2026, 2:51:06 pm","tags":["domain/ai"],"related":"","author":"Gavin"}}
---


## 配置文件位置

配置文件位于用户目录下的 `.claude` 文件夹中：

```bash
vim ~/.claude/settings.json
```

> [!tip]
> 如果目录不存在，先运行一次 `claude` 命令会自动创建配置目录。

## 完整配置示例

```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "your_zhipu_api_key",
    "ANTHROPIC_BASE_URL": "https://open.bigmodel.cn/api/anthropic",
    "API_TIMEOUT_MS": "3000000",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "glm-4.5-air",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "glm-4.7",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "glm-4.7"
  },
  "enabledPlugins": {
    "obsidian@obsidian-skills": true
  },
  "extraKnownMarketplaces": {
    "obsidian-skills": {
      "source": {
        "source": "github",
        "repo": "kepano/obsidian-skills"
      }
    }
  },
  "model": "haiku"
}
```

## 配置项说明

### 环境变量 (env)

| 配置项 | 说明 | 示例值 |
|--------|------|--------|
| `ANTHROPIC_AUTH_TOKEN` | API 密钥 | 你的智谱 API Key |
| `ANTHROPIC_BASE_URL` | API 基础地址 | `https://open.bigmodel.cn/api/anthropic` |
| `API_TIMEOUT_MS` | 请求超时时间（毫秒） | `3000000` (50 分钟) |
| `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` | 禁用非必要流量 | `1` 表示启用 |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | Haiku 级别模型 | `glm-4.5-air` |
| `ANTHROPIC_DEFAULT_SONNET_MODEL` | Sonnet 级别模型 | `glm-4.7` |
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | Opus 级别模型 | `glm-4.7` |

### 模型映射说明

Claude Code 将内部模型级别映射到具体的模型名称：

- **haiku**: 快速响应，适合简单任务
- **sonnet**: 平衡型，适合大多数任务
- **opus**: 最强模型，适合复杂推理

### 默认模型

配置文件底部的 `model` 字段指定启动时默认使用的模型级别：

```json
"model": "haiku"
```

可选值：`haiku`、`sonnet`、`opus`

## 智谱 AI 模型配置

如果你使用智谱 AI (GLM) 作为后端：

| Claude 级别 | 推荐模型 | 说明 |
|------------|---------|------|
| Haiku | `glm-4.5-air` | 轻量快速 |
| Sonnet | `glm-4.7` | 标准能力 |
| Opus | `glm-4.7` 或 `glm-4-plus` | 最强能力 |

## 切换模型的方法

### 方法 1：修改配置文件

编辑 `~/.claude/settings.json`，修改 `"model"` 字段的值。

### 方法 2：运行时切换

在 Claude Code 会话中，可以使用 `/model` 命令临时切换模型：

```bash
/model sonnet
```

> [!note]
> 运行时切换仅对当前会话有效，重启后会恢复配置文件中的默认值。

## 验证配置

修改配置后，重启 Claude Code 并检查配置是否生效：

```bash
claude
```

在会话中输入：

```bash
/model
```

查看当前使用的模型。

## 常见问题

### Q: 配置修改后不生效？

A: 确保完全退出 Claude Code 后再重启，检查 JSON 格式是否正确。

### Q: 如何恢复默认配置？

A: 删除或重命名 `~/.claude/settings.json` 文件，重启 Claude Code 会生成新的配置文件。

### Q: 支持哪些 API 提供商？

A: Claude Code 兼容 Anthropic API 格式的服务，包括：

- 官方 Anthropic API
- 智谱 AI (GLM)
- 其他兼容 Anthropic API 格式的服务商
