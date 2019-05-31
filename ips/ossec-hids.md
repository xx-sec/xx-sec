# [ossec-hids](https://github.com/ossec/ossec-hids)


> 这个是主机层面的IDS
- 虽然也很强大，但是对于外面的网络，2,3，4基本上就丧失了保护能力，也只是告警。


## [使用参考](https://github.com/the-champions-of-capua/OHSP/tree/master/ossec-hids)
- 这是很久前我用的时候部署使用。
- 服务端可以直接用docker。修改数据库mysql即可。


## 客户端安装
```bash
#!/bin/bash


yum -y install wget curl git unzip

OSSEC_DIR=/home/ossec-hids
OSSEC_VERSION=3.2.0
mkdir $OSSEC_DIR  && cd $OSSEC_DIR && \
 wget "https://github.com/ossec/ossec-hids/archive/"$OSSEC_VERSION".zip" && \
 unzip $OSSEC_VERSION".zip" && cd "ossec-hids-"$OSSEC_VERSION

## 用于顺序安装，不基于对话模式
cat > etc/preloaded-vars.conf << EOF
USER_LANGUAGE="cn"
USER_NO_STOP="y"
USER_INSTALL_TYPE="agent"
USER_DIR="/opt/ossec"
USER_DELETE_DIR="y"
USER_ENABLE_ACTIVE_RESPONSE="y"
USER_ENABLE_SYSCHECK="y"
USER_ENABLE_ROOTCHECK="y"
USER_UPDATE="y"
USER_UPDATE_RULES="n"
USER_BINARYINSTALL="x"
USER_AGENT_SERVER_IP="192.168.2.41"
USER_AGENT_CONFIG_PROFILE="generic"
USER_ENABLE_EMAIL="n"
USER_ENABLE_SYSLOG="y"
USER_PF_TABLE="ossec_fwtable"
USER_WENABLE_PF="y"
USER_HITE_LIST="192.168.2.0/24 192.168.1.0/24 192.168.3.0/24"
EOF

##开始安装
./install.sh

##下载key文件，下面主要导入key
#cat >> etc/client.key << EOF
#002 99_test 192.168.2.99 fb2b60a2d9dbae6dfad99d65be91fed114322ae7f3761b715c55a7a4aff37e0d
#EOF

##下载客户端统一配置文件// 也许不用

##启动客户端程序
/opt/ossec/bin/ossec-control start
```

