# 技术因子

## SDK 方法

```python
client.technical_factors(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.technical_factors(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "close_qfq", "macd", "kdj_k", "rsi_6"]])
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

| 分类 | 字段 |
|------|------|
| **后复权价** | `open_hfq`, `close_hfq`, `high_hfq`, `low_hfq`, `pre_close_hfq` |
| **前复权价** | `open_qfq`, `close_qfq`, `high_qfq`, `low_qfq`, `pre_close_qfq` |
| **MACD** | `macd_dif`, `macd_dea`, `macd` |
| **KDJ** | `kdj_k`, `kdj_d`, `kdj_j` |
| **RSI** | `rsi_6`, `rsi_12`, `rsi_24` |
| **布林带** | `boll_upper`, `boll_mid`, `boll_lower` |
| **CCI** | `cci` |

## 备注

- qfq = 前复权，hfq = 后复权
- API 路径：`GET /v1/market/technical-factors`
