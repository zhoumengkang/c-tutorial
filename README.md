# 初识 C 语言

## 前言

该系列文章适合于一些有开发经验却不太懂 C 的程序员，比如大部分的 php 程序员。一些常规的名词（比如参数、函数、返回值）和一些通用的语法（比如 `if else`、`for 循环`等）不再任何说明和解释，大家自行搜索即可。 我希望我的这个系列的博客能帮大家对 C 语言基础做到一个穿针引线的作用，让大家能够上手 C 语言的开发，比如 php 程序员开发 php 扩展。

## 实验

新建文件`test1.c`

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
    printf("%s\n", "1111");
    return 0;
}
```

## 编译

```c
zhoumengkang@bogon:~/Downloads$ gcc test1.c -o test1
```

## 执行

```javascript
zhoumengkang@bogon:~/Downloads$ ./test1
1111
```

## 总结

我们从上往下看，有两个知识点需要学习。

### 头文件

我们发现我们在最开始使用了`#include <stdio.h>`这个文件，这是因为我们在使用的`printf`函数是在`stdio.h`里面定义的。我们可以通过

```bash
man 3 printf
```

来查阅

```bash
PRINTF(3)                  Linux Programmer's Manual                 PRINTF(3)

NAME
       printf,   fprintf,  sprintf,  snprintf,  vprintf,  vfprintf,  vsprintf,
       vsnprintf - formatted output conversion

SYNOPSIS
       #include <stdio.h>

       int printf(const char *format, ...);
       int fprintf(FILE *stream, const char *format, ...);
       int sprintf(char *str, const char *format, ...);
       int snprintf(char *str, size_t size, const char *format, ...);
```

如上所示，也就是说在使用这四个打印函数的时候都需要包含`<stdio.h>`。

1. `#include <xxx.h>` 系统头文件
2. `#include "xxx.h"` 自定义头文件

#### 认识 man 命令

顺便说下为什么是`man 3`，因为`man`查看手册的时候是分章节的，章节列表

| 章节编号 | 章节名称 | 章节主要内容 |
| :--- | :--- | :--- |
| 1 | General Commands | 用户在shell中可以操作的指令或者可执行文档 |
| 2 | System Calls | 系统调用的函数与工具等 |
| 3 | Sunroutines | C语言库函数 |
| 4 | Special Files | 设备或者特殊文件 |
| 5 | File Formats | 文件格式与规则 |
| 6 | Games | 游戏及其他 |
| 7 | Macros and Conventions | 表示宏、包及其他杂项 |
| 8 | Maintenence Commands | 表示系统管理员相关的命令 |

如果我输入的是

```bash
man printf
```

出来的结果和`man 1 printf`一样，查的是 shell 命令里面的`printf`

```text
PRINTF(1)                        User Commands                       PRINTF(1)

NAME
       printf - format and print data

SYNOPSIS
       printf FORMAT [ARGUMENT]...
       printf OPTION
...
```

man 是按照手册的章节号的顺序进行搜索的，所以我们在查C语言库函数的时候，记得使用`man 3 xxx`

### main 函数

main 函数是整个程序的入口，所以编译一个项目，main 函数有且仅有有几个。

> [https://www.zhihu.com/question/28360770](https://www.zhihu.com/question/28360770) main函数就是这个约定好的用户代码默认入口。 当然，只要你愿意，改成啥都行。比如你改成nomain，那么编译链接时就要指定入口了（同时指定不链接CRT的入口代码）。

```c
#include <stdio.h>
#include <stdlib.h>

int nomain(int argc, char const *argv[])
{
    printf("%s\n", "1111");
    exit(0);
}
```

```bash
gcc xxx.c -e nomain -nostartfiles
```

