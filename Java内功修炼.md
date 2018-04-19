---
title: Java内功修炼 
tags: Java,基础
grammar_cjkRuby: true
---
1. 定义一个类那些修饰符是允许被使用的？
* ==普通类（外部类）==：只能用public、default（不写）、abstract、final修饰。
* ==（成员）内部类==：可理解为外部类的成员，所以修饰类成员的public、protected、default、private、static等关键字都能使用。
* ==局部内部类==：出现在方法里的类，不能用上述关键词来修饰。
* ==匿名内部类==：给的是直接实现，类名都没有，没有修饰符。
2. 关于Java异常处理？
* throws用于在方法上声明该方法不需要处理的异常类型,用在方法上后面跟异常类名 可以是多个异常类
 * throw用于抛出具体异常类的对象,用在方法内 后面跟异常对象只能是一个异常类型实体.
 * try块必须和catch块或和finally同在,不能单独存在,二者必须出现一个
 *  finally块总会执行,不论是否有错误出现.但是若try语句块或会执行的
 *   catch语句块使用了JVM系统退出语句,finally块就不会被执行了. 一般我们把关闭资源的代码放在finally里面 保证资源总是能关闭