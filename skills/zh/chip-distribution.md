# 筹码分布

## 背景说明 — A 股特色技术分析

**筹码分布**是 A 股市场广泛使用的技术分析概念，欧美市场少见。它把每一股都当作一个"筹码"，按购入成本价分布建模。

### 它追踪什么
对每只股票每个交易日，估算：
- 当前所有持有者的历史买入成本分布
- 当前盈利者占比 vs 亏损者占比
- 所有持有者的成交量加权平均成本

### 投资应用
- **套牢盘构成阻力**：高位有大量持有者套牢，他们想"解套就跑"，自然形成压力位。`cost_85pct`（85% 分位成本）常用于识别阻力。
- **密集成本构成支撑**：成本密集区构成支撑。`weight_avg`（加权平均成本）常被关注。
- **`winner_rate` 反映情绪**：极高（>80%）时大多盈利，可能止盈；极低（<20%）时大多亏损，可能见底。

### 关键字段解读
- **`weight_avg`**：所有持有者的成交量加权平均成本（元）。
- **`winner_rate`**：当前盈利筹码占比（0–100）。
- **`cost_5pct`、`cost_15pct`、`cost_50pct`、`cost_85pct`、`cost_95pct`**：分位成本。如 `cost_50pct` 是中位持有者的成本。
- **`his_low` / `his_high`**：筹码分布历史最低/最高成本。

### 注意事项
- 这是**统计模型**而非真实持仓，是从历史成交量和价格反推估算的。
- 在 A 股散户技术分析圈很流行，机构研究较少使用。
- 最适合识别短期情绪和心理价位。

## SDK 方法

```python
client.chip_distribution(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.chip_distribution(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "weight_avg", "winner_rate"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码，如 `000001.SZ` |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code`, `trade_date` | 股票代码、日期 |
| `his_low`, `his_high` | 历史最低/最高价（元） |
| `cost_5pct` | 5% 成本分位（元） |
| `cost_15pct` | 15% 成本分位（元） |
| `cost_50pct` | 50% 成本分位 / 中位成本（元） |
| `cost_85pct` | 85% 成本分位（元） |
| `cost_95pct` | 95% 成本分位（元） |
| `weight_avg` | 加权平均成本（元） |
| `winner_rate` | 获利比例（0-100），>80 通常为强势行情 |

## 数据范围

- 起始日期：2020-01-02
- 记录数：730万+
- 中国市场特有的持仓成本分析指标
- API 路径：`GET /v1/chips/distribution`
