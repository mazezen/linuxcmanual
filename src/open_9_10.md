# open

open（打开文件）

相关函数：creat，close，read，write，fcntl，lseek

表头文件：#include <sys/types.h> #include <sys/stat.h> #include <fcntl.h>

定义函数：int open(const char *pathname, int flags); int open(const char *pathname, int flags, mode_t mode);

函数说明：open()用来打开或创建文件。参数pathname为文件路径，参数flags为打开方式。 flags取值： O_RDONLY：只读模式 O_WRONLY：只写模式 O_RDWR：读写模式 O_CREAT：如果文件不存在则创建 O_EXCL：与O_CREAT一起使用时，如果文件已存在则返回错误 O_TRUNC：如果文件存在则将文件长度截断为0 O_APPEND：追加模式 参数mode为创建文件时的权限。open()返回最小的未用文件描述符。

返回值：如果成功返回文件描述符，如果出错则返回-1。

错误代码：EACCES：权限不足。 EEXIST：文件已存在且设置了O_CREAT和O_EXCL。 EINTR：调用被信号中断。 EISDIR：pathname指向目录。 EMFILE：进程已打开的文件描述符数量已达上限。 ENOENT：文件或目录不存在。

范例：

```c
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdio.h>
main()
{
    int fd;
    fd = open("/tmp/test.txt", O_CREAT | O_RDWR, 0777);
    if (fd != -1)
    {
        printf("打开文件成功，文件描述符=%d\n", fd);
        close(fd);
    }
else printf("打开文件失败\n");
}
```