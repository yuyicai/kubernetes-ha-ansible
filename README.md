# kube-ansible

```
.  
├── inventory  //配置目录  
└── roles  
    ├── download  //下载文件  
    ├── cri       //容器运行时(选择一个安装)    
    │   ├── docker  
    │   ├── cri-o  
    │   ├── containerd  
    │   └── frakti   
    ├── etcd        //etcd集群  
    │   ├── etcd  
    │   └── pki  
    ├── kubernetes  //kubernetes集群 
    │   ├── pki   
    │   ├── sys-setup  
    │   ├── master  
    │   └── node  
    ├── network   //网络插件(选择一个安装)    
    └── addons     //扩展插件(按需选择)    
```