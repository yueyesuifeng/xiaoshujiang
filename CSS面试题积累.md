---
title: CSS面试题积累
tags: cdd,匠心攻城,小书匠
grammar_cjkRuby: true
---
### 成功没有奇迹，唯有积累
#### 关于BFC，以下说法错误的是？
A. 能够清除浮动元素带来的布局塌陷
B. 浮动元素不会超出它的范围
C. 相邻元素外边距合并
D. dispaly:table-caption能触发BFC
排除的话：正确答案应该是C
BFC(Block Formatting Contexts)即块级格式化上下文，从样式上看，它与普通的容器没有什么区别，但是功能上，BFC可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且BFC具有普通容器没有的一些特性。
Formatting context是指页面中的一块渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。
最常见的Formatting cocntext 有Block formatting context（简称BFC）和Inline formatting (简称IFC).
如何触发BFC即触发BFC的条件是什么？
1. 浮动元素，float除none以外的值
2. 绝对定位元素，position（absolute，fixed）
3. display为以下其中之一的值inline-blocks,table-cells,table-captions
4. overflow除了visible以外的值（hidden,auto,scroll）
BFC主要有三个特性：
1. BFC会阻止外边距折叠
2. BFC可以包含浮动的元素
3. BFC可以阻止元素被浮动元素覆盖
注意：这里只是浅显的理解，更深层次的理解，可以知乎搜索BFC
