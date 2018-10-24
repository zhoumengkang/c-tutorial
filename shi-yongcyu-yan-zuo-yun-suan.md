# 使用C语言做运算

## 编写`test2.c`

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    int i = 2;
    int j = 3;

    int sum = i + j;

    printf("%d\n", sum);

    return 0;
}
```

## 编译运行

```javascript
zhoumengkang@bogon:~/Downloads$ gcc test2.c -o test2
zhoumengkang@bogon:~/Downloads$ ./test2
5
```

