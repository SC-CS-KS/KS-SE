# What Is Multi-DataCenter
```md
异地多活技术是随着互联网环境进步发展到PB量级后，出现并逐步完善的一种用于解决高并发、大流量、高可用、热灾备需求的分布式解决方案。
当前异地多活技术是仅次于微服务架构、区块链等领域之后的热门技术话题，并且已经逐渐形成一套稳定的分布式SOA化理论。
```
## 发展历史
### 数据中心(DC)
```md
单DC是为企业等提供服务器硬件、存储、宽带、链路监控、安全保障等软硬件服务的机房。
```
### 光纤传输数据延迟问题
```md
光的传输速度是3.0×10^8m/s, 光纤中的数据传输速率远低于此，光纤传输延迟是互联网链路层的瓶颈。
两地三中心方案、同城多活、异地多活等的底层方案，很大部分都是围绕解决数据传输延迟带来的问题。
例如新浪微博北京的两个核心机房间延时在1ms左右，但北京机房到广州机房则有近40ms的延时。
```
### 两地三中心技术方案
```md
即生产数据中心、同城灾备中心、异地灾备中心。
多个数据中心是主备关系，即存在主次，业务部署优先级存在差别，针对灾难的响应与切换周期非常长，
RTO ( Recovery Point Objective)  与 RPO（Recovery Time Objective）目标无法实现业务零中断，资源利用率低下，投资回报无法达到预期。
本质上是一种通过简单资源堆砌提高可用性的模式，对高可用的提高、业务连续性的保证仍然只是量变，业务连续性及容灾备份一直没有实质性的跨越。
```
* 问题
```md
灾备中心是冷备份，在真正出现灾难性故障后，不能确定冷数据是否能及时恢复运行甚至及时恢复业务线。
浪费硬件资源，冷备份中心正常情况下始终全量备份，不对外提供业务，很可能是长期一直不使用的情况。
```
### “分布式多活数据中心”（Distributed Active/Active Data Centers）
*** 分布式 ***
```md
1. 是指数据中心在机房基础设施、地理空间、计算/存储/网络资源的软硬件部署上是分布而非集中的，
    满足灾备建设与业务联系的要求，多个DC在建设上可以循序渐进的展开，
    彼此保持一定的独立性，未来扩容升级可与现有架构保持良好兼容。
2. 是资源的调度可以跨越多个数据中心，运维管理可以基于全局，
    多个数据中心间实现有机结合与资源共享，逻辑上可以视为一个全局的大数据中心。
```
*** 多活 ***
```md
1. 是多中心之间地位均等，正常模式下协同工作，并行的为业务访问提供服务，实现了对资源的充分利用，
    避免一个或两个备份中心处于闲置状态，造成资源与投资浪费，通过资源整合，
    多活数据中心的服务能力往往双倍甚至数倍于主备数据中心模式；
2. 是在一个数据中心发生故障或灾难的情况下，其他数据中心可以正常运行并对关键业务或全部业务实现接管，
    达到互为备份的效果，实现用户的“故障无感知”。
```
#### 双活数据中心
```md
双活可以看作多活数据中心的一个特殊简化子集，也是最常见的模型。
双活聚焦两个数据中心的工作模式与机制，建设思路与技术选择是基于多活的裁剪和优化，
一些适合双活的方案在扩展性等方面未必适合于多活的应用场景，双活数据中心是多活数据中心的必经阶段。
```
#### 同城多活
```md
传统两地三中心架构在互联网行业的早期实践成熟方案是同城多活。

真正意思上的同城多活是指应用层多活和数据层同时多活，只有这两层层多活，才能达到实际的流量切换与连续业务，
当然在实施过程中从开发效率及商业目标等考虑，会使用一些伪同城多活的方案。
```
#### 异地多活
```md
是在相距有一定远距离地点的数据中心有多个相同业务需求的交易平台，并且每个地点的交易平台都是用来支撑分担流量的。

通常异地多活是跨地域的，而且距离一定要做到1000公里以上的范围。
异地多活的每个多活数据中心都要承担用户的读写流量。如果只是备或只读业务来讲，作用不是很大。

因为物理光纤的熟读传输限制，实际在同城使用的方案，几乎是不能完全使用在异地多活需求上。

Google做到了全球多个数据中心，都是多活的。
```
* 需要解决的问题
```md
数据传输延时
请求延迟
消息延迟
专线
数据一致性
分布式事务
服务依赖
队列依赖
流量控制
部署便捷
```
* 实施和运维成本
```md
1. 机房之间的延时
2. 专线问题: 机房专线成本巨大。同时单条专线的稳定性也很难保障。
3. 数据同步最最大的挑战
4. 依赖服务部署问题
    将小服务全部部署改造成本、维护成本问题。
5. 运维体系问题
    要求配套的服务和流程都能支持异地部署，包括预览、发布、测试、监控、降级等一系列高实施成本的运维改造方案。
6. 冗余
    如果有两个异地的数据中心，冗余量可能是一倍，因为要接管全量。
    但是如果有三个数据中心，互为备份，就不需要冗余两倍了。
```

* 总结
```md
多活的技术成本非常高，每家公司都不断在成本与业务之间综合平衡各种利弊，选择最好的方式服务业务。
多活技术并不能100%解决全部业务多活，只能尽量保证绝大部分用户的核心业务异地多活。
```

## 分布式多活数据中心与云计算
```md
现代多活方案常常会利用云计算平台的低部署和弹性运营成本与云计算平台搭建混合云环境。
分布式多活数据中心与云计算建设的思路既有相同之处也有差别，
云的形成可以基于数据中心的分布式技术，建设模型更接近互联网数据中心，
而分布式多活数据中心的实现和实践门槛相对要低，用户在建设运维时更多的会关注于自身业务联系性的要求与业务的快速响应及IT建设的持续优化，
对复杂的企业级应用提供更好的支撑，使得IT建设更多的基于自身现有资源和能力。

总之使用混合方式，而不盲目追求先进，体现了企业对于自身IT建设的把握与未来方向的掌控，
是大型企业数据中心、大型多活系统持续稳健前行的必经之路。
```