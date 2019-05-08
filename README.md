# kube-ansible

.  
├── LICENSE  
├── README.md  
├── inventory  //配置目录  
├── playbooks  //剧本  
└── roles  
    ├── download  //下载文件  
    ├── cri       //容器运行时(选择一个安装)    
    │   ├── docker  
    │   ├── cri-o  
    │   ├── containerd  
    │   └── frakti   
    ├── pki         //证书  
    │   ├── etcd  
    │   └── kubernetes  
    ├── etcd        //etcd集群   
    ├── kubernetes  //kubernetes集群  
    │   ├── sys-setup  
    │   ├── master  
    │   └── node  
    ├── network   //网络插件(选择一个安装)    
    └── addons     //扩展插件(按需选择)    
