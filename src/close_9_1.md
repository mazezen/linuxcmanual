# close

close（关闭文件）

相关函数：open，fcntl，shutdown，unlink，fclose

表头文件：#include <unistd.h>

定义函数：int close(int fd);

函数说明：close()用来关闭参数fd所指向的文件。当文件关闭后，该文件描述符可以被重新使用。所有与文件相关的记录锁也会被移除。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符。

范例：

```c
#include <unistd.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
main()
{
    int fd;
    fd = open("/tmp/test.txt", O_CREAT | O_RDWR, 0777);
    if (fd != -1)
    {
        printf("打开文件成功\n");
        close(fd);
    }
else printf("打开文件失败\n");
}
```