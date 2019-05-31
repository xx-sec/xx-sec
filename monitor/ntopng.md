# [ntopng](https://github.com/ntop/ntopng)


```bash
 rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
 wget http://packages.ntop.org/centos/ntop.repo -O /etc/yum.repos.d/ntop.repo && \
 yum install pfring-dkms n2disk nprobe ntopng cento -y && \
 systemctl start redis && systemctl start ntopng 
 
 ## 配置文件增加
 -i eth0 
```

## 界面很好看, 普通的监控功能都有
- 主要的实用优点是监控的环境比较好。安装需要libcap监听网卡流量
- 就是设备和指纹的保存鉴别，服务的判断。这部分下了功夫。其他的不如suricata.
- 另外就是这个工具集成了 SNMP 专业版才能用。
 

## 总结
- 看看就行, 学习其中很多的字段设计。
- 不完善的地方太多。比如流量异常的判断。