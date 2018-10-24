# C 语言内存初探

## 前言

在上课 [https://mengkang.net/987.html](https://mengkang.net/987.html) 中，我们在内存中申请了三个变量，这节课我们一起分析下它们在内存中的分布。

而我们习惯用16进制来表示内存地址，我当前电脑为64位的，所以内存的地址空间范围为`64个0`~`64个1`的跨度，但是我们只用48位，用十六进制表示就是

```javascript
0x000000000000
0xffffffffffff
```

### 为什么64位机指针只用48个位？

> [https://www.zhihu.com/question/28638698](https://www.zhihu.com/question/28638698) [https://stackoverflow.com/questions/6716946/why-do-64-bit-systems-have-only-a-48-bit-address-space](https://stackoverflow.com/questions/6716946/why-do-64-bit-systems-have-only-a-48-bit-address-space)

## 代码完善`test2.c`

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int i = 2;
    int j = 3;

    int sum = i + j;

    printf("%d\n", sum);

    // 增加内存输出测试
    printf("i addr is: %p\n",&i);
    printf("j addr is: %p\n",&j);
    printf("sum addr is: %p\n",&sum);

    return 0;
}
```

## 编译运行

```javascript
zhoumengkang@bogon:~/Downloads$ gcc test2.c -o test2
zhoumengkang@bogon:~/Downloads$ ./test2
5
i addr is: 0x7fff5ab02adc
j addr is: 0x7fff5ab02ad8
sum addr is: 0x7fff5ab02ad4
```

我们可以通过`sizeof`来查看每个变量占用的内存大小

```c
printf("i size\t%lu",sizeof(i)); // 4
```

由此可见`i`,`j`,`sum`的地址是连续的，而且是先分配的地址的值更大。 栈的内存分布就是自上而下的。 先到这里。

