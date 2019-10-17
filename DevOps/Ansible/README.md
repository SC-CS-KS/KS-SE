# Ansible

## [What Is Ansible](WhatIs.md)

## Host - 定义部署的机器，可以根据用途去划分机器
```yaml
[data_switch_service]
127.0.0.1
```

## Vars - 定义变量

## Task - 任务
```md
根据 Ansible 提供的语意定义一些基础的动作,可以嵌套其他的task。
最关键的是Ansible定义了一些任务执行过程中的判断入口，由用户来实现，
每一步骤均会判断错误，一旦错误就会自动退出，除非用户明确忽略
```
```yaml
- name: "construct application install dir"
      include: "construct_application_dir.yml"
```

## Role - 角色
```md
是所需的 tasks, handler, variables 组成，能够根据固定的目录层次自动加载涉及的variables、定义的task。
Ansible引入的Role的概念，按照统一的规则下可以进行role的组装，同时能够共享一些Task。
```
```md
├── defaults
│   └── main.yml
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── README.md
├── tasks
│   ├── main.yml
├── templates
│   ├── app_ctrl.py.j2
└── vars
    └── main.yml
```
## PlayBook - 剧本
```md
定义了各个角色在这个剧本中需要做什么以及具体做的顺序。
Ansible 的强大之处在于playbooks，使用 yaml语法，尽量使得对这个流程的描述不再通过脚本的串联去实现，而是通过关系配置化的方式进行。
```
```yaml
  - name: deploy data config center
    hosts: data_config_center
    tasks:
    vars:
        xxx:xxx
        xxx:xxx
    roles:
     - role: autoumars.springboot-role
```



