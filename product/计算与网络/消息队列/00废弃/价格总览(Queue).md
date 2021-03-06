腾讯云消息队列的收费由以下三部分组成：请求次数费用、消息堆积费用和出流量费用。所有费用按地域分别收取，每小时进行一次结算。

**注意：当前CMQ的请求次数费用、消息堆积费用，还未正式扣费。正式扣费前将邮件、电话、短信通知您，请各位开发者放心使用**


## 请求次数费用

单地域下，用户开通CMQ服务后，腾讯云将对 ***每小时*** 内消息队列的 API /SDK 请求次数进行统计。每百万次请求收费为： ***2.00元/百万次*** ，每小时结算一次。请求次数以百万为单位，精确到小数点后两位。

以下为计费示例：

- 2016年5月20号下午16：00-17：00，用户总请求次数为 1,323,454 次。则计算的请求次数 1.32（百万次），本时间段请求次数费用为 1.32 \* 2.00 = 2.64 元。
- 2016年5月20号下午18：00-19：00，用户总请求次数为181,000次。则计算的请求次数 0.18（百万次），本时间段请求次数费用为 0.18 \* 2.00 = 0.36 元。

## 消息堆积费用（包括消息回溯费用）

每小时 CMQ 将对单地域下的所有消息收取堆积费用，计算公式如下：

```
堆积消息费用＝消息总数 * 堆积消息单价
```

其中堆积消息单价为： ***0.010元/百万条/小时*** 。消息总数的统计以百万为单位，单小时内消息总数是每分钟消息堆积总数的平均数（即每小时抽取60个点取平均值）。计算精确到小数点后两位。消息回溯费用会合并在消息堆积费用里，一起计算

以下为计费示例： 
- 2016年5月20号下午16：00-17：00，A 队列的堆积消息总数量为1323450条，则该小时 A 队列的消息堆积费用为 0.01\*1.32 = 0.01 元

## 出流量费用

腾讯云网络流量计费原则：入流量免费，出流量计费。（内测期，公网流量费正常收取，建议您使用内网api地址进行内测）

| 流量类型 | 定义 | 用量 |单价 |
|---------|---------|---------|---------|
| 入流量 | 数据传入至CMQ |所有 |免费 |
| 内网出流量（同地域） | 同一个地域内的业务系统，使用消息队列的内网域名从CMQ主动获取数据或CMQ主动推送数据至此业务系统，产生的流量（经由腾讯云内网） |所有 |免费 |
| 外网出流量 | 同一个地域内的业务系统，使用消息队列的Internet域名从CMQ主动获取数据或CMQ主动推送数据至此业务系统，产生的流量（经由Internet） |所有 |中国大陆 0.80元/GB ; 中国香港 1.00元/GB ;北美 0.50元/GB |
