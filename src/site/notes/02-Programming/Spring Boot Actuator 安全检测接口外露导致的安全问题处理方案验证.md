---
{"aliases":null,"created":"Thursday, April 2nd 2026, 4:58:44 pm","modified":"Saturday, April 4th 2026, 3:52:11 pm","dg-publish":true,"tags":["Develop/Java","1-Areas"],"related":["[[Spring Boot Actuator]]"],"author":"Gavin","permalink":"/02-Programming/Spring Boot Actuator 安全检测接口外露导致的安全问题处理方案验证/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":null,"created":"Thursday, April 2nd 2026, 4:58:44 pm","modified":"Saturday, April 4th 2026, 3:52:11 pm","tags":["Develop/Java","1-Areas"],"related":["[[Spring Boot Actuator]]"],"author":"Gavin"}}
---


## actuator 服务配置

![](/img/user/000_Obsidian/900_System/Assets/assets/net-img-1693214951776-dab327d3-530d-407d-8152-a59a6e1d0321-20240202175843-obmtm6n.png)

## 行云配置

![](/img/user/000_Obsidian/900_System/Assets/assets/net-img-1693214959986-442e7db2-efa4-464c-b4ef-91466735dc82-20240202175843-yjo0ma2.png)

![](Repositories/Pasted%20image%2020230711173852.png)

## ingress 配置

![](/img/user/000_Obsidian/900_System/Assets/assets/net-img-1693214968898-500c7dc7-cd25-4155-b642-24e415f88d9a-20240202175843-85zc95d.png)

## 服务正常启动

 **（说明就绪探针正常，k8s 完成 9091 端口的访问 且 health 接口返回服务状态正常）**
​![](Repositories/Pasted%20image%2020230711173921.png)![](/img/user/000_Obsidian/900_System/Assets/assets/net-img-1693214977335-01857b86-1de4-4642-9289-67e2ae0aa5e3-20240202175843-2w2cieo.png)

## 容器内访问 9091

![](/img/user/000_Obsidian/900_System/Assets/assets/net-img-1693214985417-d70e093b-058b-48b1-a964-2695fac1cebd-20240202175844-lfgo9hl.png)

![](Repositories/Pasted%20image%2020230711173952.png)

## 外网域名访问：

**提示 404 说明匹配 ingress 失败了**

![](/img/user/000_Obsidian/900_System/Assets/assets/net-img-1693214991794-9b78e6e8-38fd-4bf7-ba28-43fb6268db57-20240202175844-3gf02t8.png)

![](Repositories/Pasted%20image%2020230711174005.png)

‍
