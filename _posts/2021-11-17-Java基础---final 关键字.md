---
layout:     post
title:      final 关键字
subtitle:   基本汇总
date:       2021-11-17
author:     汤键|兔子队列
header-img: https://pic.imgdb.cn/item/65d09b519f345e8d03336264.jpg
catalog: true
tags:
    - Java
---

## **定义：**
- Java中，final 表示最终，也可以称为完结器，表示对象是最终形态的，不可改变的意思

## **用途：**
- 把方法锁定，以防任何继承类修改它的含义
- final 变量，可以安全的在多线程环境下进行共享，而不需要额外的同步开销(只读)
- 提高了性能，JVM 和 Java 应用都会缓存 final 变量
- 效率
  - 在早期的Java实现版本中，会将final方法转为内嵌调用
  - 但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升（现在的Java版本已经不需要使用final方法进行这些优化了）
- final 应用于类、方法和变量时意义是不同的，但本质是一样的，都表示不可改变

## **使用注意事项：**
- final 修饰变量，表示变量的值不可改变，此时该变量可被称为常量
- final 修饰方法，表示方法不能被子类重写
- final 用在类的前面表示该类不能有子类，即该类不可以被继承

## **final 变量**
- final变量，凡是对成员变量或者(在方法中的或者代码块中的变量称为本地变量)声明为 final 的都叫作 final 变量
- final 变量经常和 static 关键字一起使用，作为常量
- 下面是 final 变量的例子：
![](https://pic.imgdb.cn/item/65d0ae3d9f345e8d0386f1e8.png)
- final 变量是只读的

## **final 方法**
- final 声明方法，这个方法不允许在派生类中进一步被覆写（override）
- Java 中非私有的成员方法默认都是虚方法，而虚方法就可以在派生类中被覆写
- 为保证某个类上的某个虚方法不在派生类中被进一步覆写，就需要使用 final 修饰符来声明，让编译器（例如 javac）与 JVM 共同检查并保证这个限制总是成立
- 下面是 final 方法的例子：
![](https://pic.imgdb.cn/item/65d0ae3d9f345e8d0386f29b.png)
- final方法在编译阶段绑定，称为静态绑定(static binding)；提高了调用速度

## **final 类**
- final 修饰的类叫作 final 类，final类通常是功能完整的，不能被继承，Java 中有许多类是 final 的，比如 String，Interger 以及其他包装类
- 当用final修饰一个类时，表明这个类不能被继承
- final类中的所有成员方法都会被隐式地指定为final方法

## **小结**
- final 关键字可以用于修饰成员变量、本地变量、方法以及类
- final 成员变量，必须在声明的时候初始化或者在构造器中初始化，否则报编译错误
- final 变量不能再次赋值；final 方法不能被重写；final 类不能被继承
  - 对于一个final变量，如果是基本数据类型的变量，则其数值一旦在初始化之后便不能更改
  - 如果是引用类型的变量，则在对其初始化之后便不能再让其指向另一个对象，但是它指向的对象的内容是可变的
- 在匿名类中，所有变量都必须是 final 变量
- 接口中，声明的所有变量本身是 final 的
- final 和 abstract 这两个关键字是反相关的，final 类就不可能是 abstract 的
- 声明时未初始化的 final 变量，称为空白 final 变量(blank final variable)，必须在构造器中进行初始化，或者调用 this() 初始化，否则，编译器会报错final变量(变量名)需要进行初始化
- 按照 Java 编码规范，final 变量就是常量，而且通常常量名要大写