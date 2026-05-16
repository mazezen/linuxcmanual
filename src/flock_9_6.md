# flock

flock（文件加锁/解锁）

相关函数：fcntl，lockf

表头文件：#include <sys/file.h>

定义函数：int flock(int fd, int operation);

函数说明：flock()用来对参数fd所指向的文件进行加锁或解锁操作。参数operation为操作类型。 operation取值： LOCK_SH：共享锁（多个进程可同时持有） LOCK_EX：排他锁（只有一个进程可持有） LOCK_UN：解锁 LOCK_NB：非阻塞模式（与LOCK_SH或LOCK_EX组合使用）

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符。 EWOULDBLOCK：文件已被锁定（在非阻塞模式下）。

范例：

```c
#include <sys/file.h>
#include <unistd.h>
#include <stdio.h>
main()
{
    int fd;
    fd = open("/tmp/test.txt", O_RDWR);
    if (fd != -1)
    {
        if (flock(fd, LOCK_EX) == 0) /* 加排他锁 */
        {
            printf("加锁成功\n");
            /* 对文件进行操作 */
            flock(fd, LOCK_UN);
            /* 解锁 */
        }
    close(fd);
}
}
```