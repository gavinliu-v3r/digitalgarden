---
{"aliases":null,"created":"Tuesday, March 31st 2026, 3:12:53 pm","modified":"Saturday, April 4th 2026, 2:18:10 pm","dg-publish":true,"tags":["domain/software","domain/tool","domain/draw"],"related":"","author":"Gavin","permalink":"/03-Software & Tools/PlantUML - 时序图示例/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":null,"created":"Tuesday, March 31st 2026, 3:12:53 pm","modified":"Saturday, April 4th 2026, 2:18:10 pm","tags":["domain/software","domain/tool","domain/draw"],"related":"","author":"Gavin"}}
---


## 示例

```plantuml
Bob -> Alice : hello
Alice -> Wonderland: hello
Wonderland -> next: hello
next -> Last: hello
Last -> next: hello
next -> Wonderland : hello
Wonderland -> Alice : hello
Alice -> Bob: hello
```

```plantuml
@startuml
actor 用户 as actor_user
participant diss_gateway as system_gateway
participant diss_order as system_order
participant diss_product as system_product

actor_user -> system_gateway : 1、\n商详页：立即购买 \n 购物车：立即购买
system_gateway -> system_gateway : 2、网关校验
system_gateway -> system_order : 3、通过验证、路由服务
system_order -> system_order : 4、用户信息验证
system_order -> system_product : 路由product
system_product -> system_product : 5、查询商品信息
system_product --> system_order : 响应
system_order -> system_order : 6、数据校验 \n a：商品信息 \n b：上下架情况 \n c：商品库存 \n d：销售区域 \n e：VOP接口校验


system_order --> system_gateway : 响应
system_gateway --> actor_user : 响应用户下单结果
@enduml
```

```plantuml
@startuml
actor 用户 as actor_user
participant 用户中心 as customerSystem
participant 易航标签 as yhTagSystem

actor_user -> customerSystem : 1、查看通用标签列表
customerSystem -> customerSystem : 2、分页查询，条件IsGlobal = 1
customerSystem -> yhTagSystem : 3、查询标签覆盖人群数
yhTagSystem --> customerSystem : 返回
customerSystem -> customerSystem : 4、数据整合
customerSystem --> actor_user : 返回
@enduml
```

```plantuml
@startuml
actor 用户 as actor_user
participant 用户中心 as customerSystem
participant 易航标签 as yhTagSystem
participant xxl_Job as taskSystem

actor_user -> customerSystem : 1、创建通用标签
customerSystem -> customerSystem : 2、数据校验
customerSystem -> yhTagSystem : 3、查看kudu表名
yhTagSystem --> customerSystem : 返回
customerSystem -> customerSystem : 4、数据整合入库、同步缓存
customerSystem -> customerSystem : 6、判断是否为规则标签
customerSystem -> taskSystem : 7、是：动态创建xxl-job任务
taskSystem --> customerSystem : 返回
customerSystem -> customerSystem : 8、更新任务id
customerSystem --> actor_user : 返回
@enduml
```

临期提醒

```plantuml
@startuml
participant xxl_Job as taskSystem
participant 用户中心 as customerSystem
participant 消息中心 as messageSystem


taskSystem -> customerSystem : 1、任务调度
customerSystem -> customerSystem: 2、根据临期通知规则检索需要通知的用户
customerSystem -> customerSystem: 3、数据整合
customerSystem -> messageSystem: 4、消息发送请求
messageSystem -> messageSystem: 5、渠道消息处理
messageSystem --> customerSystem: 返回
customerSystem --> taskSystem: 返回
@enduml
```

定时券包

```plantuml
@startuml
participant xxl_Job as taskSystem
participant 用户中心 as customerSystem
participant 卡券中心 as couponSystem


taskSystem -> customerSystem : 1、任务调度
customerSystem -> customerSystem: 2、匹配权益发放规则（月、周)
customerSystem -> customerSystem: 3、获取付费会员产品信息
customerSystem -> customerSystem: 4、检索对应会员信息
customerSystem -> customerSystem: 5、初始化权益发放记录—>DB
customerSystem -> couponSystem: 6、组装发券请求，发券请求
couponSystem --> customerSystem: 返回（状态：失败，成功：发券批次号）
customerSystem -> customerSystem: 7、更新权益发放记录状态
customerSystem --> taskSystem: 返回
@enduml
```

生日券包

```plantuml
@startuml
participant xxl_Job as taskSystem
participant 用户中心 as customerSystem
participant 卡券中心 as couponSystem


taskSystem -> customerSystem : 1、任务调度
customerSystem -> customerSystem: 2、ES检索生日用户
customerSystem -> customerSystem: 3、检查用户会员状态
customerSystem -> customerSystem: 4、获取会员权益信息
customerSystem -> customerSystem: 5、初始化权益发放记录—>DB
customerSystem -> couponSystem: 6、组装发券请求，发券请求
couponSystem --> customerSystem: 返回（状态：失败，成功：发券批次号）
customerSystem -> customerSystem: 7、更新权益发放记录状态
customerSystem --> taskSystem: 返回
@enduml
```

异步查询发券结果

```plantuml
@startuml
participant xxl_Job as taskSystem
participant 用户中心 as customerSystem
participant 卡券中心 as couponSystem


taskSystem -> customerSystem : 1、任务调度
customerSystem -> customerSystem: 2、检索非终态权益发放记录
customerSystem -> customerSystem: 3、获取queryId批次号去重
customerSystem -> couponSystem: 4、券包发放状态查询
couponSystem --> customerSystem: 返回
customerSystem -> couponSystem: 5、发券状态：处理中
customerSystem --> taskSystem: 返回
customerSystem -> couponSystem: 5、发券状态：发券成功、发券失败
customerSystem -> customerSystem: 6、更新权益发放记录状态
customerSystem --> taskSystem: 返回
@enduml
```

发券补偿

```plantuml
@startuml
participant xxl_Job as taskSystem
participant 用户中心 as customerSystem
participant 卡券中心 as couponSystem


taskSystem -> customerSystem : 1、任务调度
customerSystem -> customerSystem: 2、检索失败状态，重试次数<3的权益发放记录
customerSystem -> couponSystem: 3、组装发券请求，发券请求
couponSystem --> customerSystem: 返回（状态：失败，成功：发券批次号）
customerSystem -> customerSystem: 4、请求成功：更新queryId，记录状态，重试次数+1
customerSystem --> taskSystem: 返回
customerSystem -> customerSystem: 4、请求失败：更新记录状态失败，重试次数+1
customerSystem --> taskSystem: 返回

@enduml
```
