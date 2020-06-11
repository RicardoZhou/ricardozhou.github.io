---
title: Swoole框架
categories: 笔记
tags: php
---
[Swoole框架文档中心](https://wiki.swoole.com/wiki/index/prid-1)
## Coroutine
从<code>4.0</code>版本开始Swoole提供了完整的**协程（Coroutine）+ 通道（Channel）**特性，带来全新的<code>CSP</code>编程模型。应用层可使用完全同步的编程方式，底层自动实现异步<code>IO</code>。
```php
go(function () {
    $redis = new Swoole\Coroutine\Redis();
    $redis->connect('127.0.0.1', 6379);
    $val = $redis->get('key');
});
```
><code>4.0.0</code>或更高版本仅支持PHP7
><code>4.0.1</code>版本开始去除了--enable-coroutine编译选项，改为动态配置
协程可以理解为纯用户态的线程，其通过**协作**而不是抢占来进行切换。相对于进程或者线程，协程所有的操作都可以在用户态完成，创建和切换的消耗更低。<code>Swoole</code>可以为每一个请求创建对应的协程，根据<code>IO</code>的状态来合理的调度协程，这会带来了以下优势：
1. 开发者可以无感知的用同步的代码编写方式达到异步IO的效果和性能，避免了传统异步回调所带来的离散的代码逻辑和陷入多层回调中导致代码无法维护。
2. 同时由于底层封装了协程，所以对比传统的<code>PHP</code>层协程框架，开发者不需要使用<code>yield</code>关键词来标识一个协程<code>IO</code>操作，所以不再需要对<code>yield</code>的语义进行深入理解以及对每一级的调用都修改为<code>yield</code>，这极大的提高了开发效率。

可以满足大部分开发者的需求。对于私有协议，开发者可以使用协程的TCP或者UDP接口去方便的封装。





