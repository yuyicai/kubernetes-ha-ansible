# kube-ansible





# 快速部署部署

- 复制一份配置文件
  根据自己的集群IP地址信息配置`inventory/k8s-cluster/hosts.ini`文件

  ```
  cp -r inventory/k8s-example inventory/k8s-cluster
  ```

- 测试节点的连通性

  ```
  ansible -i inventory/k8s-cluster/hosts.ini -m ping all
  ```

- 执行剧本，部署集群

  ```
  ansible-playbook -i inventory/k8s-cluster/hosts.ini deploy.yml
  ```

- 查看集群信息

  ```
  NAME                 STATUS    MESSAGE             ERROR
  controller-manager   Healthy   ok                  
  scheduler            Healthy   ok                  
  etcd-0               Healthy   {"health":"true"}   
  etcd-2               Healthy   {"health":"true"}   
  etcd-1               Healthy   {"health":"true"}   
  ```

  ```
  root@ubuntu:~ # kubectl get no -owide
  NAME      STATUS   ROLES    AGE     VERSION   INTERNAL-IP     EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
  master1   Ready    <none>   2m11s   v1.15.0   172.16.16.112   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  master2   Ready    <none>   2m12s   v1.15.0   172.16.16.113   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  master3   Ready    <none>   2m12s   v1.15.0   172.16.16.114   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  worker1   Ready    <none>   113s    v1.15.0   172.16.16.115   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  worker2   Ready    <none>   113s    v1.15.0   172.16.16.116   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  worker3   Ready    <none>   112s    v1.15.0   172.16.16.117   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  worker4   Ready    <none>   112s    v1.15.0   172.16.16.118   <none>        Ubuntu 18.04.2 LTS   4.15.0-51-generic   docker://18.6.3
  ```


# roles目录结构
```
.  
├── inventory     //配置目录  
└── roles  
    ├── download  //下载文件  
    ├── cri       //容器运行时(选择一个安装)    
    │   ├── docker  
    │   ├── cri-o   //TODO
    │   └── containerd   //TODO
    ├── etcd        //etcd 集群  
    │   ├── pki  
    │   └── etcd  
    ├── k8s         //kubernetes 集群 
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
