---
layout:     post
title:      "std::function<>"
date:       2019-07-19 16:30:00 +0000
author:     "cy1c0n9"
header-img: "img/post-bg-2019.jpg"
tags:
    - c++
---


    static std::function<Layer*()> createFunctions[] = {
        CL(CameraTest1),
        //...
    };                      

其中CL是一个宏，对应如下lambda表达式：

    #define CL(__className__) []( \
        { return __className__::create(); }

这个std::function<Layer*()>是C++11的新特性——可调用对象模板类。
std::function<Layer*()>代表一个可调用对象，接收0个参数，返回Layer*。

至于function的深入理解，还是用代码说明吧。

    #include <iostream>
    #include <map>
    #include <functional>
    using namespace std;
    // 普通函数
    int add(int i, int j) { return i + j; }
    // lambda表达式
    auto mod = [](int i, int j){return i % j; };
    // 函数对象类
    struct divide {
        intoperator() (int denominator, int divisor) {
            returndenominator / divisor;
        }
    };

    ///////////////////////////SubMain//////////////////////////
    int main(int argc, char *argv[]) {
        // 受限的map
        map<char, int(*)(int, int)> binops_limit;
        binops_limit.insert({ '+', add });
        binops_limit.insert({ '%', mod });
        // 错误 1 error C2664: “void std::_Tree<std::_Tmap_traits<_Kty,_Ty,_Pr,_Alloc,false>>::
        // insert(std::initializer_list<std::pair<const _Kty,_Ty>>)”:
        //  无法将参数 1 从“initializer-list”转换为“std::pair<const _Kty,_Ty>&&”

        // binops_limit.insert({ '%', divide() });
        // 灵活的map
        map<char, function<int(int, int)>> binops = {
            { '+', add },
            { '-', minus<int>() },
            { '*', [](int i, int j){return i - j; } },
            { '/', divide() },
            { '%', mod },
        };
        cout << binops['+'](10, 5) << endl;
        cout << binops['-'](10, 5) << endl;
        cout << binops['*'](10, 5) << endl;
        cout << binops['/'](10, 5) << endl;
        cout << binops['%'](10, 5) << endl;
        system("pause");
        return 0;
    }
    ///////////////////////////End Sub//////////////////////////

如上所示，function可以将普通函数，lambda表达式和函数对象类统一起来。它们并不是相同的类型，然而通过function模板类，可以转化为相同类型的对象（function对象），从而放入一个map里。

在VS2013编译器下，上述代码可以通过,《C++ Primer》第512页第一行所言“错误：mod不是一个函数指针”并没有发生错误，有可能是对C++11标准的不同实现吧。
