# Douban-Crawler
爬豆瓣小组的帖子信息。

## CRAWLER库表结构
三个数据表：小组表，用户表，帖子表。

### GROUP表
注备：豆瓣小组、贴吧

##### 小组基本信息
|字段名|类型|含义|举例|  
|-|  
|GROUP_SOURCE|VARCHAR(10)|数据来源|"douban"或"tieba"|  
|GROUP_QUERY|VARCHAR(20)|查询query(类似GROUP_TAG)|"北京,IT"|  
|GROUP_NAME|VARCHAR(30)|组名、吧名|"北京读书交友会"|  
|GROUP_ID|VARCHAR(10)|全站唯一性ID|"576850"|  
|GROUP_MEMBER_NUM|INT|小组人数|300|  
|GROUP_URL|TEXT|地址|"https://www.douban.com/group/10274/"|  
|GROUP_CREATE_DATE|VARCHAR(10)|小组创建时间|2010-10-10|  
|GROUP_TAG|VARCHAR(20)|小组标签|"北京,读书,交友"|  

##### 活跃度基本信息(每天字段更新)  
|字段名|类型|含义|举例|  
|-|  
|POST_FIRST_REPLY_DATE|VARCHAR(16)|小组首页第一条最后回复时间|"2015-11-19 21:04"|  
|POST_FIRST_CREATE_DATE|VARCHAR(16)|小组首页第一条创建时间|"2015-11-19 21:04"|  
|POST_MIDDLE_REPLY_DATE|VARCHAR(16)|小组首页中间一条最后回复时间|"2015-11-19 21:04"|  
|POST_MIDDLE_CREATE_DATE|VARCHAR(16)|小组首页中间一条创建时间|"2015-11-19 21:04"|  
|POST_LAST_REPLY_DATE|VARCHAR(16)|小组首页第一条最后回复时间|"2015-11-19 21:04"|  
|POST_LAST_CREATE_DATE|VARCHAR(16)|小组首页最后一条创建时间|"2015-11-19 21:04"|  

##### 表更新时间(定期更新)  
|字段名|类型|含义|举例|  
|-|  
|TABLE_UPDATE_DATE|VARCHAR(16)|最后一次表更新时间|"2015-11-19 21:04:48"|  

##### 管理员基本信息  
|字段名|类型|含义|举例|  
|-|  
|ADMIN_NAME|VARCHAR(50)|管理员姓名|"章小希"|  
|ADMIN_ID|VARCHAR(10)|全站唯一性ID(豆瓣唯一ID、贴吧唯一ID)|"148647315"|  
|ADMIN_URL|TEXT|管理员账号页面|"https://www.douban.com/people/148647315/"|  

### POST表  

##### 来源和所在小组基本信息  
|字段名|类型|含义|举例|  
|-|  
|GROUP_SOURCE|VARCHAR(10)|小组来源|"douban"或"tieba"|  
|GROUP_ID|VARCHAR(20)|所在来源的全(站)局唯一性ID|"hangzhougonglue"|  
|GROUP_NAME|VARCHAR(30)|小组名称|"杭州旅游"|  

##### 帖子基本信息  
|字段名|类型|含义|举例|  
|-|  
|POST_TITLE|TEXT|帖子标题|"这是标题"|  
|POST_CREATE_DATE|VARCHAR(19)|帖子创建时间|"2014-08-10 16:58:21"|  
|POST_LAST_REPLY_DATE|VARCHAR(16)|帖子最后回复时间|"2015-08-13 15:22"|  
|POST_REPLY_NUM|INT|帖子回复个数|10|  
##### 帖子创建者基本信息  
|字段名|类型|含义|举例|  
|-|  
|POST_CREATE_USER_NAME|VARCHAR(50)|帖子创建者名称|"章小希"|  
|POST_CREATE_USER_ID|VARCHAR(10)|帖子创建者全站唯一性ID|"148647315"|  
|POST_CREATE_USER_URL|TEXT|帖子创建者个人页面地址|"https://www.douban.com/people/148647315/"|  
##### 内容和评论  
|字段名|类型|含义|举例|  
|-|  
|POST_CONTENT|TEXT|帖子内容|"这是帖子内容"|  
|POST_CREATE_USER_COMMENT|TEXT|帖子创建者的所有评论|"这是评论1+2+3拼接起来的结果"|  
##### 感兴趣信息(需要提取/抽取)  
|字段名|类型|含义|举例|  
|-|  
|POST_CONTENT_QQ|VARCHAR(12)|帖子内容里的QQ号|"12345"|  
|POST_CONTENT_WECHAT|VARCHAR(16)|帖子内容里的微信号|"12345"|  
|POST_CONTENT_TEL|VARCHAR(15)|帖子内容里的电话号|"13312345678"|  
|POST_CONTENT_ADDRESS|VARCHAR(30)|帖子内容里的地址|"北京市海淀区"|  

### USER表  
注备:主要用来记录小组(或贴吧)管理员和发帖人个人信息  
##### 基本信息  
|字段名|类型|含义|举例|  
|-|  
|USER_SOURCE|VARCHAR(10)|用户来源|"douban"或"tieba"|  
|USER_NAME|TEXT|用户名、昵称|"小豆芽"|  
|USER_ID|VARCHAR(10)|全站唯一性ID|"yncyd"|  
|USER_URL|TEXT|个人页面|"https://www.douban.com/people/yncyd/"|  
|USER_SEX|INT|性别|1(男)或0(女)|  
  
##### 发帖情况(定期更新)  
|字段名|类型|含义|举例|  
|-|  
|POST_NUM|INT|发帖总数|32|  
|POST_LAST_CREATE_DATE|VARCHAR(16)|用户发帖目录页第1页最后一次发帖日期|"2015-01-01 11:11"|  
|POST_MIDDLE_CREATE_DATE|VARCHAR(16)|用户发帖目录页第1页中间一次发帖日期|"2015-01-01 11:11"|  
|POST_FIRST_CREATE_DATE|VARCHAR(16)|用户发帖目录页第1页第一次发帖日期|"2015-01-01 11:11"|  
##### 活跃程度(定期更新)  
|字段名|类型|含义|举例|  
|-|  
|USER_LAST_LOGIN|VARCHAR(16)|上次登陆时间|"2015-01-01 11:11"|  
|USER_CREATE_DATE|VARCHAR(12)|用户创建日期|"2015-01-01"|  
##### 表更新时间(定期更新)  
|字段名|类型|含义|举例|  
|-|  
|TABLE_UPDATE_DATE|VARCHAR(16)|最后一次表更新时间|"2015-11-19 21:04:48"|  

##### 感兴趣信息(需要提取/抽取)  
|字段名|类型|含义|举例|  
|-|  
|USER_QQ|VARCHAR(12)|QQ号码|"111111111"|  
|USER_WECHAT|VARCHAR(16)|微信号|"ZhangSan0912"|  
|USER_TEL|VARCHAR(15)|手机号|"13311111111"|  
|USER_MAIL|TEXT|邮箱|"zhangsan0912@gmail.com"|  
|USER_ADDRESS|TEXT|所在位置|"北京市海淀区XXX路XXX号"或"XXX区"或"南京"|
