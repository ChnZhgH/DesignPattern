# 设计模式简介

## 写在前面
* 直接看设计模式的原则比较抽象，可以先看一下，有个概念，然后结合具体例子来理解
* 以下简单介绍一下五个设计原则(以下引用来自维基百科)

## 单一原则  
> 规定每个类都应该有一个单一的功能，并且该功能应该由这个类完全封装起来。
<br>所有它的（这个类的）服务都应该严密的和该功能平行（功能平行，意味着没有依赖）。
 
* 即：一个类只做一件事情
* 我认为这个原则是最最最重要的一个原则，说起来也是最简单的，但是做起来却不容易
* 我将会在后续讲解设计模式的过程中
    * 通过一些具体的例子，讲代码怎么写才算职责单一，
    <br>也就是我代码能写A样子，也能写成B样子，为什么我要写成A，而不写成B
    * 类/方法的职责单一了，有什么好处？

## 开放封闭原则
> 软件中的对象（类，模块，函数等等）应该对于扩展是开放的，但是对于修改是封闭的 

* 即：对扩展开放，对修改关闭
* 开放封闭原则是说，当我们需求产生变动，或者需要增加新功能时，如果之前的代码写的好，那么我只需要添加新的部分，而无需改动原有代码
* 比如：一个计算器，当我要增加一个指数操作时，我无需修改既有代码，添加一个指数操作类即可，甚至连case判断运算类型都不需要

## 依赖反转原则
> 1.高层次的模块不应该依赖于低层次的模块，两者都应该依赖于抽象接口。
<br>2.抽象接口不应该依赖于具体实现。而具体实现则应该依赖于抽象接口。

* 抽象不应该依赖细节，细节应该依赖抽象。就是要针对接口编程，不要对实现编程

* 高层模块不应该依赖底层模块，两者都应该依赖抽象，就是高层模块不应该由底层模块，
比如直接依赖某数据库什么的，如果依赖了，高层的复用性就没有了，比如现在要高层的结构，但是想把数据库换了，
所以无论是高层还低层，都应该依赖于接口编程
		
* 例子(仅用于帮助理解)：电脑主板为高层，显卡，内存，CPU等为底层，底层是面对接口的，只要插针规格满足，
遵循接口规定，内存不同牌子随便换，高层也是面对接口的，主板换了，不影响底层的使用
		
* 面向接口编程应用：web开发用service层一般都是service接口及serviceImpl，
<br>service接口决定我对外提供哪些服务，serviceImpl为具体实现，
<br>所以针对一个service我们可以有多个实现类，配合Spring的Resource我们可以具体制定使用哪个实现类进行注入

## 里氏替换原则

> 派生类（子类）对象可以在程式中代替其基类（超类）对象

* 如何保证里氏替换(仅帮助理解)：
    * 比如抽象类鸟，有抽象方法—飞，那么企鹅属于鸟吗？现实生活中企鹅是属于鸟的，但是企鹅不具有飞的能力，
		所以企鹅不能继承鸟，所以编程中，企鹅不属于鸟，因为企鹅无法替换鸟

## 迪米特法则(得墨忒耳定律-Law of Demeter)

> 亦称最少知识原则（Principle of Least Knowledge）
> 如果两个类不必彼此直接通信，那么这两个类就不应当发生直接对相互作用。
<br>如果其中一个类需要调用另一个类的某一个方法的话，可以通过第三者去转发这个调用

* 通过一个例子来理解：
比如一个公司中，电脑坏了要找人修，要找IT部，这时候会出现几种不理想情况：
<br>去找IT部的小李修，去找IT部的小王修;去找IT部的主管，让主管分配部员修
<br>    a.首先他们中任何一个人都可能在忙
<br>    b.其次，这其实违背了迪米特原则，部门之间的成员不必要直接发生作用
<br>    c.再有，这其实违背了依赖反转原则，不管是主管还是成员，都应该面向接口编程，当我电脑坏的时候，去找IT部，而不是去找具体的人

* 所以迪米特原则强调的是低耦合，这样复用性也将更强

