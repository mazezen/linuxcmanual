# lseek

lseek（移动文件的读写指针）

相关函数：fseek，ftell

表头文件：#include <sys/types.h> #include <unistd.h>

定义函数：off_t lseek(int fd, off_t offset, int whence);

函数说明：lseek()用来移动参数fd所指向的文件的读写指针位置。参数offset为偏移量，参数whence为基准位置。 whence取值： SEEK_SET：从文件开头计算 SEEK_CUR：从当前位置计算 SEEK_END：从文件末尾计算

返回值：如果成功返回指针移动后的文件位置（相对于文件开头的字节数），如果出错则返回-1。

错误代码：EBADF：参数fd无效的文件描述符。 ESPIPE：参数fd指向管道或FIFO。

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
    off_t size;
    fd = open("/tmp/test.txt", O_RDONLY);
    if (fd != -1)
    {
        size = lseek(fd, 0, SEEK_END);
        /* 移到文件末尾 */
        printf("文件大小为%d字节\n", (int)size);
        close(fd);
    }
}
```