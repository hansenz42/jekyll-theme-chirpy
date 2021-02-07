---
layout: post
title: 教你识别“神逻辑”——三段论逻辑中的常见错误
date: 2019-6-18
categories:
- 读书笔记
tags:
- 三段论
- 逻辑
---

# 引用申明

本文中引用了《形式逻辑——第五版》（华东师范大学哲学系逻辑学教研室著，华东师范大学出版社）中的一部分定义和概念。引用内容会在文章中注明。

# 开始

在开始前，我先问你个问题。
你觉得这段话符合逻辑吗？

> 出国需要学好英语，我不出国，所以我不需要学好英语。

是不是听起来很耳熟？也许你我的学生时代跟父母吵架时都说过这样的话。

但是，这段话究竟符合逻辑吗？

# 逻辑学中的几个定义

在介绍三段论之前，我们现在需要阐明等会儿会用到的几个逻辑学中定义：
* 命题
* 特称命题和全称命题
* 概念
* 概念的内涵和外延
* 概念的周延性 

## 命题
首先是命题，命题的定义是：
> 命题是判断的语言表达，即是表达判断的语句。 （来自《形式逻辑》）

一个命题必须要表达一个判断，所以在之前的例子中，“出国需要学好英语”、“我不出国”和“我不需要学好英语”都表达了判断，所以他们都是命题。

## 特称命题和全称命题
命题又分许多种，但为了我们更好的了解三段论，我们只需要了解特称命题和全称命题。
> 特称命题是断定某类事物中**有**对象具有（或不具有）某种性质的命题。（来自《形式逻辑》）

例如：“有的公司是有限责任制公司”
特称命题中往往包含“有的”，“有些”，“一部分”，“大多数”，“小部分” 这类词

> 全称命题是断定某类事物中的**每一个**对象都具有（或不具有）某种性质的命题。（来自《形式逻辑》）

例如：“所有程序猿都头发稀疏”（哈哈哈哈）
全称命题中往往包含“所有”，“全部”这类词。

## 概念
概念比较好理解，所以这里只写出概念在逻辑学上的定义
> 概念是通过揭示对象的特性或本质来反映对象的一种思维形式。（来自《形式逻辑》）

例如，“京巴犬”就是一个概念，它反映了一种很可爱的狗的种类。

## 概念的内涵和外延
> 概念的**内涵**是指反映在概念中事物的**特性或本质**。（来自《形式逻辑》）

我们举“商品”这个概念作为例子。“商品”的内涵可以是“是一种用于满足购买者欲望和需求的产品同时提供效用的物品”，它表示的是成为“商品”的**条件**。

> 概念的**外延**是指反映在概念中的**一个个、一类类的事物**。（来自《形式逻辑》）

而“商品”的外延可以是在商店中售卖的任何东西，一台电视机，一件衣服或者一瓶酒，它通常表示的是成为“商品”的**对象**。

## 概念的周延性
周延性是个相对复杂的概念，在这里，你只需要知道：
> 在命题中，如果对一个概念的全部外延都做了断定，那么这个概念就是周延的。

上面这句话是我总结的，不是《形式逻辑》这本书中的原话。

举个栗子：

对于命题
> 所有的程序猿都头发稀疏

在这个命题中，我们能知道“程序猿”的外延被全部断定了，因为“所有的”这个词告诉我们需要把所有的程序猿都囊括其中。所以，“程序猿”这个概念在这个命题中是**周延**的。

相反地，“头发稀疏”这个概念的外延没有被全部断定，因为从这个命题中我们只能知道程序猿都头发稀疏，但是也可能有别的人“头发稀疏”，例如建筑设计师或者硬件工程师（随便举例的，工程师设计师同学们别打我……）。所以，“头发稀疏”这个概念在这个命题中是**不周延**的。

我们先后了解了：命题，特称和全称命题，概念，概念的内涵和外延，概念的周延性。现在，我们有足够的知识储备，可以一起来认识三段论了。

# 什么是三段论？

> 三段论是由三个直言命题所组成的，前两个命题是推理的前提，后一个命题是推理的结论。（来自《形式逻辑》）

所以，在最开始的关于出国学英语的推理就是一个典型的三段论。现在，我们来分析一下它的结构。

## 三段论的结构

> 出国需要学好英语，我不出国，所以我不需要学好英语。

