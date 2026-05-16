# fsync

fsync（将缓冲区数据写入磁盘）

相关函数：sync，write

表头文件：#include <unistd.h>

定义函数：int fsync(int fd);

函数说明：fsync()用来将参数fd所指向的文件的所有缓冲区数据写入磁盘。该函数会等待数据写入完成才返回。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符。 EIO：发生I/O错误。

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
        write(fd, "test", 4);
        fsync(fd);
        /* 将数据写入磁盘 */
        close(fd);
    }
}
```