#####　动态数组

猎豹32

```cpp
#include <iostream>

using namespace std;

class Dog
{

};

int main()
{
    int *p = (int *)malloc(10 * sizeof(int));

    if (p != NULL) {
        cout << "(malloc)Create dynamic array success" << endl;
    }

    int *np = new int[10];
    if (np != nullptr) {
        cout << "(new)Create dynamic array success" << endl;
    }
    
    free(p);
    p = NULL;

    delete []np;
    np = nullptr;

    /* 不进行初始化　*/
    int *pa1 = new int[10];

    /* 默认的构造函数进行初始化 */
    string *pstr = new string[10];

    /* 使用Ｄｏｇ默认的构造函数初始化　*/
    Dog *pDog = new Dog;

    /* 初始化　0 */
    int *pa2 = new int[10]();
    cout << *(pa2+2) << endl;

    return 0;
}
```

