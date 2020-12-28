[toc]

## 简介
PHP 8.0 是 PHP 语言的一个主版本更新。
它包含了很多新功能与优化项， 包括命名参数、联合类型、注解、构造器属性提升、match 表达式、nullsafe 运算符、JIT，并改进了类型系统、错误处理、语法一致性。

## Nullsafe 运算符
现在可以用新的 nullsafe 运算符链式调用，而不需要条件检查 null。 如果链条中的一个元素失败了，整个链条会中止并认定为 Null。

```php
PHP 7
$country =  null;
if ($session !== null) {
  $user = $session->user;
  if ($user !== null) {
    $address = $user->getAddress();
 
    if ($address !== null) {
      $country = $address->country;
    }
  }
}

PHP 8
$country = $session?->user?->getAddress()?->country;

```

## Match 表达式

新的 match 类似于 switch，并具有以下功能：

- Match 是一个表达式，它可以储存到变量中亦可以直接返回。
- Match 分支仅支持单行，它不需要一个 break; 语句。
- Match 使用严格比较。

```php
PHP 7
switch (8.0) {
  case '8.0':
    $result = "Oh no!";
    break;
  case 8.0:
    $result = "This is what I expected";
    break;
}
echo $result;
//> Oh no!

PHP 8
echo match (8.0) {
  '8.0' => "Oh no!",
  8.0 => "This is what I expected",
};
//> This is what I expected
```

## 命名参数

```php
PHP 7
htmlspecialchars($string, ENT_COMPAT | ENT_HTML401, 'UTF-8', false);

PHP 8
htmlspecialchars($string, double_encode: false);
```

## 构造器属性提升

```php
PHP 7
class Point {
  public float $x;
  public float $y;
  public float $z;
  public function __construct(
    float $x = 0.0,
    float $y = 0.0,
    float $z = 0.0
  ) {
    $this->x = $x;
    $this->y = $y;
    $this->z = $z;
  }
}

class Point {
  public function __construct(
    public float $x = 0.0,
    public float $y = 0.0,
    public float $z = 0.0,
  ) {}
}
```
## 允许参数列表中的末尾逗号 

```php
new Uri(
    $scheme,
    $user,
    $pass,
    $host,
    $port,
    $path,
    $query,
    $fragment, // <-- Huh, this is allowed!
);
```


##参考链接

- [php.net](https://www.php.net/releases/8.0/zh.php)

- [PHP 8 Released! My Top 5 Killer New Features
](https://www.youtube.com/watch?v=P5ML-Fl8sUk)