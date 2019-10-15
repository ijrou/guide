#### return 和 exit 的区别

```c
#include <stdio.h>
int main(){
    return 0;        // 中断函数，返回整数
    printf("main\n");
}

void main(){
    return;        // 中断函数
}

#include<stdlib.h>
int main(){
    exit(416);
}
```



#### 声明和定义

```c
#include <stdio.h>

int my_strlen(char str[]);       // 函数声明
void test(int, int);      // 虽然没有定义test函数，但也可以声明，调用会出错

int main(){
    printf("len = %d\n", my_strlen("0123456789"));
    return 0;
}

int my_strlen(char str[]){        // 定义一个函数 my_strlen
    int i = 0;
    while(str[i] != '\0'){
        i++;
    }
    return i++;
}
```



取地址 &

int a;    int占4直接，在内存中占4个格（在内存中，以1个字节为单位分配内存的）；

每个字节在内存中都有标号，这个标号就是地址，也叫指针；即指针就是地址、地址就是指针；

&a  表示取a变量的首地址



指针也是一种数据类型：

```c
int * p;    // 声明一个指针p，p是专门用于保存地址的，其类型为 int *
p = 123;    // 正确，因为 p是变量，可以赋值啊
printf("%d\n", p);      // 输出 123
```

指针指向谁，就把谁的地址赋值给指针；

```c
int *p;
int a = 10;
p = &a;       // 将a的地址给指针p保存
prinf("%p, %p\n", p, &a);     // %p打印的地址，实际上是以16进制方式打印的；
// 输出：    0x7fffc2c77adc，0x7fffc2c77adc
```

>   直接操作指针变量本身没有任何意义，为啥？
>
>   int * p;
>
>   int a = 123;
>
>   p = &a;
>
>   p = 1234;         // 这个就相当操作变量而已，并没有意义；p本身就是保存内存地址的；
>
>   *p = 1234;       // *p相当于 a变量



上面知识说了很简单的了，可能并不全，但是该有的都有了，可以看书了

























