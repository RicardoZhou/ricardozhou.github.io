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
**其他**
* **dump：**显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。
* **print_r：**打印关于变量的易于理解的信息,如果给出的是 string、integer 或 float，将打印变量值本身。如果给出的是 array，将会按照一定格式显示键和元素。object 与数组类似。 记住，print_r() 将把数组的指针移到最后边。使用 reset() 可让指针回到开始处。
* **var_dump和print_r的区别：**var_dump 返回表达式的类型与值而 print_r 仅返回结果，相比调试代码使用 var_dump 更便于阅读。

## PHP EOF(heredoc)
PHP EOF(heredoc)是一种在命令行shell（如sh、csh、ksh、bash、PowerShell和zsh）和程序语言（像Perl、PHP、Python和Ruby）里定义一个字符串的方法。
**使用概述**
1. 必须后接分号，否则编译通不过。
2. EOF 可以用任意其它字符代替，只需保证结束标识与开始标识一致。
3. 结束标识必须顶格独自占一行(即必须从行首开始，前后不能衔接任何空白和字符)。
4. 开始标识可以不带引号或带单双引号，不带引号与带双引号效果一致，解释内嵌的变量和转义符号，带单引号则不解释内嵌的变量和转义符号。
5. 当内容需要内嵌引号（单引号或双引号）时，不需要加转义符，本身对单双引号转义，此处相当与q和qq的用法。
```
<?php
echo <<<EOF
    <h1>我的第一个标题</h1>
    <p>我的第一个段落。</p>
EOF;
// 结束需要独立一行且前后不能空格
?>
```
**注意**
1. 以 **<<<EOF** 开始标记开始，以 **EOF** 结束标记结束，结束标记必须顶头写，不能有缩进和空格，且在结束标记末尾要有分号 。
2. 开始标记和结束标记相同，比如常用大写的 **EOT、EOD、EOF** 来表示，但是不只限于那几个(也可以用：JSON、HTML等)，只要保证开始标记和结束标记不在正文中出现即可。
3. 位于开始标记和结束标记之间的变量可以被正常解析，但是函数则不可以。在 heredoc 中，变量不需要用连接符 **.** 或 **,** 来拼接。
```
<?php
$name="runoob";
$a= <<<EOF
    "abc"$name
    "123"
EOF;
// 结束需要独立一行且前后不能空格
echo $a;
?>
```

## 数据类型
String（字符串）, Integer（整型）, Float（浮点型）, Boolean（布尔型）, Array（数组）, Object（对象）, NULL（空值）。
**字符串**
一个字符串是一串字符的序列，就像 "Hello world!"。
可以将任何文本放在单引号和双引号中。
**整型**
整数是一个没有小数的数字。
* 整数必须至少有一个数字 (0-9)
* 整数不能包含逗号或空格
* 整数是没有小数点的
* 整数可以是正数或负数
* 整型可以用三种格式来指定：十进制， 十六进制（ 以 0x 为前缀）或八进制（前缀为 0）。

**浮点型**
浮点数是带小数部分的数字，或是指数形式。
```
<?php 
$x = 10.365;
var_dump($x);
echo "<br>"; 
$x = 2.4e3;
var_dump($x);
echo "<br>"; 
$x = 8E-5;
var_dump($x);
?>
```
**布尔型**
布尔型可以是 TRUE 或 FALSE。
**数组**
数组可以在一个变量中存储多个值。
**对象**
对象数据类型也可以用于存储数据。
在 PHP 中，对象必须声明。
首先，你必须使用class关键字声明类对象。类是可以包含属性和方法的结构。
然后我们在类中定义数据类型，然后在实例化的类中使用数据类型：
```
<?php
class Car
{
  var $color;
  function __construct($color="green") {
    $this->color = $color;
  }
  function what_color() {
    return $this->color;
  }
}
?>
```
**NULL值**
NULL 值表示变量没有值。NULL 是数据类型为 NULL 的值。
NULL 值指明一个变量是否为空值。 同样可用于数据空值和NULL值的区别。
可以通过设置变量值为 NULL 来清空变量数据：
```
<?php
$x="Hello world!";
$x=null;
var_dump($x);
?>
```

## 类型比较
* 松散比较：使用两个等号 **==** 比较，只比较值，不比较类型。
* 严格比较：用三个等号 **===** 比较，除了比较值，也比较类型。

对于多种类型，比较运算符根据下表比较（按顺序）。
**比较多种类型**

