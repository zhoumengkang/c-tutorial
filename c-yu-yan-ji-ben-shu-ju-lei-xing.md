# C语言基本数据类型

## 基本数据类型

> 下面的占用空间大小都是我电脑上的输出

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    printf("sizeof(char)\t%lu\n",sizeof(char));
    printf("sizeof(short)\t%lu\n",sizeof(short));
    printf("sizeof(int)\t%lu\n",sizeof(int));
    printf("sizeof(float)\t%lu\n",sizeof(float));
    printf("sizeof(double)\t%lu\n",sizeof(double));
    printf("sizeof(long)\t%lu\n",sizeof(long));

    return 0;
}
```

| 数据类型 | 说明 | 字节 |
| :--- | :--- | :--- |
| char | 字符型 | 1 |
| short | 短整型 | 2 |
| int | 整型 | 4 |
| float | 单精度浮点型 | 4 |
| double | 双精度浮点型 | 8 |
| long | 长整型 | 8 |

各类型还可以配合`unsigned`使用，mysql 中也经常看到

## 结合类型

`*`（指针），`[]`（数组）

## 自定义

`struct`，`enum`，`union`

## 空类型

`void`

