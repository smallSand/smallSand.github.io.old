---
layout:  post
title:  "Stack Overflow 上排名前十的与API相关的问题"
date:    2016-08-11
excerpt: "从program greek 翻译 "
categories:  笔记 翻译
comments: true
---

# Stack Overflow 上排名前十的与API相关的问题 #

[原文链接](http://www.programcreek.com/2015/12/top-10-api-related-questions-from-stack-overflow)

Stack Overflow是一个庞大的编程知识仓库,在Stack Overflow 上，数百万的提问被回答，并且这些回答都是高质量的。这就是为什么在Google搜索结果的排行榜上,Stack Overflow 总是位居首位。

虽然Stack Overflow上有非常多的提问，但是仍然每天都有大量的问题被提出，其中的很多都等待解答或者没有得到好的解答。因此，问题是如何找到答案的，通过Stack Overflow是不够的。

随着成千上万的开发者使用Java的API并且在Github上分享他们的项目，这些项目可以提供很多很好的例子来展示如何使用Java的API。[Java API Example](http://www.programcreek.com/java-api-examples/index.php)是一个提供常用Java API代码示例搜索的入口

在这篇文章中，我将会探索只通过开源的代码(jExample)能否解决投票前几名的API相关问题。“API相关的问题”指的是如何通过一些API来解决一个任务的问题。Stack Overflow上投票靠前的问题在[http://stackoverflow.com/questions/tagged/java](http://stackoverflow.com/questions/tagged/java)可以找到

对于每一个问题，最好的回答首先会被展示，随后通过Java API examples(jExample)的解决方案也会图文并茂的展示。


1. Iterate through a HashMap （遍历一个HashMap）


被接受的回答：

    Map<String, Object> map = ...; 
    for (String key : map.keySet()) { 
     // ... 
    }

如果我们在jExample搜索“HashMap”，前往java.util.HashMap示例页面。然后点击其中一个最常用的方法-entrySet()，我们就能快速的如下的示例：

	HashMap<BigInteger,R> subMap = rowie.getValue();
	for( Entry<BigInteger, R> colie : subMap.entrySet() )
	{
		BigInteger col = colie.getKey();
		R vali = colie.getValue();
		ret.setVal(row, col, mutr.mutate( vali ) );
	}

这个例子展示了如何通过使用`HashMap.entrySet(),Entry.getKey()`和`Entry.getValue()`去迭代循环去遍历一个HashMap

Links: [HashMap.entrySet()](http://www.programcreek.com/java-api-examples/index.php?class=java.util.HashMap&method=entrySet)


2.Create ArrayList from array(通过一个数组创建一个ArrayList)

