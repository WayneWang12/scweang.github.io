---
layout: page
title: 一门神奇的语言
time: 2016-01-23 23:01:00
---

###简述

>有人的地方就有江湖；有江湖的地方就有门派。

二十世纪以来，计算机科学的发展大大推动了人类历史进程的发展。从图灵创建图灵机理论，摹绘出计算机的基础蓝图开始，计算机科学的发展真真就是扶摇直上、日新月异。信息技术革命带来生产力的极大解放，也更促进了众多的才智之士投入这股信息化大潮里。从事计算机科学的人才越来越多，做研究的人越来越多，进而门派也越来越多。从最早的计算机基础理论开始，[图灵](https://zh.wikipedia.org/wiki/%E8%89%BE%E4%BC%A6%C2%B7%E5%9B%BE%E7%81%B5)于1936年提出了著名的[图灵机](https://zh.wikipedia.org/wiki/%E5%9B%BE%E7%81%B5%E6%9C%BA)模型，定义了什么样的语言可以被称作是程序语言，从而名垂千史，被尊为计算机科学之父；但其实在同一年的更早的几个月前，他的博士生导师[阿隆佐·邱奇](https://zh.wikipedia.org/wiki/%E9%98%BF%E9%9A%86%E4%BD%90%C2%B7%E9%82%B1%E5%A5%87)在[λ演算](https://zh.wikipedia.org/wiki/%CE%9B%E6%BC%94%E7%AE%97)方面的证明更早地指出了不存在一个对可判断性问题的通用解法。他所创建的λ演算方法，最终被证明和图灵机模型是等价的([邱奇－图灵论题](https://zh.wikipedia.org/wiki/%E9%82%B1%E5%A5%87%EF%BC%8D%E5%9B%BE%E7%81%B5%E8%AE%BA%E9%A2%98))，而且某种程度上来讲甚至也许更好，因为λ演算为后世所有的[函数式编程语言](https://zh.wikipedia.org/wiki/%E5%87%BD%E6%95%B8%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80)提供了理论基础。但是由于图灵的模型更加直观并且易于理解，所以传播得更广泛，也指导了硬件的设计。现代电子计算机其实就是这样一种通用图灵机，它能接受一段描述其他图灵机的程序，并运行程序实现该程序所描述的算法。而λ演算更多地停留在学术界里面，为后来出现的各种函数式编程语言(Lisp、ML、Haskell)提供着养分。

在某篇有趣的博文[编程语言简史(伪)](http://blog.jobbole.com/41073/)里面，就以一种幽默的形式调侃了因之而来的计算机科学里面各种流派的纷争故事（中文翻译版本还加有空格和制表符之争、vim和emacs之争、大括号换行和不换行之争等）。而文章最后的结尾，讲述了这样的一个有趣情景：

>2003 – 一个叫Martin Odersky的醉汉看见了好时瑞森花生酱杯的广告，展示了某个人的花生酱倒入另一个人的巧克力的场景，他忽然有了个点子。他创造了Scala，一种结合了面向对象和函数式编程的语言。这同时激怒了两个阵营的忠实信徒，他们立刻宣布要发动圣战烧死异教徒。

虽然这样的调侃只是图君一乐而已，但是这个也正指出了[Scala](http://www.scala-lang.org/)的一大特色，同时也是Scala官网首页标记出的语言的最大卖点：

>Object-Oriented Meets Functional

那么，当面向对象拥抱函数式编程的时候，到底会擦出什么样的火花呢？

###从圣战说起

Scala将面向对象和函数式编程结合在一起是一个比较重大的创新。当然我不太确定Scala是否是第一门这样做的语言，但是无疑Scala是在这方面的实践做的最好的(需要带之一吗？)。Scala官方宣称的是Have the best of both worlds。而我在使用的时候确实有如此的感受。Scala可以看作是Java的一个超集，如果你对函数式编程没有任何的基础，掌握了Scala的基础使用方法以后，你可以用Scala语言写出等价的Java代码，并且可以享受Scala在语言层面对你的贴心的支持。比如，在Java中写一个打印Hello, world!的程序，你可能需要这样写:

{% highlight java %}
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
{% endhighlight %}

而在Scala里面，则只需要三行：
{% highlight scala %}
object HelloWorld extends App {
    println("Hello, world")
}
{% endhighlight %}








