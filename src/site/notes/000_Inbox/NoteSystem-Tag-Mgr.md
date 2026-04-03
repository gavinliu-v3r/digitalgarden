---
{"aliases":null,"created":"Friday, April 3rd 2026, 6:46:01 pm","modified":"Friday, April 3rd 2026, 10:10:51 pm","dg-publish":true,"tags":["2-System/Config/Tag","Me/System","Note","gardenEntry"],"related":"","author":"Gavin","dg-home":true,"permalink":"/000_Inbox/NoteSystem-Tag-Mgr/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":null,"created":"Friday, April 3rd 2026, 6:46:01 pm","modified":"Friday, April 3rd 2026, 10:10:51 pm","tags":["2-System/Config/Tag","Me/System","Note","gardenEntry"],"related":"","author":"Gavin"}}
---


## 1. 标签树结构

**分类：** PARA 标签（类型）、管理标签（管理）、自定义标签（命题）

PARA 标签：其中 Areas、Resource 为叶子标签；Projects、Archives 为二级标签，用于有明确时限任务管理。例如：Projects/恒大系统开发，结束后转为 Archives/恒大系统开发；

管理标签：包含文件管理、系统管理、任务管理等，固定三级结构，例如：Task/Progress/草稿；

自定义标签：根据需求不断新增的标签。

**使用方法**：PARA 标签 + 自定义标签，实现内容定位；管理标签辅助进度状态管理。

**组合示例**：

- 公共营养师项目最终产出：Project + Nutrition/公共营养师 + Task/progress/最终输出
- 公共营养师项目任务管理：Project + Nutrition/公共营养师 + Task/Status/进行中 + Task/Priority/重要紧急
- 公共营养师领域任务管理：Areas + Nutrition/公共营养师 + Task/progress/学习中

### 1.1. 内容类型

#### 1.1.1. PARA 细分标签

P.A.R.A.是由著名效率管理大师 Tiago Forte 发明的，也是他《打造第二大脑》一书的核心内容。

P.A.R.A.的本质是一套生产系统，它无意为笔记找一个完美的位置，事实上这样的位置也并不存在；它旨在为我们的认知减负，把我们的注意力聚焦到当下真正重要的事情上去。

#1-Projects : 也称项目，是有明确时限的任务；

#1-Areas : 也称领域，是长期重点研究的领域，是我们 80% 精力应该投入的地方；

#1-Resources : 也称资源，是感兴趣的领域，是我们额外 20% 的精力会去关注的地方，可能会在未来转成重点事项，转入 80% 的领域；

#1-Archives : 也称归档，是我们当下不再关注的领域。不需要去删除它们，把它们移出我们的注意力范围就好，在一定程度上为认知减负的同时，还能保证未来我们需要它们的时候，还能随时找回来。

### 1.2. 管理类型

#### 1.2.1. 任务管理细分标签

#2-Task # 任务管理

##### 1.2.1.1. 进度管理标签

#2-Task/3-progress/草稿 : 初始阶段

#2-Task/3-progress/整理中 : 正在整理

#2-Task/3-progress/学习中 : 正在学习

#2-Task/3-progress/实践应用 : 正在应用

#2-Task/3-progress/掌握 : 已掌握

#2-Task/3-progress/回顾 : 需要回顾

#2-Task/3-progress/最终输出 : 成品文章

##### 1.2.1.2. 优先级标签

#2-Task/2-Priority/1-重要紧急 : 马上处理

#2-Task/2-Priority/2-重要不紧急 : 计划处理

#2-Task/2-Priority/3-紧急不重要 : 尽量委派

#2-Task/2-Priority/4-不紧急不重要 : 考虑删除

##### 1.2.1.3. 状态标签

#2-Task/1-Status/1-待完成 : 未开始

#2-Task/1-Status/2-进行中 ：正在进行

#2-Task/1-Status/3-已完成 ：已经完成

#2-Task/1-Status/4-暂停 ：暂停

#2-Task/1-Status/5-放弃 ：放弃

#### 1.2.2. 系统管理细分标签

 #2-System ：系统管理

 #2-System/config ：配置项

#### 1.2.3. 文件管理细分标签

 #2-File ：文件管理

#2-File/Trashpending ：待删垃圾、临时废文件

## 2. 补充

re.ism 的核心：“**终身学习、终身成长**”。

**rethink, redefine, recreate, refactor, reborn, …, reminds.**
