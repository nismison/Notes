## Key

#### Value为String时：

`'name1|1-3': 'a'` 重复生成1到3个a

`'name2|2': 'b'` 生成bb

#### Value为Number时：

`'name1|+1': 4` 生成4，如果循环每次加1

`'name2|1-7': 2` 生成一个数字，1到7之间（此时value没有实际作用，只标记数据类型）

`'name3|1-4.5-8': 1` 生成一个小数，整数部分1到4，小数部分5到8位（此时value没有实际作用，只标记数据类型）

#### Value为Boolean时：

`"name|1": true` 生成一个布尔值，几率参半

`'name1|1-3': true` 1/4是true，3/4是false，横线前后之和为分母

#### Value为Boolean时：

`'name1|1': ['Nick', 'Amazon']` 从数组里随机取出1个值

`'name2|2': ['Nick', 'Amazon']` 数组重复2次

`'name3|1-3': ['Nick', 'Amazon']` 数组重复1到3次

#### Value为RegExp时，根据正则表达式反向生成对应的字符串，用于生成自定义格式的字符串：

```
'name1': /[a-z][A-Z]/
'name2': /\d{1,3}/
```





------

## Value

#### Name

`@name` 生成英文人名

`@first` 生成英文姓氏

`@last` 生成英文名（除姓氏外）

`@cname` 生成中文人名

`@cfirst` 生成中文姓氏

`@clast` 生成中文名（除姓氏外）

#### Time

`@date('yyyy-MM-dd')` 生成随机日期

`@time('hh:mm:ss')` 生成随机时间

`@now(yy-MM-dd hh:mm-ss)` 生成当前日期时间

`@datetime(yy-MM-dd hh:mm-ss)` 随机生成日期时间

#### Address

`@region` 生成中国区域，如华南、华中

`@province` 生成中国省份

`@city(true)` 生成中国市名，括号内控制是否显示省

`@county(true)` 生成中国县名，括号内控制是否显示省市

`@zip` 生成中国邮编

#### Web

`@url` 生成网址

`@ip` 生成IP地址

`@email` 生成邮箱地址

`@protocol` 生成协议头

`@domain` 生成域名

#### Text

`@ctitle(10, 20) / @title(10, 20)` 生成10到20字数/单词的一句话（看起来毫无意义）

`@cword('abc', 5, 7) / @word('abc', 5, 7)` 从第一个参数中随机拿出5到7个字进行拼接（如果第一个参数为空则随机出现汉字/单词，第二个参数不填则为1，第三个参数不填则长度为第二个参数）

`@csentence(3, 5) / @sentence(3, 5)` 生成一个长度为3到5个汉字/单词的句子（带句号）

`@cparagraph(1, 3) / @paragraph(1, 3)` 生成1到3句话

#### Color

`@hsl` 生成hsl(296, 82, 71)

`@rgba` 生成rgba(243, 82, 71, 0.32)

`@rgb` 生成 rgb(243, 82, 71)

`@hex` 生成 #792feb

`@color` 生成 #792feb

#### Image

`@image('200x200', '#50B347', '#FFF', 'FastMock')` 生成图片（第一个参数为尺寸，单位px，第二个参数为背景色，第三个参数为文字颜色，第四个参数为文字内容）

##### Basic

`@range(3, 7)` 生成数组[3, 4, 5, 6]

`@string(7, 20)` 生成长度为7到20的随机字符串

`@character('abcde')` 从abcde中随机取一个字符

`@float(60, 100)` 生成一个60到100之间的浮点数

`@integer(10000, 15000)` 生成10000到15000之间的整数

`@natural(60, 100)` 生成一个自然数

`@boolean` 生成一个布尔值

#### Helper

`@shuffle(['fast', 'mock', 'eee', 'aaa'])` 打乱数组

`@pick(['fast', 'mock', 'eee', 'aaa'])` 从数组中随机取一个值

`@lower('FASTMOCK')` 转小写

`@upper('fastmock')` 转大写

`@capitalize('fastmock')` 首字母大写