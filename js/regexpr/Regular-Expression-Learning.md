因为本系列文章意在介绍有关前端的技术，所以这里介绍的正则表达式也主要针对 JavaScript 中的正则表达式。


# 语法

## 匹配单个字符

### 匹配纯文本

`/hello/`： 匹配 "hello"

### 匹配任意字符串

`.` 可以匹配任何单个的字符、数字、空格，甚至 "." 本身

`/c.t/`： 匹配 "cat"、 "cot" 等等

#### 匹配多个结果

`//g`

#### 忽略大小写

`//i`

### 匹配特殊字符

使用 `\` 进行转义

`/c.t\.md/`： 匹配 "cat.md"、 "cot.md" 等等

有的字符在特定条件下才是特殊字符，需要进行转义，比如 `-` 只有在 `[]` 内才是特殊字符

## 匹配一组字符串

### 匹配多个字符中的某一个

`[]`

`[abc]`： 匹配 "a"、 "b" 和 "c"

### 字符集合区间

`-` 用于表示字符区间

`[0-9]`： 匹配 0-9 中的任意一个数字

需要注意的是， `[]` 表示一个字符集合，`-` 只有在 `[]` 中才能有效

常用的还有 `[a-z]`、 `[A-Z]` 等

### 取非匹配

`^` 对字符集合进行取非

`[^0-9]`： 匹配非 0-9 的任意字符


## 使用元字符

### 对特殊字符进行转义

`\`

### 匹配空白字符

| 元字符 | 说明     |
|:-----:|:-------:|
|\f     |换页符    |
|\n     |换行符    |
|\r     |回车符    |
|\t     |制表符    |
|\v     |垂直制表符|
|\r\n   |回车+换行组合，Windows 将这个组合用作文本结束标志|

### 匹配特定的字符类别

一些常用的字符集合可以用特殊元字符来表示

#### 匹配数字

- `\d`： 任何一个数字集合，等价于 `[0-9]`
- `\D`： 任何一个非数字集合，等价于 `[^0-9]`

#### 匹配字母数字下划线

- `\w`： 任何一个字母、数字或者下划线，等价于 `[0-9A-Za-z_]`
- `\W`： 任何一个非字母、数字以及下划线，等价于 `[^0-9A-Za-z_]`

#### 匹配空白字符

- `\s`： 任何一个空白字符，等价于 `[\f\n\r\t\v]`
- `\S`： 任何一个非空白字符，等价于 `[^\f\n\r\t\v]`

## 重复匹配

### 匹配一个或多个字符

`+`

`6+`： 匹配 6、 66、 666 等

### 匹配零个或多个字符

`*`

`36*`： 匹配 3、 36、 366 等等

### 匹配零个或一个字符

`?`

`36?`： 匹配 3 和 36

### 指定匹配次数 （待验证）

- `{m}`： 匹配 m 次
- `{m, }`： 至少匹配 m 次
- `{m, n}`： 匹配 m - n 次


## 位置匹配

### 单词边界

`\b`

`\bcat\b`： 匹配 "cat"， 却无法匹配 "cats"

`\B`

`\Bcat\B`： 匹配 "bcats"， 却无法匹配 "cat" 或 "cats"

### 字符串边界

- `^` 表示字符串开头
- `$` 表示字符串结尾


## 子表达式

用 `()` 表示子表达式


## 回溯引用，前后一致匹配

`\1` 表示对第一个子表达式进行引用，以此类推，`\2` 对第二个子表达式进行引用

`(6{3}\w)\1`： 可以匹配 `666a666a` 等



# JavaScript 中的正则表达式

JavaScript 中有两种办法创建正则表达式：

``` JavaScript
const re = /ab+c/; // 方式 1
const re = new RegExp("ab+c"); // 方式 2
```


# 练习

- <http://regex.alf.nu/> 答案： <http://felixc.at/regex.alf.nu>

拓展资料：

- <http://notes.maxwi.com/2015/10/04/Regular-Expression-Study-Note/>
