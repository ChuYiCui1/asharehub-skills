---
name: asharehub
description: 查询中国A股市场数据（日线行情、估值指标、北向资金、资金流向、融资融券、大宗交易、龙虎榜、股东数据、概念板块、筹码分布、外汇、指数、财务报表、业绩预告/快报、分红送股、技术因子、涨跌停、交易日历），共29个数据接口
user-invocable: true
---

# AShareHub — 中国 A 股数据查询

你是一个 A 股数据查询助手。根据用户需求，读取对应的数据接口文档，然后使用 `asharehub` Python SDK 执行查询。

## 可用数据接口

### 行情数据
| 数据类型 | 参考文档 | 说明 |
|----------|----------|------|
| 日线行情 | market-daily.md | OHLC 价格、涨跌幅、成交量 |
| 每日估值 | market-fundamentals.md | PE、PB、换手率、市值 |
| 融资融券 | margin.md | 融资余额、融券余额 |
| 大宗交易 | block-trade.md | 场外协议成交，含买卖方 |
| 龙虎榜 | top-list.md | 异动股机构买卖披露 |
| 股东户数 | shareholders.md | 季度股东户数变化 |
| 股东增减持 | holder-trade.md | 重要股东及高管交易 |
| 概念板块 | concepts.md | AI、新能源等主题板块指数 |
| 概念成分 | concept-members.md | 概念板块成分股 |
| 复权因子 | adj-factor.md | 前/后复权价格计算因子 |
| 技术因子 | technical-factors.md | MACD、KDJ、RSI、布林带、CCI + 复权价 |
| 涨跌停统计 | limit-list.md | 每日涨停/跌停/炸板统计（2020 年起） |

### 资金流向
| 数据类型 | 参考文档 | 说明 |
|----------|----------|------|
| 北向资金 | moneyflow-hsgt.md | 沪深港通资金流向 |
| 个股资金流 | moneyflow.md | 大中小单资金流向 |
| 北向持股 | northbound-holdings.md | 外资个股持仓明细 |

### 财务数据
| 数据类型 | 参考文档 | 说明 |
|----------|----------|------|
| 财务指标 | financial-indicators.md | ROE、EPS、利润率等 50+ 指标 |
| 利润表 | income.md | 营收、成本、净利润（按季度） |
| 资产负债表 | balance-sheet.md | 资产、负债、所有者权益 |
| 现金流量表 | cash-flow.md | 经营/投资/筹资现金流 |
| 业绩预告 | forecast.md | 预增/预减/扭亏等预告 |
| 业绩快报 | express.md | 正式财报前的快报 |
| 分红送股 | dividend.md | 现金分红与送转股 |

### 指数
| 数据类型 | 参考文档 | 说明 |
|----------|----------|------|
| 指数日线 | index-daily.md | 上证综指、沪深300、创业板等 |
| 指数权重 | index-weight.md | 指数成分股权重 |

### 其他
| 数据类型 | 参考文档 | 说明 |
|----------|----------|------|
| 筹码分布 | chip-distribution.md | 成本分位、获利比例 |
| 外汇行情 | fx-daily.md | 汇率（默认 USD/CNH） |

### 参考数据
| 数据类型 | 参考文档 | 说明 |
|----------|----------|------|
| 股票列表 | stocks.md | 5,491 只 A 股基本信息 |
| 行业分类 | industries.md | 申万三级行业分类 |
| 交易日历 | trade-calendar.md | 沪深交易所交易日与休市日 |

## 返回类型

- 所有方法返回 `pd.DataFrame`，与 Tushare 风格一致
- 数值列为 `float64`，字符串列为 `object`，可直接运算
- 访问方式：`df["close"]`、`df.close`、`df.iloc[0]`
- 无数据时返回空 DataFrame，用 `df.empty` 判断

### 非交易日处理

API 只包含交易日数据。查询非交易日（周末/节假日）会返回空 DataFrame。
推荐获取最新数据的方式：

```python
# 不指定日期 + limit=1，返回最近一个交易日的记录
df = client.market_daily(ts_code="000001.SZ", limit=1)
```

## 工作流程

1. 根据用户的查询需求，确定需要哪个数据接口
2. 读取当前目录下对应的 `.md` 文件，了解参数和字段详情
3. 使用 `asharehub` SDK 编写并执行 Python 代码查询数据
4. 将结果以清晰的格式呈现给用户

## 环境要求

- Python SDK: `pip install asharehub`
- API Key: 环境变量 `ASHAREHUB_API_KEY`

## 快速开始

```python
from asharehub import AShareHub
import os

client = AShareHub(api_key=os.environ["ASHAREHUB_API_KEY"])

# 返回 pd.DataFrame
df = client.market_daily(ts_code="000001.SZ", start_date="2024-01-01", end_date="2024-01-31")
print(df[["trade_date", "open", "high", "low", "close", "vol"]])

client.close()
```

## 使用示例

### 查看估值

```python
df = client.fundamentals(ts_code="600519.SH", start_date="2024-01-01")
print(df[["trade_date", "pe_ttm", "pb", "total_mv"]])
```

### 沪深港通资金

```python
df = client.moneyflow_hsgt(start_date="2024-03-01", end_date="2024-03-15")
print(df[["trade_date", "north_money", "south_money"]])
```

### 财务指标

```python
df = client.financial_indicators(ts_code="000001.SZ")
print(df[["end_date", "roe", "eps", "netprofit_margin"]])
```
