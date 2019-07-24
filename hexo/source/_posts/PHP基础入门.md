---
title: PHP基础入门
categories: 笔记
tags: php
---

## PHP简介
PHP（全称：PHP：Hypertext Preprocessor，即"PHP：超文本预处理器"）是一种通用开源脚本语言。
PHP 文件可包含文本、HTML、JavaScript代码和 PHP 代码
PHP 代码在服务器上执行，结果以纯 HTML 形式返回给浏览器
PHP 文件的默认文件扩展名是 ".php"

## PHP语法
**基本语法**
PHP 脚本可以放在文档中的任何位置。
PHP 脚本以 尖括号、问号、PHP<?php 开始，以 ?> 问号、尖括号结束：
```
<?php
     //这里是我们要写的PHP代码
?>
```
PHP 文件的默认文件扩展名是 ".php"。
PHP 文件通常包含 HTML 标签和一些 PHP 脚本代码。
**echo显示命令**
echo 是在PHP里面最常用的一个输出、显示功能的命令。
我们可以让他显示任何可见的字符。
```
<!DOCTYPE html>
<html>
<body> 
    <?php
        echo "Hello World!";
    ?>
</body>
</html>
```
**注意事项**
* php的代码部份全部要用半角的英文、很多人容易写成全角的英文和符号造成PHP代码报错。
* PHP 中的每个代码行都必须以分号结束。分号是一种分隔符，用于把指令集区分开来。
* PHP代码的最后一行可以加也可不加分号。（但通常一行代码写完，就必须要加分号）

## PHP中的注释
**单行注释**
// 双斜杠表示单行注释   有时也用 # 表示  但用的比较少，多用 //
**多行注释**
以 /* 开始   */结束 代表多行注释

## PHP变量
**变量规则**
1. 必须要以$开始，后面跟着变量的名称
2. 变量名必须以字母或者下划线字符开始
3. 变量名只能包含字母数字字符以及下划线（A-z、0-9 和 _ ）
4. 变量名不能包含空格
5. 变量名是区分大小写的（$y 和 $Y 是两个不同的变量）
**创建（声明）PHP变量**
PHP没有声明变量的命令，变量在第一次赋值时被创建。
**PHP是一门弱类型语言**
不必向 PHP 声明该变量的数据类型。
PHP会根据变量的值，自动把变量转换为正确的数据类型。
在强类型的编程语言中，我们必须在使用变量前先声明（定义）变量的类型和名称。
**PHP变量作用域**
变量的作用域是脚本中变量可被引用/使用的部分。
PHP 有四种不同的变量作用域：
* local
* global
* static
* parameter

**局部和全局作用域**
在所有函数外部定义的变量，拥有全局作用域。除了函数外，全局变量可以被脚本中的任何部分访问，要在一个函数中访问一个全局变量，需要使用 global 关键字。
**PHP global 关键字**
global 关键字用于函数内访问全局变量。
```
<?php
$x=0;
function myTest()
{
    global $x;
    $x=$x+5;
}
myTest();
echo $x; // 输出 5
?>
```
PHP 将所有全局变量存储在一个名为 $GLOBALS[index] 的数组中。 index 保存变量的名称。这个数组可以在函数内部访问，也可以直接用来更新全局变量。
```
<?php
$x=0;
function myTest()
{
    global $x;
    $GLOBALS['x']=$GLOBALS['x']+5;
}
myTest();
echo $x; // 输出 5
?>
```
**Static 作用域**
使局部变量不被释放，每次调用函数时，该变量将会保留着函数前一次被调用时的值。
**参数作用域**
参数是通过调用代码将值传递给函数的局部变量。

## echo和print语句
**区别**
* echo：可以输出一个或多个字符串
* print：只允许输出一个字符串，返回值总为1

**提示：**echo输出的速度比print快，echo没有返回值，print有返回值1。
**echo语句**
echo 是一个语言结构，使用的时候可以不用加括号，也可以加上括号： echo 或 echo()。
显示字符串（字符串可以包含 HTML 标签）
```
<?php
echo "<h2>PHP 很有趣!</h2>";
echo "Hello world!<br>";
echo "我要学 PHP!<br>";
echo "这是一个", "字符串，", "使用了", "多个", "参数。";
?>
```
显示变量
```
<?php
$txt1="学习 PHP";
$txt2="PHP";
$cars=array("Volvo","BMW","Toyota");
 
echo $txt1;
echo "<br>";
echo "学习 $txt2 ,很开心";
echo "<br>";
echo "我车的品牌是 {$cars[0]}";
?>
```
**print语句**
print 同样是一个语言结构，可以使用括号，也可以不使用括号： print 或 print()。
显示字符串（字符串可以包含 HTML 标签）
```
<?php
print "<h2>PHP 很有趣!</h2>";
print "Hello world!<br>";
print "我要学习 PHP!";
?>
```
显示变量
```
<?php
$txt1="学习 PHP";
$txt2="PHP";
$cars=array("Volvo","BMW","Toyota");
 
print $txt1;
print "<br>";
print "学习 $txt2 ,很开心";
print "<br>";
print "我车的品牌是 {$cars[0]}";
?>
```


















