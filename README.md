# kube-ansible

```
.  
├── inventory     //配置目录  
└── roles  
    ├── download  //下载文件  
    ├── cri       //容器运行时(选择一个安装)    
    │   ├── docker  
    │   ├── cri-o   //TODO
    │   └── containerd   //TODO
    ├── etcd        //etcd集群  
    │   ├── pki  
    │   └── etcd  
    ├── k8s         //kubernetes集群 
    │   ├── pki   
    │   ├── sys-setup  
    │   ├── master  
    │   └── node      
    └── addons     //扩展插件(按需选择)    
        ├── network  
        │   ├── flannel  
        │   └── calico  //TODO
        ├── croedns 
        ├── metrics_server //TODO
        └── ingress_controller //TODO 
```
