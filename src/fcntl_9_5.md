# fcntl

fcntl（文件描述符控制）

相关函数：open，flock，lockf

表头文件：#include <unistd.h> #include <sys/types.h> #include <fcntl.h>

定义函数：int fcntl(int fd, int cmd, ... /* arg */);

函数说明：fcntl()用来操作文件描述符的一些属性。参数fd为文件描述符，参数cmd为操作命令。 支持的cmd命令： F_DUPFD：复制文件描述符 F_GETFD：获取文件描述符标志 F_SETFD：设置文件描述符标志 F_GETFL：获取文件状态标志 F_SETFL：设置文件状态标志 F_GETLK：获取文件锁信息 F_SETLK：设置文件锁 F_SETLKW：设置文件锁（阻塞） F_GETOWN：获取当前接收SIGIO信号的进程ID F_SETOWN：设置当前接收SIGIO信号的进程ID

返回值：如果成功则返回值取决于cmd命令，如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符。 EINVAL：参数cmd无效。

范例：

```c
#include <unistd.h>
#include <sys/types.h>
#include <fcntl.h>
#include <stdio.h>
main()
{
    int fd, flags;
    fd = open("/tmp/test.txt", O_RDONLY);
    if (fd != -1)
    {
        flags = fcntl(fd, F_GETFL);
        /* 获取文件状态标志 */
        if (flags & O_RDONLY)
            printf("只读模式\n");
        close(fd);
    }
}
```