# PHP 开发规范



> Note：个人记录，仅作为参考



其他

- [PSR](https://www.php-fig.org/psr/)
- [PHP: The Right Way](https://phptherightway.com/)



## 目录

[编码规范](#编码规范)

- [命名规则](#命名规则)
- [其他](#其他)



## 编码规范

### 命名规则

1.1 名副其实

在为任何一个变量、函数、类命名前，首先要明确地想清楚它是做什么的，人后再为它取一个直达其意的名字。如果在看到一个命名的五秒钟内，你还是想不起来它是做什么的话，那么这个命名就是糟糕的；如果还需要查手册才能明白它的含义时，这个命名的糟糕程度与`#¥#*&（@#¥`无异。

```
// bad
$u = xxx

// good
$userName = xxx
```



1.2 变量名

1) 统一使用驼峰式，首字母小写，例如：`$fileName`

2) 如果是类的保护或私有变量，应在变量标记`$`后以（ _ ）下划线开头，例如：`$_fileName`
3) 全局常量或静态变量，一般使用全大写，（ _ ）下划线分割的命名方式，例如：`$FILE_NAME`



1.3 方法和函数名

1. 类中的方法必须显式声明（如：public）
2. 统一使用驼峰式，首字母小写
3. 通常每个方法和函数都是执行一个动作的，所以对它们以动词宾结构进行命名会更清楚地说明它们是做什么的（如：checkForError代替errorCheck(), dumpDataToFile()代替dataFile()）

常用动词参考（set、get、check、save、remove、create、find、open、close、show、view、add、delete）



1.4 类名

1. 统一使用驼峰式，首字母大写
2. 类名应该是名词或名词短语（如：Customer等，避免使用Date、Manager这样不明含义的类名，类名也不应该是动词）



1.5 缩写词

缩写词应该使用首字母大写，其余字母小写的方式来书写命名

例如：使用GetHtmlStatistics，而不是用GetHTMLStatistics



1.6 关键词

pulic、protected、private这类关键词应统一使用小写



1.7 文件与文件夹

1. 文件名与类名保持一致，增加.php后缀
2. 文件夹名称统一使用小写字母



**[⬆ 回到顶部](#目录)**



### 格式化



### 字符串引用

1. 纯字符串使用单引号界定（单引号比双引号效率高---双引号解析变量）
2. 字符串中引用变量时，变量用{}界定，例如：`{$abc}`（可以避免"$abc"到底是$a.'bc' 还是$ab.'c'的疑问）



**[⬆ 回到顶部](#目录)**



### 忠告

1. 避免魔鬼数字

```
// 22是什么意思？
if (22 === $foo) {

}
```



### 注释

文件注释

```
/**
* github - Controller - 用护消息控制类
* ==================================
* Copyright 2023-2023 github.com
* ==================================
*
* @file
* @since 2023-01-01
* @author lisi
* @version $id: $
*
*/
```



``` 
/**
* 获取用户的消息列表
* @param int $uid 用户id
* @return array $arrayName 用户名称列表
* @since 2023-01-01
* @author lisi
* @lastupdate 2023-01-01 lisi
*/
```



**[⬆ 回到顶部](#目录)**



### 其他

6.1 PHP文件

1. 统一使用 <?php 开头，前面不应有任何多余字符，且不要使用 <? 这种简易方式（这种方式在PHP配置中已经禁用），否则可能和某些其他语言的文件混淆（如：xml）

2. 文件结尾不要使用 ?> ，以避免文件末尾带有其他字符造成的文件解析或代码无法执行等问题



6.2 异常处理

1. try/catch使用在可能抛出异常的代码段外层，原则上不同类型的多个异常应该分别使用try/catch捕获，同类型的多个异常可以使用同一组try/catch捕获，尽量避免多层的try/catch嵌套，很难追查定位问题
2. 对于可能抛出异常的系统调、数据库操作、缓存操作等必须有try/catch错失，以免给用户保留系统错误信息
3. 捕获异常的类型统一使用CException



**[⬆ 回到顶部](#目录)**



## 设计风格

### 类

### 函数或方法

### 系统调用

### 不要采用缺省方法测试非零值

使用`if(flase != f())`而不是`if(f())`



### 布尔逻辑类型

### 避免嵌入式的复制

```
// bad
while ($a != ($c = getChar())) {

}

// good
$c = getChar();
while ($a != $c) {

}
```



### 面向对象

1. 是否使用了设计模式？
   1. 很多人觉得过分追去设计模式反而会影响开发效率，但作为过来人，我可以直白的说，不使用优秀的设计模式，软件可能会死的更快



## 数据库设计

### 存储引擎

存储引擎一般情况下使用InnoDB



### 表设计

### 字段类型

### SQL编写

1. 避免SQL注入
2. 可使用 （小撇）

```
// 注意：一般字段或表名不要用MySQL的关键词. 如已使用，SQL查询时加上两撇，不然会报错
SELECT * FROM `order`;
```

3. 所有SQL关键字使用大写（如：SELECT、FROM、ORDER BY等）

4. 少用SELECT *
5. DISTINCT、ORDER BY、GROUP BY相当消耗资源，慎用
6. 编写SQL时，尽量避免大型SQL
7. 尽可能命中覆盖索引
8. 关于OR可以IN代替
9. 避免负向查询（NOT、!=、<>、NOT EXISTS等）
10. 避免使用%前缀模糊查询，因为无法使用索引
11. LIMIT 10000, 10，偏移量越大越慢
12. 避免使用大事务
13. 尽量避免子查询，一般用WHERE IN或JOIN替代



**[⬆ 回到顶部](#目录)**



### 查询方式

### 表规模

1. 纯INT表控制在千万级
2. 含CHAR表控制在百万级
3. 单表不超20个CHAR(10)字段，不超50个纯INT字段



**[⬆ 回到顶部](#目录)**



## 开发测试流程

### 开发

1. 开始
   1. 是否使用Git？是否有Git仓库权限？
   2. 注意分支
   3. 注意当前开发环境（Linux+Nginx+PHP+Redis+Yii等）
   4. 注意Linux中文件（覆盖/删除）
   5. 开发环境不允许连接线上数据库

2. 进阶
   1. Git提交，是否认真写描述？是否准守本公司提交规范？
   2. 系统生成数据（上传文件、图片等），统一存放在代码根目录下data目录中
   3. 系统日志（用户操作日志、系统自身），统一存放在代码根目录下logs目录中
   4. 注意所有用户的增删改操作，应都留有操作日志



### 测试

1. 是否review？
2. 推荐进行单元测试
3. 正式测试：开发者自测+产品设计师+用户试用



### 上线

1. 是否有自动上线脚本？
2. 配置文件修改千万注意，一失足成千古恨
3. 上线完成后注意线上检查，保证原有功能和新功能ok



**[⬆ 回到顶部](#目录)**



## 文档

### 文档命名

文档名称示例：《PHP 开发规范_20230101V1r2-­‐draft_lisi_comments》

注解：

1. 20230101：创建大版本号的日期
2. V1r2：V为version，表示大版本号，从1开始；r为revision，表示小版本号，从1开始增加，每次文档发给别人时，该数字+1
3. -draft：表明为草案，在正式发给别人时，这个去掉即可
4. _lisi_comments：任何的说明，可以表示谁谁做了什么，空格用（ _ ）代替



**[⬆ 回到顶部](#目录)**



