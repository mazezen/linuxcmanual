# creat

creat（创建文件）

相关函数：open，close

表头文件：#include <sys/types.h> #include <sys/stat.h> #include <fcntl.h>

定义函数：int creat(const char *pathname, mode_t mode);

函数说明：creat()用来创建一个新文件。参数pathname为要创建的文件路径，参数mode为文件的权限。creat()等价于open(pathname, O_CREAT | O_TRUNC | O_WRONLY, mode)。如果文件已存在，则会清空文件内容。

返回值：如果成功返回文件描述符，如果出错则返回-1。

错误代码：EACCES：权限不足。 EEXIST：文件已存在且设置了O_EXCL。

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
    fd = creat("/tmp/test.txt", 0755);
    if (fd != -1)
    {
        printf("创建文件成功\n");
        close(fd);
    }
else printf("创建文件失败\n");
}
```