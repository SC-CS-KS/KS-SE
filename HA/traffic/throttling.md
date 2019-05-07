# 限流

## 策略
* 计数器法
* 固定窗口
* 滑动窗口 - 适用于对异常结果「高容忍」的场景
* 漏桶 - 最适合作为一个通用方案
* 令牌桶 - 需要尽可能的压榨程序的性能

## 模式
* 客户端模式
* 服务端模式

## Implement
* [Nnginx 限流](https://github.com/SunnnyChan/knowledge-Sys-of-web/blob/master/nginx/utilities/Throttling.md)