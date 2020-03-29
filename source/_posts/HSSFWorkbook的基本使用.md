---
title: HSSFWorkbook的基本使用
date: 2019-03-26 18:51:48
tags:
---
### HSSF概况
HSSF接口能够处理的是MS Excel对象，通过HSSF，可以用纯Java代码来读取、写入、修改Excel文件

### Excel表结构
```
HSSFWorkbook excell 文档对象介绍
HSSFSheet excell的表单
HSSFRow excell的行
HSSFCell excell的格子单元
HSSFFont excell字体
HSSFName 名称
HSSFDataFormat 日期格式
在poi1.7中才有以下2项：
HSSFHeader sheet头
HSSFFooter sheet尾
HSSFCellStyle cell样式
辅助操作包括
HSSFDateUtil 日期
HSSFPrintSetup 打印
HSSFErrorConstants 错误信息表
```
