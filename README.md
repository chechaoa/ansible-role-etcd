## ansible playbook 部署 etcd

etcd版本 3.1.8，二进制文件已经保存在roles/etcd/files目录下

默认变量保存在roles/etcd/defaults/main.yml，部署之前需要修改如网卡名等参数

以三个节点为例：

将3个主机ip地址写入inventory：
```
[etcd]
192.168.199.16
192.168.199.17
192.168.199.18
```

执行playbook：
```
ansible-playbook -i inventory etcd.yml
```

测试验证:

ssh到其中一个节点，执行：
```
etcdctl cluster-health
```

playbook参考自 https://github.com/retr0h/ansible-etcd
