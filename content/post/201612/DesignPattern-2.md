---
title: 设计模式（2）：创建型模式
date: 2016-12-11 19:08:01
tags:
  - 笔记
  - 设计模式
categories:
  - 笔记
---

创建型模式实例化了过程。

设计模式中两个不断出现的主旋律：

1. 它们都将关于该系统使用哪些具体的类的信息封装起来
2. 隐藏了这些类的实例是如何被创建和放在一起的

整个系统关于这些对象所知道的是由抽象类所定义的接口

## Abstract Factory（抽象工厂）——对象创建型模式

提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类。

适用：

- 一个系统要独立于它是产品创建、组合和表示时
- 一个系统要由多个产品系列中的一个来配置时
- 当你要强调一系列相关的产品对象的设计以便进行联合适用时
- 提供一个产品类库，而只想显示它们的接口而不是实现时

优缺点：

1. 分离了具体的类
2. 使得易于交换产品系列
3. 有利于产品的一致性
4. 难以支持新种类的产品

一些实现：

1. 将工厂作为单件
2. 创建产品
3. 定义可扩展的工厂

一个具体的工厂通常是一个单件的

## Builder（生成器）——对象创建模型模式

将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。

每一个转换器类创建和装配一个复杂对象的机制隐含在抽象接口的后面。

适用：

- 当创建复杂对象的算法应该独立于该对象的组成部分以及它们的装配方式时
- 当构造过程必须运行被构造的对象有不同表示时

效果：

1. 它使你可以改变一个产品的内部表示
2. 它将构造代码和表示代码分开
3. 它使你对构造过程进行更精细的控制

Builder模式着重于一步步构造一个复杂对象。而Factory Method着重于多个系列的产品对象。Builder在最后一步返回厂品，而对于Abstract Factory来说，产品是立即返回的。

## Factory Method（工厂方法）——对象创建型模式

定义一个用于创建对象的接口，让子类决定实例化哪一个类。

适用：

- 当一个类不知道它所必须创建的对象的类的时候、
- 当一个类希望由它的子类来指定它所创建的对象的时候
- 当类将创建对象的职责委托给多个帮助子类的某一个，并且你希望将哪一个帮助子类是代理者这一信息局部化的时候

效果：

1. 为子类提供挂钩
2. 连接评选的类层次

实现：

1. 主要两种不同的情况
   1. 是一个抽象类并且不提供它所声明的工厂方法的实现
   2. 是一个具体类而且为工厂方法提供一个缺省的实现
2. 参数化工厂方法
3. 特定语言的变化和问题
4. 使用模板以避免创建子类

## Prototype（原型）——对象创建型模式

用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。

当一个系统应该独立于它的产品创建、构成和表示时，要用Prototype模式或

- 当要实例化的类是在运行时刻指定时
- 为了避免创建一个与产品类层次平行的工厂类层次时
- 当一个类的实例只能与几个不同状态组合中的一种时

优点：

1. 运行时刻增加和删除产品
2. 改变值以指定新对象
3. 改变结构以指定新对象
4. 减少子类构造
5. 用类动态配置应用

考虑的问题：

1. 使用一个原型管理器
2. 实现克隆操作
3. 初始化克隆对象

## Singleton（单件）——对象创建型模式

保证一个类仅有一个实例，并提供一个访问它的全局访问点。

一个全局变量使得一个对象可以被访问，但它不能防止你实例化多个对象。一个更好的办法是让类自身负责保存它的唯一实例。

适用：

- 当类只能有一个实例而且客户可以从一个众所周知的访问点访问它时
- 当这个唯一实例应该是通过子类化可扩展的，并且客户应该无需更改代码就能使用一个扩展的实例时

优点：

1. 对唯一实例的受控访问
2. 缩小名空间
3. 允许对操作和表示的精化
4. 允许可变数目的实例
5. 比类操作更灵活

问题：

1. 保证一个唯一实例
2. 创建类的子类