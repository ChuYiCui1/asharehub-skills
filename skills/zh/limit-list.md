# 涨跌停统计

## 背景说明 — A 股特色机制

A 股市场实行**每日价格涨跌停板制度**：股票当日价格涨跌幅度不能超过前一交易日收盘价的固定百分比。

| 板块 | 日涨跌幅 | 说明 |
|------|---------|------|
| 沪深主板 | **±10%** | 主流股票 |
| 创业板（300xxx） | **±20%** | 科技成长板 |
| 科创板（688xxx） | **±20%** | 科创板 |
| ST 股票 | **±5%** | 风险警示，财务异常公司 |
| 新股上市前 5 日 | 无限制 | 之后恢复对应板块限幅 |

### 投资意义
- **`limit_type="U"`（涨停）**：触及上限是 A 股重要看多信号，"首板"和"连板"（连续涨停）是游资和散户主流策略。
- **`limit_type="D"`（跌停）**：触及下限通常是恐慌抛售或重大利空。
- **`limit_type="Z"`（炸板）**：日内触及涨停但未能收于涨停价，往往是短线见顶反转信号。

### 关键字段解读
- **`fd_amount`（封单金额）**：涨停价位上的买单总额。封单越大代表买盘强劲。
- **`first_time` / `last_time`**：日内首次/最后一次触及涨停时间。早封 + 一字封死 = 信号强。
- **`open_times`**：日内被打开次数。0 次 = 一字板，越多越弱。
- **`limit_times`（连板数）**：连续涨停天数。"3 连板"是动量交易者关注的重点。

### 注意事项
- 涨跌停制度会**抑制极端行情下的价格发现**，重大利空时可能连续多日跌停才能跌到位。
- 这会造成"**锁仓**"——可能连续几天无法卖出。
- 连板股走势是 A 股财经媒体和散户社区的高频话题。

## SDK 方法

```python
client.limit_list(ts_code=None, start_date=None, end_date=None, limit_type=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.limit_list(limit=3, limit_type="U")
print(df[["trade_date", "ts_code", "name", "pct_chg"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit_type` | str | None | `U`=涨停，`D`=跌停，`Z`=炸板 |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `trade_date` | 交易日期 |
| `ts_code` / `name` | 股票代码 / 名称 |
| `close` / `pct_chg` | 收盘价 / 涨跌幅 |
| `first_time` / `last_time` | 首次/最后封板时间 |
| `open_times` | 开板次数 |
| `limit_times` | 连板天数 |
| `limit` | 类型：U=涨停，D=跌停，Z=炸板 |

## 数据范围

- 起始日期：2020 年起
- 不含 ST 股
- API 路径：`GET /v1/market/limit-list`
