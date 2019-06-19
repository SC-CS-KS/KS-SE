# High Availability Architectures

## [What Is HA](What.md)

## 策略
### [流量](traffic/README.md)
* 限流
* 削峰
* 整型
### [服务](service/README.md)
* 服务隔离
* 服务降级
* 服务熔断

### 故障转移（failover）
* [负载平衡（Load balancing）](LoadBalancing/README.md)
* 灾难恢复（Disaster recovery，也称灾备）
* 虚拟化 - 一种资源管理技术
```md
一般所指的虚拟化资源包括计算能力和数据存储。
```
### [监控](monitor/README.md)

## [Implement](framework/README.md)
* Hystrix
* Sentinel

## Middleware
* [Apache ZooKeeper](https://github.com/SunnnyChan/sc.drill-code/tree/master/infra/apache-zookeeper)

## 参考
* [可伸缩架构 : 面向增长应用的高可用](https://github.com/SunnnyChan/SunnnyChan.github.io/blob/master/post/readme/reading/arch/scalable_arch)
* [分布式服务框架：原理与实践](https://github.com/SunnnyChan/SunnnyChan.github.io/blob/master/post/readme/reading/arch/DS-Service-Framework)
