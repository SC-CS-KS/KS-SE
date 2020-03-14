# What Is Ansible?
```md
是一种自动化运维工具，基于 paramiko 开发的，基于模块化工作。

是一种集成IT系统的配置管理、应用部署、执行特定任务的开源平台，
它是基于python语言，由 Paramiko 和 PyYAML 两个关键模块构建。

集合了众多运维工具的优点，实现了批量系统配置、批量程序部署、批量运行命令等功能。
真正具有批量部署的是ansible 所运行的模块，ansible 只是提供一种框架。

ansible不需要在远程主机上安装client/agents，因为它们是基于 SSH 来和远程主机通讯的。
```

## 设计哲学
```md
1. Ansible，它很大的价值或者说设计理念，就是尽量的简单化。
2. 最大程度贴近自然语言。
3. 以确定性替代不确定性。
```

## vs Puppet、Chef
```md
优势在于
1. 模块化自动部署，将复杂的机器、角色和组件剥离，易于扩展
2. 对环境依赖较少（仅需要SSH的信任关系）
3. 上手的成本较低，构建的速度也较快
```

|项目|Puppet|SaltStack|Ansible|
|-------|-------|-------|-------|
|开发语言|Ruby	|Python	|Python|
|是否有客户端	|有	|有	|无|
是否支持二次开发	|不支持	|支持	|支持|
服务器与远程机器是否相互验证	|是	|是	|是|
服务器与远程机器的通信是否加密	|是，标准的SSL协议	|是，使用AES加密	|是，使用OpenSSH|
平台支持	|AIX , BSD, HP-UX, Linux , Mac OSX , Solaris, Windows  |BSD, Linux , Mac OS X , Solaris, Windows	|AIX , BSD , HP-UX , Linux , Mac OS X , Solaris|
是否提供Web UI	|提供	|提供	|提供，但是是商业版本|
配置文件格式	|Ruby 语法格式	|YAML	|YAML|
命令行执行	|不支持，大师可以通过配置模块实现	|支持	|支持|