在这里我们有三个命题：
* 命题1: “出国需要学好英语”，我们称之为“**大前提**”
* 命题2: “我不出国”，我们称之为“**小前提**”
* 命题3: “我不需要学好英语”，我们称之为“**结论**”

结论中的主语（我）称为“**小项**”，结论中的谓语（学好英语）称为“**大项**”，在结论中不出现，而在大小前提中都出现的名词（这里隐含了名词：“出国的人”）称为“**中项**”。

中项在三段论中起到连接大小项的作用。

## “神逻辑”——三段论的规则与常见错误

三段论的成立是有要求的，如果违反了这些要求，那么这个三段论就会变成“神逻辑”。现在是让我们进入重点环节的时候了，让我们来看看三段论的规则有哪些。

### 规则一：一个三段论中，只能有三个不同的概念

也就是说一个三段论中只能存在大项，小项和中项，不能存在第四个概念，如果存在，那么这个三段论就犯了“**四概念**”错误。

让我们来看第一个“神逻辑”：

> 人是自然选择中生存下来的物种，我是人，所以我是自然选择中生存下来的物种。

大前提中的“人”泛指全人类，逻辑学上叫“**集合概念**”，而小前提中的“人”指“某一个人”，是一个一般的普通概念。虽然都称为“人”，但是指的却是两个意思。

所以，这个三段论中除了“我”和“自然选择中生存下来的物种”之外还有两个概念，是四概念错误。

### 规则二：中项在前提中必须至少周延一次

中项在三段论中分别在大前提中和小前提中出现，如果中项在两个前提中都不周延，就犯了“**中项不周延**”的错误。

第二个“神逻辑”：

> 世界500强公司是大公司，微软是大公司，所以微软是世界500强公司。

虽然结论是正确的，但是这个三段论的推理形式却是错的。“大公司”这个概念作为中项，在大前提中不周延，在小前提中也不周延，所以不能推出任何结论。

### 规则三：如果大项和小项在前提中不周延，那么在结论中也不得周延

如果违反了这条规则，就会犯“大项不当扩大”或者“小项不当扩大”的错误

第三个“神逻辑”：

> 你说甲生疮。甲是中国人，你就是说中国人生疮了。（鲁迅《华盖集》）

在这里，“中国人”作为小项，在小前提中不周延，但是在结论中却周延，所以这里是“小项不当扩大”。

### 规则四：两个否定前提推不出结论，前提之一否定的，结论必否定，结论否定的，前提之一必否定

这条规则说明了前提中的否定命题是如何影响结论的否定的。

第四个“神逻辑”：

> 纯电动汽车不烧汽油，大众POLO不是纯电动车，所以大众POLO不烧汽油。

这里大前提是否定的，小前提也是否定的，所以推不出任何结论。关于另一条规则，前提之一是否定的，这里就不举例了。

### 规则五：两个特称前提推不出结论，前提之一是特称的，结论必特称

这条规则说明了前提中的特称命题和结论是特称还是全称的关系。

第五个“神逻辑”：

> 我有些朋友会吉他，有些会吉他的人也会钢琴，所以我有些朋友会钢琴。

大前提是特称命题，小前提也是特称命题，这两个命题推不出任何结论。如果前提之一是特称的情况，就不举例了，相信你能够随便举出一个来。

# 后记

现在你应该在生活中能够识别一些听起来很对，但是其实根本不合逻辑的错误了。现在，你能告诉我文章开头“出国学英语”的推理是犯了哪个逻辑错误吗？

我是“得到”app中《刘润五分钟商学院》的订阅用户。有一天，我听到了一讲关于逻辑三段论的一课，觉得很有意思，于是去阅读了专栏推荐的书《形式逻辑》。

《形式逻辑》是本大学教材，本身枯燥乏味，但是对于像初步了解逻辑学的我来说非常有帮助。如果你也有兴趣，也推荐给你，我们一起学习。

**愿世界在你眼前更清澈！**

# 如需转载

本文原创，非商业转载注明本文出处和作者Hansen Zheng，未经许可不得商业转载，谢谢。

本作品采用知识共享 署名-非商业性使用-禁止演绎 2.5 中国大陆 许可协议进行许可。要查看该许可协议，可访问 http://creativecommons.org/licenses/by-nc-nd/2.5/cn/ 或者写信到 Creative Commons, PO Box 1866, Mountain View, CA 94042, USA。