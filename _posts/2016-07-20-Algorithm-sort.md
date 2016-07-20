---
layout: post
title:  "排序算法"
date:   2016-07-20
excerpt: "记录排序算法和对应的java实现"
categories:  算法  笔记
comments: true
---

# 冒泡排序（bubble）

冒泡排序（Bubble Sort），是一种计算机科学领域的较简单的排序算法。

它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。

这个算法的名字由来是因为越大的元素会经由交换慢慢“浮”到数列的顶端，故名。

![](http://smallsand.github.io/image/201111301912294589.gif)

## 算法原理

冒泡排序算法的运作如下：（从后往前）

1.比较相邻的元素。如果第一个比第二个大，就交换他们两个。

2.对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。

3.针对所有的元素重复以上的步骤，除了最后一个。

4.持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

## java实现

{% highlight java %}
public class BubbleSort
{
    public void sort(int[] a)
    {
        int temp = 0;
        for (int i = a.length - 1; i > 0; --i)
        {
            for (int j = 0; j < i; ++j)
            {
                if (a[j + 1] < a[j])
                {
                    temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            }
        }
    }
}
{% endhighlight %}