|运算数 1 类型|运算数 2 类型|结果|
|-|-|-|
|null 或 string|string|将 **NULL** 转换为 ""，进行数字或词汇比较|
|bool 或 null|任何其它类型|转换为 bool，**FALSE < TRUE**|
|object|object|内置类可以定义自己的比较，不同类不能比较，相同类和数组同样方式比较属性（PHP 4 中），PHP 5 有其自己的说明|
|string，resource 或 number|string，resource 或 number|将字符串和资源转换成数字，按普通数学比较|
|array|array|具有较少成员的数组较小，如果运算数 1 中的键不存在于运算数 2 中则数组无法比较，否则挨个值比较（见下例）|
|object|任何其它类型|object 总是更大|
|array|任何其它类型|array 总是更大|

**松散比较==**

||TRUE|FALSE|1|0|-1|"1"|"0"|"-1"|NULL|array()|"php"|""|
|-|-|-|-|-|-|-|-|-|-|-|-|-|
|TRUE|TRUE|FALSE|TRUE|FALSE|TRUE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|
|FALSE|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|TRUE|TRUE|FALSE|TRUE|
|1|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|
|0|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|TRUE|FALSE|TRUE|TRUE|
|-1|TRUE|FALSE|FALSE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|
|"1"|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|
|"0"|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|
|"-1"|TRUE|FALSE|FALSE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|
|NULL|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|TRUE|TRUE|FALSE|TRUE|
|array()|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|TRUE|TRUE|FALSE|FALSE|
|"php"|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|TRUE|FALSE|
|""|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|TRUE|FALSE|FALSE|TRUE|

**严格比较===**

||TRUE|FALSE|1|0|-1|"1"|"0"|"-1"|NULL|array()|"php"|""|
|-|-|-|-|-|-|-|-|-|-|-|-|-|
|TRUE|TRUE|FALSE|TRUE|FALSE|TRUE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|
|FALSE|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|TRUE|TRUE|FALSE|TRUE|
|1|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|
|0|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|TRUE|FALSE|TRUE|TRUE|
|-1|TRUE|FALSE|FALSE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|
|"1"|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|
|"0"|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|
|"-1"|TRUE|FALSE|FALSE|FALSE|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|
|NULL|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|TRUE|TRUE|FALSE|TRUE|
|array()|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|TRUE|TRUE|FALSE|FALSE|
|"php"|TRUE|FALSE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|FALSE|FALSE|TRUE|FALSE|
|""|FALSE|TRUE|FALSE|TRUE|FALSE|FALSE|FALSE|FALSE|TRUE|FALSE|FALSE|TRUE|

