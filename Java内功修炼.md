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