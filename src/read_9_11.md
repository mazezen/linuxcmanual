# read

read（从文件读取数据）

相关函数：write，open，close，lseek，fcntl

表头文件：#include <unistd.h>

定义函数：ssize_t read(int fd, void *buf, size_t count);

函数说明：read()用来从参数fd所指向的文件中读取数据，读取的数据存放到参数buf所指向的内存中。参数count为要读取的字节数。实际读取的字节数可能会小于count，例如在读取到文件末尾时。

返回值：如果成功返回实际读取的字节数，如果返回0表示已到达文件末尾，如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符或不可读。 EFAULT：参数buf指向的内存空间不可访问。 EINTR：调用被信号中断。 EIO：发生I/O错误。

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
    char buf[100];
    fd = open("/tmp/test.txt", O_RDONLY);
    if (fd != -1)
    {
        int n = read(fd, buf, sizeof(buf));
        if (n > 0)
            write(STDOUT_FILENO, buf, n);
        close(fd);
    }
}
```