---
layout:     post
title:      "python digit precision"
date:       2019-07-24 23:00:00 +0000
author:     "cy1c0n9"
header-img: "img/post-bg-2019.jpg"
tags:
    - python
---


### round()

这个是使用最多的，刚看了round()的使用解释，也不是很容易懂。round()不是简单的四舍五入的处理方式。(ROUND_HALF_EVEN)
> For the built-in types supporting round(), values are rounded to the closest multiple of 10 to the power minus ndigits; if two multiples are equally close, rounding is done toward the even choice (so, for example, both round(0.5) and round(-0.5) are 0, and round(1.5) is 2).

    >>> round(2.5)
    3.0
    >>> round(-2.5)
    -3.0
    >>> round(2.675)
    3.0
    >>> round(2.675,2)
    2.67

round()如果只有一个数作为参数，不指定位数的时候，返回的是一个整数，而且是最靠近的整数。一般情况是使用四舍五入的规则，但是碰到舍入的后一位为5的情况，如果要取舍的位数前的数是偶数，则直接舍弃，如果奇数这向上取舍。看下面的示例：

    >>> round(2.555,2)
    2.56
    >>> round(2.565,2)
    2.56
    >>> round(2.575,2)
    2.58
    >>> round(2.585,2)
    2.58

### format
=round()

    >>> a = ("%.2f" % 2.555)
    >>> a
    '2.56'
    >>> a = ("%.2f" % 2.565)
    >>> a
    '2.56'
    >>> a = ("%.2f" % 2.575)
    >>> a
    '2.58'
    >>> a = ("%.2f" % 2.585)
    >>> a
    '2.58'
    >>> a = int(2.5)
    >>> a
    2

### 要求超过17位的精度分析
python默认的是17位精度，当我们的计算需要使用更高的精度（超过17位有效）的时候该怎么做呢？

#### 高精度使用decimal模块，配合getcontext

    >>> from decimal import *
    >>> print(getcontext())
    Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999, capitals=1, clamp=0, flags=[], traps=[InvalidOperation, DivisionByZero, Overflow])
    >>> getcontext().prec = 50
    >>> b = Decimal(1)/Decimal(3)
    >>> b
    Decimal('0.33333333333333333333333333333333333333333333333333')
    >>> c = Decimal(1)/Decimal(7)
    >>> c
    Decimal('0.14285714285714285714285714285714285714285714285714')
    >>> float(c)
    0.14285714285714285

默认的context的精度是28位，可以设置为50位甚至更高。这样在分析复杂的浮点数的时候，可以有更高的自己可以控
制的精度。其实可以留意下context里面的这rounding=ROUND_HALF_EVEN 参数。ROUND_HALF_EVEN， 当half的时候，靠近even.

#### 使用格式化(不推荐)
    >>> a = ("%.30f" % (1.0/3))
    >>> a
    '0.333333333333333314829616256247'

可以显示，但是不准确，后面的数字基本没有意义。

math模块的ceil(x)
取大于或者等于x的最小整数。
math模块的floor(x)
去小于或者等于x的最大整数。

    >>> from math import ceil, floor
    >>> round(2.5)
    2
    >>> ceil(2.5)
    3
    >>> floor(2.5)
    2
    >>> round(2.3)
    2
    >>> ceil(2.3)
    3
    >>> floor(2.3)
    2
