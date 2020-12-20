# PHP 记录日志与发送邮箱组件
- 基于Modern PHP源码
- Monolog
- SwiftMailer

## 开始

1、开始前目录下面只有一个 `composer.json` 文件
2、执行`composer install` or  `composer update` 会多出 vendor 目录

## production.php

- Password：是授权密码，不是你的邮箱登录密码
    163邮箱，单击左侧菜单栏`POP3/SMTP/IMAP`，进入页面新增授权密码
- Port：25

## 其他

- 网易163邮箱客户端协议服务器信息请参考：

    |  服务器   | 服务器地址 | SSL协议端口号 | 非SSL协议端口号 |
    |  ----  | ----  | ---- | ---- |
    | IMAP  | imap.163.com | 993 | 143 |
    | SMTP(发件)  | smtp.163.com | 465/994 | 25 |
    | POP3(收件)  | pop.163.com | 995 | 110 |

- 本地测试报错
    `PHP Fatal error:  Uncaught Swift_TransportException: Expected response code 220 but got code "", with message ""`
    解决：把端口 `465/994` 修改为 `25`

- 接收邮件效果展示
    ```sh
    Website error!
    发件人：John Doe <xxxxxx@163.com>
    时   间：2020年12月20日（星期日）下午1 : 17
    收件人：小明 <xxxxx@qq.com>

    [2020-12-20 00:17:18] my-app-name.CRITICAL: The server is on fire! [] []
    ```

## 参考

- 《Modern PHP（中文版）》 与 书籍源码
- [网易163文档](http://help.mail.163.com/faqDetail.do?code=d7a5dc8471cd0c0e8b4b8f4f8e49998b374173cfe9171305fa1ce630d7f67ac2478c3849ded415e1)
- [QQ邮箱文档](https://service.mail.qq.com/cgi-bin/help?subtype=1&&id=28&&no=371)

