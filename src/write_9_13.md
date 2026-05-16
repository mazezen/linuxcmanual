# write

write（写入文件）

相关函数：read，open，close，lseek，fcntl

表头文件：#include <unistd.h>

定义函数：ssize_t write(int fd, const void *buf, size_t count);

函数说明：write()用来将参数buf所指向的内存中的数据写入参数fd所指向的文件中。参数count为要写入的字节数。实际写入的字节数可能会小于count。

返回值：如果成功返回实际写入的字节数，如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符或不可写。 EFAULT：参数buf指向的内存空间不可访问。 EINTR：调用被信号中断。 EIO：发生I/O错误。 ENOSPC：磁盘空间不足。

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
    char buf[] = "Hello, World!";
    fd = open("/tmp/test.txt", O_CREAT | O_RDWR, 0777);
    if (fd != -1)
    {
        write(fd, buf, sizeof(buf) - 1);
        close(fd);
    }
}
```