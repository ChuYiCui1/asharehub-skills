<div align="center">

# AShareHub Skills

**AI-powered access to Chinese A-share market data**

[![PyPI](https://img.shields.io/pypi/v/asharehub.svg)](https://pypi.org/project/asharehub/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[Website](https://asharehub.com) · [API Docs](https://asharehub.com/docs) · [Get API Key](https://asharehub.com/console/register)

**English** | [中文](README_ZH.md)

</div>

---

## Overview

Official skills and reference docs for querying Chinese A-share market data via [AShareHub](https://asharehub.com). Compatible with Claude Code, Cursor, Windsurf, Cline, and any AI coding assistant.

## Prerequisites

```bash
pip install asharehub
export ASHAREHUB_API_KEY="ash_your_key_here"
```

Get your free API key at [asharehub.com/console/register](https://asharehub.com/console/register).

## Available Data

| Skill | Description | Data Range |
|-------|-------------|------------|
| [Market Daily](skills/en/market-daily.md) | Daily OHLC prices, volume, returns | 2020+ |
| [Market Fundamentals](skills/en/market-fundamentals.md) | PE, PB, turnover rate, market cap | 2010+ |
| [Northbound Flows](skills/en/northbound-flows.md) | Stock Connect capital flows | 2014+ |
| [Chip Distribution](skills/en/chip-distribution.md) | Cost basis percentiles, winner rate | 2020+ |
| [FX Daily](skills/en/fx-daily.md) | Foreign exchange rates (USD/CNH) | 2012+ |
| [Index Daily](skills/en/index-daily.md) | SSE Composite, CSI 300, ChiNext | 2010+ |
| [Financial Indicators](skills/en/financial-indicators.md) | ROE, EPS, margins, 50+ metrics | Quarterly |

## Installation

### Claude Code

```bash
git clone https://github.com/ChuYiCui1/asharehub-skills.git
cp -r asharehub-skills/skills/en/ /path/to/your/project/.claude/skills/asharehub/
```

Then invoke with `/asharehub` in Claude Code.

### Other AI Assistants

Each `.md` file is a self-contained reference with SDK method signature, parameters, and response fields. Paste into your assistant's context or reference directly.

## Project Structure

```
skills/
├── en/                         # English
│   ├── SKILL.md                # Main entry point
│   ├── market-daily.md
│   ├── market-fundamentals.md
│   ├── northbound-flows.md
│   ├── chip-distribution.md
│   ├── fx-daily.md
│   ├── index-daily.md
│   └── financial-indicators.md
└── zh/                         # 中文
    ├── SKILL.md
    └── ...
```

## All Access Methods

| Method | Description |
|--------|-------------|
| **Python SDK** | `pip install asharehub` — [Documentation](https://asharehub.com/docs) |
| **MCP Server** | `https://asharehub.com/mcp/sse` — Claude Desktop, Cursor, etc. |
| **REST API** | 7 endpoints at `https://asharehub.com/v1/` |
| **Skills** | This repository |

## License

[MIT](LICENSE)