[比较运算符](https://www.php.net/manual/zh/language.operators.comparison.php)
[PHP 类型比较表](https://www.php.net/manual/zh/types.comparisons.php)

## 常量
常量是一个简单值的标识符。该值在脚本中不能改变。
一个常量由英文字母、下划线、和数字组成,但数字不能作为首字母出现。 (常量名不需要加 $ 修饰符)。
**注意：**常量在整个脚本中都可以使用，即便常量定义在函数外也可以正常使用常量。
设置常量，使用 define() 函数，函数语法如下：
`bool define ( string $name , mixed $value [, bool $case_insensitive = false ] )`
* **name：**必选参数，常量名称，即标志符。
* **value：**必选参数，常量的值。
* **case_insensitive ：**可选参数，如果设置为 TRUE，该常量则大小写不敏感。默认是大小写敏感的。
```
<?php
define("HELLO", "hello world", true);
echo hello;//输出“hellow world”；
?>
```
**常量是全局的。**

## 字符串
字符串变量用于包含有字符的值。
可以直接在函数中使用字符串，或者把它存储在变量中。
**并置运算符**
在 PHP 中，只有一个字符串运算符。
并置运算符 (.) 用于把两个字符串值连接起来。
```
<?php 
$txt1="Hello world!"; 
$txt2="What a nice day!"; 
echo $txt1 . " " . $txt2; 	//输出“Hello world! What a nice day!”
?>
```
**strlen() 函数**
返回字符串的长度（字符数）。
**strpos() 函数**
用于在字符串内查找一个字符或一段指定的文本。
如果在字符串中找到匹配，该函数会返回第一个匹配的字符位置。如果未找到匹配，则返回 FALSE。（第一个字符的位置是 0，而不是 1。）
```
<?php 
echo strpos("Hello world!","world"); 	//输出 6
?>
```

## 运算符
**算术运算符**
+ ， - ， * ， / ， % ， -（取反） ， .（并置）
PHP7+ 版本新增整除运算符 intdiv()
```
<?php
var_dump(intdiv(10, 3));	//输出 int(3)
?>
```
**赋值运算符**
= ， += ， -= ， *= ， /= ， %= ， .=
**递增/递减运算符**
++x , x++ , --x , x--
**比较运算符**
== ， === ， != ， !== ， > ， < ， >= ， <=
**逻辑运算符**
and ， or ， xor（异或） ， && ， || ， !（非）
**数组运算符**

|运算符|名称|描述|
|-|-|-|
|x + y|集合|x 和 y 的集合|
|x == y|相等|如果 x 和 y 具有相同的键/值对，则返回 true|
|x === y|恒等|如果 x 和 y 具有相同的键/值对，且顺序相同类型相同，则返回 true|
|x != y|不相等|如果 x 不等于 y，则返回 true|
|x <> y|不相等|如果 x 不等于 y，则返回 true|
|x !== y|不恒等|如果 x 不等于 y，则返回 true|

**三元运算符**
```
<?php
$test = 'test string';
// 普通写法
$username = isset($test) ? $test : 'nobody';
echo $username, PHP_EOL;
 
// PHP 5.3+ 版本写法
$username = $test ?: 'nobody';
echo $username, PHP_EOL;
?>
```
**注意：**PHP_EOL 是一个换行符，兼容更大平台。
在 PHP7+ 版本多了一个 NULL 合并运算符 **??** 。
```
<?php
// 如果 $_GET['user'] 不存在返回 'nobody'，否则返回 $_GET['user'] 的值
$username = $_GET['user'] ?? 'nobody';
// 类似的三元运算符
$username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
?>
```
$a=$c?:$b;  等同于  $a=$c?$c:$b;
$a=$c??$b;  等同于  $a=isset($c)?$c:$b;
**组合比较符(PHP7+)**
PHP7+ 支持组合比较符（combined comparison operator）也称之为太空船操作符，符号为 **<=>**。组合比较运算符可以轻松实现两个变量的比较，当然不仅限于数值类数据的比较。
`$c = $a <=> $b;`
* 如果 $a > $b, 则 $c 的值为 1。
* 如果 $a == $b, 则 $c 的值为 0。
* 如果 $a < $b, 则 $c 的值为 -1。
**运算符优先级**
下表按照优先级从高到低列出了运算符。同一行中的运算符具有相同优先级，此时它们的结合方向决定求值顺序。
**说明：**左 ＝ 从左到右，右 ＝ 从右到左。

|结合方向|运算符|附加信息|
|-|-|-|
|无|clone new|clone 和 new|
|左|[[](])|array()|
|右|++ -- ~ (int) (float) (string) (array) (object) (bool) @|类型和递增／递减|
|无|instanceof|类型|
|右|!|逻辑运算符|
|左|* / %|算术运算符|
|左|+ – .|算术运算符和字符串运算符|
|左|<< >>|位运算符|
|无|== != === !== <>|比较运算符|
|左|&|位运算符和引用|
|左|^|位运算符|
|左|||位运算符|
|左|&&|逻辑运算符|
|左||||逻辑运算符|
|左|? :|三元运算符|
|右|= += -= *= /= .= %= &= |= ^= <<= >>= =>|赋值运算符|
|左|and|逻辑运算符|
|左|xor|逻辑运算符|
|左|or|逻辑运算符|
|左|,|多处用到|

运算符优先级中，or 和 ||，&& 和 and 都是逻辑运算符，效果一样，但是其优先级却不一样。
```
<?php
// 优先级： &&  >  =  >  and
// 优先级： ||  >  =  >  or
 
$a = 3;
$b = false;
$c = $a or $b;
var_dump($c);          // 这里的 $c 为 int 值3，而不是 boolean 值 true
$d = $a || $b;
var_dump($d);          //这里的 $d 就是 boolean 值 true 
?>
```
**括号的使用**
我们通过括号的配对来明确标明运算顺序，而非靠运算符优先级和结合性来决定，通常能够增加代码的可读性。

## If...Else 语句
* if语句
* if...else语句
* if...elseif...else语句
* switch语句

## Switch 语句
switch 语句用于根据多个不同条件执行不同动作。

## 数组
数组是一个能在单个变量中存储多个值的特殊变量。
**创建数组**
`array();`
* **数值数组** - 带有数字 ID 键的数组
* **关联数组** - 带有指定的键的数组，每个键关联一个值
* **多维数组** - 包含一个或多个数组的数组

**数值数组**
自动分配 ID 键（ID 键总是从 0 开始）
`$cars=array("Volvo","BMW","Toyota");`
人工分配 ID 键
```
$cars[0]="Volvo";
$cars[1]="BMW";
$cars[2]="Toyota";
```
可使用 for 循环遍历数值数组。
**获取数组的长度 - count() 函数**
用于返回数组的长度（元素的数量）
**关联数组**
使用自己分配给数组的指定的键的数组。
`$age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");`
```
$age['Peter']="35";
$age['Ben']="37";
$age['Joe']="43";
```
可使用 foreach 循环遍历关联数组。

## 数组排序
数组中的元素可以按字母或数字顺序进行降序或升序排列。
* sort() - 对数组进行升序排列
* rsort() - 对数组进行降序排列
* asort() - 根据关联数组的值，对数组进行升序排列
* ksort() - 根据关联数组的键，对数组进行升序排列
* arsort() - 根据关联数组的值，对数组进行降序排列
* krsort() - 根据关联数组的键，对数组进行降序排列

## 超级全局变量
超级全局变量在PHP 4.1.0之后被启用, 是PHP系统中自带的变量，在一个脚本的全部作用域中都可用。
PHP中预定义了几个超级全局变量（superglobals） ，这意味着它们在一个脚本的全部作用域中都可用。 你不需要特别说明，就可以在函数及类中使用。
* $GLOBALS
* $_SERVER
* $_REQUEST
* $_POST
* $_GET
* $_FILES
* $_ENV
* $_COOKIE
* $_SESSION

**$GLOBALS**
$GLOBALS 是PHP的一个超级全局变量组，在一个PHP脚本的全部作用域中都可以访问。
$GLOBALS 是一个包含了全部变量的全局组合数组。变量的名字就是数组的键。
```
<?php 
$x = 75; 
$y = 25;
function addition() 
{ 
    $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y']; 
}
addition(); 
echo $z; 
?>
```
**$_SERVER**

$_SERVER 是一个包含了诸如头信息(header)、路径(path)、以及脚本位置(script locations)等等信息的数组。这个数组中的项目由 Web 服务器创建。不能保证每个服务器都提供全部项目；服务器可能会忽略一些，或者提供一些没有在这里列举出来的项目。

|元素/代码|描述|
|-|-|
|$_SERVER['PHP_SELF']|当前执行脚本的文件名，与 document root 有关。例如，在地址为 http://example.com/test.php/foo.bar 的脚本中使用 $_SERVER['PHP_SELF'] 将得到 /test.php/foo.bar。__FILE__ 常量包含当前(例如包含)文件的完整路径和文件名。 从 PHP 4.3.0 版本开始，如果 PHP 以命令行模式运行，这个变量将包含脚本名。之前的版本该变量不可用。|
|$_SERVER['GATEWAY_INTERFACE']|服务器使用的 CGI 规范的版本；例如，"CGI/1.1"。|
|$_SERVER['SERVER_ADDR']|当前运行脚本所在的服务器的 IP 地址。|
|$_SERVER['SERVER_NAME']|当前运行脚本所在的服务器的主机名。如果脚本运行于虚拟主机中，该名称是由那个虚拟主机所设置的值决定。(如: www.runoob.com)|
|$_SERVER['SERVER_SOFTWARE']|服务器标识字符串，在响应请求时的头信息中给出。 (如：Apache/2.2.24)|
|$_SERVER['SERVER_PROTOCOL']|请求页面时通信协议的名称和版本。例如，"HTTP/1.0"。|
|$_SERVER['REQUEST_METHOD']|访问页面使用的请求方法；例如，"GET", "HEAD"，"POST"，"PUT"。|
|$_SERVER['REQUEST_TIME']|请求开始时的时间戳。从 PHP 5.1.0 起可用。 (如：1377687496)|
|$_SERVER['QUERY_STRING']|query string（查询字符串），如果有的话，通过它进行页面访问。|
|$_SERVER['HTTP_ACCEPT']|当前请求头中 Accept: 项的内容，如果存在的话。|
|$_SERVER['HTTP_ACCEPT_CHARSET']|当前请求头中 Accept-Charset: 项的内容，如果存在的话。例如："iso-8859-1,*,utf-8"。|
|$_SERVER['HTTP_HOST']|当前请求头中 Host: 项的内容，如果存在的话。|
|$_SERVER['HTTP_REFERER']|引导用户代理到当前页的前一页的地址（如果存在）。由 user agent 设置决定。并不是所有的用户代理都会设置该项，有的还提供了修改 HTTP_REFERER 的功能。简言之，该值并不可信。)|
|$_SERVER['HTTPS']|如果脚本是通过 HTTPS 协议被访问，则被设为一个非空的值。|
|$_SERVER['REMOTE_ADDR']|浏览当前页面的用户的 IP 地址。|
|$_SERVER['REMOTE_HOST']|浏览当前页面的用户的主机名。DNS 反向解析不依赖于用户的 REMOTE_ADDR。|
|$_SERVER['REMOTE_PORT']|用户机器上连接到 Web 服务器所使用的端口号。|
|$_SERVER['SCRIPT_FILENAME']|当前执行脚本的绝对路径。|
|$_SERVER['SERVER_ADMIN']|该值指明了 Apache 服务器配置文件中的 SERVER_ADMIN 参数。如果脚本运行在一个虚拟主机上，则该值是那个虚拟主机的值。(如：someone@runoob.com)|
|$_SERVER['SERVER_PORT']|Web 服务器使用的端口。默认值为 "80"。如果使用 SSL 安全连接，则这个值为用户设置的 HTTP 端口。|
|$_SERVER['SERVER_SIGNATURE']|包含了服务器版本和虚拟主机名的字符串。|
|$_SERVER['PATH_TRANSLATED']|当前脚本所在文件系统（非文档根目录）的基本路径。这是在服务器进行虚拟到真实路径的映像后的结果。|
|$_SERVER['SCRIPT_NAME']|包含当前脚本的路径。这在页面需要指向自己时非常有用。__FILE__ 常量包含当前脚本(例如包含文件)的完整路径和文件名。|
|$_SERVER['SCRIPT_URI']|URI 用来指定要访问的页面。例如 "/index.html"。|

**$_REQUEST**
$_REQUEST 用于收集HTML表单提交的数据。
**$_POST**
$_POST 被广泛应用于收集表单数据，在HTML form标签的指定该属性："method="post"。
**$_GET**
$_GET 同样被广泛应用于收集表单数据，在HTML form标签的指定该属性："method="get"。

## While 循环
* **while** - 只要指定的条件成立，则循环执行代码块
* **do...while** - 首先执行一次代码块，然后在指定的条件成立时重复这个循环
* **for** - 循环执行代码块指定的次数
* **foreach** - 根据数组中每个元素来循环代码块

## For/Foreach 循环
**for循环**
```
for (初始值; 条件; 增量)
{
    要执行的代码;
}
```
**foreach循环**
```
foreach ($array as $value)	//$value 可用 $key => $value 替换
{
    要执行代码;
}
```

## 函数
**内建函数**
PHP 中，提供了超过 1000 个内建的函数。
**创建 PHP 函数**
```
<?php
function functionName()
{
    // 要执行的代码
}
?>
```
函数准则
* 函数的名称应该提示出它的功能
* 函数名称以字母或下划线开头（不能以数字开头）

**参数**
为了给函数添加更多的功能，我们可以添加参数，参数类似变量。
参数就在函数名称后面的一个括号内指定。
**返回值**
如需让函数返回一个值，请使用 return 语句。

## 魔术常量
PHP 向它运行的任何脚本提供了大量的预定义常量。
不过很多常量都是由不同的扩展库定义的，只有在加载了这些扩展库时才会出现，或者动态加载后，或者在编译时已经包括进去了。
有八个魔术常量它们的值随着它们在代码中的位置改变而改变。

|名称|说明|
|-|-|
|__LINE__|文件中的当前行号。|
|__FILE__|文件的完整路径和文件名。如果用在被包含文件中，则返回被包含的文件名。自 PHP 4.0.2 起，__FILE__ 总是包含一个绝对路径（如果是符号连接，则是解析后的绝对路径），而在此之前的版本有时会包含一个相对路径。|
|__DIR__|文件所在的目录。如果用在被包括文件中，则返回被包括的文件所在的目录。它等价于 dirname(__FILE__)。除非是根目录，否则目录中名不包括末尾的斜杠。（PHP 5.3.0中新增）|
|__FUNCTION__|函数名称（PHP 4.3.0 新加）。自 PHP 5 起本常量返回该函数被定义时的名字（区分大小写）。在 PHP 4 中该值总是小写字母的。|
|__CLASS__|类的名称（PHP 4.3.0 新加）。自 PHP 5 起本常量返回该类被定义时的名字（区分大小写）。在 PHP 4 中该值总是小写字母的。类名包括其被声明的作用区域（例如 Foo\Bar）。注意自 PHP 5.4 起 __CLASS__ 对 trait 也起作用。当用在 trait 方法中时，__CLASS__ 是调用 trait 方法的类的名字。|
|__TRAIT__|Trait 的名字（PHP 5.4.0 新加）。自 PHP 5.4 起此常量返回 trait 被定义时的名字（区分大小写）。Trait 名包括其被声明的作用区域（例如 Foo\Bar）。|
|__METHOD__|类的方法名（PHP 5.0.0 新加）。返回该方法被定义时的名字（区分大小写）。|
|__NAMESPACE__|当前命名空间的名称（区分大小写）。此常量是在编译时定义的（PHP 5.3.0 新增）。|

## 命名空间(namespace)
命名空间(namespace)是在PHP 5.3中加入的，如果你学过C#和Java，那命名空间就不算什么新事物。 不过在PHP当中还是有着相当重要的意义。
命名空间可以解决以下两类问题：
1. 用户编写的代码与PHP内部的类/函数/常量或第三方类/函数/常量之间的名字冲突。
2. 为很长的标识符名称(通常是为了缓解第一类问题而定义的)创建一个别名（或简短）的名称，提高源代码的可读性。
**定义命名空间**
默认情况下，所有常量、类和函数名都放在全局空间下，就和PHP支持命名空间之前一样。
命名空间通过关键字namespace 来声明。如果一个文件中包含命名空间，它必须在其它所有代码之前声明命名空间。
```
<?php  
// 定义代码在 'MyProject' 命名空间中  
namespace MyProject;  
 
// ... 代码 ...  
```
也可以在同一个文件中定义不同的命名空间代码
```
<?php  
namespace MyProject;

const CONNECT_OK = 1;
class Connection { /* ... */ }
function connect() { /* ... */  }

namespace AnotherProject;

const CONNECT_OK = 1;
class Connection { /* ... */ }
function connect() { /* ... */  }
?>  
```
不建议使用这种语法在单个文件中定义多个命名空间。建议使用下面的大括号形式的语法。
```
<?php
namespace MyProject {
    const CONNECT_OK = 1;
    class Connection { /* ... */ }
    function connect() { /* ... */  }
}

namespace AnotherProject {
    const CONNECT_OK = 1;
    class Connection { /* ... */ }
    function connect() { /* ... */  }
}
?>
```
将全局的非命名空间中的代码与命名空间中的代码组合在一起，只能使用大括号形式的语法。全局代码必须用一个不带名称的 namespace 语句加上大括号括起来。
```
<?php
namespace MyProject {

const CONNECT_OK = 1;
class Connection { /* ... */ }
function connect() { /* ... */  }
}

namespace { // 全局代码
session_start();
$a = MyProject\connect();
echo MyProject\Connection::start();
}
?>
```
在声明命名空间之前唯一合法的代码是用于定义源文件编码方式的 declare 语句。所有非 PHP 代码包括空白符都不能出现在命名空间的声明之前。
```
<?php
declare(encoding='UTF-8'); //定义多个命名空间和不包含在命名空间中的代码
namespace MyProject {
/* ... */
}

namespace { // 全局代码
/* ... */
}
?>
```
以下代码会出现语法错误
```
<html>
<?php
namespace MyProject; // 命名空间前出现了“<html>” 会致命错误 -　命名空间必须是程序脚本的第一条语句
?>
```
**子命名空间**
与目录和文件的关系很像，PHP 命名空间也允许指定层次化的命名空间的名称。因此，命名空间的名字可以使用分层次的方式定义：
```
<?php
namespace MyProject\Sub\Level;  //声明分层次的单个命名空间

const CONNECT_OK = 1;
class Connection { /* ... */ }
function Connect() { /* ... */  }
?>
```
**命名空间使用**
1. **非限定名称，或不包含前缀的类名称**，例如 $a=new foo(); 或 foo::staticmethod();。如果当前命名空间是 currentnamespace，foo 将被解析为 currentnamespace\foo。如果使用 foo 的代码是全局的，不包含在任何命名空间中的代码，则 foo 会被解析为foo。 警告：如果命名空间中的函数或常量未定义，则该非限定的函数名称或常量名称会被解析为全局函数名称或常量名称。
2. **限定名称,或包含前缀的名称**，例如 $a = new subnamespace\foo(); 或 subnamespace\foo::staticmethod();。如果当前的命名空间是 currentnamespace，则 foo 会被解析为 currentnamespace\subnamespace\foo。如果使用 foo 的代码是全局的，不包含在任何命名空间中的代码，foo 会被解析为subnamespace\foo。
3. **完全限定名称，或包含了全局前缀操作符的名称**，例如， $a = new \currentnamespace\foo(); 或 \currentnamespace\foo::staticmethod();。在这种情况下，foo 总是被解析为代码中的文字名(literal name)currentnamespace\foo。
注意访问任意全局类、函数或常量，都可以使用完全限定名称，例如 \strlen() 或 \Exception 或 \INI_ALL。
**命名空间和动态语言特征**
命名空间的实现受到其语言自身的动态特征的影响。因此，如果要将下面的代码转换到命名空间中，动态访问元素。
```
<?php
class classname
{
    function __construct()
    {
        echo __METHOD__,"\n";
    }
}
function funcname()
{
    echo __FUNCTION__,"\n";
}
const constname = "global";

$a = 'classname';
$obj = new $a; // prints classname::__construct
$b = 'funcname';
$b(); // prints funcname
echo constant('constname'), "\n"; // prints global
?>
```
必须使用完全限定名称（包括命名空间前缀的类名称）。注意因为在动态的类名称、函数名称或常量名称中，限定名称和完全限定名称没有区别，因此其前导的反斜杠是不必要的。
动态访问命名空间的元素
```
<?php
namespace namespacename;
class classname
{
    function __construct()
    {
        echo __METHOD__,"\n";
    }
}
function funcname()
{
    echo __FUNCTION__,"\n";
}
const constname = "namespaced";

include 'example1.php';

$a = 'classname';
$obj = new $a; // 输出 classname::__construct
$b = 'funcname';
$b(); // 输出函数名
echo constant('constname'), "\n"; // 输出 global

/* 如果使用双引号，使用方法为 "\\namespacename\\classname"*/
$a = '\namespacename\classname';
$obj = new $a; // 输出 namespacename\classname::__construct
$a = 'namespacename\classname';
$obj = new $a; // 输出 namespacename\classname::__construct
$b = 'namespacename\funcname';
$b(); // 输出 namespacename\funcname
$b = '\namespacename\funcname';
$b(); // 输出 namespacename\funcname
echo constant('\namespacename\constname'), "\n"; // 输出 namespaced
echo constant('namespacename\constname'), "\n"; // 输出 namespaced
?>
```
**namespace关键字和\_\_NAMESPACE\_\_常量**
PHP支持两种抽象的访问当前命名空间内部元素的方法，\_\_NAMESPACE\_\_ 魔术常量和namespace关键字。
常量\_\_NAMESPACE\_\_的值是包含当前命名空间名称的字符串。在全局的，不包括在任何命名空间中的代码，它包含一个空的字符串。
\_\_NAMESPACE\_\_ 示例, 在命名空间中的代码
```
<?php
namespace MyProject;

echo '"', __NAMESPACE__, '"'; // 输出 "MyProject"
?>
```
\_\_NAMESPACE\_\_ 示例，全局代码
```
<?php

echo '"', __NAMESPACE__, '"'; // 输出 ""
?>
```
使用\_\_NAMESPACE\_\_动态创建名称
```
<?php
namespace MyProject;

function get($classname)
{
    $a = __NAMESPACE__ . '\\' . $classname;
    return new $a;
}
?>
```
关键字 namespace 可用来显式访问当前命名空间或子命名空间中的元素。它等价于类中的 self 操作符。
**使用命名空间：别名/导入**
有两种使用别名或导入方式：为类名称使用别名，或为命名空间名称使用别名。
在PHP中，别名是通过操作符 use 来实现的。
```
<?php
use My\Full\Classname as Another, My\Full\NSname;

$obj = new Another; // 实例化 My\Full\Classname 类
$a = 'Another';
$obj = new $a;      // 实际化 Another 类
$obj = new \Another; // 实例化 Another 类
?>
```
**使用命名空间：后备全局函数/常量**
在一个命名空间中，当 PHP 遇到一个非限定的类、函数或常量名称时，它使用不同的优先策略来解析该名称。类名称总是解析到当前命名空间中的名称。因此在访问系统内部或不包含在命名空间中的类名称时，必须使用完全限定名称。
对于函数和常量来说，如果当前命名空间中不存在该函数或常量，PHP 会退而使用全局空间中的函数或常量。
**全局空间**
如果没有定义任何命名空间，所有的类与函数的定义都是在全局空间，与 PHP 引入命名空间概念前一样。在名称前加上前缀 \ 表示该名称是全局空间中的名称，即使该名称位于其它的命名空间中时也是如此。
**命名空间的顺序**
```
<?php
namespace A;
use B\D, C\E as F;

// 函数调用

foo();      // 首先尝试调用定义在命名空间"A"中的函数foo()
            // 再尝试调用全局函数 "foo"

\foo();     // 调用全局空间函数 "foo" 

my\foo();   // 调用定义在命名空间"A\my"中函数 "foo" 

F();        // 首先尝试调用定义在命名空间"A"中的函数 "F" 
            // 再尝试调用全局函数 "F"

// 类引用

new B();    // 创建命名空间 "A" 中定义的类 "B" 的一个对象
            // 如果未找到，则尝试自动装载类 "A\B"

new D();    // 使用导入规则，创建命名空间 "B" 中定义的类 "D" 的一个对象
            // 如果未找到，则尝试自动装载类 "B\D"

new F();    // 使用导入规则，创建命名空间 "C" 中定义的类 "E" 的一个对象
            // 如果未找到，则尝试自动装载类 "C\E"

new \B();   // 创建定义在全局空间中的类 "B" 的一个对象
            // 如果未发现，则尝试自动装载类 "B"

new \D();   // 创建定义在全局空间中的类 "D" 的一个对象
            // 如果未发现，则尝试自动装载类 "D"

new \F();   // 创建定义在全局空间中的类 "F" 的一个对象
            // 如果未发现，则尝试自动装载类 "F"

// 调用另一个命名空间中的静态方法或命名空间函数

B\foo();    // 调用命名空间 "A\B" 中函数 "foo"

B::foo();   // 调用命名空间 "A" 中定义的类 "B" 的 "foo" 方法
            // 如果未找到类 "A\B" ，则尝试自动装载类 "A\B"

D::foo();   // 使用导入规则，调用命名空间 "B" 中定义的类 "D" 的 "foo" 方法
            // 如果类 "B\D" 未找到，则尝试自动装载类 "B\D"

\B\foo();   // 调用命名空间 "B" 中的函数 "foo" 

\B::foo();  // 调用全局空间中的类 "B" 的 "foo" 方法
            // 如果类 "B" 未找到，则尝试自动装载类 "B"

// 当前命名空间中的静态方法或函数

A\B::foo();   // 调用命名空间 "A\A" 中定义的类 "B" 的 "foo" 方法
              // 如果类 "A\A\B" 未找到，则尝试自动装载类 "A\A\B"

\A\B::foo();  // 调用命名空间 "A" 中定义的类 "B" 的 "foo" 方法
              // 如果类 "A\B" 未找到，则尝试自动装载类 "A\B"
?>
```
名称解析遵循下列规则：
1. 对完全限定名称的函数，类和常量的调用在编译时解析。例如 new \A\B 解析为类 A\B。
2. 所有的非限定名称和限定名称（非完全限定名称）根据当前的导入规则在编译时进行转换。例如，如果命名空间 A\B\C 被导入为 C，那么对 C\D\e() 的调用就会被转换为 A\B\C\D\e()。
3. 在命名空间内部，所有的没有根据导入规则转换的限定名称均会在其前面加上当前的命名空间名称。例如，在命名空间 A\B 内部调用 C\D\e()，则 C\D\e() 会被转换为 A\B\C\D\e() 。
4. 非限定类名根据当前的导入规则在编译时转换（用全名代替短的导入名称）。例如，如果命名空间 A\B\C 导入为C，则 new C() 被转换为 new A\B\C() 。
5. 在命名空间内部（例如A\B），对非限定名称的函数调用是在运行时解析的。例如对函数 foo() 的调用是这样解析的：
	1. 在当前命名空间中查找名为 A\B\foo() 的函数
	2. 尝试查找并调用 全局(global) 空间中的函数 foo()。
6. 在命名空间（例如A\B）内部对非限定名称或限定名称类（非完全限定名称）的调用是在运行时解析的。下面是调用 new C() 及 new D\E() 的解析过程： new C()的解析:
	1. 在当前命名空间中查找A\B\C类。
	2. 尝试自动装载类A\B\C。
	new D\E()的解析:
	1. 在类名称前面加上当前命名空间名称变成：A\B\D\E，然后查找该类。
	2. 尝试自动装载类 A\B\D\E。
	为了引用全局命名空间中的全局类，必须使用完全限定名称 new \C()。

## 面向对象
在面向对象的程序设计（英语：Object-oriented programming，缩写：OOP）中，对象是一个由信息及对信息进行处理的描述所组成的整体，是对现实世界的抽象。
对象的主要三个特性：
* 对象的行为：可以对 对象施加那些操作，开灯，关灯就是行为。
* 对象的形态：当施加那些方法是对象如何响应，颜色，尺寸，外型。
* 对象的表示：对象的表示就相当于身份证，具体区分在相同的行为与状态下有什么不同。










