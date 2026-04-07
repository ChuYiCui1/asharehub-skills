# 港股通持股 — 南向资金持仓

## 背景说明 — 内地资金持有港股

本接口是**北向持股的镜像数据**。追踪内地投资者通过沪深港通持有港股的明细。

### 重要性
- **"南向重仓股"**：内地投资者大量买入的港股，反映内地投资者的共识——通常是腾讯、美团、比亚迪、互联网平台、港股银行等。
- **港股定价权部分转移到内地**：对 A+H 双重上市公司，内地大量持有 H 股意味着 H 股定价越来越受内地情绪影响。
- **A/H 溢价信号**：`ratio` 大幅上升时，H 股相对 A 股的折价常常收窄（内地投资者套利）。

### 关键字段解读
- **`ts_code`**：港股代码（如腾讯为 "00700"）。
- **`vol`**：内地投资者持有股数。
- **`ratio`**：占总股本比例。
- **`exchange`**：SH 或 SZ，标识通过哪个通道持有。

### 注意事项
- 港股代码使用港股格式，非 A 股格式。
- 包括 H 股（内地注册、港股上市）和红筹股（港股注册的内地企业子公司）。
- 内地公募基金和个人投资者都可使用港股通，本数据为汇总。


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
