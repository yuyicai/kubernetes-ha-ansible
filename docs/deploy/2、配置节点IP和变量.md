# 配置节点IP

`inventory/k8s-example`文件夹是示例配置，部署集群时复制这个文件夹，对里面的内容进行修改。  

## 配置文件夹目录

```
inventory/
└── k8s-example（部署时复制一份这个文件夹进行配置更改）
    ├── group_vars
    │   └── all································全局变量
    │       ├── addnos.yml·····················插件相关变量
    │       ├── all.yml
    │       ├── cri.yml························运行时相关变量
    │       ├── download.yml···················二进制文件下载相关变量
    │       ├── etcd.yml·······················etcd集群相关变量
    │       ├── image.yml······················镜像相关变量
    │       ├── k8s.yml························kubernetes集群相关变量
    │       └── reset.yml······················重置集群相关变量
    └── hosts.ini······························节点IP信息
```

- 复制一份配置文件
  根据自己的集群IP地址信息配置`inventory/k8s-cluster/hosts.ini`文件

  ```
  cp -r inventory/k8s-example inventory/k8s-cluster
  ```

## 配置节点IP信息

- 更改文件夹`k8s-cluster`下的`hosts.ini`配置集群节点IP信息

  ```
  [all]
  # node_name变量作为节点的名称，配置在kubelet和kube-proxy中，node_name不能有重复。
  # etcd_name变量是etcd配置的节点名称，也不能重复。
  172.16.16.112 node_name=master1 etcd_name=etcd1
  172.16.16.113 node_name=master2 etcd_name=etcd2
  172.16.16.114 node_name=master3 etcd_name=etcd3
  172.16.16.115 node_name=worker1
  172.16.16.116 node_name=worker2
  172.16.16.117 node_name=worker3
  172.16.16.118 node_name=worker4
  
  [kube-master]
  172.16.16.112
  172.16.16.113
  172.16.16.114
  
  [kube-node]
  # node节点可以[kube-master]有重叠
  172.16.16.115
  172.16.16.116
  172.16.16.117
  172.16.16.118
  
  [etcd]
  # 要求在[all]组中添加了etcd_name变量
  # etcd节点数要求是单数
  172.16.16.112
  172.16.16.113
  172.16.16.114
  
  [kube-cluster:children]
  kube-master
  kube-node
  ```

## 更改变了信息

- 更改配置文件下`group_vars/all`文件夹下的文件，这里的变量都是全局变量
