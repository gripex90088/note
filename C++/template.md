### stack 

+ C

  ```cpp
  
  ```

+ C++

  ```cpp
  
  ```

  



```
#include <iostream>

using namespace std;

template <typename T>
class MyClass
{
public:
    MyClass();
    void push(T e);
    T pop();
    void clear();
    int size();
    
private:
};

int main()
{

}
```









```cp
#include <iostream>

using namespace std;

__attribute__((constructor)) void constructor_func()
{
    printf("before main function\n");
}

__attribute__((destructor)) void destructor_func()
{
    printf("after main function\n");
}

#define STACKMAXLENGTH 10
#define STACKINCREMENT 10

typedef int ElementType;

typedef struct
{
    int *base;
    int *top;
    int stackSize;
} myStack;

int InitStack(myStack *s)
{
    s->base = (ElementType *)malloc(STACKMAXLENGTH * sizeof(ElementType));
    if (!s->base) {
        return 0;
    }

    s->top = s->base = nullptr;
    s->stackSize = STACKINCREMENT;
}

int Push(myStack *s, ElementType e)
{
    if (s->top - s->base >= STACKMAXLENGTH) {
        s->base = (ElementType *)realloc(s->base, (s->stackSize + STACKINCREMENT) * sizeof(ElementType));
        if (!s->base) {
            return 0;
        }
    }

    *s->top++ = e;
}

ElementType Pop(myStack *s)
{
    return *--(s->top);
}

int ClearStack(myStack *s)
{
    s->top = s->base;
}

int StackSize(myStack s)
{
    return (s.top - s.base);
}

int DestoryStack(myStack *s)
{
    free(s->base);
    s->top = s->base;
    s->stackSize = 0;
}

template <typename T>
class Stack
{
public:
    Stack(int len);
    void push(T s);
    void pop(T *s);
    bool isNull();
    bool isFull();
    int stackSize();
    void destoryStack(T *s);
    void clearStack();
    ~Stack();

private:
    T *base;
    int top;
    int stack_max_length;
};

template <typename T>
Stack<T>::Stack(int len) : stack_max_length(len)
{
    base = new T(stack_max_length);
    top = -1;
}

template <typename T>
int Stack<T>::stackSize()
{
    return top + 1;
}

template <typename T>
void Stack<T>::push(T val)
{
    if (true == isFull()) {
        cout << "Stack is full" << endl;
        return;
    }

    /* top++会执行top取值之后进行＋1,  ++top会进行＋１赋值给top再取值, 所以如果从top从-1开始，top++将取arr[-1]位置的值 */
    base[++top] = val;
}

template <typename T>
void Stack<T>::pop(T *s)
{
    if (true == isNull()) {
        cout << "Stack is null" << endl;
        return;
    }
    *s = base[top--];
}

template <typename T>
void Stack<T>::destoryStack(T *s)
{
}

template <typename T>
Stack<T>::~Stack<T>()
{
    delete base;
    base = nullptr;
    cout << "destructor" << endl;
}

template <typename T>
void Stack<T>::clearStack()
{
    top = -1;
}

template <typename T>
bool Stack<T>::isNull()
{
    return (top <= 0) ?  true : false;
}

template <typename T>
bool Stack<T>::isFull()
{
    return (top >= stack_max_length) ? true : false;
}

int main()
{
    Stack<char> s(10);
    s.push('a');
    s.push('b');
    s.push('c');

//    return 0;
    char e;
    s.pop(&e);
    cout << e << endl;

    s.pop(&e);
    cout << e << endl;

    s.pop(&e);
    cout << e << endl;

    int a[] = {1,2,3,4,5,6};
//    int li = 0;
    int lj = 0;
//    int ri = 5;
//    int rj = 5;
//    cout << a[li++] << endl;
//    cout << "[li++]" << li << endl;

    cout << a[++lj] << endl;
    cout <<"[++li]" << lj << endl;

//    cout << a[ri--] << endl;
//    cout << a[--rj] << endl;

    for (int i = 0; i < 15; i++) {
        s.push('a');
        cout << "push size " << s.stackSize() << endl;
     }

    for (int i = 0; i < 15;  i++) {
        s.pop(&e);
        cout << "pop " << e << " size " <<  s.stackSize() << endl;
    }
    return 0;
}
```

