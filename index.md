# this a decription of storage duration    
![banner](https://cdn.pixabay.com/photo/2021/02/28/11/00/moe-6056901_640.png)


在 C++ 中，存储期限（storage duration）主要有以下几种：

1. **自动存储期限**（Automatic Storage Duration）：局部变量默认的存储期限，通常在函数或代码块内定义。变量在进入该作用域时分配内存，离开作用域时自动销毁。

2. **静态存储期限**（Static Storage Duration）：全局变量、静态变量及静态成员变量的存储期限。它们在程序开始时分配内存，直到程序结束时才被销毁。

3. **动态存储期限**（Dynamic Storage Duration）：通过动态内存分配（如使用 `new`）创建的对象，内存会在使用 `delete` 时释放。

### 局部变量的默认存储期限

局部变量的默认存储期限是**自动存储期限**。这意味着它们的生命周期仅限于它们所在的函数或代码块。

### 改变局部变量的存储期限

要改变局部变量的存储期限，可以使用 `static` 关键字。例如：

```cpp
#include <iostream>

void example() {
    static int count = 0; // count 是静态局部变量
    count++;
    std::cout << count << std::endl;
}

int main() {
    example(); // 输出: 1
    example(); // 输出: 2
    example(); // 输出: 3
    return 0;
}
```

在这个例子中，`count` 是一个静态局部变量，尽管它在 `example` 函数中定义，但它的生命周期持续到程序结束，因此在多次调用时，它的值会保留。

如果需要动态存储期限的局部变量，可以使用 `new` 关键字：

```cpp
#include <iostream>

void example() {
    int* p = new int(5); // 动态分配内存
    std::cout << *p << std::endl;
    delete p; // 使用完后释放内存
}

int main() {
    example();
    return 0;
}
```

在这个例子中，`p` 指向动态分配的内存，生命周期由程序员控制，需要手动释放。 
``` c
extern int global_var; //变量的声明      
```
- [x] 当使用static修饰变量时 会将作用域限制在当前文件 
