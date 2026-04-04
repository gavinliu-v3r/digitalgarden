---
{"aliases":["Excel","excel-formula","spreadsheet"],"created":"Saturday, April 4th 2026, 2:04:45 pm","modified":"Saturday, April 4th 2026, 2:07:19 pm","dg-publish":true,"tags":["domain/software"],"related":"","author":"Gavin","permalink":"/03-Software & Tools/Excel - 常用公式/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":["Excel","excel-formula","spreadsheet"],"created":"Saturday, April 4th 2026, 2:04:45 pm","modified":"Saturday, April 4th 2026, 2:07:19 pm","tags":["domain/software"],"related":"","author":"Gavin"}}
---


## 📊 财务公式

### 人民币大写转换

```excel
=IF(G13=0,"零元",IF(G13<0,TEXT(INT(ABS(G13)),"负[DBNum2]g/通用格式")&"元"&IF((INT(G13*10)-INT(G13)*10)=0,"",TEXT(INT(G13*10)-INT(G13)*10,"[DBNum2]")&"角")&IF((INT(G13*100)-INT(G13*10)*10)=0,"整",TEXT(INT(G13*10)-INT(G13*10),"[DBNum2]")&TEXT(INT(G13*100)-INT(G13*10)*10,"[DBNum2]")&"分"),TEXT(INT(G13),"[dbnum2]")&"元"&IF(INT(G13*10)-INT(G13)*10=0,"",TEXT(INT(G13*10)-INT(G13)*10,"[dbnum2]")&"角")&IF((INT(G13*100)-INT(G13*10)*10)=0,"整",TEXT(INT(G13*10)-INT(G13*10),"[DBNum2]")&TEXT(INT(G13*100)-INT(G13*10)*10,"[DBNum2]")&"分")))
```

### 带人民币前缀

```excel
=CONCATENATE("人民币",IF(G13=0,"零元",IF(G13<0,TEXT(INT(ABS(G13)),"负[DBNum2]g/通用格式")&"元"&IF((INT(G13*10)-INT(G13)*10)=0,"",TEXT(INT(G13*10)-INT(G13)*10,"[DBNum2]")&"角")&IF((INT(G13*100)-INT(G13*10)*10)=0,"整",TEXT(INT(G13*10)-INT(G13*10),"[DBNum2]")&TEXT(INT(G13*100)-INT(G13*10)*10,"[DBNum2]")&"分"),TEXT(INT(G13),"[dbnum2]")&"元"&IF(INT(G13*10)-INT(G13)*10=0,"",TEXT(INT(G13*10)-INT(G13)*10,"[dbnum2]")&"角")&IF((INT(G13*100)-INT(G13*10)*10)=0,"整",TEXT(INT(G13*10)-INT(G13*10),"[DBNum2]")&TEXT(INT(G13*100)-INT(G13*10)*10,"[DBNum2]")&"分"))))
```

## 🔢 常用计算公式

### 基础统计

```excel
=SUM(A1:A10)          # 求和
=AVERAGE(A1:A10)      # 平均值
=MAX(A1:A10)          # 最大值
=MIN(A1:A10)          # 最小值
=COUNT(A1:A10)       # 计数
=COUNTA(A1:A10)      # 非空计数
=COUNTIF(A1:A10,">60")# 条件计数
```

### 条件判断

```excel
=IF(A1>60,"及格","不及格")                      # 单条件
=IF(AND(A1>60,B1>60),"优秀","待改进")           # 多条件与
=IF(OR(A1>60,B1>60),"通过","不通过")            # 多条件或
=IF(A1>60,IF(B1>80,"优秀","良好"),"不及格")     # 嵌套条件
```

### 查找引用

```excel
=VLOOKUP(A1,B1:C10,2,FALSE)  # 垂直查找
=HLOOKUP(A1,B1:J2,3,FALSE)  # 水平查找
=INDEX(B1:B10,MATCH(A1,C1:C10,0))  # 组查找
=SUMIF(A1:A10,"苹果",B1:B10)  # 条件求和
```

## 📈 日期时间函数

### 当前日期时间

```excel
=TODAY()          # 当前日期
=NOW()            # 当前日期时间
=YEAR(TODAY())    # 年份
=MONTH(TODAY())   # 月份
=DAY(TODAY())     # 日
=WEEKDAY(TODAY()) # 星期几
```

### 日期计算

```excel
=DATE(2024,1,1)          # 创建日期
=EDATE(A1,3)             # 月份加减
=DATEDIF(A1,B1,"D")     # 日期间隔天数
=WORKDAY(A1,10)          # 工作日计算
=NETWORKDAYS(A1,B1)      # 工作日天数
```

## 🔍 文本处理

### 基础文本

```excel
=LEFT(A1,3)      # 左取
=MID(A1,2,3)     # 中间取
=RIGHT(A1,3)     # 右取
=LEN(A1)         # 长度
=TRIM(A1)        # 去空格
=UPPER(A1)       # 转大写
=LOWER(A1)       # 转小写
```

### 高级文本

```excel
=FIND("文本",A1)          # 查找位置
=REPLACE(A1,2,3,"新")    # 替换文本
=SUBSTITUTE(A1,"旧","新") # 替换文本
=CONCAT(A1:B1)          # 连接文本
=TEXT(A1,"yyyy-mm-dd")   # 格式化文本
```

## 🎯 实用技巧

### 快捷键

- `Ctrl + ;` - 输入当前日期
- `Ctrl + Shift + ;` - 输入当前时间
- `F4` - 切换单元格引用类型
- `Ctrl + '` - 切换公式/结果视图

### 公式调试

- `F9` - 计算选中部分
- `Ctrl + ~` - 显示/隐藏公式
- `Ctrl + [` - 追踪引用单元格
