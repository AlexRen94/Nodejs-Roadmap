# 性能指标 QPS、TPS 

## 快速导航
- 什么是 QPS？
- 什么是 TPS
- TPS 与 QPS 的区别？
- 系统扩容评估

## 什么是 QPS

QPS（Query Per Second）指每秒查询量，规定时间内所能处理的流量大小，通常 QPS 值越大服务器的吞吐量也就越大，相对的服务器负荷也会越高。

QPS = 并发量 / 平均响应时间
并发量 = QPS * 平均响应时间

## 什么是 TPS

TPS（TransactionPerSecond）指每秒事物处理量，每秒钟系统所能处理的交易或事务的数量，用来形容系统的性能。

## TPS 与 QPS 的区别？

例如一次下单请求，访问一次创建订单接口产生一次 TPS，对于服务器的请求可能会产生多次，比如查询用户地址信息、商品数据信息、商品报价信息，这些请求计入 QPS，也就是产生了 3 次 QPS。

## 系统扩容评估

根据二八法则来评估系统扩容需要多少台机器，二八法则即 20% 的时间承载 80% 的流量，我们把这 20% 时间称为峰值时间。

换算公式：
```
(总 PV 数 * 80%)／(每天描述 * 20%) = 峰值时间每秒请求数
峰值时间内每秒请求数 (QPS)／单台机器 QPS = 需要的机器
```

假设我们有 1000 万 PV，总共需要的 QPS 为多少？

```
(10000000 * 0.8) / (24 * 60 * 60 * 0.2) = 463 (QPS)
```

假设每台机器支撑 100 QPS，则总共需要的机器为

```
463（总共 QPS）/ 100（单机 QPS）= 5（约需要 5 台机器）
```
