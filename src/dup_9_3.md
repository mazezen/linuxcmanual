# dup

dup（复制文件描述符）

相关函数：open，close，fcntl，dup2

表头文件：#include <unistd.h>

定义函数：int dup(int oldfd);

函数说明：dup()用来复制参数oldfd所指向的文件描述符。复制成功后，新的文件描述符和原来的文件描述符共享同一个文件指针。dup()会使用当前最小的未使用文件描述符作为新的文件描述符。

返回值：如果成功返回新的文件描述符，如果出错则返回-1。

错误代码：EBADF：参数oldfd无效的文件描述符。 EMFILE：进程已打开的文件描述符数量已达上限。

范例：

```c
#include <unistd.h>
#include <stdio.h>
main()
{
    int newfd;
    newfd = dup(1);
    /* 复制标准输出 */
    if (newfd != -1)
        printf("复制成功，新文件描述符为%d\n", newfd);
}
```