# 港股通持股 — 南向资金持仓

## SDK 方法

```python
client.southbound_holdings(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 6 列。无数据时返回空 DataFrame。

## 示例

```python
df = client.southbound_holdings(limit=5)
print(df[["trade_date", "ts_code", "name", "vol", "ratio"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 港股代码 |
| `start_date` | str | None | 起始日期 YYYY-MM-DD |
| `end_date` | str | None | 结束日期 YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

trade_date、ts_code(港股代码)、name、vol(内地持有股数)、ratio(占总股本比例)、exchange(SH/SZ 通道)。

## 数据范围

- 起始日期：2020-01-02
- 北向持股的镜像数据：内地投资者持有港股的明细
- API 路径：`GET /v1/flows/southbound-holdings`
