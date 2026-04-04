# 个股资金流向

## SDK 方法

```python
client.moneyflow(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 金额为 `float64`，成交量为 `int`。无数据时返回空 DataFrame。

## 示例

```python
df = client.moneyflow(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "net_mf_amount", "buy_elg_amount"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码，如 `000001.SZ`（平安银行）、`600519.SH`（贵州茅台） |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 股票代码 |
| `trade_date` | 交易日期 |
| `buy_sm_vol` | 小单买入量 |
| `buy_sm_amount` | 小单买入额 |
| `sell_sm_vol` | 小单卖出量 |
| `sell_sm_amount` | 小单卖出额 |
| `buy_md_vol` | 中单买入量 |
| `buy_md_amount` | 中单买入额 |
| `sell_md_vol` | 中单卖出量 |
| `sell_md_amount` | 中单卖出额 |
| `buy_lg_vol` | 大单买入量 |
| `buy_lg_amount` | 大单买入额 |
| `sell_lg_vol` | 大单卖出量 |
| `sell_lg_amount` | 大单卖出额 |
| `buy_elg_vol` | 特大单买入量 |
| `buy_elg_amount` | 特大单买入额 |
| `sell_elg_vol` | 特大单卖出量 |
| `sell_elg_amount` | 特大单卖出额 |
| `net_mf_vol` | 净流入量 |
| `net_mf_amount` | 净流入额（万元，正值=净买入） |

## 数据范围

- 起始日期：2020-01-02
- 记录数：570万+
- API 路径：`GET /v1/flows/moneyflow`
