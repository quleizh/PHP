# PHP_CodeSniffer

## 1、Windows安装

```sh
- 首先你要安装好compose

composer global require "squizlabs/php_codesniffer=*"

//解决报错（openssl）
composer config -g -- disable-tls false / true (我修改的flase)
//其他报错
	- 提示开启一些php.ini里面的扩展

//安装成功后，查看全局 Vendor 目录位置:
composer global config bin-dir --absolute

//安装后会在全局的 Vendor目录下的 bin 中生成两个软链接：
phpcbf -> ../squizlabs/php_codesniffer/bin/phpcbf
phpcs -> ../squizlabs/php_codesniffer/bin/phpcs

C:\Users\28268\AppData\Roaming\Composer\vendor\bin
```

## 2、使用

```sh
//加入环境变量
phpcs --config-set default_standard PSR2
phpcbf --config-set default_standard PSR2

//测试
phpcs test.php
	//指定格式标准
	phpcs --standard=PSR2 test.php

//修正代码
phpcbf test.php
```

## 3、PHPStrom配置

- 版本：中文版-2020.3

```sh
//1
File->Settine
	Editor->Code Style->php
		Set Form(最右边)->PSR1/PSR2
		
//2
	Setting->Languages and Frameworks->PHP->Quality Tools->Code Sniffer
		PHP_CodeSniffer Path:C:\Users\28268\AppData\Roaming\Composer\vendor\bin\phpcs.bat
		
		点击下面的检查，弹出弹框
			- 打对勾
			- 编码标准：PSR2
		或者
			- Setting->Editor->Inspections

//3
	Setting->Tools -> External Tools
		- 程序：C:\Users\28268\AppData\Roaming\Composer\vendor\bin\phpcbf.bat
		- 参数：--standard=PSR2 $FileDir$/$FileName$
		- 工作目录：C:\Users\28268\AppData\Roaming\Composer\vendor\bin
		
		可以取消对勾：打开工具输出的控制台
		
	//使用
	IDE工具栏->Tools->External Tools
	//添加快捷键
	 Settings -> Keymap -> External Tools -> phpcbf 中进行添加快捷键操作
```

## 命令

```sh
$ phpcs --version
PHP_CodeSniffer version 3.5.8 (stable) by Squiz (http://www.squiz.net)

> php --ini
Configuration File (php.ini) Path:
Loaded Configuration File:         C:\PHP\php.ini
Scan for additional .ini files in: (none)
Additional .ini files parsed:      (none)

- > composer
	Composer version 2.0.7 2020-11-13 17:31:06

```



## 参考

- [PHP代码修正之CodeSniffer](https://segmentfault.com/a/1190000019136556)

- [pear](https://pear.php.net/package/PHP_CodeSniffer)

- [phpstorm官方文档](https://www.jetbrains.com/help/phpstorm/using-php-code-sniffer.html#prerequisites)