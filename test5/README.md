# 实验5：图书管理系统数据库设计与界面设计
|学号|班级|姓名|
|:-------:|:-------------: | :----------:|
|201510414214|软件(本)15-2|奈飞|

## 1.数据库表设计

## 1.1. 图书表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|id|int|主键|否|||自增|
|isbn|varchar2(15)||否||||
|title|varchar2(30)| |否||||
|type|varchar2(30)|外键 |否||||
|memo|varchar2(100)| |是||||
|author|varchar2(20)| |是||||
|publishing|varchar2(20)| |是||||
|date|date| |是|||出版日期|
|price|float| |是||||

## 1.2. 图书类型表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|id|int|主键|否|||自增|
|name|varchar2(30)| |否||||
|introduce|text| |是||||

## 1.3. 读者表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|uid|int|主键|否|||自增|
|username|varchar2(20)| |否||||
|password|varchar2(20)| |否||||
|tel|varchar2(15)| |是||||
|sex|varchar2(1)| |是||||

## 1.4. 管理员表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|uid|int|主键|否|||自增|
|username|varchar2(20)| |否||||
|password|varchar2(20)| |否||||
|level|int| |否|||权限等级|

## 1.4. 借书信息表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|id|int|主键|否|||自增|
|student_id|int| |否||||
|book_id|int| |否||||
|borrow_date|datetime| |否|||借书时间|
|except_return_date|datetime| |否|||预计归还时间|
|status|varchar2(1)| |否|否||是否已还书|
|return_date|datetime| |是|||实际归还时间|
***

## 2. 界面设计
## 2.1. 借书界面设计
![pic1](https://github.com/icemaplen/is_analysis/blob/master/test5/image/20180508160025.png)
- 用例图参见：借书用例
- 类图参见：借书类，读者类
- 顺序图参见：借书顺序图
- API接口如下：

1. 获取全部分类

- 功能：用于获取全部分类
- 请求地址： http://[YOUR_DOMAIN]/v1/api/shop_cate
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|access_token|是|用于验证请求合法性的认证信息。 |
|method|是|固定为 “GET”。|
|key|是|查询关键字|

- 返回实例：
``` json
{
  "code": 200,
  "book": [
    {
      "title": "C# 6.0本质论",
      "type": "IT",
      "isbn": "9787115441317",
      "author": "Mark Michaelis",
      "publishing": "人民邮电出版社",
      "date": "2017-01-01"
    },
    {
      "title": "C# 4.0本质论",
      "type": "IT",
      "isbn": "9787115233837",
      "author": "Mark Michaelis",
      "publishing": "人民邮电出版社",
      "date": "2010-9"
    }
  ]
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|code|操作码|
|book|书籍信息|

2. 查询用户API
- 功能：用于查找目标用户是否存在
- 请求地址： http://[YOUR_DOMAIN]/v1/api/shop_cate
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|access_token|是|用于验证请求合法性的认证信息。 |
|method|是|固定为 “GET”。|
|username|是|想要查询的用户名|

- 返回实例：
```
{
    "code": 200
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|code|返回码<br>200:操作成功，目标存在<br>300,查询失败，目标不存在|


 