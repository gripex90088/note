##### 函数指针

```cpp
#include <iostream>
#include <vector>

using namespace std;

typedef int (*pf)(int *, int);

typedef bool (*pfunc) (const string &, const string &);


bool funcPointerTest(bool (*funcTest) (const string &, const string &))
//bool funcPointerTest(pfunc funcTest)
{
    funcTest("Hello ", "World");
    return false;
}

bool func(const string &a, const string &b)
{
    cout << a << b << endl;
    return false;
}

bool lengthCompare(const string &s1, const string &s2)
{
    return s1.size() == s2.size();
}

int demo(int *p, int a)
{
    return 112;
}

/*  ff函数，　有一个形参x,
 * 　返回结果为一个函数指针　int(*)(int *, int) */
pf ff(int x)  /* 简化版　*/
//int ( *ff(int x) ) (int *, int)
{
    cout << x << endl;
    return demo;
}


/* 指向重载函数的指针　*/
void ff(vector<double> vec)
{
    cout << "ff(vector) func" << endl;
}

void ff(unsigned int x)
{
    cout << "ff(unsigned int) func" << endl;
}

int main() {

    pfunc  p;
    p = 0; // 表示指针变量未进行初始化
    p = &lengthCompare;

    cout << lengthCompare("hello", "function") << endl;
    cout << p("hello", "world") << endl;

    pfunc p1;
    p1 = &func;
    funcPointerTest(p1);

    /* Ｃ与Ｃ＋＋中函数名就是指向函数地址的指针　C与C++中函数名就是指向函数地址的指针　*/
    funcPointerTest(func);

    int a= 5;
    int *pa;
    cout << ff(2)(&a, a) << endl;

    /* 指向重载函数的指针　*/
    /* 指向重载函数的指针所指向的函数必须有一个函数与它精确匹配　*/
    void (*pfh1) (unsigned int) = &ff;
    void (*pfh2) (vector<double>) = &ff;

    unsigned int ub;
    vector<double> ad;

    pfh1(ub);
    pfh2(ad);
    return 0;
}
```

