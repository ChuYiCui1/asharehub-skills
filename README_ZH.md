<div align="center">

# AShareHub Skills

**AI 驱动的中国 A 股市场数据查询**

[![PyPI](https://img.shields.io/pypi/v/asharehub.svg)](https://pypi.org/project/asharehub/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[官网](https://asharehub.com) · [API 文档](https://asharehub.com/docs) · [获取 API Key](https://asharehub.com/console/register)

[English](README.md) | **中文**

</div>

---

## 概述

AShareHub 官方 Skills 和参考文档，用于通过 AI 助手查询中国 A 股市场数据。兼容 Claude Code、Cursor、Windsurf、Cline 及任何 AI 编程助手。

## 环境准备

```bash
pip install asharehub
export ASHAREHUB_API_KEY="ash_你的密钥"
```

在 [asharehub.com/console/register](https://asharehub.com/console/register) 免费注册获取 API Key。

## 可用数据

| 数据接口 | 说明 | 数据范围 |
|----------|------|----------|
| [日线行情](skills/zh/market-daily.md) | OHLC 价格、成交量、涨跌幅 | 2020+ |
| [每日估值](skills/zh/market-fundamentals.md) | PE、PB、换手率、市值 | 2010+ |
| [北向资金](skills/zh/moneyflow-hsgt.md) | 沪深港通资金流向 | 2014+ |
| [筹码分布](skills/zh/chip-distribution.md) | 成本分位、获利比例 | 2020+ |
| [外汇行情](skills/zh/fx-daily.md) | 汇率（默认 USD/CNH） | 2012+ |
| [指数日线](skills/zh/index-daily.md) | 上证综指、沪深300、创业板 | 2010+ |
| [财务指标](skills/zh/financial-indicators.md) | ROE、EPS、利润率等 50+ 指标 | 按季度 |

## 安装使用

### Claude Code

```bash
git clone https://github.com/ChuYiCui1/asharehub-skills.git
cp -r asharehub-skills/skills/zh/ 你的项目路径/.claude/skills/asharehub/
```

在 Claude Code 中输入 `/asharehub` 即可调用。

### 其他 AI 助手

每个 `.md` 文件都是独立的参考文档，包含 SDK 方法签名、参数说明和返回字段。直接粘贴到你的 AI 助手上下文中即可使用。

## 项目结构

```
skills/
├── en/                         # English
│   ├── SKILL.md                # 主入口
│   ├── market-daily.md
│   ├── market-fundamentals.md
│   ├── moneyflow-hsgt.md
│   ├── chip-distribution.md
│   ├── fx-daily.md
│   ├── index-daily.md
│   └── financial-indicators.md
└── zh/                         # 中文
    ├── SKILL.md
    └── ...
```

## 所有访问方式

| 方式 | 说明 |
|------|------|
| **Python SDK** | `pip install asharehub` — [文档](https://asharehub.com/docs) |
| **MCP Server** | `https://asharehub.com/mcp/sse` — 支持 Claude Desktop、Cursor 等 |
| **REST API** | 7 个端点，`https://asharehub.com/v1/` |
| **Skills** | 本仓库 |

## 开源协议

[MIT](LICENSE)
