---
layout:     post
title:      "如何定义一个只能在堆上（栈上）生成对象的类"
subtitle:   " \"From online test\""
date:       2019-07-19 16:15:00 +0000
author:     "cy1c0n9"
header-img: "img/post-bg-2019.jpg"
tags:
    - c++
---

## 只能在堆上

#### 方法：
将析构函数设置为私有

#### 原因：
C++ 是静态绑定语言，编译器管理栈上对象的生命周期，编译器在为类对象分配栈空间时，会先检查类的析构函数的访问性。若析构函数不可访问，则不能在栈上创建对象。

## 只能在栈上

#### 方法：
将 new 和 delete 重载为私有

#### 原因：
在堆上生成对象，使用 new 关键词操作，其过程分为两阶段：第一阶段，使用 new 在堆上寻找可用内存，分配给对象；第二阶段，调用构造函数生成对象。将 new 操作设置为私有，那么第一阶段就无法完成，就不能够在堆上生成对象。



## C++中类的对象如何建立？
1. 静态建立

        class A{
        ...
        };
        A a;
    静态建立一个类的对象，编译器为该对象在栈中分配内存，通过直接移动栈顶指针，挪出适当空间；然后调用类的构造函数形成一个栈上的对象。

    **注意：直接调用类的构造函数。当销毁对象时，调用类的析构函数。**

2. 动态建立

    动态建立类对象，使用new运算符将对象简历在堆空间中。

        class A{
            ...
        };

        A *ptr = new A();
        A *ptr = new A;

    首先执行operator new()函数，在堆中找到合适空间分配；然后调用构造函数初始化。
    **注意：间接调用类的构造函数。**

3. 只能在堆上

    要求类对象只能建在堆上，就是说用户不能调用类的构造函数。将构造函数设为私有？

        class B {
        private:
            B() {}
        public:
            ~B() {}
        };
        //error！B::B()不可访问
        B * p2 = new B;
    new无法创建对象.

    继续分析：将对象建立在栈上时，编译器管理该对象的整个生命周期。编译器为类对象分配空间时，会先检查类的析构函数的访问性。如果编译器无法调用析构函数则不会再栈上分配空间。

        class C {      
        public:
            C() {}
        private:
            ~C() {}
        };
        // on heap ok
        C * p3 = new C;
        // on stack error!
        C c;

    既然构造函数不能设为私有，将析构函数设为私有，然后用new调用构造函数在堆上分配，就可以达到禁止用户在栈上创建对象的目的。

    既然是在堆上，程序员控制对象的生命周期。显示调用new，显示调用delete。

        class C {
        public:
            C() {}
                void destory() { delete this; }
        private:
            ~C() {}
        };

    还是有不满意的地方。比如继承。A若作为基类，析构函数通常声明为虚函数，子类重写，实现多态。因此析构函数可以设置为protected，用户无法访问，子类可以访问。

    比较考虑周全的如下示：

        class A {

        protected:
            A() { cout << "constructor" << endl; }
            ~A() { cout << "destructor" << endl; }
        public:
            static A * create() {
                return new A();
            }
            void destory() {
                delete this;
            }
        };

        A * p1 = A::create();
        cout << &(*p1) << endl;
        p1->destory();

4. 只能在栈上

    只有使用new运算符，对象才会建在堆上。因此用户禁用new就可以实现。将operator new()重载设为私有即可。如下：

        class D {
        private:
            void *operator new(size_t) {}
            void operator delete(void * ptr) {}
        public:
            D() {}
            ~D() {}
        };

        // error：函数不可访问
        D * p4 = new D;
