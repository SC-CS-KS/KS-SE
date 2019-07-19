# Web APIs

* [RESTful API](restful/README.md)
* [GraphQL API](GraphQL/README.md)

## Design
* [The Web API Checklist -- 43 Things To Think About When Designing, Testing, and Releasing your API](https://mathieu.fenniak.net/the-api-checklist/)

## RPC vs REST vs GraphQL
```md
在下列情况考虑 RPC 风格的 API：
偏向内部的API
没有太多的时间考虑API的设计或没有架构师
提供的API很难进行资源、对象抽象
对性能有高要求

在下列情况考虑REST风格：
偏向外部API
提供的API天生围绕资源、对象、管理展开
不能耦合客户端实现
资源的CRUD是可以对齐的（功能完整的）

在下列情况考虑GraphQL：
客户端对于数据的需求多变
数据具有图的特点
```

## References
* [How I measure Response Times of Web APIs using curl](https://www.tuicool.com/articles/ymyqUrr)