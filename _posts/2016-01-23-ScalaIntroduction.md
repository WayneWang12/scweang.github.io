---
layout: page
title: 一门神奇的语言(上)
time: 2016-01-23 23:01:00
---

###简述

>有人的地方就有江湖；有江湖的地方就有门派。

二十世纪以来，计算机科学的发展大大推动了人类历史进程的发展。从图灵创建图灵机理论，摹绘出计算机的基础蓝图开始，计算机科学的发展真真就是扶摇直上、日新月异。信息技术革命带来生产力的极大解放，也更促进了众多的才智之士投入这股信息化大潮里。从事计算机科学的人才越来越多，做研究的人越来越多，进而门派也越来越多。从最早的计算机基础理论开始，[图灵](https://zh.wikipedia.org/wiki/%E8%89%BE%E4%BC%A6%C2%B7%E5%9B%BE%E7%81%B5)于1936年提出了著名的[图灵机](https://zh.wikipedia.org/wiki/%E5%9B%BE%E7%81%B5%E6%9C%BA)模型，从而名垂千史，被尊为计算机科学之父；但其实在同一年的更早的几个月前，他的博士生导师[阿隆佐·邱奇](https://zh.wikipedia.org/wiki/%E9%98%BF%E9%9A%86%E4%BD%90%C2%B7%E9%82%B1%E5%A5%87)在[λ演算](https://zh.wikipedia.org/wiki/%CE%9B%E6%BC%94%E7%AE%97)方面的证明更早地指出了不存在一个对可判断性问题的通用解法。他所创建的λ演算方法，最终被证明和图灵机模型是等价的([邱奇－图灵论题](https://zh.wikipedia.org/wiki/%E9%82%B1%E5%A5%87%EF%BC%8D%E5%9B%BE%E7%81%B5%E8%AE%BA%E9%A2%98))，而且某种程度上来讲甚至也许更好，因为λ演算为后世所有的[函数式编程语言](https://zh.wikipedia.org/wiki/%E5%87%BD%E6%95%B8%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80)提供了理论基础。但是由于图灵的模型更加直观并且易于理解，所以传播得更广泛，也指导了硬件的设计。现代电子计算机其实就是这样一种通用图灵机，它能接受一段描述其他图灵机的程序，并运行程序实现该程序所描述的算法。而λ演算更多地停留在学术界里面，为后来出现的各种函数式编程语言(Lisp、ML、Haskell)提供着养分。

在某篇有趣的博文[编程语言简史(伪)](http://blog.jobbole.com/41073/)里面，就以一种幽默的形式调侃了因之而来的计算机科学里面各种流派的纷争故事（中文翻译版本还加有空格和制表符之争、vim和emacs之争、大括号换行和不换行之争等）。而文章最后的结尾，讲述了这样的一个有趣情景：

>2003 – 一个叫Martin Odersky的醉汉看见了好时瑞森花生酱杯的广告，展示了某个人的花生酱倒入另一个人的巧克力的场景，他忽然有了个点子。他创造了Scala，一种结合了面向对象和函数式编程的语言。这同时激怒了两个阵营的忠实信徒，他们立刻宣布要发动圣战烧死异教徒。

虽然这样的调侃只是图君一乐而已，但是这个也正指出了[Scala](http://www.scala-lang.org/)的一大特色，同时也是Scala官网首页标记出的语言的最大卖点：

>Object-Oriented Meets Functional

那么，当面向对象拥抱函数式编程的时候，到底会擦出什么样的火花呢？

###从圣战说起

Scala将面向对象和函数式编程结合在一起是一个比较重大的创新。当然我不太确定Scala是否是第一门这样做的语言，但是无疑Scala是在这方面的实践做的最好的(需要带之一吗？)。Scala官方宣称的是Have the best of both worlds。而我在使用的时候确实有如此的感受。Scala可以看作是Java的一个超集，如果你对函数式编程没有任何的基础，掌握了Scala的基础语法以后，你可以用Scala语言写出等价的Java代码，并且可以享受Scala在语言层面对你的贴心的支持。比如，在Java中写一个打印Hello, world!的程序，你可能需要这样写:

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

Java里面定义一个字符串变量：
{% highlight java %}
String s = "Hello, world!"
{% endhighlight %}
而Scala则是
{% highlight scala %}
val s:String = "Hello, world!"
{% endhighlight %}
或者
{% highlight scala %}
var s:String = "Hello, world!"
{% endhighlight %}
看起来好像是Java里面的更加简洁，字符更少，但是Scala自带的类型推断可以帮助我们不需要显式地写出数据类型。也就是说，这样的定义，只需要一句`val s = "Hello, world!"`或者`var s = "Hello, world!"`就搞定。这其中，`val`和`var` 只是代表`s`是否是可变的。`val s = "Hello, world!"`基本等价于Java里面的`final String s = "Hello, world!"`。`val`这个关键字可以帮助编译器做出许多的代码优化。函数式编程里面强调的一个重点就是 **不可变性**。当不需要变化的变量用`val`声明的时候，编译器会做出一些主动的优化，来增加多线程环境下的执行效率。当然，如果你来自“面向对象圣教”的话，你可以完全不理会`val`。一切都使用`var`，然后利用Scala提供的一些语法糖来帮助你写面向对象的代码。例如我同事在做Java开发的时候嫉妒很久的来自Scala的`case class`语法。

假设有一个对象，这个对象被称作是Customer。一个Customer会有一个ID、名称、年龄、邮箱、手机号、地址等等字段。在Java里面，我们可能需要定义如下的一个值类：
{% highlight java %}
public class Customer {
    //手写所有字段
    private Long ID;
    private String name;
    private int age;
    private String emailAddress;
    private String phoneNumber;
    private String address;

    //借助IDE生成getter和setter
    public Long getID() {
        return ID;
    }

    public void setID(Long ID) {
        this.ID = ID;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getEmailAddress() {
        return emailAddress;
    }

    public void setEmailAddress(String emailAddress) {
        this.emailAddress = emailAddress;
    }

    public String getPhoneNumber() {
        return phoneNumber;
    }

    public void setPhoneNumber(String phoneNumber) {
        this.phoneNumber = phoneNumber;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }
}
{% endhighlight %}

然后为了相等性判断，我们可能还需要重写equals方法和hashcode方法：
{% highlight java %}
    //借助IDE重写equals和hashCode方法
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        Customer customer = (Customer) o;

        if (age != customer.age) return false;
        if (!ID.equals(customer.ID)) return false;
        if (!name.equals(customer.name)) return false;
        if (emailAddress != null ? !emailAddress.equals(customer.emailAddress) : customer.emailAddress != null)
            return false;
        if (phoneNumber != null ? !phoneNumber.equals(customer.phoneNumber) : customer.phoneNumber != null)
            return false;
        return address != null ? address.equals(customer.address) : customer.address == null;

    }

    @Override
    public int hashCode() {
        int result = ID.hashCode();
        result = 31 * result + name.hashCode();
        result = 31 * result + age;
        result = 31 * result + (emailAddress != null ? emailAddress.hashCode() : 0);
        result = 31 * result + (phoneNumber != null ? phoneNumber.hashCode() : 0);
        result = 31 * result + (address != null ? address.hashCode() : 0);
        return result;
    }
{% endhighlight %}

然后为了序列化和反序列化，我们可能还需要Customer实现`Serializable`接口；然后为了创建Customer对象，我们还得写相应的构造器；为了提供更好的阅读性，还要重写`toString`方法……

天哪，为了遵循《Effective Java》上面的指导写出更好的代码，得记得多少东西！做多少事情啊！

当然，以上代码大部分可以由IDE自动生成。可是即便如此，一个普通的值类就需要这么多行代码来支持，不得不说是一个严重阻碍编程趣味性的问题。那么，对于这样的问题，Scala提出了什么样的解决办法呢？那就是样例类，`case class`：

{% highlight scala %}
case class Customer(ID: Long, name: String, age: Int, emailAddress: String, phoneNumber: String, address: String)
{% endhighlight %}

这就是我那个了解过Scala而最近又在做Java项目的同事最垂涎欲滴的Scala特性。一个样例类，就解决了所有的getter和setter，equals和hashCode，序列化和反序列化、构造器、toString方法，也仍然保持了良好的封装性。大体上来说，一行就能基本解决值类相关的所有问题。而为了对象特性而做的封装，也可以通过很简洁方便的方式来达成。更何况Scala还有强大的`trait`来扩展对象的接口和行为，还有更加强大的模式匹配（[pattern matching](https://en.wikipedia.org/wiki/Pattern_matching))来解构对象，获取对象的内容。trait和pattern matching后来都会有单独的博文来讲解，而这两个特性都是来源于Scala强大的类型系统的支持。

所以，来自面向对象领域的小伙伴们，你们可以尽情地按照面向对象的用法来使用Scala，并且享受Scala在语言层面提供的针对面向对象编程的帮助和便利。Martin Odersky可能是世界上写过Java代码最多的人了（写了Java泛型和现代版本的Javac），他深刻地了解Java，并且知道Java的优点和缺点，了解利用Java编程时的痛点在哪里。所以他的Scala为了解决这些问题提供了众多的来自语言层面上面的便利，帮助程序员从琐细中解脱，能够花更多的时间专注于自己的代码的逻辑，而不是繁琐、枯燥而又不得不处理的样板代码。因此Scala对Java程序员来讲，具有一种天然的吸引力（我就是没做多久Java然后了解了Scala以后就打死不写Java的那种……）。没必要纠结于Scala的学习成本，没必要去理会函数式编程的那部分。如果你现在想尝试一下Scala，直接用就行。就只是把它当成更好的Java，就只是把它当作那个可以帮助你写更少代码的在语言层面上做出支持的IDE。上手写习惯以后，你会发现，Scala，用起来真是爽！

然后，“面向对象圣教”真的不需要对Scala做出圣战。为什么呢？因为Scala的每一个函数，都是对象……

###函数皆对象



