---
{"aliases":null,"created":"Tuesday, March 31st 2026, 2:50:03 pm","modified":"Friday, April 3rd 2026, 11:21:44 pm","dg-publish":true,"tags":["Blog"],"related":"","author":"Gavin","permalink":"/000_Inbox/halo 建站工具（可用于搭建博客）/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":null,"created":"Tuesday, March 31st 2026, 2:50:03 pm","modified":"Friday, April 3rd 2026, 11:21:44 pm","tags":["Blog"],"related":"","author":"Gavin"}}
---


官网：[https://www.halo.run/](https://www.halo.run/)

备份与恢复：[https://docs.halo.run/user-guide/backup](https://docs.halo.run/user-guide/backup)

## 1. 安装 jdk17

```bash
wget http://49.232.8.65/jdk/jdk17/jdk-17_linux-x64_bin.tar.gz


mkdir /usr/local/java17/ && 
tar -zxvf /usr/local/install_package/jdk-17_linux-x64_bin.tar.gz -C /usr/local/java17/ &&
cd /usr/local/java17/


vim /etc/profile

# java17 环境变量
export JAVA_HOME=/usr/local/java17/jdk-17.0.1
export CLASSPATH=.:$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar
export PATH=$JAVA_HOME/bin:$PATH

export PATH



source /etc/profile


java -version
```

mkdir ~/halo && cd ~/halo  
mkdir ~/.halo2 && cd ~/.halo2  
vim application.yaml

```bash
server:
  # 运行端口
  port: 8090
spring:
  # 数据库配置，支持 MySQL、MariaDB、PostgreSQL、H2 Database，具体配置方式可以参考下面的数据库配置
  r2dbc:
    url: r2dbc:pool:mysql://127.0.0.1:3306/halo
    username: root
    password: aliyunapssword
  sql:
    init:
      mode: always
      # 需要配合 r2dbc 的配置进行改动
      platform: mysql
halo:
  caches:
    page:
      # 是否禁用页面缓存
      disabled: true
  # 工作目录位置
  work-dir: ${user.home}/.halo2
  # 外部访问地址
  external-url: http://localhost:8090
  # 附件映射配置，通常用于迁移场景
  attachment:
    resource-mappings:
      - pathPattern: /upload/**
        locations:
          - migrate-from-1.x
```

cd ~/halo && java -Dfile.encoding=UTF-8 -jar halo.jar --spring.config.additional-location=optional:file:$HOME/.halo2/

### 1.1. 设置为服务

vim /etc/systemd/system/halo.service

```bash
[Unit]
Description=Halo Service
Documentation=https://docs.halo.run
After=network-online.target
Wants=network-online.target

[Service]
Type=simple
ExecStart=/usr/local/java17/jdk-17.0.1/bin/java -Dfile.encoding=UTF-8 -server -Xms256m -Xmx256m -jar /root/halo/halo.jar --spring.config.additional-location=optional:file:/root/.halo2/
ExecStop=/bin/kill -s QUIT $MAINPID
Restart=always
StandOutput=syslog

StandError=inherit

[Install]
WantedBy=multi-user.target
```

1) 重新加载 systemd

    ```bash
    systemctl daemon-reload
    ```

2) 运行服务

    ```bash
    systemctl start halo
    ```

3) 在系统启动时启动服务

    ```bash
    systemctl enable halo
    ```

最后，你可以通过下面的命令查看服务日志：

```bash
journalctl -n 20 -u halo
```

1) 停止 Halo 服务

```bash
service halo stop
```

​![](/img/user/900_System/990_Attachments/halo%20%E5%BB%BA%E7%AB%99%E5%B7%A5%E5%85%B7%EF%BC%88%E5%8F%AF%E7%94%A8%E4%BA%8E%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2%EF%BC%89/file-20260404045812725.png)
