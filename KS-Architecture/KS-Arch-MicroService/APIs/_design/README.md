# API Design



## [POSIX File API](POSIX-File-API.md)

## [API 演进的正确方式](https://www.toutiao.com/i6695217482640130567/)
```md
10 个约定大致可以分为三类：
1. 谨慎发展
    避免不良功能
    最小化特性
    保持功能单一
    标记实验特征“临时”
    温柔删除功能
    
2. 严格记录历史
    维护更改日志
    选择版本方案
    编写升级指南

3. 缓慢而明显地改变
    兼容添加参数
    逐渐改变行为
```

# RPC Design

## 设计原则
* 单一性职责原则
* 安全性
* 可扩展性
* [幂等性](idempotence.md)


## 数据传输协议
### 二进制方式
```md
JRMP 专为Java远程对象制定的协议 Java Remote Method Protocol
RMI 参考Java 网络编程 RMI
```
* JSON-RPC
### 文本方式s
```md
	HTTP协议
		REST
		GraphQL
		Webhooks
```md

## [序列化](serialization/README.md)
* [JSON](https://github.com/SunnnyChan/knowledge-Sys-of/blob/master/knowledge-Sys-of-JSON/README.md)
* [Protocol Buffers](https://github.com/SunnnyChan/sc.drill-code/tree/master/cpp/protobuf)
* XML

## 功能
```md
动态代理
反射
序列化、反序列化
网络通信
编解码
服务发现和注册
心跳与链路检测
```

## 调用方式
```md
同步调用
异步调用
```
## 组件
```md
RpcServer 负责导出（export）远程接口

RpcClient 负责导入（import）远程接口的代理实现

RpcProxy 远程接口的代理实现

RpcInvoker
客户方实现：负责编码调用信息和发送调用请求到服务方并等待调用结果返回
服务方实现：负责调用服务端接口的具体实现并返回调用结果

RpcProtocol
负责协议编/解码

RpcConnector
负责维持客户方和服务方的连接通道和发送数据到服务方

RpcAcceptor
负责接收客户方请求并返回请求结果

RpcProcessor
负责在服务方控制调用过程，包括管理调用线程池、超时时间等

RpcChannel
数据传输通道
```

## 最佳实践
```md
* 路径规则
    API 获取的是一种资源，所以网址中尽量为名词，而非动词

* HTTP 请求方式
* 请求
> * 输入参数

* 响应
> * 返回码
> * 数据格式

* 版本

* 接口授权
```

## * [轻量级分布式 RPC 框架](http://www.importnew.com/20327.html)
```md
第一步：编写服务接口
第二步：编写服务接口的实现类
第三步：配置服务端
第四步：启动服务器并发布服务
第五步：实现服务注册
第六步：实现 RPC 服务器
第七步：配置客户端
第八步：实现服务发现
第九步：实现 RPC 代理
	CGLib
		CGLIB是一个功能强大，高性能的代码生成包
			它为没有实现接口的类提供代理，为JDK的动态代理提供了很好的补充
		通常可以使用Java的动态代理创建代理，但当要代理的类没有实现接口或者为了更好的性能
			CGLIB是一个好的选择。
第十步：发送 RPC 请求
```
